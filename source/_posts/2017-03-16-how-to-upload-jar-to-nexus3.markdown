---
layout: post
title: "How to upload jar to Nexus3?"
date: 2017-03-16 19:42:48 +0800
comments: true
categories: Nexus Nginx
---

# Prepare pom.xml 
	<project>
		<modelVersion>4.0.0</modelVersion>
		<groupId>oracle</groupId>
		<artifactId>ojdbc6</artifactId>
		<version>1.0</version>
	</project>


1. Upload pom.xml 
`curl -v -u admin:<nexus-passwd> --upload-file pom.xml http://<host>/nexus/repository/maven-releases/oracle/ojdbc6/1.0/ojdbc6-1.0.pom`


1. Upload jar 
`curl -v -u admin:<nexus-passwd> --upload-file ojdbc6-1.0.jar http://<host>/nexus/repository/maven-releases/oracle/ojdbc6/1.0/ojdbc6-1.0.jar`


# Exception

Resp: HTTP/1.1 413 Request Entity Too Large

	vi /etc/nginx.conf
	# added the following lines in http section
	client_max_body_size 16M;
	client_body_buffer_size 128K;

	nginx -s reload

