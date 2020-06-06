# SQL_and_API

sheet 範例

https://medium.com/彼得潘的-swift-ios-app-開發教室/訂飲料-app-學習串接後台-api-新增讀取後台資料-99e18648abe9

API 範例

https://ithelp.ithome.com.tw/articles/10206863

* 區域網路連線的連線字串式

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
