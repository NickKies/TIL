# maven의 이해

### 1. 메이븐 사용 목적

 1. **빌드**

    소스 코드를 컴파일 하고, 패키지 생성을 위한 바이너리 파일 생성

2. **패키지**

   배포를 위한 파일을 생성

3. **테스트**

   단위 테스트 수행

4. **리포트**

   빌드 수행에 대한 결과를 기록하고, 분석

5. **배포**

   로컬 혹은 원격에 빌드 내용 배포



### 2. 메이븐 설정 파일(pom.xml)설명	

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
	
	<!-- 기본설정 -->
	<modelVersion>4.0.0</modelVersion> 			<!-- POM 모델의 버전-->
	<groupId>kr.or.connect.guestbook</groupId>	<!-- 조직의 고유 id-->
	<artifactId>guestbook</artifactId>			<!-- groupId 내의 프로젝트 고유 식별 id-->
	<packaging>war</packaging>					<!-- 프로젝트 패키징 방식-->
	<version>0.0.1-SNAPSHOT</version>			<!-- 프로젝트의 버전, 접미사로 SNAPSHOT 사용가능-->
	<name>guestbook Maven Webapp</name>
	<url>http://maven.apache.org</url>
	
	<!-- 프로퍼티 설정 -->
	<!-- pom 내에서 사용할 프로퍼티를 아래처럼 설정한 경우, ${spring.version} 같은 표현으로 사용가능하다 -->
	<properties>
		<jdk-version>1.8</jdk-version>
		<source-encoding>UTF-8</source-encoding>
		<resource-encoding>UTF-8</resource-encoding>
		<spring.version>4.3.5.RELEASE</spring.version>
		<!-- jackson -->
		<jackson2.version>2.8.6</jackson2.version>
	</properties>
	
	<!-- 저장소 설정 -->
	<!-- 외부 프로젝트 사용이 필요한 경우, 해당 프로젝트가 포함되어 있는 저장소의 주소를 포함시킨다. -->
	<repositories>
		<repository>
			<id>central</id>
			<url>http://repo1.maven.org/meven2</url>
			<releases>
			<enabled>true</enabled>
			</releases>
		</repository>
	</repositories>
		
	<!--  의존성 설정 -->
	<!-- repository에 등록되어 있는 외부의 프로젝트를 사용하고자 하는 경우 해당 프로젝트의 dependency를 쓴다. -->
	<dependencies>
        
		<!-- SPRING -->
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-context</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-jdbc</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-tx</artifactId>
			<version>${spring.version}</version>
		</dependency>
        
		<!-- MYSQL 
		<dependency>
			<groupId>mysql</groupId>
			<artifactId>mysql-connector-java</artifactId>
			<version>5.1.45</version>
		</dependency>
        
		 DATASOURCE
		<dependency>
			<groupId>org.apache.commons</groupId>
			<artifactId>commons-dbcp2</artifactId>
			<version>2.0</version>
		</dependency> -->

		<!-- Servlet JSP JSTL -->
		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>javax.servlet-api</artifactId>
			<version>3.1.0</version>
			<scope>provided</scope>
		</dependency>
		<dependency>
			<groupId>javax.servlet.jsp</groupId>
			<artifactId>javax.servlet.jsp-api</artifactId>
			<version>2.3.1</version>
			<scope>provided</scope>
		</dependency>
		<dependency>
			<groupId>jstl</groupId>
			<artifactId>jstl</artifactId>
			<version>1.2</version>
		</dependency>

		<!-- Jackson Module -->
		<dependency>
			<groupId>com.fasterxml.jackson.core</groupId>
			<artifactId>jackson-databind</artifactId>
			<version>${jackson2.version}</version>
		</dependency>
		<dependency>
			<groupId>com.fasterxml.jackson.datatype</groupId>
			<artifactId>jackson-datatype-jdk8</artifactId>
			<version>${jackson2.version}</version>
		</dependency>

		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>3.8.1</version>
			<scope>test</scope>
		</dependency>
        
        <!-- https://mvnrepository.com/artifact/org.springframework/spring-jdbc -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-jdbc</artifactId>
            <version>4.3.16.RELEASE</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/org.mybatis/mybatis -->
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis</artifactId>
            <version>3.4.5</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/org.mybatis/mybatis-spring -->
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis-spring</artifactId>
            <version>1.3.0</version>
        </dependency>
    </dependencies>
	
	<!-- 플러그인 저장소 설정 -->
	<!-- 플러그인을 사용하고자 하는 경우 해당 프럴그인이 저장되어 있는 저장소를 포함시킨다. -->
	<pluginRepositories>
		<pluginRepository>
			<id>central</id>
			<name>Maven Plugin Repository</name>
			<url>http://repo1.maven.org/maven2</url>
			<layout>default</layout>
			<snapshots>
				<enabled>false</enabled>
			</snapshots>
			<releases>
				<updatePolicy>never</updatePolicy>
			</releases>
		</pluginRepository>
	</pluginRepositories>
	
	<!-- 리포팅 설정 -->
	<!-- 외부 플러그인을 사용하여 코드에 대한 여러가지 검사를 수행할 수 있다. -->
	<!-- ex) checkstyle, codelnspection check등 -->
	<reporting>
		<plugins>
		<!-- maven-pmdplugin은 codelnspection을 체크하는 플러그인이다 -->
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-pmd-plugin</artifactId>
				<version>2.3</version>
				<configuration>
					<linkXref>true</linkXref>
					<sourceEncoding>utf-8</sourceEncoding>
					<minimunTokens>100</minimunTokens>
					<targetJdk>1.5</targetJdk>
				</configuration>
			</plugin>
		</plugins>
	</reporting>
	
