AWS \[Metric Streams\](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Metric-Streams.html) is a service provided by Amazon Web Services (AWS) that enables real-time streaming of AWS CloudWatch metrics.  
  
Configure CloudWatch using the AWS Console :

\## Create a new Kinesis Data Firehose Delivery Stream

1.  Sign in to the AWS Management Console and open the Kinesis console at \[https://console.aws.amazon.com/kinesis\](https://console.aws.amazon.com/kinesis).
2.  Choose **Data Firehose** in the navigation panel.
3.  Choose **Create delivery stream**.
4.  The stream’s Source should be **Direct PUT** and Destination set to **HTTP Endpoint** with the following details:  
    **Kinesis endpoint:** https://\`{ACCOUNT-UID}\`.middleware.io/v1/metrics/cloudwatch  
    **API Key:** Enter your Middleware API key.
5.  In the Backup settings, select an S3 backup bucket to receive any failed events that exceed the retry duration.

Replace \`{ACCOUNT-UID}\` with the text in the URL (ex URL is "s05zpimz.middleware.io" , here s05zpimz is \`{ACCOUNT-UID}\`.) ## Create a new CloudWatch Metric Stream

1.  Open the CloudWatch AWS console at \[https://console.aws.amazon.com/cloudwatch/\](https://console.aws.amazon.com/cloudwatch).
2.  In the left navigation pane, choose **Metrics → Streams**.
3.  Click the **Create metric stream button**.
4.  Choose the **All namespaces** in the metric stream.
5.  Choose **Select an existing Firehose owned by your account**, and select the Firehose Delivery Stream you created earlier.
6.  Specify an **Output Format of OpenTelemetry 0.7**.
7.  Optionally, specify a name for this metric stream under **Metric Stream Name**.
8.  Choose **Create metric stream**.
