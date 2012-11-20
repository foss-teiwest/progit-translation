# Κατανεμημενο Git #

Τώρα που έχετε ένα απομακρυσμένο χώρο αποθήκευσης(repository) στο Git που έχει συσταθεί ως ένα σημείο για όλους τους προγραμματιστές να μοιραζονται τον κωδικό τους, και είστε εξοικειωμένοι με τις βασικές εντολές Git σε μια τοπική ροή εργασίας, θα εξετάσουμε το πώς να αξιοποιήσεται ορισμένες από τις κατανεμημένες ροές εργασίας που Git σας προσφέρει.

Σε αυτό το κεφάλαιο, θα δείτε πώς να εργαστείτε με το Git σε ένα κατανεμημένο περιβάλλον ως contributor και integrator.  Δηλαδή, θα μάθετε πώς να συμβάλεται με επιτυχία στον κώδικα σε ένα έργο και να το καταστήται τόσο εύκολο για εσάς και το συντηρητή του έργου όσο αυτο ειναι δυνατόν, και επίσης πώς να διατηρήσεται ένα έργο επιτυχώς με έναν αριθμό από προγραμματιστές που συμβάλλουν.

## Κατανεμημένες Ροές ##

Αντιθετα με τα Centralized Version Control Systems (CVCSs), η κατανεμημένη φύση του το Git σας δίνει τη δυνατότητα να είναι πολύ πιο ευέλικτη για το πώς οι προγραμματιστές συνεργάζονται σε έργα. Σε κεντρικά συστήματα, κάθε προγραμματιστής είναι ένας κόμβος που εργάζονται περισσότερο ή λιγότερο εξίσου σε ένα κομβικό σημείο. Στο Git, όμως, κάθε προγραμματιστής είναι πιθανώς τόσο ένας κόμβος όσο και ένα κομβικό σημείο — αύτο είναι, κάθε προγραμματιστής μπορεί τόσο να συμβάλει στον κώδικα σε άλλα repository και ταυτοχρονα να διατηρήσει ένα δημόσιο repository με τα οποίο άλλοι μπορούν να βασισουν το έργο τους και στο οποίο μπορούν να συμβάλουν. Αυτό ανοίγει ένα ευρύ φάσμα από δυνατότητες ροή εργασιών για το έργο σας και / ή την ομάδα σας, Για 'το θα καλύψουμε μερικα συνηθεις παραδειγματα οπου εκμεταλευονται αυτην την ευελιξια. Θα εξετασουμε τις δυνάμεις και τις πιθανές αδυναμίες του κάθε σχεδείου; μπορείτε να επιλέξετε ένα μόνο από αυτά που θα χρησιμοποιηθουν, ή μπορείτε να συνδυάσετε και να ταιριάξετε χαρακτηριστικά από το καθένα.

### Κεντρικοποιημενες Ροες ###

Σε κεντρικοποιημένα συστήματα, υπάρχει γενικά ένα ενιαίο μοντέλο-η κεντρικοποιημένη ροή εργασιών. Ένα κομβικό σημείο(Hub), ή χώρο αποθήκευσης(repository), μπορεί να δεχτεί κώδικα, και ο καθένας συγχρονίζει την εργασία του σε αυτό. Ένας αριθμός προγραμματιστών είναι κόμβοι - καταναλωτές του εν λόγω κέντρου - και να συγχρονίζovτε σε αυτό το κοινό μέρος (βλ. Σχήμα 5-1).

Insert 18333fig0501.png 
Σχήμα 5-1. Κεντρικοποιημένη ροή εργασιών.

Αυτό σημαίνει ότι αν δύο προγραμματιστές κατεβασουν(clone) από το κέντρο και κάνουν αλλαγές, ο πρώτος προγραμματιστής που θα προωθήσει(push) τις αλλαγές πίσω μπορεί να το κάνει χωρίς κανένα πρόβλημα. Ο δεύτερος προγραμματιστής πρέπει να συγχωνευθεί στο έργο του πρώτου κάποιου πριν ώθηση(push) τις αλλαγές κατά τετοιο τρόπο ώστε να μην αντικατασταθούν οι αλλαγές του πρώτου προγραμματιστή. Αυτή η έννοια ισχύει στο Git, όπως είναι και στο Subversion (ή σε οποιαδήποτε CVCS), και αυτό το μοντέλο λειτουργεί άψογα στο Git.

Εάν έχετε μια μικρή ομάδα ή είστε ήδη εξοικειωμένοι με μια κεντρική ροή εργασιών στην εταιρεία ή την ομάδα σας, μπορείτε εύκολα να συνεχίσετε να χρησιμοποιείτε αυτή τη ροή εργασίας με Git. Απλά συγκροτήστε ένα ενιαίο χώρο αποθήκευσης(repository), και δωστε στον καθενα στην ομαδα σας push access; Το Git δεν θα επιτρέπει στους χρήστες να αντικαθιστούν ο ένας τον άλλον. Αν κάποιος προγραμματιστής κατεβασει(clone), κανει αλλαγες, και στη συνέχεια προσπαθεί να ωθήσει τις αλλαγές τους, ενώ ένας άλλος προγραμματιστής έχει ωθήσει(push) στο μεσοδιάστημα, ο server θα απορρίψει τις αλλαγές του δευτερου προγραμματιστή. Θα τους υποθει οτι προσπαθουν να προωθήσουν(push) γρηγορες αλλαγες aκαι ότι δεν θα είναι σε θέση να προωθησουν μεχρι να λυφθει και ενωθει.
Αυτή η ροή εργασίας είναι ελκυστική για πολλούς ανθρώπους επειδή είναι ένα παράδειγμα ότι πολλοί είναι εξοικειωμένοι και άνετοι με αυτό.

### Διαχειρηση Ενταξης Ροης Εργασίας ###

Επειδή Git σας επιτρέπει να έχετε πολλαπλουςς απομακρυσμένους χωρους αποθήκευσης(remote repositories), είναι δυνατόν να έχουμε μια ροή εργασίας, όπου κάθε προγραμματιστής έχει πρόσβαση εγγραφής στο δικό του κοινό χώρο αποθήκευσης(own public repository) και αδεια να διαβάζει τους αποθηκευτικους χωρους(repositories) σε όλους τους άλλους. Αυτό το σενάριο περιλαμβάνει συχνά ενα "κανονικό" χώρο αποθήκευσης που αντιπροσωπεύει την επίσημη εκδοση του έργου. Για να συμβαλετε σε αυτο το εργο, δημιουργειτε τον δικο σας κοινο κλωνο του εργου (public clone) και προωθειτε(push) τις αλλαγες σας σε αυτο. Μετα, μπορειτε να στηλεται μια αιτηση(request) στον συντηριτη του κεντρικου εργου για να παρει (pull) τις αλλαγες σας. Μπορουν να προσθεσουν τον αποθηκευτικο σας χωρο(repository) σαν απομακρινσμενο , να τεσταρουν τις αλλαγεσας τοποικα, να τις ενοσουν με το δικο τους παραρτημα, και να τις προωθησουν (push) πισω στον δικοτους αποθηκευτικο χωρο (repository). Η διαδικασία λειτουργεί ως εξής (βλ. Σχήμα 5-2):


1. Ο συντηρητής του έργου ωθεί τo δημόσιo χώρο αποθήκευσης του (push public repository).
2. Ένας contributor κλώνοποιει τον χώρο αποθήκευσης(repository) και κάνει τις αλλαγές.
3. Ο contributor ωθεί(push) στο δικό χωρο(repository) το δημόσιο αντίγραφο του.
4. Ο contributor στέλνει στον συντηρητή ένα e-mail ζητώντας τους να τραβήξει(pull) τις αλλαγές.
5. Ο project maintainer προσθέτει τον χωρο(repository) του contributor ως απομακρυσμένο και συγχωνεύει τις αλλαγες σε τοπικό επίπεδο.
6. Ο contributor ωθεί(push) τις συγχωνεύμενες αλλαγές στον κεντρική χώρο αποθήκευσης.

Insert 18333fig0502.png 
Σχήμα 5-2. Διαχειρηση Ενταξης Ροης Εργασίας.

