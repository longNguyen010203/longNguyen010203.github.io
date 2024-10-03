---
weight: 2
title: "Workshop - 2: 👷 Stream Processing with Amazon Kinesis 🌊"
date: 2024-09-22T15:58:26+08:00
lastmod: 2024-09-22T15:58:26+08:00
draft: false
author: "Long Nguyễn"
authorLink: "https://www.facebook.com/profile.php?id=100013806768346"
description: "Setup and build infrastructure for stream processing with Amazon Kinesis on Amazon Web Services (AWS)."
resources:
- name: "featured-image"
  src: "aws-cloud-img.jpg"
- name: "featured-image-preview"
  src: "featured-image-preview.webp"

tags: ["content", "Markdown"]
categories: ["documentation"]

lightgallery: true

toc:
  auto: false
math:
  enable: true
---

Find out how to create and organize your content quickly and intuitively in **FeelIt** theme.

<!--more-->

## 1. 🌍 Introduction

### 1.1. Amazon Lambda

### 1.2. Amazon CloudWatch

### 1.3. Amazon Kinesis Data Streams

### 1.4. Amazon Kinesis Data Firehose


## 2. 📊 Present the problem

## 3. 🔦 Architecture
![Architecture](stream_processing_architecture.drawio.png "Stream Processing with Amazon Kinesis Diagram")

- 📦 Technology and Services:
  - `S3`
  - `Lambda`
  - `Kinesis Data Streams`
  - `Kinesis Data Firehose`
  - `CloudFormation`
  - `CloudWatch`
  - `IAM`


## 4. 📑 Preparation

### 4.1. Source Code

See source code details here: [GitHub](https://github.com/longNguyen010203/Stream-Processing-with-Amazon-Kinesis)

Download the source code to your local machine with the following command:
```bash
git clone https://github.com/longNguyen010203/Stream-Processing-with-Amazon-Kinesis.git
```

- **model/StockTrade.py** - The file contains the `StockTrade` object definition class containing the following properties: `tickerSymbol`, `tradeType`, `price`, `quantity`, `id`. Methods: `toJsonAsBytes`, `fromJsonAsBytes`,...
- **model/KinesisStream.py** - The file contains the class that defines the `KinesisStream` object with the properties: `kinesis_client`, `streamName` and methods: `put_record`, `get_records`,... to manipulate `Amazon Kinesis` through the [SDK for Python (Boto3)](https://docs.aws.amazon.com/code-library/latest/ug/python_3_kinesis_code_examples.html).
- **writer/StockTradeGenerator.py** - The file contains the class that defines the `StockTradeGenerator` object, which is responsible for generating data from existing data. More specifically, creating stock transactions. It has a `getRandomTrade` method, which returns a `StockTrade` object, a stock trade.
- **writer/StockTradesWriter.py** - The file contains the class that defines the `StockTradesWriter` object, this class defines the `sendStockTrade` method, which is responsible for sending data to `kinesis data streams`, acting as a `producer`.
- **processor/StockTradeReader.py** - The file contains the class that defines the `StockTradeReader` object, which defines the `getStockTrade` method, which is responsible for reading data from `kinesis data streams`, acting as a `consumer`.
- **processor/StockStatistic** - The file contains the class that defines the `StockStatistics` object, this class is responsible for statistics on collected transactions with the following statistics: `Most Popular Stock Count`,...
- **lambda/StreamLambda.py** - The file contains data transformation logic.


### 4.2. Initialize python virtual environment
Before creating the `virtual environment`, you need to install `Python`. If your computer does not have it, please visit [python.org](https://www.python.org/) to install it.
Next you need to download the `source code` by following the instructions above.
Then in the `Terminal` window, move to the `root` directory of the source code, specifically the `stream-processing-with-amz-kinesis` directory.

<div style="text-align: center;">
    <img src="./1.png" alt="Description" />
</div>

To create a `python virtual environment`, run the following command:
```bash
python3 -m venv .ws2-venv
```
{{< admonition >}}
You can name the `virtual environment` any way you want.
{{< /admonition >}}
<div style="text-align: center;">
    <img src="./2.png" alt="Description" />
</div>

Next to `activate` the `virtual environment`, run the following command:
```bash
source .ws2-venv/bin/activate
```
{{< admonition >}}
A sign that you have successfully activated the `virtual environment` is that the `virtual environment name` appears after the folder name.
{{< /admonition >}}
<div style="text-align: center;">
    <img src="./3.png" alt="Description" />
</div>


### 4.3. Install libraries and dependencies
The `requirements.txt` file in the `source code` contains the `libraries` and `dependencies` required for this `workshop`.
To install we run the following command:
```bash
pip install -r requirements.txt
```
<div style="text-align: center;">
    <img src="./4.png" alt="Description" />
</div>

To check if `libraries and dependencies` are installed, run the following command:
```bash
pip list
```
<div style="text-align: center;">
    <img src="./5.png" alt="Description" />
</div>
<div style="text-align: center;">
    <img src="./6.png" alt="Description" />
</div>

If your `terminal` window appears as above, you have successfully installed.

## 5. 📡 Setup Infrastructure
### 5.1. Create and Testing Kinesis Data Streams
#### 5.1.1. Create Kinesis Data Streams
In the search bar, enter the keyword `"kinesis"` and click to select the `kinesis service`.

![image](./1a.png)

In the `Kinesis service console`, select `Create Data Stream`.

![image](./2a.png)

In the `Data stream name` field, fill in `StockTradeStream`
{{< admonition >}}
You can give it any name you want.
{{< /admonition >}}

![image](./3a.png)

In the `Data stream capacity` section, we fill in `1` in the `Provisioned shards` field.

![image](./4a.png)

Finally, we choose `Create data stream` to create `kinesis data streams`.

![image](./5a.png)

In the `StockTradesWriter.py` and `StockTradeReader.py` files, we need to check the following parameters: `streamName`, `region_name`, `aws_access_key_id`, `aws_secret_access_key`. Board

![image](./6a.png)
![image](./7a.png)

You need to write down your correct `kinesis stream name`, write down the correct `region name` where you are using the service, and finally you need to fill in your `AccessKeys`, to make sure the stream works.

#### 5.1.2. Demo and Test Kinesis Data Streams
On your local machine, open two `terminal` windows, then navigate to the `root` directory (`stream-processing-with-amz-kinesis`) of the source code, then activate the `virtual environment` as instructed above. Then move the `Stock-Trade-Kinesis` folder to both windows with the following command:

```bash
cd Stock-Trade-Kinesis
```
![image](./terminal-1.png)

The `first Terminal window` represents the `Producer` who is responsible for `sending data` to `Kinesis Data Streams`, the `second Terminal window` represents the `Consumer` who is responsible for `multiplying data` from `Kinesis Data Streams`. To launch, run the following commands on two `Terminal` window:

```bash
python3 -m writer.StockTradesWriter
python3 -m processor.StockTradeReader
```

![image](./terminal-2.png)

Then we press `Enter` on each window.

<div style="max-width: 100%; text-align: center;">
    <video width="100%" controls>
        <source src="./producer_consumer_testing.webm" type="video/webm">
    </video>
</div>

We can see data being sent and received in `real time`, the `producer` `sends` immediately the `commsumer` `receives` it. That is the main effect of `Kinesis Data Streams`.


