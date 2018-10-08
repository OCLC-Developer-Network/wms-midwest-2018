# A Beginner's Guide to Working with WorldShare APIs
## WMS Midwest Meeting 2018 - API Workshop
### Tutorial Part 9 - Route using a Model 

#### Displaying the Bibliographic Record
In order to display the actual bibliographic data we have to retrieve it from the API and pass it to our view.
1. Open routes.php
2. Find display bib route
```php
$app->get('/bib[/{oclcnumber}]', function ($request, $response, $args){
```
3. Remove line
```php
return $this->view->render($response, 'bib.html');
``` 
4. Get the OCLC Number you want to look up. It can come from POSTED form data or the url
    1. If the OCLC Number came in the url in $oclcnumber
    2. If OCLC Number came in form data, if so store it in the $oclcnumber
    3. Otherwise return an error page
    4. If you have an OCLC Number, use the Bib class to find the record
    5. check to make sure Bib is returned
        - if so, return the bib record view. Pass Bib object to it as the bib variable
```php
    if (isset($args['oclcnumber'])){
        $oclcnumber = $args['oclcnumber'];
    } elseif ($request->getParam('oclcnumber')) {
        $oclcnumber = $request->getParam('oclcnumber');
    } else {
        $this->logger->addInfo("No OCLC Number present");
        return $this->view->render($response, 'error.html', [
                'error' => 'No OCLC Number present',
                'error_message' => 'Sorry you did not pass in an OCLC Number'
        ]);
    }
    $bib = Bib::find($oclcnumber, $_SESSION['accessToken']);
    
    if (is_a($bib, "Bib")){
        
        return $this->view->render($response, 'bib.html', [
                'bib' => $bib
        ]);
    }else {
        // catch the error
    }
```

#### Adding Authentication
If we ran the bib rout right now it would fail because we aren't authenticated and don't have a valid Access Token.
So we need to make sure that before this request is handled we authenticate and get a valid Access Token.
We'll do this using the authentication middleware we created in tutorial 7.

1. Add the authentication middleware to the bib route
```php
$app->get('/bib[/{oclcnumber}]', function ($request, $response, $args){
    // some more code
})->setName('display_bib')->add($auth_mw);
```

**[on to Part 10](tutorial-10.md)**

**[back to Part 8](tutorial-08.md)**