Αυτη ειναι μια πολυ κοινη ροη εργασιας σε ιστοτοπους οποτ το Git, όπου είναι εύκολο να κανεις ενα παραρτημα σε ένα σχέδιο και να προωθήσει τις αλλαγές σας στο παραρτημα σας για να το δουν όλοι. Ένα από τα κύρια πλεονεκτήματα αυτής της προσέγγισης είναι ότι μπορείτε να συνεχίσετε να εργάζεστε, και ο συντηρητής του κύριου χώρου αποθήκευσης μπορεί να τραβήξει σε αλλαγές ανά πάσα στιγμή. Συνεισφερόντες δεν χρειάζεται να περιμένουν για το έργο να ενσωματώσει τις αλλαγές τους - κάθε κόμμα μπορεί να λειτουργήσει με το δικό τους ρυθμό.

###  Ροής Εργασίας Δικτάτορα και Aξιωματικού ###

Αυτή είναι μια παραλλαγή της πολλαπλής αποθήκευσης ροής εργασιών. Γενικά χρησιμοποιείται από μεγάλα έργα με εκατοντάδες συνεργάτες; Ένα διάσημο παράδειγμα είναι ο πυρήνας του Linux.Διάφοροι διαχειριστές ολοκλήρωσης είναι υπεύθυνοι για ορισμένα μέρη του χώρου αποθήκευσης; όπου ονομάζονται υπολοχαγοί. Όλες οι υπολοχαγοί έχουν ένα διαχειριστή ολοκλήρωσης γνωστό ως καλοκάγαθο δικτάτορα. Ο χορος αποθηκευσησ του δικτακτορα χρησιμοποιητε σαν αναφορα απο το οποιο ολοι οι συνεργατες χριαζεται να τραβιξουν (pull). Η διαδικασία λειτουργεί ως εξής (βλ. Σχήμα 5-3):

1.	Οι τακτοικοι προγραματιστες δουλευουν στο τοπικο τους παραρτημα και επανατοποθετουν την δουλεια τους πανω απο το αρχηκό. Το αρχηκο παραρτημα ειναι αυτο του Δικτατορα.
2.	Οι Αξιοματικοι ενονουν τα παραρτηματα των προγραματιστων σε αυτα τον αρχηγικων τους.
3.	Οι Δικτατορες ενωνουν τα αρχηγικα παραρτηματα των Αξιωμτικων σε αυτα των αρχηγικων Δικτακτορων.
4.	Ο Δικτατορας ωθει το το αρχηκο στο χορο αποθηκευσηε που ειναι για αναφορα οστε αλλοι προγραματιστες να μπορουν να δουλεψουν με αυτο.

Insert 18333fig0503.png  
Σχήμα 5-3. Φιλανθρωπική ροής εργασιών δικτάτορα.

Αυτό το είδος της ροής εργασιών δεν είναι κοινό, αλλά μπορεί να είναι χρήσιμο σε πολύ μεγάλα έργα ή σε περιβάλλοντα υψηλής ιεραρχίας, επειδή, όπως επιτρέπει ο επικεφαλής του έργου (ο δικτάτορας) να αναθέσει μεγάλο μέρος του έργου και να συλλέγουν μεγάλα υποσύνολα του κώδικα σε πολλαπλά σημεία πριν από την ενσωμάτωση.

Αυτές είναι ορισμένες ροές εργασιών που χρησιμοποιούνται συνήθως και ειναι εφαρμοσημες με ένα κατανεμημένο σύστημα όπως το Git, αλλα μπορειτε να δειτε να υπαρχουν αρκετες παραλαγες και να τεριαζουν σε καποια ροη εργασιας σας. Τώρα που μπορείτε να καθορίζετε ποιος συνδυασμός ροής εργασιών μπορεί να λειτουργήσει για σας, θα καλύψουμε ορισμένα πιο συγκεκριμένα παραδείγματα για το πώς να επιτύχει τους κύριους ρόλους που συνθέτουν τις διαφορετικές ροές.

## Συμβολή στο έργο ##

Ξέρετε τι είναι οι διαφορετικές ροές εργασίας, και θα πρέπει να έχετε μια αρκετά καλή κατανόηση θεμελιώδους χρήσης του Git. Σε αυτή την ενότητα, θα μάθετε για μερικά κοινά μοντέλα για τη συμβολή στο έργο.

Η κύρια δυσκολία με την περιγραφή αυτής της διαδικασίας είναι ότι υπάρχει ένας τεράστιος αριθμός των παραλλαγών σχετικά με το πώς έχει κάνει. Επειδή είναι πολύ ευέλικτο, οι άνθρωποι μπορούν και συνεργάζονται με πολλούς τρόπους, και είναι προβληματικό για την περιγραφή το πώς θα πρέπει να συνεισφέρουμε σε ένα έργο — Κάθε έργο είναι λίγο διαφορετικό. Μερικες απο τοις εμπλεκομενες μεταβλητες ειναι το ποσοι ειναι οι ενεργοι συντελεστες του εργου, η επιλεγμενη ροη εργασιας, δικαίωματα πρόσβασης, και πιθανόν η εξωτερική μέθοδος συνεισφοράς.

Η πρωτη μεταβλητη ειναι ο αριθμος των ενεργων συντελεστων. Ποσοι χρηστες ειναι ενεργοι στο να συνησφερουν στον κωδικα στο Project αυτο, και ποσο συχνα? Σε πολλές περιπτώσεις, θα έχετε δύο ή τρεις προγραμματιστές με λίγες αληλεπιδρασεις σε μια ημέρα, ή ενδεχομένως, λιγότερο για κάπως πιο αδρανή έργα.ια πολύ μεγάλες επιχειρήσεις και έργα, ο αριθμός των προγραμματιστών θα μπορούσε να είναι σε χιλιάδες,με δεκάδες και ακόμη και εκατοντάδες από patches που έρχονται κάθε μέρα. Αυτό είναι σημαντικό επειδή με όλο και περισσότερους προγραμματιστές, εχεται προβληματα στο να ειστε συγουροι πως θα εχετε σωστη εφαρμογη κωδικα και θα μπορει να συνενοθει. Οι αλλαγες που υποβαλεται μπορει να ειναι καθίστανται άνευ αντικειμένου ή σοβαρα κατεστραμενες απο δουλεια οπου εγηνε στην συνενοση στην περιοδο που δουλευατε ή οσο οι αλλαγες σας περιμεναν να εγγριθουν ή να εφαρμοστουν. Πώς μπορείτε να κρατήσετε τον κωδικό σας συνεχώς ενημερωμένο και έγκυρα ενημερομενο?

Η επόμενη μεταβλητή είναι η ροής εργασιών σε χρήση για το έργο. Είναι της κεντρικοποιημενης μορφης, με κάθε developer να έχει ίση πρόσβαση εγγραφής στην κύριο κωδικα? Μήπως το έργο έχει ένα διαχειριστή και συντηρητή ενσωμάτωση που ελέγχει όλα τα patches? Είναι όλα τα patches αξιολογιμενα και εχουν εγκριθεί απο κριτες? Ειστε εμπλεκομενος στην εν λογο διαδικασια? Είναι το σύστημα υπολοχαγών στη θέση του, και δεν θα πρέπει να υποβάλετε την εργασία σας σε αυτους πρώτα?

Το επομενο θεμα ειναι προσβαση για το commit(παραδοση). Η ροή εργασίας που απαιτείται προκειμένου να συνεισφέρουμε σε ένα έργο είναι πολύ διαφορετική εάν έχετε πρόσβαση εγγραφής στο έργο από ό, τι αν δεν εχετε. Αν δεν έχετε πρόσβαση εγγραφής, πώς το έργο προτιμούν να αποδεχθούν την συμβολησας στο έργο? Διαθέτει καποια πολιτική; Πόσο είναι το έργο που συμβάλλετε σε έναν χρόνο? Πόσο συχνά συμβάλλετε?

Ολα αυτα τα ερωτηματα μπορουν να σας επιρεασουν στο πως συμβαλετε ενεργα σε ενα project και τι ροες εργασιων προτιμουντε ή ειναι διαθεσημες σε εσας. Θα καλυψουμε τις πτυχες απο καθε μια απο αυτες τις ερωτησει σε μια σειρα περιτωσεων πηγενοντας απο το πιο απλο στο πιο συνθετο, θα πρεπει να ειστε σε θεση να μπορειτε να δημιουργησεται συγγενκριμενες ροες εργασιας για να κανετε πρακτηκη πανω σε αυτα τα παραδειγματα.

### Κατευθυντηριες γραμμες για να κανεται Commit ###

