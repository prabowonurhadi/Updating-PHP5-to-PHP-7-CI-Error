# Updating-PHP5-to-PHP-7-CI-Error

A PHP Error was encountered

Severity: Warning

Message: Declaration of MX_Lang::load($langfile, $lang = ”, $return = false, $add_suffix = true, $alt_path = ”, $_module = ”) should be compatible with CI_Lang::load($langfile = ”, $idiom = ”, $return = false, $add_suffix = true, $alt_path = ”)

A PHP Error was encountered

Severity: Warning

Message: Declaration of MX_Loader::helper($helper) should be compatible with CI_Loader::helper($helpers = Array)

A PHP Error was encountered

Severity: Warning

Message: Declaration of MX_Loader::helpers($helpers) should be compatible with CI_Loader::helpers($helpers = Array)

A PHP Error was encountered

Severity: Warning

Message: Declaration of MX_Loader::language($langfile, $idiom = ”, $return = false, $add_suffix = true, $alt_path = ”) should be compatible with CI_Loader::language($file = Array, $lang = ”)

A PHP Error was encountered

Severity: Warning

Message: Declaration of MX_Loader::_ci_get_component($component) should be compatible with & CI_Loader::_ci_get_component($component)

Fatal error: Uncaught Error: Call to undefined function mysql_pconnect() in /var/www/html/cdn/vinehub/system/database/drivers/mysql/mysql_driver.php:92 Stack trace: #0 /var/www/html/cdn/vinehub/system/database/DB_driver.php(116): CI_DB_mysql_driver->db_pconnect() #1 /var/www/html/cdn/vinehub/system/database/DB.php(149): CI_DB_driver->initialize() #2 /var/www/html/cdn/vinehub/application/third_party/MX/Loader.php(99): DB(Array, NULL) #3 /var/www/html/cdn/vinehub/system/core/Loader.php(1172): MX_Loader->database() #4 /var/www/html/cdn/vinehub/system/core/Loader.php(153): CI_Loader->_ci_autoloader() #5 /var/www/html/cdn/vinehub/application/third_party/MX/Loader.php(60): CI_Loader->initialize() #6 /var/www/html/cdn/vinehub/system/core/Controller.php(52): MX_Loader->initialize() #7 /var/www/html/cdn/vinehub/application/third_party/MX/Base.php(55): CI_Controller->__construct() #8 /var/www/html/cdn/vinehub/application/third_party/MX/Base.php(60): CI->__construct() #9 /var/www/html/cdn/vinehub/application/third_party/MX/Controlle in /var/www/html/cdn/vinehub/system/database/drivers/mysql/mysql_driver.php on line 92

SOLUTION:

Find Below solution for errors:->

1:-> download latest CI 3.1
2:-> change in mysql to mysqli “config/database.php”
3:-> replace database library in system folder “system/database”
4:-> if you are getting MX library issue then changes same code

A:)Issue:->
A PHP Error was encountered
Severity: Warning
Message: Declaration of MX_Lang::load($langfile, $lang = ”, $return = false, $add_suffix = true, $alt_path = ”, $_module = ”) should be compatible with CI_Lang::load($langfile = ”, $idiom = ”, $return = false, $add_suffix = true, $alt_path = ”)

Solution:->
“application/third_party/MX/Lang.php”line no 38

just added only array() in place of

MX_Lang::load($langfile=array(), $lang = ”, $return = false, $add_suffix = true, $alt_path = ”, $_module = ”) should be compatible with CI_Lang::load($langfile = ”, $idiom = ”, $return = false, $add_suffix = true, $alt_path = ”)

B:)Isuue:->
A PHP Error was encountered
Severity: Warning
Message: Declaration of MX_Loader::helper($helper) should be compatible with CI_Loader::helper($helpers = Array)

Solution:->
“application/third_party/MX/Loader.php” line no 105

added array() in
public function helper($helper = array())

C:)Isuue:->
A PHP Error was encountered
Severity: Warning
Message: Declaration of MX_Loader::helpers($helpers) should be compatible with CI_Loader::helpers($helpers = Array)

Solution:->
“application/third_party/MX/Loader.php” line no 120

added array() in
public function helper($helper = array())

D:)Issue:->
A PHP Error was encountered
Severity: Warning
Message: Declaration of MX_Loader::language($langfile, $idiom = ”, $return = false, $add_suffix = true, $alt_path = ”) should be compatible with CI_Loader::language($file = Array, $lang = ”)

Solution:->
“application/third_party/MX/Loader.php” line no 125

added array() in
public function language($langfile=array(), $idiom = ”, $return = FALSE, $add_suffix = TRUE, $alt_path = ”) {

E:)Issue:->
A PHP Error was encountered
Severity: Warning
Message: Declaration of MX_Loader::_ci_get_component($component) should be compatible with & CI_Loader::_ci_get_component($component)

Solution:->
“application/third_party/MX/Loader.php” line no 271

added & oprator before name of function like below
public function &_ci_get_component($component)

5:-> if you are getting session error
A PHP Error was encountered
Severity: 8192
Message: Methods with the same name as their class will not be constructors in a future version of PHP; Session_check has a deprecated constructor

Solution:->

Firstly find Session_check classs and add constructor and also add below code

function __construct()
{
$this->CI =& get_instance();
}
