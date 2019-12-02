# Simple application

## Simple application

In this example, we need to go fast and quickly deploy an application.

We'll start new project which needs to have:

* 1 application \(private port 8080\)
* Being exposed through internet on https \(public port 443\)
* 1 database \(PostgreSQL\)
* Store images on an object storage \(S3\)

The first thing to do is to initiate qovery in the repository:

```text
$ qovery init

✓ Dockerfile detected in your root directory

➤ Enter the project name: my-project

➤ What port number your application ir running on? (Hit enter if none): 8080

➤ Is this port accessible from other applications of the same project? (y/n): y

➤ Would you like to expose publicly your application on https? (y/n): y

➤ Do you need any database? (y/n): y

➤ Set the instance name: my-super-instance

➤ Estimated MySQL data size in GiB (default: 10): 20

➤ Please choose the performances you need: 1
1. Tiny   : 1 vCPU / 2GiB Ram
2. Small  : 2 vCPU / 8Gib Ram
3. Medium : 4 vCPU / 16GiB Ram
4. Big    : 8 vCPU / 32GiB Ram
5. Huge   : 16 vCPU / 64GiB Ram
c. Custom Mode

➤ Do you need any other database? (y/n): n

➤ Do you need any borker? (y/n): n

✓ Your Qovery configuration file has been successfuly created (.qovery.yml)!

➤ Commit into your repository and push it to get this deployed.
```

If you do not already have your Dockerfile, one will be suggested according to your repository content.

Now that you have your application and database declared in your Qovery configuration file. 

Now we need to add an S3 storage. Your full Qovery configuration will look like this:

{% tabs %}
{% tab title=".qovery.yml" %}
```yaml
application:
  name: my-super-instance
  project: my-project
  private-port: 8080
  public-port: 443
   
databases:
  - name: my-super-instance
    type: postgresql
    version: 11.4
    size: 20GiB

storage:
  - name: s3-images
    type: object-storage
    bucket: images
    public-access: no
```
{% endtab %}
{% endtabs %}

Then you have to add in your code the Qovery SDK to easily manage the credentials part.

Finally, once commited and pushed, you can check the status and retrieve the URL like this:

```bash
$ qovery status

* External DNS name        : <myapplicationid>.qovery.io
* SSL/TLS enabled          : https://<myapplicationid>.qovery.io
* Current deployed version : 7b3aeb5 (Marty McFly) / 2014-05-13 02:56
...
```