Πριν αρχίσετε να ψάχνετε σε ειδικές περιπτώσεις χρήσης, εδώ είναι μια γρήγορη σημείωση σχετικά με τα commit μηνύματα. Έχοντας μια καλή κατευθυντήρια γραμμή για τη δημιουργία commit και ακολουθοντας τα καθιστά την εργασία με Git και την  συνεργάσεια με άλλους πολύ πιο εύκολη. Το Git παρέχει ένα έγγραφο που καθορίζει μια σειρά από καλές συμβουλές για τη δημιουργία commit από την οποία να υποβάλλετε patch — yμπορείτε να το διαβάσετε στον πηγαίο κώδικα Git στο αρχειο `Documentation/SubmittingPatches`.

Αρχηκα δεν θελεται να υποβαλετε καποιο whitespace λαθος. Το Git σας διευκολεινει για να το ελενξεται — πριν κανεται commit, τρεχτε την εντολη `git diff --check`, η οποια βρησκει πιθανα whitespace λαθη και σας δημιουργει μια λιστα με αυτα. Εδω υπαρχει ενα παραδειγμα, οπου εχω αντικαταστισει το κοκκινο χρωμα του τερματικου με `X`s:

	$ git diff --check
	lib/simplegit.rb:5: trailing whitespace.
	+    @git_dir = File.expand_path(git_dir)XX
	lib/simplegit.rb:7: trailing whitespace.
	+ XXXXXXXXXXX
	lib/simplegit.rb:26: trailing whitespace.
	+    def command(git_cmd)XXXX

Εαν τρεξεται την εντολη αυτη πριν κανεται commit, θα σας πει πως προκειτε να κανετε commit whitespace λαθη τα οποια ειναι ενοχλητικα για τους αλλους προγραμματιστες.

Στη συνέχεια, προσπαθήστε να κάνετε κάθε commit με ξεχωριστό changeset. Εαν μπορεις, προσπαθυσε να κανεις τις αλλαγες σου "ευκολοχονευτες" — μην προγραματιζεις ολο το σαββατοκυριακο σε πεντε διαφορετικα θεματα και μετα τα κανεις submit ολα μαζι σαν ενα μαζικο commit την Δευτερα. Ακομα και αν δεν κανεις commit μεσα στο σαββατοκυριακο, χρησιμοποιησε την περιοχη ανασυγροτισης την Δευτερα να χωρισεις την δουλεια σου σε ενα commit τουλαχισον ανα θεμα, με ενα χρησημο μυνημα σε καθε commit. Εαν καποιες αλλαγες γινονται στον ιδιο αρχειο, προσπαθυστε να χρησημοποιησετε το `git add --patch` για να ορανωσετε μερικως τα αρχεια σας (Καλυπτεται αναλυτικα στο Κεφαλαιο 6). Το στιγμιοτυπο του project στην κοριφη του branch ειναι ιδιο ητε κανεται ενα η πεντε commit,αρκει ολες οι αλλαγες να προστηθονται στο ιδιο σημειο, γι αυτο προσπαθστε να κανεται τα πραγματα πιο ευκολα για τους σιναδευλφους προγραμματιστες οταν προκειτε να εξετασουν τοις αλλαγες σας. Αυτη η προσεγγιση  επιτρεπει να γινετε πιο ευκολα το  να επαναφερεται ενα απο τα Changesets αν χριαστει αργοτερα. Το κεφαλεο 6 περιγραφει εναν συνολο απο χρησιμα τρικ στο Git για ξαναγράψιμο του ιστορικου και αλληέπιδρασης με τα αρχεία σταδιοποίησης — χρησιμοποιηστε αυτα τα εργαλεια για να σας βοηθεισουν να δημιουργεισεται ενα κατανοητο ιστορικο.

Το τελευτεο πραγμα που πρεπει να θυμαστε ειναι το μηνυμα του commit. Εχοντας την σηνυθεια να δημιουγειται ποιοτικα μυνηματα commit κανει την χρηση και την συννεργασια με το Git πιο ευκολη. Σαν γενικος κανονας, το μυνημα θα ξεκινα με μια γραμμη το οποιο δεν ειναι παραπανο απο 50 χαρακτηρες και το οποιο θα περιγραφει το σετ των αλλαγων συνοπτικα, ακολουθουμενο απο μια κενη γραμη και μετ μια συνοπτικη περιγραφη.Το εργο του Git απαιτει οτι η πιο λεπτομερεις εξηγησεις περιλαμβανουν το κινητρο σας για την αλλαγη και να αντιπαραβαλει την εφαρμογη της με προηγουμενες συμπρεριφορες —αυτή είναι μια καλή κατευθυντήρια γραμμή για να ακολουθήσεται. Είναι επίσης μια καλή ιδέα να χρησιμοποιήσετε την επιτακτική ανάγκη ενεστώτα χρόνου σε αυτά τα μηνύματα. Με αλλα λογια καντε χρηση εντολων. Αντι για  "I added tests for" ή "Adding tests for," χρησιμοποιηστε "Add tests for."
Εδώ είναι ένα πρότυπο αρχικά γραμμένο από τον Tim Pope στο tpope.net:

	Σύντομη (50 χαρακτήρες ή λιγότερο) περίληψη των αλλαγών

	More detailed explanatory text, if necessary.  Wrap it to about 72
	characters or so.  In some contexts, the first line is treated as the
	subject of an email and the rest of the text as the body.  The blank
	line separating the summary from the body is critical (unless you omit
	the body entirely); tools like rebase can get confused if you run the
	two together.

	Περαιτέρω σκέψεις έρχονται μετά από κενές γραμμές.

	 - Σημεία Bullet είναι εντάξει, επίσης

	 -Τυπικά μία παύλα ή αστερίσκος χρησιμοποιείται για τη σφαίρα, απο το οποιο προηγειτε
	   μονο κενο, με κενες γραμμες στο ενδιαμεσο.

Εαν ολα τα μηνυματα σας μοιαζουν με αυτο τοτε τα πραγματα θα ειναι πολυ πιο ευκολα για εσας και τουσ προγραματιστες που εργαζονται μαζι σας. Το Git εχει πολυ καλα καθορισμενα τα μηνυματα για commit — Σας ενθαρινω να τρεξεται την εντολη  `git log --no-merges` και θα δειται ενα ομορφα σχηματισμενο ιστορικο απο commit πως μοιαζει.

Στα ακολουθα παραδειγματα, και μεσα απο το μεγαλητερο μερος του βιβλιου, και για λογους συντομια δεν μορφοποιω τα μυνηματα ομορφα οπως αυτα εδω; σε αντιθεση, χρησιμοποιηται η επολογη `-m` για  `git commit`. Καντετα οπως σας τα λεω και οχι οπως τα κανω.

### Μικρες Προσωπικες Ομαδες ###

Η πιο απλή ρύθμιση που είναι πιθανό να συναντήσετε είναι ένα ιδιωτικό έργο με έναν ή δύο άλλους προγραμματιστές. Με ιδιωτικό, εννοώ κλειστού κώδικα - not read - προσβάση για τον έξω κόσμο. Εσεις και οι αλλοι προγραμματιστες εχεται προσβαση για push στον αποθυκευτικο χωρο.

Σε αυτό το περιβάλλον, μπορείτε να ακολουθήσετε μια ροή εργασίας παρόμοιο με αυτό που μπορείτε να κάνετε, όταν χρησιμοποιεί το Subversion ή άλλο κεντρικοποιημενο σύστημα. Μπορειτε ακομα να εχετε πλεονεκτηματα οπως offline  commit και branching η συνενοση αρχειων, αλλα η ροη εργασιων θα ειναι πολυ πιο απλη;η βασικη διαφορα ειναι οτι η συνενοση γινεται στην πλευρα του χρηστη και οχι στον σερβερ οταν γινετα το commit.
Ας δούμε τι μπορεί να μοιάζει όταν δύο προγραμματιστές να αρχίσουν να εργάζονται μαζί με ένα κοινό αποθετήριο. Ο πρωτος πογραμματιστης,ο John, κλονοποιει το αποθετηριο, κανει μια αλλαγη, και την κανει commit τοπικα. (Αντικαθηστο το μυνημα με `...` σε αυτα τα παραδειγματα για να μειωθει ο ογκος τους.)

	# John's Machine
	$ git clone john@githost:simplegit.git
	Initialized empty Git repository in /home/john/simplegit/.git/
	...
	$ cd simplegit/
	$ vim lib/simplegit.rb 
	$ git commit -am 'removed invalid default value'
	[master 738ee87] removed invalid default value
	 1 files changed, 1 insertions(+), 1 deletions(-)

