# Amazon OpenSearch Service on AWS

## Main Tutorial

1. Create Domain

    Select Create Domain 
    ![](1-Domain.png)


    Enter a Domain Name. Select Development and Testing for Deployment Type
    ![](2-dev-testing.png)


    Select `t3.small.search` Node Type
    ![](3-data-nodes.png)


    Select `Public access`
    ![](4-network.png)


    Select `create master user` and Enter Username/Password 
    ![](5-access-control.png)


    Select `only use fine-grain control`
    ![](6-access-policy.png)


    Select `create`
    ![](7-create-domain.png)


    After 10-15mins Your Domain Will Be Ready
    ![](8-domain-ready.png)

2. Upload Documents 

    Upload a signle document using the api 
    ```
    curl -XPUT -u 'master-user:master-user-password' 'domain-endpoint/movies/_doc/1' -d '{"director": "Burton, Tim", "genre": ["Comedy","Sci-Fi"], "year": 1996, "actor": ["Jack Nicholson","Pierce Brosnan","Sarah Jessica Parker"], "title": "Mars Attacks!"}' -H 'Content-Type: application/json'
    ```

    Upload multiple documents 
    create a json file and upload 
    ```
    curl -XPOST -u 'master-user:master-user-password' 'domain-endpoint/_bulk' --data-binary @bulk_movies.json -H 'Content-Type: application/json'
    ```

3. Search for Document using API 

    search for a document via API 
    ```
    curl -XGET -u 'master-user:master-user-password' 'domain-endpoint/movies/_search?q=mars&pretty=true'
    ```

4. Search for document via UI
    Search Via UI
    ```
    domain-endpoint/_dashboards/
    ```

    Once on the dashboard click `Discover` on the left handside
    ![](9-discover.png)

    Click `Create index pattern`
    ![](10-create-index.png)

    Type `movies` into the text input box and click `Next Step`
    ![](12-define-index-pattern.png)

    Click `Create Index`
    ![](13-createe-index-pattern.png)

    The searchable index pattern will be created and the fields listed
    ![](14-index-fields.png)

    Click the hamburger menu on the left hand side and click `Discovery` again. 
    The searchable index will now appear. 
    ![](15-discovery-search.png)

5. Delete a domain 

    ![](16-delete-domain.png)
