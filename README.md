#below is the code that we inserted to fix this vulnerability

function csrfchecktoken(){

if($_REQUEST["csrftk"] !== $_SESSION["csrftk"]){

unset($_SESSION["csrftk"]);
die("Validation has failed.");

}
return true;
}

function gentoken(){

if(!isset($_SESSION["csrftk"])){

$token = md5(microtime());
$_SESSION["csrftk"] = $token;

}else{
session_write_close();
}
return $token;
}