<!-- 프로파일 설정
	환경에 다라 세팅을 다르게 할 필요가 있을 때 사용한다. 가령 local 환경과 서버 환경에서의
 배포 경로를 다르게 한다거나, 테스트를 하려는 경우 maven.test.skip 변수를 false로 지정한다는 
등의 세팅이 가능하다. mvn -Plocal처럼 메이븐 실행시 프로파일 선택이 가능하다. -->
	<profiles>
		<profile>
			<id>local</id>
			<activation>
				<activeByDefault>true</activeByDefault>
			</activation>
			<properties>
				<env>local</env>
				<deploy-dir>target/m2e-wtp/web-resources</deploy-dir>
			</properties>
		</profile>
		<profile>
			<id>test</id>
			<properties>
				<env>alpha</env>
				<deploy-dir>target/classess</deploy-dir>
				<maven.test.skip>false</maven.test.skip>
			</properties>
		</profile>
		<profile>
			<id>alpha</id>
			<properties>
				<env>alpha</env>
				<deploy-dir>target/classess</deploy-dir>
			</properties>
		</profile>
	</profiles>				
	
	<!-- 빌드설정
		빌드시 사용하고자 하는 플러그인 등록, 소스 및 자원의 경로 지정 등을 설정한다. -->
	<build>
		<finalName>guestbook</finalName>
		
		<!-- 플러그인 설정 -->
		<plugins>
<!-- maven-resources-plugin을 사용하면 ,필터링 사용이 가능한데 아래에서는 filtering이 true인 경우
해당 프로파일에 설정된 변수인 "env"의 경로에 있는 리소스를 사용하게 된다. 이를 활용해 환경에 따라
다른  DB를 보게하거나, 로그 출력 방식을(에러 레벨) 다르게 잡을 수 있다. -->
			<plugin>	
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-resources-plugin</artifactId>
				<version>2.6</version>
				<configuration>
					<encoding>UTF-8</encoding>
					<nonFilteredFileExtensions>
                        <!--p12 확장자를 가진 파일은 필터링 제외 -->
						<nonFilteredFileExtension>p12</nonFilteredFileExtension>         
					</nonFilteredFileExtensions>
				</configuration>
			</plugin>	
			
