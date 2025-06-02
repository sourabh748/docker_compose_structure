**jmx Query string**
- ***http://<name_node>:<port>/jmx?qry=Hadoop:service=NameNode,name=NameNodeInfo***
- ***http://localhost:5000/jmx?qry=Hadoop:service=NameNode,name=NameNodeInfo***

```python
    import requests
    import json
    
    info = requests.get('http://<name_node>:<port>/jmx?qry=Hadoop:service=NameNode,name=NameNodeInfo')

    live_data_nodes = json.loads(info_json['beans'][0]['LiveNodes'])

    for data_node, info_ in live_data_nodes.items():
        #getting ipaddress of datanodes
        ip_address = info_['infoAddr'].split(':')[0]
        data_host_name = data_node.split(':')[0]
        print(f'{data_host_name} {ip_address}')
```