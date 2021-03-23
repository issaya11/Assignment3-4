#below is the code that we inserted to fix this vulnerability

header("Location: /admin.php");
                $date = date("Y-m-d H:i:s");
                $name = $_POST['username'];
                $logmsg = "  Log Information: name: " .$name ." date: " .$date;
                file_put_contents("./assignment3-4_Andriy_Yahya.log", $logmsg, FILE_APPEND);