Ο δευτερος πογραμματιστης,η Jessica, κανει το ιδιο πραγμα —κλονοποιει το αποθετηριο και κανει commit τις αλλαγες:

	# Jessica's Machine
	$ git clone jessica@githost:simplegit.git
	Initialized empty Git repository in /home/jessica/simplegit/.git/
	...
	$ cd simplegit/
	$ vim TODO 
	$ git commit -am 'add reset task'
	[master fbff5bc] add reset task
	 1 files changed, 1 insertions(+), 0 deletions(-)

Τωρα,η Jessica στελνει την δουλεια της στον server:

	# Jessica's Machine
	$ git push origin master
	...
	To jessica@githost:simplegit.git
	   1edee6b..fbff5bc  master -> master

Ο John προσπαθει να στηλει την δουλεια του και αυτος:

	# John's Machine
	$ git push origin master
	To john@githost:simplegit.git
	 ! [rejected]        master -> master (non-fast forward)
	error: failed to push some refs to 'john@githost:simplegit.git'

Στον John δεν του επιτρεπεται να στηλει γιατι η Jessica εστηλε στον ενδιαμεσο χρονο. This is especially important to understand if you’re used to Subversion, because you’ll notice that the two developers didn’t edit the same file. Although Subversion automatically does such a merge on the server if different files are edited, in Git you must merge the commits locally. John has to fetch Jessica’s changes and merge them in before he will be allowed to push:

	$ git fetch origin
	...
	From john@githost:simplegit
	 + 049d078...fbff5bc master     -> origin/master

At this point, John’s local repository looks something like Figure 5-4.

Insert 18333fig0504.png 
Figure 5-4. John’s initial repository.

John has a reference to the changes Jessica pushed up, but he has to merge them into his own work before he is allowed to push:

	$ git merge origin/master
	Merge made by recursive.
	 TODO |    1 +
	 1 files changed, 1 insertions(+), 0 deletions(-)

The merge goes smoothly — John’s commit history now looks like Figure 5-5.

Insert 18333fig0505.png 
Figure 5-5. John’s repository after merging origin/master.

Now, John can test his code to make sure it still works properly, and then he can push his new merged work up to the server:

	$ git push origin master
	...
	To john@githost:simplegit.git
	   fbff5bc..72bbc59  master -> master

Finally, John’s commit history looks like Figure 5-6.

Insert 18333fig0506.png 
Figure 5-6. John’s history after pushing to the origin server.

In the meantime, Jessica has been working on a topic branch. She’s created a topic branch called `issue54` and done three commits on that branch. She hasn’t fetched John’s changes yet, so her commit history looks like Figure 5-7.

Insert 18333fig0507.png 
Figure 5-7. Jessica’s initial commit history.

Jessica wants to sync up with John, so she fetches:

	# Jessica's Machine
	$ git fetch origin
	...
	From jessica@githost:simplegit
	   fbff5bc..72bbc59  master     -> origin/master

That pulls down the work John has pushed up in the meantime. Jessica’s history now looks like Figure 5-8.

Insert 18333fig0508.png 
Figure 5-8. Jessica’s history after fetching John’s changes.

Jessica thinks her topic branch is ready, but she wants to know what she has to merge her work into so that she can push. She runs `git log` to find out:

	$ git log --no-merges origin/master ^issue54
	commit 738ee872852dfaa9d6634e0dea7a324040193016
	Author: John Smith <jsmith@example.com>
	Date:   Fri May 29 16:01:27 2009 -0700

	    removed invalid default value

Now, Jessica can merge her topic work into her master branch, merge John’s work (`origin/master`) into her `master` branch, and then push back to the server again. First, she switches back to her master branch to integrate all this work:

	$ git checkout master
	Switched to branch "master"
	Your branch is behind 'origin/master' by 2 commits, and can be fast-forwarded.

She can merge either `origin/master` or `issue54` first — they’re both upstream, so the order doesn’t matter. The end snapshot should be identical no matter which order she chooses; only the history will be slightly different. She chooses to merge in `issue54` first:

	$ git merge issue54
	Updating fbff5bc..4af4298
	Fast forward
	 README           |    1 +
	 lib/simplegit.rb |    6 +++++-
	 2 files changed, 6 insertions(+), 1 deletions(-)

No problems occur; as you can see it was a simple fast-forward. Now Jessica merges in John’s work (`origin/master`):

	$ git merge origin/master
	Auto-merging lib/simplegit.rb
	Merge made by recursive.
	 lib/simplegit.rb |    2 +-
	 1 files changed, 1 insertions(+), 1 deletions(-)

Everything merges cleanly, and Jessica’s history looks like Figure 5-9.

Insert 18333fig0509.png 
Figure 5-9. Jessica’s history after merging John’s changes.

Now `origin/master` is reachable from Jessica’s `master` branch, so she should be able to successfully push (assuming John hasn’t pushed again in the meantime):

	$ git push origin master
	...
	To jessica@githost:simplegit.git
	   72bbc59..8059c15  master -> master

Each developer has committed a few times and merged each other’s work successfully; see Figure 5-10.

Insert 18333fig0510.png 
Figure 5-10. Jessica’s history after pushing all changes back to the server.

That is one of the simplest workflows. You work for a while, generally in a topic branch, and merge into your master branch when it’s ready to be integrated. When you want to share that work, you merge it into your own master branch, then fetch and merge `origin/master` if it has changed, and finally push to the `master` branch on the server. The general sequence is something like that shown in Figure 5-11.

Insert 18333fig0511.png 
Figure 5-11. General sequence of events for a simple multiple-developer Git workflow.

### Private Managed Team ###

In this next scenario, you’ll look at contributor roles in a larger private group. You’ll learn how to work in an environment where small groups collaborate on features and then those team-based contributions are integrated by another party.

Let’s say that John and Jessica are working together on one feature, while Jessica and Josie are working on a second. In this case, the company is using a type of integration-manager workflow where the work of the individual groups is integrated only by certain engineers, and the `master` branch of the main repo can be updated only by those engineers. In this scenario, all work is done in team-based branches and pulled together by the integrators later.

Let’s follow Jessica’s workflow as she works on her two features, collaborating in parallel with two different developers in this environment. Assuming she already has her repository cloned, she decides to work on `featureA` first. She creates a new branch for the feature and does some work on it there:

	# Jessica's Machine
	$ git checkout -b featureA
	Switched to a new branch "featureA"
	$ vim lib/simplegit.rb
	$ git commit -am 'add limit to log function'
	[featureA 3300904] add limit to log function
	 1 files changed, 1 insertions(+), 1 deletions(-)

At this point, she needs to share her work with John, so she pushes her `featureA` branch commits up to the server. Jessica doesn’t have push access to the `master` branch — only the integrators do — so she has to push to another branch in order to collaborate with John:

	$ git push origin featureA
	...
	To jessica@githost:simplegit.git
	 * [new branch]      featureA -> featureA

Jessica e-mails John to tell him that she’s pushed some work into a branch named `featureA` and he can look at it now. While she waits for feedback from John, Jessica decides to start working on `featureB` with Josie. To begin, she starts a new feature branch, basing it off the server’s `master` branch:

	# Jessica's Machine
	$ git fetch origin
	$ git checkout -b featureB origin/master
	Switched to a new branch "featureB"

Now, Jessica makes a couple of commits on the `featureB` branch:

	$ vim lib/simplegit.rb
	$ git commit -am 'made the ls-tree function recursive'
	[featureB e5b0fdc] made the ls-tree function recursive
	 1 files changed, 1 insertions(+), 1 deletions(-)
	$ vim lib/simplegit.rb
	$ git commit -am 'add ls-files'
	[featureB 8512791] add ls-files
	 1 files changed, 5 insertions(+), 0 deletions(-)

Jessica’s repository looks like Figure 5-12.

Insert 18333fig0512.png 
Figure 5-12. Jessica’s initial commit history.

She’s ready to push up her work, but gets an e-mail from Josie that a branch with some initial work on it was already pushed to the server as `featureBee`. Jessica first needs to merge those changes in with her own before she can push to the server. She can then fetch Josie’s changes down with `git fetch`:

	$ git fetch origin
	...
	From jessica@githost:simplegit
	 * [new branch]      featureBee -> origin/featureBee

Jessica can now merge this into the work she did with `git merge`:

	$ git merge origin/featureBee
	Auto-merging lib/simplegit.rb
	Merge made by recursive.
	 lib/simplegit.rb |    4 ++++
	 1 files changed, 4 insertions(+), 0 deletions(-)

There is a bit of a problem — she needs to push the merged work in her `featureB` branch to the `featureBee` branch on the server. She can do so by specifying the local branch followed by a colon (:) followed by the remote branch to the `git push` command:

	$ git push origin featureB:featureBee
	...
	To jessica@githost:simplegit.git
	   fba9af8..cd685d1  featureB -> featureBee

