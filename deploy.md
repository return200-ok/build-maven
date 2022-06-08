Publish Artifacts from a Maven Project to Nexus Repository
1: Open file m2 config settings.xml
~/.m2 ❯ pwd                                                                                                   took 12m 37s  system at 11:21:43
/home/caolv/.m2
~/.m2 ❯ vim settings.xml
<settings>
    <servers>
        <server>
            <id>my-repo</id>
            <username>secret</username>
            <password>N8dL9NKPwdPiYH7</password>
        </server>
    </servers>
</settings>

2:  Add this to file pom.xml
	<groupId>com.example</groupId>
	<artifactId>demo</artifactId>
	<version>0.0.1</version>
	<distributionManagement>
	<repository>
		<id>my-repo</id>
		<name>java-web-app-releases</name>
		<url>http://192.168.3.45:8081/repository/biplus-maven-release/</url>
	</repository>
	<snapshotRepository>
		<id>my-repo</id>
		<name>java-web-app-snapshots</name>
		<url>http://192.168.3.45:8081/repository/biplus-maven-snapshot/</url>
	</snapshotRepository>
	</distributionManagement>

Lưu ý: id phải trùng với phần cấu hình trong file setttings.xml

Có 2 loại repo: releases và snapshot, cần đặt version đúng cho từng loại repo

 

3. Deploy artifacts to Nexus 
mvn deploy