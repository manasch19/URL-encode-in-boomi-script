# URL-encode-in-boomi-script

This code is used encode the incoming data to a URL encoded format using a data process shape

import java.util.Properties;
import java.io.InputStream;
import java.net.URLEncoder;

String stringToEncode = '';
String encodedString = '';

for( int i = 0; i < dataContext.getDataCount(); i++ ) 
{
    InputStream is = dataContext.getStream(i);
    def inputDataString = is.getText("UTF8");
    Properties props = dataContext.getProperties(i);
    encodedString = URLEncoder.encode(inputDataString, "UTF-8");
    InputStream stream = new ByteArrayInputStream(encodedString.getBytes());
    dataContext.storeStream(stream, props);
}





Input looks like:..

![image](https://user-images.githubusercontent.com/97012694/201964814-a0439418-60e6-4377-ad43-57b28f3ab72b.png)


and the output will be looking like..

![image](https://user-images.githubusercontent.com/97012694/201965037-d60b0f81-dcfd-4568-bc1a-cb804927eb9e.png)