This is called a _refspec_. See Chapter 9 for a more detailed discussion of Git refspecs and different things you can do with them.

Next, John e-mails Jessica to say he’s pushed some changes to the `featureA` branch and ask her to verify them. She runs a `git fetch` to pull down those changes:

	$ git fetch origin
	...
	From jessica@githost:simplegit
	   3300904..aad881d  featureA   -> origin/featureA

Then, she can see what has been changed with `git log`:

	$ git log origin/featureA ^featureA
	commit aad881d154acdaeb2b6b18ea0e827ed8a6d671e6
	Author: John Smith <jsmith@example.com>
	Date:   Fri May 29 19:57:33 2009 -0700

	    changed log output to 30 from 25

Finally, she merges John’s work into her own `featureA` branch:

	$ git checkout featureA
	Switched to branch "featureA"
	$ git merge origin/featureA
	Updating 3300904..aad881d
	Fast forward
	 lib/simplegit.rb |   10 +++++++++-
	1 files changed, 9 insertions(+), 1 deletions(-)

Jessica wants to tweak something, so she commits again and then pushes this back up to the server:

	$ git commit -am 'small tweak'
	[featureA ed774b3] small tweak
	 1 files changed, 1 insertions(+), 1 deletions(-)
	$ git push origin featureA
	...
	To jessica@githost:simplegit.git
	   3300904..ed774b3  featureA -> featureA

Jessica’s commit history now looks something like Figure 5-13.

Insert 18333fig0513.png 
Figure 5-13. Jessica’s history after committing on a feature branch.

Jessica, Josie, and John inform the integrators that the `featureA` and `featureBee` branches on the server are ready for integration into the mainline. After they integrate these branches into the mainline, a fetch will bring down the new merge commits, making the commit history look like Figure 5-14.

Insert 18333fig0514.png 
Figure 5-14. Jessica’s history after merging both her topic branches.

Many groups switch to Git because of this ability to have multiple teams working in parallel, merging the different lines of work late in the process. The ability of smaller subgroups of a team to collaborate via remote branches without necessarily having to involve or impede the entire team is a huge benefit of Git. The sequence for the workflow you saw here is something like Figure 5-15.

Insert 18333fig0515.png 
Figure 5-15. Basic sequence of this managed-team workflow.

### Public Small Project ###

Contributing to public projects is a bit different. Because you don’t have the permissions to directly update branches on the project, you have to get the work to the maintainers some other way. This first example describes contributing via forking on Git hosts that support easy forking. The repo.or.cz and GitHub hosting sites both support this, and many project maintainers expect this style of contribution. The next section deals with projects that prefer to accept contributed patches via e-mail.

First, you’ll probably want to clone the main repository, create a topic branch for the patch or patch series you’re planning to contribute, and do your work there. The sequence looks basically like this:

	$ git clone (url)
	$ cd project
	$ git checkout -b featureA
	$ (work)
	$ git commit
	$ (work)
	$ git commit

You may want to use `rebase -i` to squash your work down to a single commit, or rearrange the work in the commits to make the patch easier for the maintainer to review — see Chapter 6 for more information about interactive rebasing.

When your branch work is finished and you’re ready to contribute it back to the maintainers, go to the original project page and click the "Fork" button, creating your own writable fork of the project. You then need to add in this new repository URL as a second remote, in this case named `myfork`:

	$ git remote add myfork (url)

You need to push your work up to it. It’s easiest to push the remote branch you’re working on up to your repository, rather than merging into your master branch and pushing that up. The reason is that if the work isn’t accepted or is cherry picked, you don’t have to rewind your master branch. If the maintainers merge, rebase, or cherry-pick your work, you’ll eventually get it back via pulling from their repository anyhow:

	$ git push myfork featureA

When your work has been pushed up to your fork, you need to notify the maintainer. This is often called a pull request, and you can either generate it via the website — GitHub has a "pull request" button that automatically messages the maintainer — or run the `git request-pull` command and e-mail the output to the project maintainer manually.

The `request-pull` command takes the base branch into which you want your topic branch pulled and the Git repository URL you want them to pull from, and outputs a summary of all the changes you’re asking to be pulled in. For instance, if Jessica wants to send John a pull request, and she’s done two commits on the topic branch she just pushed up, she can run this:

	$ git request-pull origin/master myfork
	The following changes since commit 1edee6b1d61823a2de3b09c160d7080b8d1b3a40:
	  John Smith (1):
	        added a new function

	are available in the git repository at:

	  git://githost/simplegit.git featureA

	Jessica Smith (2):
	      add limit to log function
	      change log output to 30 from 25

	 lib/simplegit.rb |   10 +++++++++-
	 1 files changed, 9 insertions(+), 1 deletions(-)

The output can be sent to the maintainer—it tells them where the work was branched from, summarizes the commits, and tells where to pull this work from.

On a project for which you’re not the maintainer, it’s generally easier to have a branch like `master` always track `origin/master` and to do your work in topic branches that you can easily discard if they’re rejected.  Having work themes isolated into topic branches also makes it easier for you to rebase your work if the tip of the main repository has moved in the meantime and your commits no longer apply cleanly. For example, if you want to submit a second topic of work to the project, don’t continue working on the topic branch you just pushed up — start over from the main repository’s `master` branch:

	$ git checkout -b featureB origin/master
	$ (work)
	$ git commit
	$ git push myfork featureB
	$ (email maintainer)
	$ git fetch origin

Now, each of your topics is contained within a silo — similar to a patch queue — that you can rewrite, rebase, and modify without the topics interfering or interdepending on each other as in Figure 5-16.

Insert 18333fig0516.png 
Figure 5-16. Initial commit history with featureB work.

Let’s say the project maintainer has pulled in a bunch of other patches and tried your first branch, but it no longer cleanly merges. In this case, you can try to rebase that branch on top of `origin/master`, resolve the conflicts for the maintainer, and then resubmit your changes:

	$ git checkout featureA
	$ git rebase origin/master
	$ git push -f myfork featureA

This rewrites your history to now look like Figure 5-17.

Insert 18333fig0517.png 
Figure 5-17. Commit history after featureA work.

Because you rebased the branch, you have to specify the `-f` to your push command in order to be able to replace the `featureA` branch on the server with a commit that isn’t a descendant of it. An alternative would be to push this new work to a different branch on the server (perhaps called `featureAv2`).

Let’s look at one more possible scenario: the maintainer has looked at work in your second branch and likes the concept but would like you to change an implementation detail. You’ll also take this opportunity to move the work to be based off the project’s current `master` branch. You start a new branch based off the current `origin/master` branch, squash the `featureB` changes there, resolve any conflicts, make the implementation change, and then push that up as a new branch:

	$ git checkout -b featureBv2 origin/master
	$ git merge --no-commit --squash featureB
	$ (change implementation)
	$ git commit
	$ git push myfork featureBv2

The `--squash` option takes all the work on the merged branch and squashes it into one non-merge commit on top of the branch you’re on. The `--no-commit` option tells Git not to automatically record a commit. This allows you to introduce all the changes from another branch and then make more changes before recording the new commit.

Now you can send the maintainer a message that you’ve made the requested changes and they can find those changes in your `featureBv2` branch (see Figure 5-18).

Insert 18333fig0518.png 
Figure 5-18. Commit history after featureBv2 work.

### Public Large Project ###

Many larger projects have established procedures for accepting patches — you’ll need to check the specific rules for each project, because they will differ. However, many larger public projects accept patches via a developer mailing list, so I’ll go over an example of that now.

The workflow is similar to the previous use case — you create topic branches for each patch series you work on. The difference is how you submit them to the project. Instead of forking the project and pushing to your own writable version, you generate e-mail versions of each commit series and e-mail them to the developer mailing list:

	$ git checkout -b topicA
	$ (work)
	$ git commit
	$ (work)
	$ git commit

Now you have two commits that you want to send to the mailing list. You use `git format-patch` to generate the mbox-formatted files that you can e-mail to the list — it turns each commit into an e-mail message with the first line of the commit message as the subject and the rest of the message plus the patch that the commit introduces as the body. The nice thing about this is that applying a patch from an e-mail generated with `format-patch` preserves all the commit information properly, as you’ll see more of in the next section when you apply these commits:

	$ git format-patch -M origin/master
	0001-add-limit-to-log-function.patch
	0002-changed-log-output-to-30-from-25.patch

