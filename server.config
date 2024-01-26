
Lambda Code:
----------------
import json
from time import sleep
from json import dumps
from kafka import KafkaProducer
import json

topic_name='sensor_data_consumer'
producer = KafkaProducer(bootstrap_servers=['{}:9092']
,value_serializer=lambda x: dumps(x).encode('utf-8'))

def lambda_handler(event, context):
    # TODO implement
    print(event)
    payload_part=json.loads(event['body'])['payload']
    for i in payload_part:
        acc_x=i['values']['x']
        acc_y=i['values']['y']
        acc_z=i['values']['z']
        capture_time=i['time']
        data={"acc_x":acc_x,"acc_y":acc_y,"acc_z":acc_z,"capture_time":capture_time}
        print(data)
        producer.send(topic_name, value=data)
    producer.flush()
    return {
        'statusCode': 200,
        'body': json.dumps('Hello from Lambda!')
    }
   
