---
layout: page-fullwidth
title: "Υπηρεσίες SMS"
subheadline: "API για την αποστολή και λήψη σύντομων μηνυμάτων"
meta_teaser: "API για την αποστολή και λήψη σύντομων μηνυμάτων από και προς τα ακαδημαϊκά ιδρύματα."
teaser: "Με το <em>SMS services</em></a> API τα ακαδημαϊκά ιδρύματα μπορούν να επικοινωνούν με τα μέλη της ακαδημαϊκής κοινότητας μέσω σύντομων μηνυμάτων (SMS) από και προς τις κινητές συσκευές τηλεφώνου."
header:
   image_fullwidth: "sms-splash.jpg"
image:
    thumb:  sms-splash.jpg
    homepage: sms-splash.jpg
categories:
    - apis 
permalink: "/apis/sms-services/"
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

## Επισκόπηση##
Η Πλατφόρμα Παροχής Υπηρεσιών Αποστολής και Λήψης Σύντομων Μηνυμάτων προσφέρεται από την [GUNet][] στα Πανεπιστημιακά Ιδρύματα της χώρας και υλοποιείται απο τον όμιλο  [OTE-Cosmote][] και την [App-Art][] προκειμένου να γίνονται:

- Αποστολές SMS μηνυμάτων (μεσω Web Service) στους φοιτητές και τα λοιπά μέλη της Ακαδημαικής Κοινότητας
- Προώθηση SMS μηνυμάτων (μεσω Web Service) των SMS που στέλνουν οι χρήστες. Η προώθηση γίνεται από την πλατφόρμα προς τα προκαθορισμένα εξωτερικά συστήματα

Tα Web Service που χρησιμοποιεί η πλατφόρμα είναι της μορφής JSON.

## Mobile Terminated (MT) κίνηση##

Η πλατφόρμα προσφέρει διαφορετικές υπηρεσίες SMS που ορίζονται από την GUNet. Κάθε υπηρεσία έχει έναν αριθμό από προκαθορισμένα μηνύματα και κάθε ένα από τα οποία μπορεί να σταλεί σε έναν παραλήπτη (Mobile terminated κίνηση). Τα προκαθορισμένα μηνύματα μπορούν να υποστηρίξουν δυναμικά πεδία, τις τιμές των οποίων θα καθορίζει η πλευρά του καλούντος. 
Για παράδειγμα, μπορεί να υπάρξει ένα προκαθορισμένο μήνυμα "Η βαθμολογία σας για το μάθημα {Πεδίο 1,1} είναι {Πεδίο 2,2}". Τα Πανεπιστημιακά Ιδρύματα μπορούν να καλέσουν την υπηρεσία δίνοντας τιμές στα δυναμικά πεδία "Πληροφορική Ι" και "7" και το τελικό μήνυμα προς το χρήστη να είναι "Η βαθμολογία σας για το μάθημα Πληροφορική Ι είναι 7".

## Mobile Originated (MO) κίνηση##
Επίσης, κάθε υπηρεσία περιέχει έναν αριθμό keywords τα οποία μπορεί να χρησιμοποιήσει ο τελικός χρήστης, στέλνοντας τα με SMS στην πλατφόρμα. Το κομμάτι αυτό των υπηρεσιών ονομάζεται Mobile Originated (MO). Όταν η πλατφόρμα λαμβάνει ένα SMS με κάποιο keyword, τότε προωθεί στο SMS σε κάποιο προκαθορισμένο εξωτερικό σύστημα μέσω Web Service

##Τι πρέπει να υλοποιήσετε##
Προκειμένου να πετύχετε απόλυτη διασύνδεση με την πλατφόρμα, θα πρέπει να υλοποιήσετε τα εξης:

- Application που να κάνει consume το **send SMS** web service της πλατφόρμας. Η κλήση γίνεται με μορφή JSON.

- Web Service που θα φιλοξενεί το 3rd party. Αυτό το Web Service θα γίνεται consume από την πλατφόρμα. Το Web Service πρέπει να υποστηρίζει τα εξης functions:

1. **SMS forward** (Η κλήση αυτή γίνεται από την πλατφόρμα της GUNet προς ένα συγκεκριμένο Πανεπιστημιακό Ίδρυμα, όταν κάποιος χρήστης στείλει ένα SMS στην πλατφόρμα που περιλαμβάνει ένα συγκεκριμένο Keyword.)

