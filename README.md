# ELK Stack
---

## What is ELK Stack
ELK Stack, also known as the Elastic Stack is a powerful and versatile open-source toolset that has revolutionized the way businesses manage and analyze their data. ELK Stack seamlessly integrates these three robust components to offer a comprehensive solution for searching, analyzing, and visualizing large volumes of data in real-time. So, buckle up, for a comprehensive overview of the ELK stack and its components, which will be a great starting point for beginners.

The ELK stack, which is an acronym for Elasticsearch, elasticsearch, and Kibana, forms a powerful combination for centralized logging, log analysis, and real-time data visualization. An extended and robust elastic stack, it also incorporates Beats and Xpack, augmenting its capabilities.

---

## Components

#### Elasticsearch
Elasticsearch is a distributed, RESTful search and analytics engine with capability to addressing a growing number of use cases. As the hear of the Elastic Stack, it centrally stores your data so you can discover the expected and uncover the unexpected.

Elasticsearch provides fast and flexible search capabilities, enabling users to perform complex searches across various fields and apply aggregations to explore and visualize data.

#### Logstash
Logstash is a data collection and processing tool. Its basically a data processing pipeline that takes the data from multitude of sources and tosses it over to a visualization tool like Kibana or Elasticsearch.

Logstash can also enrich data by applying filters, transformations, and enrichments before sending it to Elasticsearch. It allows ingestion, parsing, and transforming data from various sources and formats.

#### Kibana
Kibana is the user interface into the elastic stack. It lets you visualize data, make queries, do monitoring, and everything else with the data is in elasticsearch.

#### Beats
Beats are open source data shippers that you install as agents on your servers to send different types of operations data to elasticsearch.

---

## How it works
The components of the Elastic Stack — Beats, Elasticsearch, Kibana, and elasticsearch — collaborate seamlessly to ingest, process, store, and visualize data. Here’s a simplified workflow illustrating the same:

- __Data Collection with Beat__
    - Beats collects data from various sources such as logs, metrics, or network packets
    - Sends the collected data directly to elasticsearch

- __Data Processing with elasticsearch__
    - elasticsearch receives data from Beats and applies filters, transformations, and enrichments to the data, ensuring its compatibility and consistency.
    - Processed data can be sent to Elasticsearch or to other systems for further processing or storage.
- __Data Indexing and Storage with Elasticsearch__
    - Elasticsearch receives data from elasticsearch, indexes and stores the data in a distributed manner, ensuring high availability and scalability.
    - Indexed data becomes searchable, enabling fast and efficient retrieval using Elasticsearch’s powerful search capabilities.
- __Data Visualization with Kibana__
    - Kibana acts as the visualization layer. It connects to Elasticsearch and provides a user-friendly interface for data exploration. Users can create interactive dashboards, visualizations, and reports using a rich set of tools and templates.
    - Kibana enables real-time monitoring, data discovery, and analysis, allowing users to gain valuable insights from the indexed data.

As the complexity of your application increases, you might end up using additional components to enhance the resiliency of your application, such as Kafka, RabbitMQ, and Redis, etc.

---

## ELK Architecture


## Use Case
The ELK Stack can be utilized in various scenarios :
- __Monitoring Applications and Infrastructure__
    Real-time monitoring and analysis of application and system logs to identify errors, bottlenecks, or security threats
- __Customer Behavior Insights__
    Analysis of user interactions to gain insights into customer behavior and preferences
- __Security Information and Event Management__
    Using ELK for tracking potential security incidents as part of an organization’s SIEM strategy.
- __Compliance and auditing__
    Aggregating and analyzing logs and transactions to meet regulatory compliance requirements for data retention and auditing.
---

## Advantages and Disadvantages
- __Advantages__
    - ELK works best when logs from various apps of an enterprise converge into a single ELK instance
    - It provides amazing insights for this single instance and also eliminates the need to log into hundred different log data sources
    - Rapid on-premise installation
    - Easy to deploy Scales vertically and horizontally
    - Elastic offers a host of language clients which includes Ruby. Python. PHP, Perl, .NET, Java, and JavaScript, and more
    - Availability of libraries for different programming and scripting languages

