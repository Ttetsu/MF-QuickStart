# Introduction
  This guide will help you access MovingFeatures Server with python or java code.

## Python
  It will be Added later.

## Java
  - You have installed the JDK  (at least Java 8) . 
  - You have installed IntelliJ IDE.
  
### Get Token
**Create a New Project**  
  It will be Added later.
  
**Add jar lib**  
  We will provide you a jar lib to connect to our system(pntml-client-pwd-1.0.0.jar).

**Information confirm**  
  If your Informations like following:
  >For example
  >>| username | password | clientId | clientSecret |
  >>| ------------ | ------------- | ------------ | ------------ | 
  >>| dprt001 | 123456  | b72112cd-6d77-4204-9e6e-ffa4 | f72112cd-6d77-4204-9e6e-bbs3 |
  

**Create ApplicationStart.java**  
  Fill in the following code(Using Information above):
      
```
package jp.go.aist.dprt;

import java.io.IOException;

import org.springframework.http.ResponseEntity;
import jp.go.aist.dprt.model.AccessToken;
import jp.go.aist.dprt.model.MetadataQuery;
import jp.go.aist.dprt.service.LoginService;
import jp.go.aist.dprt.service.Map3DService;
import jp.go.aist.dprt.service.impl.LoginServiceImpl;
import jp.go.aist.dprt.service.impl.Map3DServiceImpl;

public class ApplicationStart {
	
	/**
	 * parameters
	 */
	public static final String username = "dprt001";
	public static final String password = "123456";
	public static final String clientId = "b72112cd-6d77-4204-9e6e-ffa4";
	public static final String clientSecret = "f72112cd-6d77-4204-9e6e-bbs3";
	
	public static void main(String[] args) {
		//start
		try {
			LoginService aLoginService = new LoginServiceImpl();
			AccessToken token = aLoginService.getToken(username, password);
			 
			 Map3DService map3dService = new Map3DServiceImpl();
			 MetadataQuery query = new MetadataQuery();
			 query.setTags("Test");
		     ResponseEntity<String> metadata = map3dService.getMetadata(token, query);
		     System.out.println("Get Metadata End : " + metadata.toString());
		} catch (IOException e) {
			e.printStackTrace();
		}

	}
}

```
** Run ApplicationStart** 

Right-click  And Run ApplicationStart  
Then you will get the catalog of map3d.
  
  