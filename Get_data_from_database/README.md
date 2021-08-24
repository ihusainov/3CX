```bash
CONCATENATE("select isnull((\r\nSELECT extension \r\nFROM KI \r\nWHERE SUBSTRING(phone_client, 2, 10)=RIGHT(",session.ani,", 10)\r\n), '-1')")

Query: select isnull((\r\nSELECT extension \r\nFROM KI \r\nWHERE SUBSTRING(phone_client, 2, 10)=RIGHT(79641234567, 10)\r\n), '-1')
```