The `format-patch` command prints out the names of the patch files it creates. The `-M` switch tells Git to look for renames. The files end up looking like this:

	$ cat 0001-add-limit-to-log-function.patch 
	From 330090432754092d704da8e76ca5c05c198e71a8 Mon Sep 17 00:00:00 2001
	From: Jessica Smith <jessica@example.com>
	Date: Sun, 6 Apr 2008 10:17:23 -0700
	Subject: [PATCH 1/2] add limit to log function

	Limit log functionality to the first 20

	---
	 lib/simplegit.rb |    2 +-
	 1 files changed, 1 insertions(+), 1 deletions(-)

	diff --git a/lib/simplegit.rb b/lib/simplegit.rb
	index 76f47bc..f9815f1 100644
	--- a/lib/simplegit.rb
	+++ b/lib/simplegit.rb
	@@ -14,7 +14,7 @@ class SimpleGit
	   end

	   def log(treeish = 'master')
	-    command("git log #{treeish}")
	+    command("git log -n 20 #{treeish}")
	   end

	   def ls_tree(treeish = 'master')
	-- 
	1.6.2.rc1.20.g8c5b.dirty

You can also edit these patch files to add more information for the e-mail list that you don’t want to show up in the commit message. If you add text between the `--` line and the beginning of the patch (the `lib/simplegit.rb` line), then developers can read it; but applying the patch excludes it.

To e-mail this to a mailing list, you can either paste the file into your e-mail program or send it via a command-line program. Pasting the text often causes formatting issues, especially with "smarter" clients that don’t preserve newlines and other whitespace appropriately. Luckily, Git provides a tool to help you send properly formatted patches via IMAP, which may be easier for you. I’ll demonstrate how to send a patch via Gmail, which happens to be the e-mail agent I use; you can read detailed instructions for a number of mail programs at the end of the aforementioned `Documentation/SubmittingPatches` file in the Git source code.

First, you need to set up the imap section in your `~/.gitconfig` file. You can set each value separately with a series of `git config` commands, or you can add them manually; but in the end, your config file should look something like this:

	[imap]
	  folder = "[Gmail]/Drafts"
	  host = imaps://imap.gmail.com
	  user = user@gmail.com
	  pass = p4ssw0rd
	  port = 993
	  sslverify = false

If your IMAP server doesn’t use SSL, the last two lines probably aren’t necessary, and the host value will be `imap://` instead of `imaps://`.
When that is set up, you can use `git send-email` to place the patch series in the Drafts folder of the specified IMAP server:

	$ git send-email *.patch
	0001-added-limit-to-log-function.patch
	0002-changed-log-output-to-30-from-25.patch
	Who should the emails appear to be from? [Jessica Smith <jessica@example.com>] 
	Emails will be sent from: Jessica Smith <jessica@example.com>
	Who should the emails be sent to? jessica@example.com
	Message-ID to be used as In-Reply-To for the first email? y

Then, Git spits out a bunch of log information looking something like this for each patch you’re sending:

	(mbox) Adding cc: Jessica Smith <jessica@example.com> from 
	  \line 'From: Jessica Smith <jessica@example.com>'
	OK. Log says:
	Sendmail: /usr/sbin/sendmail -i jessica@example.com
	From: Jessica Smith <jessica@example.com>
	To: jessica@example.com
	Subject: [PATCH 1/2] added limit to log function
	Date: Sat, 30 May 2009 13:29:15 -0700
	Message-Id: <1243715356-61726-1-git-send-email-jessica@example.com>
	X-Mailer: git-send-email 1.6.2.rc1.20.g8c5b.dirty
	In-Reply-To: <y>
	References: <y>

	Result: OK

At this point, you should be able to go to your Drafts folder, change the To field to the mailing list you’re sending the patch to, possibly CC the maintainer or person responsible for that section, and send it off.

### Summary ###

This section has covered a number of common workflows for dealing with several very different types of Git projects you’re likely to encounter and introduced a couple of new tools to help you manage this process. Next, you’ll see how to work the other side of the coin: maintaining a Git project. You’ll learn how to be a benevolent dictator or integration manager.

## Maintaining a Project ##

In addition to knowing how to effectively contribute to a project, you’ll likely need to know how to maintain one. This can consist of accepting and applying patches generated via `format-patch` and e-mailed to you, or integrating changes in remote branches for repositories you’ve added as remotes to your project. Whether you maintain a canonical repository or want to help by verifying or approving patches, you need to know how to accept work in a way that is clearest for other contributors and sustainable by you over the long run.

### Working in Topic Branches ###

When you’re thinking of integrating new work, it’s generally a good idea to try it out in a topic branch — a temporary branch specifically made to try out that new work. This way, it’s easy to tweak a patch individually and leave it if it’s not working until you have time to come back to it. If you create a simple branch name based on the theme of the work you’re going to try, such as `ruby_client` or something similarly descriptive, you can easily remember it if you have to abandon it for a while and come back later. The maintainer of the Git project tends to namespace these branches as well — such as `sc/ruby_client`, where `sc` is short for the person who contributed the work. 
As you’ll remember, you can create the branch based off your master branch like this:

	$ git branch sc/ruby_client master

Or, if you want to also switch to it immediately, you can use the `checkout -b` option:

	$ git checkout -b sc/ruby_client master

Now you’re ready to add your contributed work into this topic branch and determine if you want to merge it into your longer-term branches.

### Applying Patches from E-mail ###

If you receive a patch over e-mail that you need to integrate into your project, you need to apply the patch in your topic branch to evaluate it. There are two ways to apply an e-mailed patch: with `git apply` or with `git am`.

#### Applying a Patch with apply ####

If you received the patch from someone who generated it with the `git diff` or a Unix `diff` command, you can apply it with the `git apply` command. Assuming you saved the patch at `/tmp/patch-ruby-client.patch`, you can apply the patch like this:

	$ git apply /tmp/patch-ruby-client.patch

This modifies the files in your working directory. It’s almost identical to running a `patch -p1` command to apply the patch, although it’s more paranoid and accepts fewer fuzzy matches than patch. It also handles file adds, deletes, and renames if they’re described in the `git diff` format, which `patch` won’t do. Finally, `git apply` is an "apply all or abort all" model where either everything is applied or nothing is, whereas `patch` can partially apply patchfiles, leaving your working directory in a weird state. `git apply` is overall much more paranoid than `patch`. It won’t create a commit for you — after running it, you must stage and commit the changes introduced manually.

You can also use git apply to see if a patch applies cleanly before you try actually applying it — you can run `git apply --check` with the patch:

	$ git apply --check 0001-seeing-if-this-helps-the-gem.patch 
	error: patch failed: ticgit.gemspec:1
	error: ticgit.gemspec: patch does not apply

If there is no output, then the patch should apply cleanly. This command also exits with a non-zero status if the check fails, so you can use it in scripts if you want.

#### Applying a Patch with am ####

If the contributor is a Git user and was good enough to use the `format-patch` command to generate their patch, then your job is easier because the patch contains author information and a commit message for you. If you can, encourage your contributors to use `format-patch` instead of `diff` to generate patches for you. You should only have to use `git apply` for legacy patches and things like that.

To apply a patch generated by `format-patch`, you use `git am`. Technically, `git am` is built to read an mbox file, which is a simple, plain-text format for storing one or more e-mail messages in one text file. It looks something like this:

	From 330090432754092d704da8e76ca5c05c198e71a8 Mon Sep 17 00:00:00 2001
	From: Jessica Smith <jessica@example.com>
	Date: Sun, 6 Apr 2008 10:17:23 -0700
	Subject: [PATCH 1/2] add limit to log function

	Limit log functionality to the first 20

This is the beginning of the output of the format-patch command that you saw in the previous section. This is also a valid mbox e-mail format. If someone has e-mailed you the patch properly using git send-email, and you download that into an mbox format, then you can point git am to that mbox file, and it will start applying all the patches it sees. If you run a mail client that can save several e-mails out in mbox format, you can save entire patch series into a file and then use git am to apply them one at a time. 

However, if someone uploaded a patch file generated via `format-patch` to a ticketing system or something similar, you can save the file locally and then pass that file saved on your disk to `git am` to apply it:

	$ git am 0001-limit-log-function.patch 
	Applying: add limit to log function

