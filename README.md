# SQL_and_API

sheet 範例

https://medium.com/彼得潘的-swift-ios-app-開發教室/訂飲料-app-學習串接後台-api-新增讀取後台資料-99e18648abe9

API 範例

https://ithelp.ithome.com.tw/articles/10206863

* 區域網路連線的連線字串式 (主從架構)

               try
               {
                  // step 1 . 宣告連接字串
                  string Constr = @"Persist Security Info=False;Integrated Security=true;
                       Initial Catalog=NorthWind;Server=.\SQLExpress";

                  // step 2 . 建立SqlConnection
                  SqlConnection conn = new SqlConnection(Constr);

                  // step 3 . 宣告查詢字串
                  string Sqlstr = "select * from zen_customer";

                  // step 4. 建立SqlDataAdapter
                  SqlDataAdapter da = new SqlDataAdapter(Sqlstr, conn);

                  // step 5. 建立DataSet來儲存Table
                  DataSet ds = new DataSet();

                  // step 6. 將DataAdapter查詢之後的結果，填充至DataSet
                  da.Fill(ds);                

                  // step 7 . 用DataGridView1 顯示出來
                  this.dataGridView1.DataSource = ds.Tables[0].DefaultView;               
              }
              catch (Exception ex)
              {
                  MessageBox.Show(ex.Message);
              }
              
 config file
 
 using mysql_connect() as driver.
 
       <?php
          $dbhost = '127.0.0.1';
          $dbuser = 'mysql_user';
          $dbpass = 'mysql_password';
          $dbname = 'mysql_databaseName';
          $conn = mysql_connect($dbhost, $dbuser, $dbpass) or die('Error with MySQL connection');
          mysql_query("SET NAMES 'utf8'");
          mysql_select_db($dbname);
          $sql = "SELECT * FROM `zen_customer` WHERE `cname` like 'Michael';";
          $result = mysql_query($sql) or die('MySQL query error');
          while($row = mysql_fetch_array($result)){
              echo $row['name'];
          }
      ?>
      
* Restful

Restful API 為因應網際網路無狀態，所演化出來的前後端完全分離的存取架構。
透過 http(精確說是 url 就是一串網址)，去後端主機取得資料或資源的一種網路服務。


    getData() {
                    const params = {
                        para01: 'zen_department',
                        para02: 'did',
                        para03: 'P',
                        para04: `${this.cur_page}^${this.cur_size}^did^*^dname like ''%${this.fulltextsearch}%''^basm01`
                    }
                    this.$axios.post('/api/orm_api/1/', qs.stringify(params)).then((res) => {
                        this.loading = false;
                        if(res.length && res[0]){
                            this.tableData = res[0];
                            if(typeof res[0][0] === 'object'){
                                this.total = res[0][0]._TotalRec;
                            }
                        }
                    })
                },
