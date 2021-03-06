---
layout: page-fullwidth
title: "Υπηρεσία διαχείρισης AMKA"
subheadline: "API διαχείρισης πληροφοριών κοινωνικής ασφάλισης"
meta_teaser: "API για την επιβεβαίωση της εγκυρότητας των στοιχείων που συνδέονται με τον ΑΜΚΑ."
teaser: "Με το <em>amka-services</em></a> API μπορείτε να λαμβάνεται έγκυρα και επικαιροποιημένα στοιχεία για τους χρήστες σας όπως αυτά εμφανίζονται στα μητρώα κοινωνικής ασφάλισης της ΗΔΙΚΑ"
header:
   image_fullwidth: "amka_splash.png"
image:
    thumb:  amka_splash.png
    homepage: amka_splash.png
categories:
    - apis 
permalink: "/apis/amka-services/"
---
<div class="row">
<div class="medium-4 medium-push-8 columns" markdown="1">
<div class="panel radius" markdown="1">
**Πίνακας περιεχομένων**
{: #toc }
*  TOC
{:toc}
</div>
</div><!-- /.medium-4.columns -->

<div class="medium-8 medium-pull-4 columns" markdown="1">
{% include improve_content.html %}

## Επισκόπηση

Στα πλαίσια της προσπάθειας μας για την καλύτερη διαλειτουργικότητα
μεταξύ των οργανισμών της ακαδημαϊκής κοινότητας, και σε συνεργασία με την
[ΗΔΙΚΑ][], η [GUNet][] παρέχει στα μέλη της μια υπηρεσία επιβεβαίωσης, αναζήτησης και ανάκτησης πληροφοριών
για τους [Αριθμούς Μητρώου Κοινωνικής Ασφάλισης (ΑΜΚΑ)][AMKA] που είναι υποχρεωτικοί για όλα τα μέλη της Ακαδημαϊκής Κοινότητας.
Μέσω της έγκυρης αντιστοίχησης των πληροφοριών που τηρούνται στα πληροφοριακά συστήματα
των ακαδημαϊκών ιδρυμάτων για τα φυσικά πρόσωπα με τον ΑΜΚΑ τους, όπως τηρείται
από την [ΗΔΙΚΑ][], δίνεται η δυνατότητα για καλύτερη διαλειτουργικότητα των
διαδικασιών που εμπλέκουν ακαδημαϊκούς φορείς και φορείς της κοινωνικής
ασφάλισης. Επίσης η υπηρεσία μπορεί να συνδράμει στην προσπάθεια βελτίωση της ποιότητας (από την άποψη της πληρότητας και
της εγκυρότητας) των πληροφοριών που τηρούν τα ακαδημαϊκά ιδρύματα για τα μέλη τους.


## Προαπαιτούμενα

Η υπηρεσία προορίζεται για χρήση από τα αρμόδια τμήματα των ακαδημαϊκών
ιδρυμάτων που συμμετέχουν στην [GUNet][]. 

Πρωτού ένα ίδρυμα μπορεί να επωφεληθεί της υπηρεσίας θα πρέπει να του εκχωρηθεί ένα
μυστικό κλειδί για το ίδρυμα, κατόπιν αίτησης των αρμόδιων προσώπων για την διασύνδεση των
πληροφοριακών συστημάτων του ιδρύματος με τις υπηρεσίες της GUNet. Προς το παρόν τα
μυστικά κλειδιά εκδίδονται μέσω της εφαρμογής του [Academic ID][]. Το αρμόδιο
πρόσωπο για την διαχείριση των πληροφοριακών συστημάτων μπορεί, αφού
ταυτοποιηθεί μέσω της ομοσπονδίας της ΕΔΕΤ, συμπληρώνει την [σχετική φόρμα
ενδιαφέροντος][academic-id-form]. Αφού γίνει η αίτηση την, και αφού αυτή
εγκριθεί, ενεργοποιείται το κλειδί και η πρόσβαση στην υπηρεσία θα είναι δυνατή.

## Τεκμηρίωση

Το API της υπηρεσίας είναι διαθέσιμο αρχικά μέσω τεχνολογιών [JSON-RPC][] και
[REST][]. Ακολουθεί η τεκμηρίωση για αυτές τις διεπαφές.

### Διεπαφή REST

Η διεπαφή REST είναι ένα είδος Web API, που προτείνεται για την κατανάλωση
υπηρεσιών που παρέχονται από τρίτους λόγω της ευελιξίας που προσφέρει και την
ευκολία εξέλιξης στο μέλλον. Είναι τεχνολογία ανεξάρτητη από συγκεκριμένες
πλατφόρμες λειτουργικών ή προγραμματιστικών περιβάλλοντων και βασίζεται
εξ'ολοκλήρου στο πρωτόκολλο HTTP και τις αρχές [REST][]. To url της υπηρεσίας
είναι το https://amka-services.gunet.gr .
{% comment %} 
 Πλήρης τεκμηρίωση για την διεπαφή
REST, μπορεί να βρεθεί στην παρακάτω σελίδα:

> [επίσημος οδηγός της υπηρεσίας](https://identity.gunet.gr/sites/default/files/apidoc_gr.pdf)
{% endcomment %}
### Παράδειγμα χρήσης με REST

Παρακάτω θα βρείτε ένα ενδεικτικό παράδειγμα χρήσης του API μέσω της διεπαφής
REST και του γνωστού προγράμματος `curl`. Υποθέτουμε ότι σας έχει εκχωρηθεί το μυστικό κλειδί `12345678912345678912345678912345`:

    curl -v -G \
     -X GET "https://amka-services.gunet.gr/api/rest/v1/ssn_validation" \
     -d "ssn=12312312312" \
     -d "birthdate=1995-01-01" \
     --data-urlencode "surname=ΧΡΗΣΤΗΣ" \
     -H "Accept: application/json" \
     -H "Authorization: Token 12345678912345678912345678912345"

     { "match": "true",
      "ssn": "12312312312",
      "father_en":"FATHERNAME",
      "birth_country":"ΕΛΛΑΔΑ",
      "address_prefecture":"ΑΤΤΙ",
      "sex":"A",
      "birth_municipality":"ΑΤΤΙΚΗ",
      "address_country":"ΕΛΛΑΔΑ",
      "citizenship":"ΕΛΛΑΔΑ",
      "surname_cur_en":"USER",
      "id_num":"XX000000",
      "father_gr":"ΠΑΤΡΩΝΥΜΟ",
      "tel1":"210-1234567",
      "tel2":"210-1234568",
      "last_mod_date":"01/01/1995",
      "id_type":"T",
      "surname_cur_gr":"ΧΡΗΣΤΗΣ",
      "tid":"123654987",
      "id_creation_year":"1995",
      "death_date":"01/01/1995",
      "birth_date":"01/01/1995",
      "name_en":"TEST",
      "address_country_code":"ΕΛ",
      "surname_birth_gr":"ΧΡΗΣΤΗΣ",
      "surname_birth_en":"USER",
      "amka_cur":"12312312312",
      "mother_en":"MOTHERNAME",
      "mother_gr":"ΜΗΤΡΩΝΥΜΟ",
      "death_note":"Λ",
      "name_gr":"ΔΟΚΙΜΑΣΤΙΚΟΣ",
      "address_town":"ΑΘΗΝΑ",
      "amka_in":"12312312312",
      "address_zipcode":"12345",
      "birth_municipality_greek_code":"ΑΤΤΙ",
      "bdate_istrue":"Π",
      "birth_country_code":"ΕΛ",
      "address_street":"ΠΑΝΕΠΙΣΤΗΜΙΟΥΠΟΛΗ" }

### Παράδειγμα χρήσης JAVA

{% highlight java %}
/*
GUnet AMKA service java code examples.

Requires the Apache HTTPClient libraries.
Available at http://hc.apache.org/downloads.cgi

How to compile: javac -cp java_libs/*:. api_call.java
How to run: java -cp java_libs/*:. api_call
*/

import java.io.BufferedReader;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.net.URLEncoder;
import java.util.Arrays;
import org.apache.http.client.methods.CloseableHttpResponse;
import org.apache.http.client.methods.HttpGet;
import org.apache.http.impl.client.CloseableHttpClient;
import org.apache.http.impl.client.HttpClients;

public class api_call
{
    public static void main(String[] args) throws Exception
    {
        String auth_token = "12345678912345678912345678912345";
        String url = "https://amka-services.gunet.gr/api/rest/v1/ssn_validation";
        String ssn = "12312312312";
        String birthdate = "1995-01-01";
        String surname = "ΧΡΗΣΤΗΣ";
        String charset = java.nio.charset.StandardCharsets.UTF_8.name();

        String query = String.format("ssn=%s&birthdate=%s&surname=%s",
                                     URLEncoder.encode(ssn, charset),
                                     URLEncoder.encode(birthdate, charset),
                                     URLEncoder.encode(surname, charset));

        CloseableHttpClient httpclient = HttpClients.createDefault();
        HttpGet req = new HttpGet(url + "?" + query);

        req.addHeader("content-type", "application/json");
        req.addHeader("Authorization", "Token " + auth_token);

        CloseableHttpResponse resp = null;
        try
        {
            resp = httpclient.execute(req);

            int code = resp.getStatusLine().getStatusCode();
            InputStream body = resp.getEntity().getContent();

            if (code != 200)
            {
                System.err.println("Erroneous status " + code + "for url " +
                url + "with headers " + Arrays.toString(req.getAllHeaders()) +
                "and parameters " + query);
            }

            BufferedReader br = new BufferedReader(
                     new InputStreamReader((resp.getEntity().getContent())));

            String output, msg="";
            while ((output = br.readLine()) != null)
                    msg += output;
            System.out.println("Server reponse: " + msg);
        }
        catch (Exception e)
        {
            System.err.println("Exception occured for url " + url + "with " +
            " headers " + Arrays.toString(req.getAllHeaders()) + "and " +
            " parameters " + query);
        }
        finally
        {
            if (resp != null)
                resp.close();
        }
    }
}

{% endhighlight %}

### Παράδειγμα χρήσης Python

{% highlight python %}
# -*- coding: utf-8 -*-

'''
GUnet AMKA service python code examples.

Requires the python "requests" library.
Available at https://github.com/kennethreitz/requests
'''

import requests

def main():
    '''The main function'''
    auth_token = '12345678912345678912345678912345'
    url = 'https://amka-services.gunet.gr/api/rest/v1/ssn_validation'
    params = {'ssn': '12312312312',
              'birthdate': '1995-01-01',
              'surname': 'ΧΡΗΣΤΗΣ'}
    ssl_verify = False

    hdrs = {'content-type': 'application/json',
            'Authorization': 'Token %s' % (auth_token)}

    try:
        req = requests.get(url, headers=hdrs, verify=ssl_verify, params=params)
    except requests.RequestException as req_exc:
        print "Request exception: %s" % (req_exc)
        return None
    except Exception as e:
        print "Generic exception: %s" % (e)
        return None

    #CHECK RESPONSE CODE HERE (b4 extracting data)!
    if req.status_code != 200:
        print ("Erroneous status %s for url %s with headers %s and parameters"
               " %s" % (req.status_code, url, hdrs, params))

    print "Server response: %s" % (req.text)

if __name__ == "__main__":
    main()

{% endhighlight %}


### Παράδειγμα PHP

{% highlight java %}
<?php
/*
GUnet AMKA service php code examples.

Requires the php curl library.
Available at http://php.net/manual/en/book.curl.php
*/

$auth_token = '12345678912345678912345678912345';
$url = 'https://amka-services.gunet.gr/api/rest/v1/ssn_validation';
$ssn = '12312312312';
$bdate = '1995-01-01';
$surname = 'ΧΡΗΣΤΗΣ';


// The data to send to the API
$params = array(
    'ssn' => $ssn,
    'birthdate' => $bdate,
    'surname' => $surname,
);

$url .= '?' . http_build_query($params);

// Setup cURL
$ch = curl_init($url);

curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false);

curl_setopt_array($ch, array(
    CURLOPT_HTTPHEADER => array(
        "Authorization: Token $auth_token",
        'Content-Type: application/json'
    ),
));

// Send the request
$response = curl_exec($ch);

// Check for errors
if($response === FALSE){
    die(curl_error($ch));
}

// Decode the response
$responseData = json_decode($response, TRUE);

echo "Server response:";
var_dump($responseData);

{% endhighlight %}

### Παραδείγματα απαντήσεων
Για αναλυτικά παραδείγματα απαντήσεων της υπηρεσίας, μπορείτε να δείτε τον [επίσημο οδηγό της υπηρεσίας](https://identity.gunet.gr/sites/default/files/apidoc_gr.pdf)






### Διεπαφή JSON-RPC

Η τεχνολογία [JSON-RPC][] είναι ένα διαδεδομένο πρωτόκολο κλήσης απομακρυσμένων μεθόδων
(Remote Procedure Call) για το οποίο υπάρχουν πολλές έτοιμες υλοποιήσεις για 
διάφορες πλατφόρμες και γλώσσες προγραμματισμού. Βασίζεται στην τεχνολογία HTTP
και [JSON][]. Η υπηρεσία υποστηρίζει την έκδοση [JSON-RPC 2.0][jsonrpcspec].
Πλήρης τεκμηρίωση για την διεπαφή JSON-RPC, στα Αγγλικά, καθώς και ένα
διαδραστικό περιβάλλον για δοκιμές μπορεί να βρεθεί στην παρακάτω σελίδα:

> [AMKA Services JSON-RPC API Documentation][amka-jsonrpc-doc]


### Παράδειγμα χρήσης με JSON-RPC με χρήση της γλώσσας Perl

Παρακάτω θα βρείτε ένα ενδεικτικό παράδειγμα χρήσης του API μέσω της διεπαφής
JSON-RPC κάνοντας χρήση της γλώσσας Perl. Υποθέτουμε ότι σας έχει εκχωρηθεί το μυστικό κλειδί `209802983402983049280394`
με αναγνωριστικό ID `7`:

    TODO

 [AMKA]: http://amka.gr/ "Αριθμός Μητρώου Κοινωνικής Ασφάλισης"
 [JSON-RPC]: http://jsonrpc.org/ "κεντρική σελίδα για τοJSON-RPC"
 [ΗΔΙΚΑ]: http://www.idika.gr "ΗΔΙΚΑ: Ηλεκτρονική Διακυβέρνηση Κοινωνικής Ασφάλισης"
 [REST]: http://wikipedia.org/wiki/REST "Representational State Transfer (Wikipedia)"
 [Academic ID]: /apis/academicid/ "GUNet: υπηρεσία AcademicID"
 [amka-rest-doc]: http://docs.amkaservices.apiary.io/ "Τεκμηρίωση διεπαφής REST για την υπηρεσία AMKA"
 [amka-jsonrpc-doc]: https://github.com/gunet/amka-services-spec/blob/master/docs/jsonrpc.md "Τεκμηρίωση διεπαφής JSON-RPC για την υπηρεσία AMKA"
 [specsrepo]: http://github.com/gunet/amka-services-specs/ "Προδιαγραφές για τα API της υπηρεσίας ΑΜΚΑ"
 [jsonrpcspec]: http://www.jsonrpc.org/specification "Προδιαγραφές για την έκδοση 2.0 του JSON-RPC"
 [JSON]: http://www.ietf.org/rfc/rfc4627.txt "RFC4627: Javascript Object Notation"
 [GUNet]: http://gunet.gr "Ακαδημαϊκό διαδίκτυο (GUNet)"
 [academic-id-form]: https://academicid.gunet.gr/#form-of-interest "AcademicID: αίτηση ενδιαφέροντος"

</div><!-- /.medium-8.columns -->

</div><!-- /.row -->


