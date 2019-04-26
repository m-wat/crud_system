# crud_system
Laravelを用いてCRUDシステムを作る  
## Laravel×MySQLの場合の設定方法
```
$ mysql -u root -p
//パスワード入力

//ユーザー作成
//CREATE USER 'ユーザー名'@'ホスト名' IDENTIFIED BY 'パスワード';
mysql> CREATE USER 'hoge'@'localhost' IDENTIFIED BY 'password';

//指定ユーザーに権限付与
//GRANT ALL PRIVILEGES ON データベース名.* TO 'ユーザー名'@'ホスト名';
mysql> GRANT ALL PRIVILEGES ON hogedatabase.* TO 'hoge'@'localhost';
```
.envファイルに書く
```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=データベース名
DB_USERNAME=ユーザー名
DB_PASSWORD=パスワード
```
config/database.phpに書く
```
//ここはデフォルトでmysqlが指定されているのでそのままに
'default' => env('DB_CONNECTION', 'mysql'),

//connections配列の中にある、mysqlを修正
'mysql' => [
            'driver' => 'mysql',
            'host' => env('DB_HOST', '127.0.0.1'),
            'port' => env('DB_PORT', '3306'),
            'database' => env('DB_DATABASE', '.envに記載したデータベース名'),
            'username' => env('DB_USERNAME', '.envに記載したユーザー名'),
            'password' => env('DB_PASSWORD', '.envに記載したパスワード'),
            'unix_socket' => env('DB_SOCKET', '/Applications/MAMP/tmp/mysql/mysql.sock'),
```
