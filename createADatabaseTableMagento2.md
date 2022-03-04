---
title: Create a database table in Magento 2
tags: software development, web development, magento
cover: COVER_IMAGE_URL
domain: blog.azcodez.com
---
# Create a database 

## First create a module and redeploy 

## Create a db schema 
- Refernce https://devdocs.magento.com/guides/v2.4/extension-dev-guide/declarative-schema/db-schema.html
- Path will be similar path to this
app\code\AzCodez\CustomerViewing\etc\db_schema.xml

- Add this code to setup your table. Modify table names, columns, types to suit your own
```
<?xml version="1.0"?>
<!-- Database schema -->
<schema xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Setup/Declaration/Schema/etc/schema. xsd">
    <table name="az_codez_followers" resource="default" engine="innodb" comment="Azcodez followers">
        <column xsi:type="int" name="follower_id" padding="19" unsigned="true" nullable="false" identity="true" comment="Follower id"/>
        <column xsi:type="text" name="name" nullable="false" comment="Follower Name"/>
        <column xsi:type="text" name="email" nullable="false" comment="Follower Contact"/>
        <constraint xsi:type="primary" referenceId="PRIMARY">
            <column name="follower_id"/>
        </constraint>
    </table>
</schema>
```

## Generate  generate db_schema_whitelist.json
```
docker-compose run --rm deploy magento-command setup:db-declaration:generate-whitelist
```

## Redeploy

## Find your table and see if it worked eg.
```
Select * From az_codez_followers;
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646408394493/fzvAB2a3I.png)