You can see that it applied cleanly and automatically created the new commit for you. The author information is taken from the e-mail’s `From` and `Date` headers, and the message of the commit is taken from the `Subject` and body (before the patch) of the e-mail. For example, if this patch was applied from the mbox example I just showed, the commit generated would look something like this:

	$ git log --pretty=fuller -1
	commit 6c5e70b984a60b3cecd395edd5b48a7575bf58e0
	Author:     Jessica Smith <jessica@example.com>
	AuthorDate: Sun Apr 6 10:17:23 2008 -0700
	Commit:     Scott Chacon <schacon@gmail.com>
	CommitDate: Thu Apr 9 09:19:06 2009 -0700

	   add limit to log function

	   Limit log functionality to the first 20

The `Commit` information indicates the person who applied the patch and the time it was applied. The `Author` information is the individual who originally created the patch and when it was originally created. 

But it’s possible that the patch won’t apply cleanly. Perhaps your main branch has diverged too far from the branch the patch was built from, or the patch depends on another patch you haven’t applied yet. In that case, the `git am` process will fail and ask you what you want to do:

	$ git am 0001-seeing-if-this-helps-the-gem.patch 
	Applying: seeing if this helps the gem
	error: patch failed: ticgit.gemspec:1
	error: ticgit.gemspec: patch does not apply
	Patch failed at 0001.
	When you have resolved this problem run "git am --resolved".
	If you would prefer to skip this patch, instead run "git am --skip".
	To restore the original branch and stop patching run "git am --abort".

This command puts conflict markers in any files it has issues with, much like a conflicted merge or rebase operation. You solve this issue much the same way — edit the file to resolve the conflict, stage the new file, and then run `git am --resolved` to continue to the next patch:

	$ (fix the file)
	$ git add ticgit.gemspec 
	$ git am --resolved
	Applying: seeing if this helps the gem

If you want Git to try a bit more intelligently to resolve the conflict, you can pass a `-3` option to it, which makes Git attempt a three-way merge. This option isn’t on by default because it doesn’t work if the commit the patch says it was based on isn’t in your repository. If you do have that commit — if the patch was based on a public commit — then the `-3` option is generally much smarter about applying a conflicting patch:

	$ git am -3 0001-seeing-if-this-helps-the-gem.patch 
	Applying: seeing if this helps the gem
	error: patch failed: ticgit.gemspec:1
	error: ticgit.gemspec: patch does not apply
	Using index info to reconstruct a base tree...
	Falling back to patching base and 3-way merge...
	No changes -- Patch already applied.

In this case, I was trying to apply a patch I had already applied. Without the `-3` option, it looks like a conflict.

If you’re applying a number of patches from an mbox, you can also run the `am` command in interactive mode, which stops at each patch it finds and asks if you want to apply it:

	$ git am -3 -i mbox
	Commit Body is:
	--------------------------
	seeing if this helps the gem
	--------------------------
	Apply? [y]es/[n]o/[e]dit/[v]iew patch/[a]ccept all 

This is nice if you have a number of patches saved, because you can view the patch first if you don’t remember what it is, or not apply the patch if you’ve already done so.

When all the patches for your topic are applied and committed into your branch, you can choose whether and how to integrate them into a longer-running branch.

### Checking Out Remote Branches ###

If your contribution came from a Git user who set up their own repository, pushed a number of changes into it, and then sent you the URL to the repository and the name of the remote branch the changes are in, you can add them as a remote and do merges locally.

For instance, if Jessica sends you an e-mail saying that she has a great new feature in the `ruby-client` branch of her repository, you can test it by adding the remote and checking out that branch locally:

	$ git remote add jessica git://github.com/jessica/myproject.git
	$ git fetch jessica
	$ git checkout -b rubyclient jessica/ruby-client

If she e-mails you again later with another branch containing another great feature, you can fetch and check out because you already have the remote setup.

This is most useful if you’re working with a person consistently. If someone only has a single patch to contribute once in a while, then accepting it over e-mail may be less time consuming than requiring everyone to run their own server and having to continually add and remove remotes to get a few patches. You’re also unlikely to want to have hundreds of remotes, each for someone who contributes only a patch or two. However, scripts and hosted services may make this easier — it depends largely on how you develop and how your contributors develop.

The other advantage of this approach is that you get the history of the commits as well. Although you may have legitimate merge issues, you know where in your history their work is based; a proper three-way merge is the default rather than having to supply a `-3` and hope the patch was generated off a public commit to which you have access.

If you aren’t working with a person consistently but still want to pull from them in this way, you can provide the URL of the remote repository to the `git pull` command. This does a one-time pull and doesn’t save the URL as a remote reference:

	$ git pull git://github.com/onetimeguy/project.git
	From git://github.com/onetimeguy/project
	 * branch            HEAD       -> FETCH_HEAD
	Merge made by recursive.

### Determining What Is Introduced ###

Now you have a topic branch that contains contributed work. At this point, you can determine what you’d like to do with it. This section revisits a couple of commands so you can see how you can use them to review exactly what you’ll be introducing if you merge this into your main branch.

It’s often helpful to get a review of all the commits that are in this branch but that aren’t in your master branch. You can exclude commits in the master branch by adding the `--not` option before the branch name. For example, if your contributor sends you two patches and you create a branch called `contrib` and applied those patches there, you can run this:

	$ git log contrib --not master
	commit 5b6235bd297351589efc4d73316f0a68d484f118
	Author: Scott Chacon <schacon@gmail.com>
	Date:   Fri Oct 24 09:53:59 2008 -0700

	    seeing if this helps the gem

	commit 7482e0d16d04bea79d0dba8988cc78df655f16a0
	Author: Scott Chacon <schacon@gmail.com>
	Date:   Mon Oct 22 19:38:36 2008 -0700

	    updated the gemspec to hopefully work better

To see what changes each commit introduces, remember that you can pass the `-p` option to `git log` and it will append the diff introduced to each commit.

To see a full diff of what would happen if you were to merge this topic branch with another branch, you may have to use a weird trick to get the correct results. You may think to run this:

	$ git diff master

This command gives you a diff, but it may be misleading. If your `master` branch has moved forward since you created the topic branch from it, then you’ll get seemingly strange results. This happens because Git directly compares the snapshots of the last commit of the topic branch you’re on and the snapshot of the last commit on the `master` branch. For example, if you’ve added a line in a file on the `master` branch, a direct comparison of the snapshots will look like the topic branch is going to remove that line.

If `master` is a direct ancestor of your topic branch, this isn’t a problem; but if the two histories have diverged, the diff will look like you’re adding all the new stuff in your topic branch and removing everything unique to the `master` branch.

What you really want to see are the changes added to the topic branch — the work you’ll introduce if you merge this branch with master. You do that by having Git compare the last commit on your topic branch with the first common ancestor it has with the master branch.

Technically, you can do that by explicitly figuring out the common ancestor and then running your diff on it:

	$ git merge-base contrib master
	36c7dba2c95e6bbb78dfa822519ecfec6e1ca649
	$ git diff 36c7db 

However, that isn’t convenient, so Git provides another shorthand for doing the same thing: the triple-dot syntax. In the context of the `diff` command, you can put three periods after another branch to do a `diff` between the last commit of the branch you’re on and its common ancestor with another branch:

	$ git diff master...contrib

This command shows you only the work your current topic branch has introduced since its common ancestor with master. That is a very useful syntax to remember.

### Integrating Contributed Work ###

When all the work in your topic branch is ready to be integrated into a more mainline branch, the question is how to do it. Furthermore, what overall workflow do you want to use to maintain your project? You have a number of choices, so I’ll cover a few of them.

#### Merging Workflows ####

One simple workflow merges your work into your `master` branch. In this scenario, you have a `master` branch that contains basically stable code. When you have work in a topic branch that you’ve done or that someone has contributed and you’ve verified, you merge it into your master branch, delete the topic branch, and then continue the process.  If we have a repository with work in two branches named `ruby_client` and `php_client` that looks like Figure 5-19 and merge `ruby_client` first and then `php_client` next, then your history will end up looking like Figure 5-20.

Insert 18333fig0519.png 
Figure 5-19. History with several topic branches.

Insert 18333fig0520.png
Figure 5-20. After a topic branch merge.

That is probably the simplest workflow, but it’s problematic if you’re dealing with larger repositories or projects.

If you have more developers or a larger project, you’ll probably want to use at least a two-phase merge cycle. In this scenario, you have two long-running branches, `master` and `develop`, in which you determine that `master` is updated only when a very stable release is cut and all new code is integrated into the `develop` branch. You regularly push both of these branches to the public repository. Each time you have a new topic branch to merge in (Figure 5-21), you merge it into `develop` (Figure 5-22); then, when you tag a release, you fast-forward `master` to wherever the now-stable `develop` branch is (Figure 5-23).

