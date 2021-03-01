OhMyDash support installation base on docker image. User can experience all OhMyDash features by installing OhMyDash docker image.

#### Prerequisite
* Docker Engine has installed and configured.

#### Apply Free License

在开始之前，你需要登录我们的网站 https://ohmydash.stdatatech.com/freeLicense 申请免费的License。 license会通过邮件发送给您的邮箱。点击邮件中的链接可以下载license文件。

#### Start OhMyDash

```shell
docker run -d -p 3000:3000 stdatatech/ohmydash-lite
```
When above command run successfully, you can access OhMyDash by http://localhost:3000.  The default username/password is admin/admin.

#### Import License

After login ,go to page http://localhost:3000/system_status and select License Tab, you can click ”Upgrade license“ button to import the license file you just applied. 

#### Use Sample Data

* Download Sample Data

User can download latest sqlite database file demo.db.gz from https://github.com/stdatatech/dash-examples/releases. <br>

Execute the following command on Linux or Mac to extract demo database
```shell
  gzip -d demo.db.gz
```
Use any available extract tool on Windows to extract demo database.

User can create sqlite database source after get demo.db file. [Reference](sqlite)

!> Please create a new sqlite datasource which name with 'demo'. 'demo' is the default name of sample charts and dashboard. It would be easy for user to see sample charts and dashboard when import sample charts and dashboard.

* Download Sample Charts and Dashboards

User can download predefined sample charts and dashboard from github https://github.com/stdatatech/dash-examples

![Example](dash-example.jpg)

After download and extract sample charts and dashboard definition, user will have a bunch of json files. Please reference to [Import/Export](imexport) to import charts and dashboard samples.