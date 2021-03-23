#below is the code that we inserted to fix this vulnerability

<?php
    session_start();
    include("config.php");
    include("lib/db.php");
        /get session 'login attempts'/
        if (!isset($_SESSION['login_attempts'])) {
            $_SESSION['login_attempts'] = 0;

            }
        /increase login attempts counter/
        $_SESSION['login_attempts']++;
        /if session gets to 4 then a "TOO MANY ATTEMPTS" page pops up/
        if($_SESSION['login_attempts'] > 4){
        echo "TOO MANY ATTEMPTS";
        exit();
        }

?>