- __Disadvantages__
    - Different components In the stack can become difficult to handle when you move on to complex setup
    - There’s nothing like trial and error. Thus, the more you do, the more you learn along the way
---

## Installation

You can follow this steps to install elasticsearch and kibana :

### Elasticsearch
<details open>
<summary><b><font size="4">Linux</font></b></summary>
<p>

__Install elasticsearch using APT :__
```shell
# Download and install the Public Signing Key:
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -

# You may need to install the apt-transport-https package on Debian before proceeding:
sudo apt-get install apt-transport-https

# Save the repository definition to /etc/apt/sources.list.d/elastic-7.x.list:
echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list

# Run sudo apt-get update and the repository is ready for use. You can install it with:
sudo apt-get update && sudo apt-get install elasticsearch

# To start
sudo systemctl start elasticsearch.service
```

__Install elasticsearch using YUM :__
```shell
# Download and install the public signing key:
sudo rpm --import https://artifacts.elastic.co/GPG-KEY-elasticsearch

# Add the following in your /etc/yum.repos.d/ directory in a file with a .repo suffix, for example elasticsearch.repo
name=Elastic repository for 7.x packages
baseurl=https://artifacts.elastic.co/packages/7.x/yum
gpgcheck=1
gpgkey=https://artifacts.elastic.co/GPG-KEY-elasticsearch
enabled=1
autorefresh=1
type=rpm-md" | sudo tee /etc/yum.repos.d/elasticsearch.repo

# And your repository is ready for use. You can install it with:
sudo yum install elasticsearch

# To start
sudo systemctl start elasticsearch
```

__Install elasticsearch using Deb Package :__
The Debian package for Elasticsearch v7.17.23 can be downloaded from the website and installed as follows:
```shell
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.17.23-amd64.deb
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.17.23-amd64.deb.sha512
shasum -a 512 -c elasticsearch-7.17.23-amd64.deb.sha512 
sudo dpkg -i elasticsearch-7.17.23-amd64.deb

# Elasticsearch can be started and stopped as follows:
sudo /bin/systemctl daemon-reload
sudo /bin/systemctl enable elasticsearch.service
sudo systemctl start elasticsearch.service
```

__Install elasticsearch using RPM Package :__
The Debian package for Elasticsearch v7.17.23 can be downloaded from the website and installed as follows:
```shell
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.17.23-x86_64.rpm
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.17.23-x86_64.rpm.sha512
shasum -a 512 -c elasticsearch-7.17.23-x86_64.rpm.sha512 
sudo rpm --install elasticsearch-7.17.23-x86_64.rpm

# Elasticsearch can be started and stopped as follows:
sudo /bin/systemctl daemon-reload
sudo /bin/systemctl enable elasticsearch.service
sudo systemctl start elasticsearch.service
```

</p>
</details>

<details open>
<summary><b><font size="4">macOS</font></b></summary>
<p>

__Install elasticserch from archive :__
The MacOS archive for Elasticsearch v7.17.23 can be downloaded and installed as follows:

```shell
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.17.23-darwin-x86_64.tar.gz
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.17.23-darwin-x86_64.tar.gz.sha512
shasum -a 512 -c elasticsearch-7.17.23-darwin-x86_64.tar.gz.sha512 
tar -xzf elasticsearch-7.17.23-darwin-x86_64.tar.gz
cd elasticsearch-7.17.23/ 

# Elasticsearch can be started from the command line as follows:
./bin/elasticsearch
```

__Install elasticsearch with homebrew :__
```shell
# To install with Homebrew, you first need to tap the Elastic Homebrew repository:
brew tap elastic/tap

# After you’ve tapped the Elastic Homebrew repo, you can use brew install to install the default distribution of elasticsearch:
brew install elastic/tap/elasticsearch-full

# Starting elasticsearch with Homebrew
brew services start elastic/tap/elasticsearch-full
```

</p>
</details>