Insert 18333fig0521.png 
Figure 5-21. Before a topic branch merge.

Insert 18333fig0522.png 
Figure 5-22. After a topic branch merge.

Insert 18333fig0523.png 
Figure 5-23. After a topic branch release.

This way, when people clone your project’s repository, they can either check out master to build the latest stable version and keep up to date on that easily, or they can check out develop, which is the more cutting-edge stuff.
You can also continue this concept, having an integrate branch where all the work is merged together. Then, when the codebase on that branch is stable and passes tests, you merge it into a develop branch; and when that has proven itself stable for a while, you fast-forward your master branch.

#### Large-Merging Workflows ####

The Git project has four long-running branches: `master`, `next`, and `pu` (proposed updates) for new work, and `maint` for maintenance backports. When new work is introduced by contributors, it’s collected into topic branches in the maintainer’s repository in a manner similar to what I’ve described (see Figure 5-24). At this point, the topics are evaluated to determine whether they’re safe and ready for consumption or whether they need more work. If they’re safe, they’re merged into `next`, and that branch is pushed up so everyone can try the topics integrated together.

Insert 18333fig0524.png 
Figure 5-24. Managing a complex series of parallel contributed topic branches.

If the topics still need work, they’re merged into `pu` instead. When it’s determined that they’re totally stable, the topics are re-merged into `master` and are then rebuilt from the topics that were in `next` but didn’t yet graduate to `master`. This means `master` almost always moves forward, `next` is rebased occasionally, and `pu` is rebased even more often (see Figure 5-25).

Insert 18333fig0525.png 
Figure 5-25. Merging contributed topic branches into long-term integration branches.

When a topic branch has finally been merged into `master`, it’s removed from the repository. The Git project also has a `maint` branch that is forked off from the last release to provide backported patches in case a maintenance release is required. Thus, when you clone the Git repository, you have four branches that you can check out to evaluate the project in different stages of development, depending on how cutting edge you want to be or how you want to contribute; and the maintainer has a structured workflow to help them vet new contributions.

#### Rebasing and Cherry Picking Workflows ####

Other maintainers prefer to rebase or cherry-pick contributed work on top of their master branch, rather than merging it in, to keep a mostly linear history. When you have work in a topic branch and have determined that you want to integrate it, you move to that branch and run the rebase command to rebuild the changes on top of your current master (or `develop`, and so on) branch. If that works well, you can fast-forward your `master` branch, and you’ll end up with a linear project history.

The other way to move introduced work from one branch to another is to cherry-pick it. A cherry-pick in Git is like a rebase for a single commit. It takes the patch that was introduced in a commit and tries to reapply it on the branch you’re currently on. This is useful if you have a number of commits on a topic branch and you want to integrate only one of them, or if you only have one commit on a topic branch and you’d prefer to cherry-pick it rather than run rebase. For example, suppose you have a project that looks like Figure 5-26.

Insert 18333fig0526.png 
Figure 5-26. Example history before a cherry pick.

If you want to pull commit `e43a6` into your master branch, you can run

	$ git cherry-pick e43a6fd3e94888d76779ad79fb568ed180e5fcdf
	Finished one cherry-pick.
	[master]: created a0a41a9: "More friendly message when locking the index fails."
	 3 files changed, 17 insertions(+), 3 deletions(-)

This pulls the same change introduced in `e43a6`, but you get a new commit SHA-1 value, because the date applied is different. Now your history looks like Figure 5-27.

Insert 18333fig0527.png 
Figure 5-27. History after cherry-picking a commit on a topic branch.

Now you can remove your topic branch and drop the commits you didn’t want to pull in.

### Tagging Your Releases ###

When you’ve decided to cut a release, you’ll probably want to drop a tag so you can re-create that release at any point going forward. You can create a new tag as I discussed in Chapter 2. If you decide to sign the tag as the maintainer, the tagging may look something like this:

	$ git tag -s v1.5 -m 'my signed 1.5 tag'
	You need a passphrase to unlock the secret key for
	user: "Scott Chacon <schacon@gmail.com>"
	1024-bit DSA key, ID F721C45A, created 2009-02-09

If you do sign your tags, you may have the problem of distributing the public PGP key used to sign your tags. The maintainer of the Git project has solved this issue by including their public key as a blob in the repository and then adding a tag that points directly to that content. To do this, you can figure out which key you want by running `gpg --list-keys`:

	$ gpg --list-keys
	/Users/schacon/.gnupg/pubring.gpg
	---------------------------------
	pub   1024D/F721C45A 2009-02-09 [expires: 2010-02-09]
	uid                  Scott Chacon <schacon@gmail.com>
	sub   2048g/45D02282 2009-02-09 [expires: 2010-02-09]

Then, you can directly import the key into the Git database by exporting it and piping that through `git hash-object`, which writes a new blob with those contents into Git and gives you back the SHA-1 of the blob:

	$ gpg -a --export F721C45A | git hash-object -w --stdin
	659ef797d181633c87ec71ac3f9ba29fe5775b92

Now that you have the contents of your key in Git, you can create a tag that points directly to it by specifying the new SHA-1 value that the `hash-object` command gave you:

	$ git tag -a maintainer-pgp-pub 659ef797d181633c87ec71ac3f9ba29fe5775b92

If you run `git push --tags`, the `maintainer-pgp-pub` tag will be shared with everyone. If anyone wants to verify a tag, they can directly import your PGP key by pulling the blob directly out of the database and importing it into GPG:

	$ git show maintainer-pgp-pub | gpg --import

They can use that key to verify all your signed tags. Also, if you include instructions in the tag message, running `git show <tag>` will let you give the end user more specific instructions about tag verification.

### Generating a Build Number ###

Because Git doesn’t have monotonically increasing numbers like 'v123' or the equivalent to go with each commit, if you want to have a human-readable name to go with a commit, you can run `git describe` on that commit. Git gives you the name of the nearest tag with the number of commits on top of that tag and a partial SHA-1 value of the commit you’re describing:

	$ git describe master
	v1.6.2-rc1-20-g8c5b85c

This way, you can export a snapshot or build and name it something understandable to people. In fact, if you build Git from source code cloned from the Git repository, `git --version` gives you something that looks like this. If you’re describing a commit that you have directly tagged, it gives you the tag name.

The `git describe` command favors annotated tags (tags created with the `-a` or `-s` flag), so release tags should be created this way if you’re using `git describe`, to ensure the commit is named properly when described. You can also use this string as the target of a checkout or show command, although it relies on the abbreviated SHA-1 value at the end, so it may not be valid forever. For instance, the Linux kernel recently jumped from 8 to 10 characters to ensure SHA-1 object uniqueness, so older `git describe` output names were invalidated.

### Preparing a Release ###

Now you want to release a build. One of the things you’ll want to do is create an archive of the latest snapshot of your code for those poor souls who don’t use Git. The command to do this is `git archive`:

	$ git archive master --prefix='project/' | gzip > `git describe master`.tar.gz
	$ ls *.tar.gz
	v1.6.2-rc1-20-g8c5b85c.tar.gz

If someone opens that tarball, they get the latest snapshot of your project under a project directory. You can also create a zip archive in much the same way, but by passing the `--format=zip` option to `git archive`:

	$ git archive master --prefix='project/' --format=zip > `git describe master`.zip

You now have a nice tarball and a zip archive of your project release that you can upload to your website or e-mail to people.

### The Shortlog ###

It’s time to e-mail your mailing list of people who want to know what’s happening in your project. A nice way of quickly getting a sort of changelog of what has been added to your project since your last release or e-mail is to use the `git shortlog` command. It summarizes all the commits in the range you give it; for example, the following gives you a summary of all the commits since your last release, if your last release was named v1.0.1:

	$ git shortlog --no-merges master --not v1.0.1
	Chris Wanstrath (8):
	      Add support for annotated tags to Grit::Tag
	      Add packed-refs annotated tag support.
	      Add Grit::Commit#to_patch
	      Update version and History.txt
	      Remove stray `puts`
	      Make ls_tree ignore nils

	Tom Preston-Werner (4):
	      fix dates in history
	      dynamic version method
	      Version bump to 1.0.2
	      Regenerated gemspec for version 1.0.2

You get a clean summary of all the commits since v1.0.1, grouped by author, that you can e-mail to your list.

## Summary ##

You should feel fairly comfortable contributing to a project in Git as well as maintaining your own project or integrating other users’ contributions. Congratulations on being an effective Git developer! In the next chapter, you’ll learn more powerful tools and tips for dealing with complex situations, which will truly make you a Git master.
