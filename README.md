# Spring Boot On SSL With Docker
This project is about configuring Spring Boot application to work on HTTPS. For this demo
purpose I added configuration for Docker service so this application works inside docker container.

## SSL Configuration
For configuring SSL first you have to generate self-signed certificate using `keystore` command and then
in `application.yml` to bind with ssl-specific properties. So let's get started.

* Step 1: Generating SSL certificate using keystore command.
```
keytool -genkeypair -alias your_alias -keyalg RSA -keysize 2048 -storetype PKCS12 -keystore your_file_name.p12 -validity 3650
```
After executing, this command will prompt you for additional information.

* Step 2: Configuring SSL specific properties inside application.yml.
1. Open application.yml file and find `server.ssl-*` properties
2. **key-store** property asks for path of your .p12 file
3. **key-alias** property asks for alias that you use in step 1
4. **key-store-type** property is type of your certificate that you use in step 1
5. **key-store-password** property asks for password that you use in step 1

**NOTE:** Certificate file (.p12) is located in `resource/keystore`. Please put your certificate inside.

## Packaging and running
For running application you have to follow the provided steps.

1. Open terminal and navigate to working directory
2. Run command: `mvn clean package -DskipTests`
3. Run command: `docker-compose up -d`
4. Wait for application to run.

## Checking container logs
To check your container logs type the following command:
```
docker logs -f spring-boot-ssl
```

## Checking application running state
To check if your application is running correctly type in browser:
```
https://localhost:8443/api/test
```
The output should be: `Working well!`.

## Author
Heril Muratović  
Software Engineer  
<br>
**Mobile**: +38269657962  
**E-mail**: hedzaprog@gmail.com  
**Skype**: hedza06  
**Twitter**: hedzakirk  
**LinkedIn**: https://www.linkedin.com/in/heril-muratovi%C4%87-021097132/  
**StackOverflow**: https://stackoverflow.com/users/4078505/heril-muratovic