<details open>
<summary><b><font size="4">Windows</font></b></summary>
<p>

__Configuring JDK in Windows__
1. Download and install Oracle Java Development Kit v8 [Download Here](https://www.oracle.com/id/java/technologies/javase/javase8-archive-downloads.html). Choose all defaults.
2. Click Start, search for "Environment Variables" and open the system properties applet. The advanced tab of the "System Properties" applet should appear.
3. Click the Environment Variables button.
4. Under System variables click "New".
5. Enter the variable name "JAVA_HOME" (without quotes) and browse to the JDK install directory and click OK. It will look like this:

__Install Elasticsearch__
1. Download the .zip archive for Elasticsearch v7.17.23 from here :
    ```shell
    https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.17.23-windows-x86_64.zip
    ```
2. Unzip it with your favourite unzip tool. This will create a folder called elasticsearch-7.17.23, which we will refer to as %ES_HOME%. In a terminal window, cd to the %ES_HOME% directory, for instance :
    ```shell
    cd c:\elasticsearch-7.17.23
    ```
3. Elasticsearch can be started from the command line as follows:
    ```shell
    .\bin\elasticsearch.bat
    ```

</p>
</details>

<details open>
<summary><b><font size="4">Docker</font></b></summary>
<p>

1. Make sure you already installed docker compose, if not please follow this url [install-docker-compose](https://docs.docker.com/compose/install)
2. Create file with name `docker-compose.yaml` and paste this configuration :
    ```yaml
    version: '3'
    services:
      elasticsearch01:
        image: docker.elastic.co/elasticsearch/elasticsearch:7.17.23
        container_name: elasticsearch01
        ports:
          - '9200:9200'
        environment:
          - discovery.type=single-node
          - ES_JAVA_OPTS=-Xmx512m -Xms512m
          - node.name=elasticsearch01
          - cluster.name=elasticsearch
          - xpack.security.enabled=false
        volumes:
          - ./elasticsearch/data:/usr/share/elasticsearch/data
        networks:
          - elk

    networks:
      elk:
        driver: bridge
    ```
3. Save it and execute this command :
    ```shell
    docker-compose up -d
    ```
> __NOTE:__  Dont forget to update the `environment` values.

</p>
</details>

---

### Kibana
<details open>
<summary><b><font size="4">Linux</font></b></summary>
<p>

__Install kibana using APT :__
```shell
# Download and install the Public Signing Key:
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -

# You may need to install the apt-transport-https package on Debian before proceeding:
sudo apt-get install apt-transport-https

# Save the repository definition to /etc/apt/sources.list.d/elastic-7.x.list:
echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list

# Run sudo apt-get update and the repository is ready for use. You can install it with:
sudo apt-get update && sudo apt-get install kibana
# To start
sudo systemctl start kibana.service
```

__Install kibana using YUM :__
```shell
# Download and install the public signing key:
sudo rpm --import https://artifacts.elastic.co/GPG-KEY-elasticsearch

# Add the following in your /etc/yum.repos.d/ directory in a file with a .repo suffix, for example elasticsearch.repo
name=Elastic repository for 7.x packages
baseurl=https://artifacts.elastic.co/packages/7.x/yum
gpgcheck=1
gpgkey=https://artifacts.elastic.co/GPG-KEY-elasticsearch
enabled=1
autorefresh=1
type=rpm-md" | sudo tee /etc/yum.repos.d/elasticsearch.repo

# And your repository is ready for use. You can install it with:
sudo yum install kibana

# To start
sudo systemctl start kibana
```

__Install kibana using Deb Package :__
The Debian package for kibana v7.17.23 can be downloaded from the website and installed as follows:
```shell
wget https://artifacts.elastic.co/downloads/kibana/kibana-7.17.23-amd64.deb
shasum -a 512 kibana-7.17.23-amd64.deb 
sudo dpkg -i kibana-7.17.23-amd64.deb

# kibana can be started and stopped as follows:
sudo /bin/systemctl daemon-reload
sudo /bin/systemctl enable kibana.service
sudo systemctl start kibana.service
```

__Install kibana using RPM Package :__
The Debian package for kibana v7.17.23 can be downloaded from the website and installed as follows:
```shell
wget https://artifacts.elastic.co/downloads/kibana/kibana-7.17.23-x86_64.rpm
wget https://artifacts.elastic.co/downloads/kibana/kibana-7.17.23-x86_64.rpm.sha512
shasum -a 512 -c kibana-7.17.23-x86_64.rpm.sha512 
sudo rpm --install kibana-7.17.23-x86_64.rpm

# kibana can be started and stopped as follows:
sudo /bin/systemctl daemon-reload
sudo /bin/systemctl enable kibana.service
sudo systemctl start kibana.service
```

</p>
</details>

<details open>
<summary><b><font size="4">macOS</font></b></summary>
<p>

__Install kibana from archive :__
The MacOS archive for kibana v7.17.23 can be downloaded and installed as follows:

```shell
curl -O https://artifacts.elastic.co/downloads/kibana/kibana-7.17.23-darwin-x86_64.tar.gz
curl https://artifacts.elastic.co/downloads/kibana/kibana-7.17.23-darwin-x86_64.tar.gz.sha512 | shasum -a 512 -c - 
tar -xzf kibana-7.17.23-darwin-x86_64.tar.gz
cd kibana-7.17.23-darwin-x86_64/ 

# Kibana can be started from the command line as follows:
./bin/kibana
```

__Install kibana with homebrew :__
```shell
# To install with Homebrew, you first need to tap the Elastic Homebrew repository:
brew tap elastic/tap

# After you’ve tapped the Elastic Homebrew repo, you can use brew install to install the default distribution of kibana:
brew install elastic/tap/kibana-full

# Starting kibana with Homebrew
brew services start elastic/tap/kibana-full
```

</p>
</details>

<details open>
<summary><b><font size="4">Windows</font></b></summary>
<p>

__Configuring JDK in Windows__
1. Download and install Oracle Java Development Kit v8 [Download Here](https://www.oracle.com/id/java/technologies/javase/javase8-archive-downloads.html). Choose all defaults.
2. Click Start, search for "Environment Variables" and open the system properties applet. The advanced tab of the "System Properties" applet should appear.
3. Click the Environment Variables button.
4. Under System variables click "New".
5. Enter the variable name "JAVA_HOME" (without quotes) and browse to the JDK install directory and click OK. It will look like this:

__Install Kibana__
1. Download the .zip archive for kibana v7.17.23 from here :
    ```shell
    https://artifacts.elastic.co/downloads/kibana/kibana-7.17.23-windows-x86_64.zip
    ```
2. UUnzip it with your favourite unzip tool. This will create a folder called kibana-7.17.23-windows-x86_64, which we will refer to as `$KIBANA_HOME`. In a terminal window, CD to the `$KIBANA_HOME` directory, for instance :
    ```shell
    cd c:\kibana-7.17.23-windows-x86_64
    ```
3. Kibana can be started from the command line as follows:
    ```shell
    .\bin\kibana.bat
    ```

</p>
</details>

<details open>
<summary><b><font size="4">Docker</font></b></summary>
<p>

1. Make sure you already installed docker compose, if not please follow this url [install-docker-compose](https://docs.docker.com/compose/install)
2. Create file with name `docker-compose.yaml` and paste this configuration :
    ```yaml
      kibana:
        image: docker.elastic.co/kibana/kibana:7.17.23
        container_name: kibana
        ports:
          - '5601:5601'
        environment:
          - SERVERNAME=kibana
          - ELASTICSEARCH_HOSTS=http://elasticsearch01:9200
          - ES_JAVA_OPTS=-Xmx512m -Xms512m
          - xpack.maps.showMapVisualizationTypes=true
        networks:
          - elk
        depends_on:
          - elasticsearch01
    ```
3. Save it and execute this command :
    ```shell
    docker-compose up -d
    ```
> __NOTE:__  Dont forget to update the `environment` values.

</p>
</details>