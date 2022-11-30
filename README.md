# PHP Custom Error Module

# Usage 
```
<?php

    require ('Error.php');

    // SETTING AN ERROR
    // each error is set with an error code and the error message

    $name = 'cet';
    if ($name != 'yung')
    {
        // create a new App/Custom/Error object
        // -1 = error code (you can pass/define your own error codes)
        $error = new App\Custom\Error (-1, 'name does not exist');
    }

    // check if an error occured
    if (App\Custom\Error::IsAnError ($error))
    {
        // handle error
        echo 'Error: '. $error->GetError(); // get error message
        // $error->GetErrorCode() get error code (useful if you want to hide sensetive error message for the user)
    }

    // ADDING MULTIPLE ERRORS
    $names = ['yung', 'cet', 'matt'];
    $name1 = 'cedric';
    $name2 = 'ced';
    $name3 = 'ray';

    if (! in_array ($name1, $names)) 
    {
        $errors = new App\Custom\Error (-1, "$name1 does not exist"); // create a new App/Custom/Error object
    }

    if (! in_array ($name2, $names)) 
    {
        $errors->AddError (-1, "$name2 does not exist"); // add another error
    }

    if (! in_array ($name2, $names))
    {
        $errors->AddError (-1, "$name3 does not exist"); // add another error
    }
    
    // check for errors
    if (App\Custom\Error::IsAnError ($errors))
    {
        // $errors->GetAllErrors() get all errors, this returns an array
        foreach ($errors->GetAllErrors() as $err)
        {
            echo $err['error']."\n"; // echo $err['code'] for error codes
        }
    }
?>

```