2. **DLR request** (Η κλήση αυτή γίνεται από την πλατφόρμα της GUNet προς ένα συγκεκριμένο Πανεπιστημιακό Ίδρυμα, όταν η πλατφόρμα ενημερωθεί από τον πάροχο πως ένα SMS παραδόθηκε στον τελικό χρήστη)

##Παραδείγματα κλήσεων##

### Παράδειγμα send SMS ###
Η send SMS παρέχεται από την πλατφόρμα και γίνεται consume απο τα Πανεπιστημιακά Ιδρύματα

Το endpoint της υπηρεσίας είναι το https://sms-services.gunet.gr:9999/sendSMS
Το request πρέπει να είναι POST και το Content Type: application/json
Ακολουθεί ένα παράδειγμα μιας κλήσης προς την δοκιμαστική υπηρεσία gradeService.
	
	{
       "serviceId": "gradeService",
       "messageId": "testMessage",
       "replacements": [
          "Προγραμματισμός Ι",
          "7"
       ],
       "recipient": "6901234567",
       "institution": "TEITHE",
       "pre-shared key": "F0fesFADSr223fA",
       "dlr-url": "https://teithe.gr/dlrs"
    }
    
Ακολουθούν και οι ενδεικτικες απαντήσεις της πλατφόρμας στο παραπάνω request

Επιτυχές:

	{
	   "serviceId": "gradeService",
       "errorCode": "",
       "error": ""
	}
Ανεπιτυχές:

	{
    	"serviceId": "gradeService",
        "errorCode": "E-002",
        "error": "Unknown Service"
    }

Παρατίθεται ένα παράδειγμα της κλήσης με curl:

	 curl -v -H "Accept: application/json" -H "Content-type: application/json" -X POST -d ' {"serviceId": "gradeService", "messageId": "testMessage", "replacements":["Προγραμματισμός Ι","2"],"recipient": "6901234567", "institution": "TEITHE","pre-shared key": "F0fesFADSr223fA","dlr-url": "https://teithe.gr/dlrs"}'  https://sms-services.gunet.gr:9999/sendSMS 


### Παράδειγμα forward SMS ###

Η forward SMS παρέχεται απο τα Πανεπιστημιακά Ιδρύματα και γίνεται consume από την πλατφόρμα

Το request θα έχει την μορφή JSON με το εξής body:

	{
    	"MSISDN": "6901234657",
        "keyword": "ΒΑ",
        "body": "ΗΛΕΚΤΡΟΝΙΚΗ",
        "pre-shared key": "F0fesFADSr223fA",
        "sms-forward-id": "123"
    }


Ακολουθούν και οι ενδεικτικες απαντήσεις τoυ Πανεπιστημιακού Ιδρύματος στο παραπάνω request

Επιτυχές:

	{
    	"result": "0",
        "errorCode": ""
        "error": ""
    }
    
Ανεπιτυχές:

	{
    	"result": "1",
        "errorCode": "error-code-1"
        "error": "error-description"
    }


### Παράδειγμα DLR Request ###

Η DLR Request παρέχεται απο τα Πανεπιστημιακά Ιδρύματα και γίνεται consume από την πλατφόρμα

Το request θα έχει την μορφή JSON με το εξής body:

Επιτυχής παράδοση μηνύματος:

	{
    	"serviceId": "gradeService",
        "recipient": "6901234657",
        "status": "DELIVRD"
	}
    
Ανεπιτυχής παράδοση μηνύματος:

	{
    	"serviceId": "gradeService",
        "recipient": "6901234657",
        "status": "ERROR",
        "error": "80"
    }





 [GUNet]: http://www.gunet.gr/ "Ακαδημαϊκό διαδίκτυο (GUNet)"
 [App-Art]: http://www.app-art.gr/ "APP-ART εταιρία νέων τεχνολογιών πληροφορικής και τηλεπικοινωνιών"
 [OTE-Cosmote]: http://www.cosmote.gr/ "OTE-Cosmote"
 [JSON]: http://www.ietf.org/rfc/rfc4627.txt "RFC4627: Javascript Object Notation"