<!-- maven-clean-plugin 사용 목적은 빌드시 생성되는 파일들을 지우는 것이다. clean gaol실행시, 디폴트로 
project.build.directory, project.build.outputDirectory, project.build.outputDirectory, 
project.build.testOutputDirectory, project.reporting.outputDirectory를 삭제한다.
추가적으로 아래에 filesets 설정을 통해 삭제 대상 추가 및 제외가 가능하다 -->
			<plugin>
				<artifactId>mavenn-clean-plugin</artifactId>
				<version>2.5</version>
				<configuration>
					<fileset>
						<directory>${deploy-dir}/WEB-INF/lib</directory>
						<includes>
							<include>*.jar</include>
						</includes>
					</fileset>
					<fileset>
						<directory>${deploy-dir}/WEB-INF/classes</directory>
						<includes>
							<include>**/*</include>
						</includes>
					</fileset>
					<fileset>
						<directory>${deploy-dir}/WEB-INF</directory>
						<includes>
							<include>web.xml</include>
						</includes>
					</fileset>
				</configuration>
			</plugin>
			
<!-- maven-compiler-plugin은 컴파일시 사용되는 플러그인이다. 사용하고 잇는 jdk 버전을 넣어준다 -->
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.6.1</version>
				<configuration>
					<source>${jdk-version}</source>
					<target>${jdk-version}</target>
					<encoding>${source--encoding}</encoding>
				</configuration>
			</plugin>
			
<!-- maven-war-plugin은 package 실행시 war 파일을 생성하는 과정을 관장한다.
아래의 설정을 통해 webResources>reource>directory의 파일들을 targetPath인 WEB-INF 디렉토리에 복사한다 -->
            <plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-war-plugin</artifactId>
				<version>2.4</version>
				<configuration>
					<webXml>${deploy-dir}/WEB-INF/web.xml</webXml>
					<encoding>UTF-8</encoding>
					<overwite>true</overwite>
					<filters>
						<filter>src/main/resources-${env}/build.properties</filter>
					</filters>
					<webResources>
						<resource>
							<directory>src/main/webapp/WEB-INF</directory>
							<includes>
								<include>web.xml</include>
							</includes>
							<targetPath>WEB-INF</targetPath>
							<filtering>true</filtering>
						</resource>
					</webResources>
				</configuration>
			</plugin>	
			
			<!-- maven-surefire-plugin은 test시, 유닛 테스트를 실행하는데 사용된다 -->
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-surefire-plugin</artifactId>
				<version>2.4.2</version>
				<configuration>
					<testFailureIgnore>true</testFailureIgnore>
					<excludes>
						<exclude>**/integration/**/*Test.java</exclude>
					</excludes>
				</configuration>			
			</plugin>
		</plugins>
		
		<!-- 리소스 경로 지정
			applicationContext.xml파일과 같은 설정 파일의 경로를 지정한다. -->
		<resources>
			<!-- 공통 사용 리소스 -->
			<resource>
				<filtering>true</filtering>
				<directory>src/main/resources</directory>
				<includes>
					<include>*.xml</include>
					<include>**</include>
				</includes>
			</resource>
			
			<!-- 환경별 사용 리소스 -->
			<resource>
				<filtering>true</filtering>
				<directory>src/main/resources--${env}</directory>
			</resource>
		</resources>	
		
		<!-- maven-resources-plugin을 적용하고, 아래의 필터를 적용하면 빌드 시점에 <resource>중 
필터링 true인 것들을 대상으로 ${..}변수를 찾아 할당하게 된다. -->
		<filters>
			<filter>src/main/resources-${env}/build.properties</filter>
		</filters>
	</build>
</project>
```


<환결 별로 사용 프로퍼티 나누기>

	1. bulid > plugins에 meven-resources-plugin 적용
 	2. profile에 각 프로필별로 환경 변수로 쓸 값 지정(위에서는 ${env})
 	3. build>fiters에 ${env}를 포함한 프로퍼티 파일 경로 설정
 	4. build>resources에 리소스 filtering을 true로 하고, 프로퍼티의 변수들이 적용될 값들이 적혀있는 설정 파일 지정
 	5. maven-war-plugin을 통해 패키지시, 환경 별 리소스 파일 복사되도록 설정



### 3. 메이븐 라이프 사이클

메이븐은 여러 goal들이 순차적으로 실행되는 구조라고 볼 수 있다.

디딤돌을 밟으며 강을 건너는 것과 같다.

다섯번째 돌에 가려면 1~4번째 돌을 순차적으로 지나게 되는 것이다.

이러한 메이븐의 대략적 디폴트 라이프 사이클은 아래와 같다.



validate - 정상 여부 및 빌드 가능 여부 판단

initalize - 빌드 상태 초기화, 작업 디렉토리 생성

complie - 프로젝트 소스 코드 컴파일

test - 단위 테스트 수행

package - 컴파일 된 코드를 war 등 설정에 따라 패키징

install - 생성한 패키지를 로컨 저장소에 설치

deploy - 생성한 패키지를 원격 저장소에 설치



그리고 clean goal의 경우 따로 노는데 그 이유는 다른 라이프 사이클과 엮이지 않고, 단순히 빌드 결과물을 지워주는 작업을 하기 때문이다.

ex) mvn clean compile - Plocal - DtestSkip=true