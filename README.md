#below is the code that we inserted to fix this vulnerability


<?php include("templates/page_header.php");?>
<?php include("lib/auth.php") ?>
<?php
    if (($row['author'] = 1) && ($_SESSION['username'] == 'student')) {


        //Redirect to admin area
        Header("Location: /admin.php");
    }else{
            header("Location: /");
    }
