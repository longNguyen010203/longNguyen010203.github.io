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


### 4.3. 