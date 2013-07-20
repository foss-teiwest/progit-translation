# Βασικές Αρχές του Git #

Εάν μπορούσατε να ασχοληθείτε μόνο με ένα κεφάλαιο για να ξεκινήσετε με το Git, αυτό θα ήταν. Αυτό το κεφάλαιο καλύπτει όλες τις βασικές εντολές που θα χρειαστείτε για τη πλειοψηφία των πραγμάτων που θα ασχοληθείτε περνώντας χρόνο στο με το Git. Κατά το τέλος του κεφαλαίου, θα είστε σε θέση να ρυθμίσετε και να αρχικοποιήσετε ένα "repository", με το να αρχίζετε και να σταματάτε να παρακολουθείτε αρχεία, να δημιουργείτε και να κάνετε αλλαγές. Θα σας δείξουμε επίσης πως να κάνετε ένα Git να αγνοεί έναν συγκεκριμένο τύπο αρχείου καθώς και συγκεκριμένα μοτίβα αρχείων, πως να αναιρείτε λάθη εύκολα και γρήγορα, πως να περιηγηθείτε στο ιστορικό της δουλείας σας και να ανατρέξετε στις αλλαγές μεταξύ των "commit", καθώς και το πως να κάνουμε "push" και "pull" από απομακρυσμένα "repositories".

## Πως Παίρνουμε ένα Git "Repository" ##

Μπορούμε να πάρουμε ένα Git χρησιμοποιώντας δύο κυρίως προσεγγίσεις. Η πρώτη χρησιμοποιεί μία ήδη υπάρχουσα δουλειά και την εισάγει στο Git. Η δεύτερδημιουργεί έναν κλόνο ενός ήδη υπάρχοντος Git "repository" από έναν άλλον εξυπηρετητή.

### Αρχικοποιώντας ένα "Repository" σε Υφιστάμενο Φάκελο ###

Εάν ξεκινάτε να εντοπίζετε μία υπάρχουσα εργασία στο Git, πρέπει να πάτε στον φάκελο της εργασίας και πληκτρολογήστε

	$ git init

Αυτό δημιουργεί έναν υποφάκελο με όνομα '.git' που περιέχει όλα τα απαραίτητα αρχεία αποθήκευσης - έναν σκελετό Git "repository". Σε αυτό το σημείο, τίποτα από την εργασία σας δεν έχει βρεθεί ακόμη.(Δείτε στο *Κεφάλαιο 9* περισσότερα για το τι ακριβώς αρχεία περιέχωνται μέσα στον '.git' φάκελο που μόλις δημιουργήσατε.)

Εάν θέλετε να ξεκινήσετε έναν έλεγχο έκδοσης των υφηστάμενων αρχείων ( σε αντίθεση με έναν άδειο φάκελο), θα πρέπει να ξεκινήσετε με τον εντοπισμό των αρχείων αυτών και να κάνετε ένα αρχικό "commit".Αυτό μπορεί να επιτευχθεί με μερικές 'git add' εντολές οι οποίες  καθορίζουν τα αρχεία που θέλετε να ακολουθήσετε, ακολουθώντας ένα "commit":

	$ git add *.c
	$ git add README
	$ git commit -m 'initial project version'

Θα αναφερθούμε στο τι κάνουν αυτές οι εντολές σε ένα λεπτό. Σε αυτό το σημείο, έχετε ένα Git "repository" με τους ακολουθούμενα αρχεία και ένα αρχικό "commit".
 
### Αντιγράφοντας ένα Υφηστάμενο "Repository" ###

Εάν θέλετε ένα αντίγραφο ενός υπάρχοντος Git "repository" - για παράδειγμα, μια εργασία στην οποία θα θέλατε να συνεισφέρετε - η εντολή που χρειάζεστε είναι η 'git clone'. Εάν είστε οικείος με άλλα VCS συστήματα όπως το Subversion, θα παρατηρησετε ότι η εντολή είναι 'clone' και όχι 'checkout'. Αυτή είναι μια σημαντικός διαχωρισμός - το Git λαμβάνει ένα αντίγραφο από σχεδόν όλα τα δεδομένα που έχει ο εξυπηρετητής. Για κάθε έκδοση κάθε αρχείου για το ιστορικό της εργασίας το οποίο κατέβηκε όταν έτρεξε η εντολή 'git clone'. Στην πραγματικότητα, εάν ο δίσκος του εξυπηρετητή φθαρθεί, μπορείτε να χρησιμοποιήσετε οποιοδήποτε αντίγραφο σε οποιονδήποτε πελάτη για να θέσετε τον εξυπηρετητη ξανά στη κατάσταση που βρισκόταν τη στιγμή που έγινε η αντιγραφή ( μπορεί να χαθούν κάποια δεδομένα από τη μεριά του εξυπηρετητή, αλλά όλα τα δεδομένα της έκδοσης θα βρίσκονται εκεί - Δείτε το *Κεφάλαιο 4* για περισσότερες πληροφορίες). 

Μπορείτε να αντιγράψετε ενα "repository" με την εντολή 'git clone [url]'. Για παράδειγμα, εάν θέλετε να αντιγράψετε την βιβλιοθήκη Ruby Git η οποία ονομάζεται Grit, θα πρέπει να κάνεις τα παρακάτω:

	$ git clone git://github.com/schacon/grit.git

Αυτό δημιουργεί έναν φάκελο με το όνομα 'grit' αρχικοποιώντας ένα '.git' κατάλογο μέσα σε αυτόν, κατεβάζει όλα τα δεδομένα για το συγκεκριμένο "repository", και ελέγχει ένα αντίγραφο της τελευταίας έκδοσης που λειτουργεί. Εάν πάτε στον νέο 'grit' φάκελο, θα δείτε εκεί τα αρχεία της δουλειάς σας, έτοιμα για να τα χρησιμοποιήσετε η να τα αλλάξετε. Εάν θέλετε να αντιγράψετε το "repository" μέσα σε έναν φάκελο ο οποίος έχει διαφορετικό όνομα από grit, μπορείτε να το συγκεκριμενοποιήσετε με την παρακάτω εντολή:

	$ git clone git://github.com/schacon/grit.git mygrit

Αυτή η εντολή κάνει την ίδια δουλειά με την προηγούμενη εντολή, αλλά ο κατάλογος που στοχεύουμε ονομάζεται 'mygrit'. 

Το Git έχει πολλά διαφορετικά πρωτοκολλα μεταφοράς που μπορείτε να χρησιμοποιήσετε. Τα προηγούμενα παραδείγματα χρησιμοποιούσαν το `git://` protocol, but you may also see `http(s)://` ή `user@server:/path.git`, το οποίο χρησιμοποιεί το SSH πρωτόκολλο μεταφοράς. Στο *Κεφάλαιο 4* θα γίνει εισαγωγή σε όλες τις επιλογές που μπορεί ένας εξυπηρετητής να στήσει έτσι ώστε να έχετε πρόσβαση στο Git "repository" σας, αλλά επίσης τα θετικά και τα αρνητηκά του καθενός.

## Καταγράφοντας Αλλαγές στο "Repository" ##

Έχετε ένα καλόπιστο Git "repository" και ένα αντίγραφο των αρχείων για τη δουλειά σας. Θα πρέπει να κάνετε κάποιες αλλαγές και να δεσμέυσετε στιγμιότυπα αυτών των αλλαγών στο "repository" σας κάθε φορά που η εργασία σας φτάνει σε ένα σημείο που θα θέλατε να καταγράψετε.

Να θυμάστε ότι κάθε αρχείο στον φάκελο εργασίας σας μπορεί να βρίσκεται σε μία απο τις δύο καταστάσεις: *Tracked* ή *Untracked*. Τα *Tracked* αρχεία είναι αυτά τα οποία βρίσκονταν στο τελευταίο στιγμιότυπο, και μπορούν να είναι τροποποιημένα, μη τροποποιημένα, ή σταδιακή. Τα *Untracked* αρχεία είναι όλα τα υπόλοιπα αρχεία στον φάκελο εργασίας σας που δεν υπήρχαν στο τελευταίο σας στιγμιότυπο και δεν υπάρχουν στην περιοχή σταδιοποίησης. Όταν αρχικά φτιάχνετε τον κλώνο ενός "repository" , όλα τα αρχεία σας θα παρακολουθούνται και δεν θα τροποποιούνται γιατί μόλις τα ελένξατε και δεν έχετε κάνει ακόμα καμιά επεξεργασία.

Όπως επεξεργάζεστε τα αρχεία σας, το Git τα αναγνωρίζει σαν τροποποιημένα, γιατί τα έχετε αλλάξει από το τελευταίο σας "commit". Πρέπει να σταδιοποιήσετε αυτά τα τροποποιημένα αρχεία και μετά να κάνετε "commit" όλα τα αλλαγμένα σας αρχεία, και ο κύκλος αυτός επαναλαμβάνεται. Αυτό τον κύκλο μπορούμε να δούμε στο Figure 2-1.

Insert 18333fig0201.png
Figure 2-1. Ο κύκλος ζωής της κατάστασης των αρχέιων σας.

### Ελέγχοντας την Κατάσταση των Αρχείων Σας ###

Το πιο βασικό εργαλείο που χρησιμοποιήτε για να προσδιορίσετε ποια αρχεία βρίσκονται σε ποια κατάσταση, είναι η εντολή 'git status'. Εάν τρέξετε αυτήν την εντολή μετά από την κατασκευή ενός κλώνου, θα δείτε κάτι παρόμοιο με τα παρακάτω: 

	$ git status
	# On branch master
	nothing to commit (working directory clean)

Αυτό σημαίνει ότι έχετε έναν καθαρό φάκελο εργασίας. Για να το πούμε διαφορετικά, εδώ δεν υπάρχουν αρχεία τα οποία παρακολουθούνται ή έχουν τροποποιηθεί.Το Git επίσης δεν βλέπει κανένα αρχείο που δεν παρακολουθείται, αλλίως θα ήταν καταχωρημένα εδώ. Τέλος, η εντολή μας λέει σε ποιον κλάδο βρίσκεστε. Για την ώρα, θα είστε στο ρποεπιλεγμένο 'master', αν και δεν θα χρειαστεί να ανησυχείτε γι'αυτό. Στην επόμενη ενότητα θα ασχοληθούμε με τους κλάδους και αναφορές με λεπτομέρεια.

Ας πούμε ότι προσθέτετε ένα καινούριο αρχείο στην εργασία σας, ένα απλό αρχείο `README`. Εάν το αρχείο δεν υπήρχε πριν, και τρέξετε το `git status`, θα δείτε το αρχείο σας που δεν παρακολουθειται ως εξής:

	$ vim README
	$ git status
	# On branch master
	# Untracked files:
	#   (use "git add <file>..." to include in what will be committed)
	#
	#	README
	nothing added to commit but untracked files present (use "git add" to track)

Μπορείτε να δείτε το νέο σας αρχείο `README` δεν παρακολουθείται, επειδή βρίσκεται κάτω από τα “Untracked files” στην έξοδο της κατάστασης σας. Αυτό σημαίνει ότι το Git βλέπει αρχεία που δεν έβλεπε στο προηγούμενο στιγμιότυπο (commit): Το Git δεν θα αρχίσει να το συμπεριλαμβάνει στα στιγμιότυπα σας εκτός αν του πείτε συγκεκριμένα να το κάνει. Αυτό γίνεται έτσι ώστε να μην αρχίσετε να συμπεριλαμβάνετε άθελα σας δυαδικά αρχεία ή άλλα αρχεία που δεν θέλατε να συμπεριλάβετε. Θα θέλατε να ξεκινήσετε να συμπεριλαμβάνετε το README, ας αρχίσουμε λοιπόν να παρακολουθούμε αυτό το αρχείο.

### Παρακολουθώντας Νέα Αρχεία ###

Για να ξεκινήσουμε την παρακολούθηση ενός νέου αρχείου, χρησιμοποιείτε την εντολή `git add`.Για να ξεκινήσετε την παρακολούθηση του αρχείου 'REDAME'
μπορείτε να τρέξετε το παρακάτω:

	$ git add README

Εάν ξανατρέξετε την εντολή κατάστασης, μπορείτε να δείτε ότι το αρχείο `README` παρακολουθείται και είναι σταδιοποιημένο:

	$ git status
	# On branch master
	# Changes to be committed:
	#   (use "git reset HEAD <file>..." to unstage)
	#
	#	new file:   README
	#

Μπορείτε να καταλάβετε ότι είναι σταδιοποιημένο γιατί βρίσκεται κάτω από το “Changes to be committed”. Εάν κάνετε ένα "commit" αυτή τη στιγμη, η έκδοση του αρχείου την στιγμή που τρέξατε το `git add` θα βρίσκεται στο στιγμιότυπο στο ιστορικό. Ίσως θυμηθείτε όταν τρέξατε προηγουμένως το `git init`, μετά τρέξατε το `git add (files)`. Αυτό έγινε για να αρχίσετε να παρακολουθείτε αρχεία στον φάκελο σας. Η εντολή `git add` λαμβάνει ένα όνομα για το path είτε του αρχείου είτε για τον φάκελο, η εντολή προσθέτει όλα τα αρχεία σε αυτόν τον φάκελο αναδρομικά.

### Σταδιοποίηση Τροποποιημένων Αρχείων ###

Ας αλλάξουμε ένα αρχείο το οποίο παρακολουθούσαμε ήδη. Εάν αλλάξετε ένα παρακολουθούμενο αρχείο με το όνομα `benchmarks.rb΄ και στη συνέχεια τρέξτε την `status` εντολή ξανά, θα λάβετε κάτι παρόμοιο με τα παρακάτω: 

	$ git status
	# On branch master
	# Changes to be committed:
	#   (use "git reset HEAD <file>..." to unstage)
	#
	#	new file:   README
	#
	# Changed but not updated:
	#   (use "git add <file>..." to update what will be committed)
	#
	#	modified:   benchmarks.rb
	#

Το αρχείο `benchmarks.rb` βρίσκεται κάτω από ένα τμήμα που ονομάζεται “Changed but not updated” - το οποίο σημαίνει ότι ένα αρχείο που παρακολουθείται έχει τροποποιηθεί στον φάκελο που δουλεύουμε αλλά δεν έχει σταδιοποιηθεί ακόμα. Για να γίνει αυτό, χρησιμοποιούμε την εντολή `git add` ( αυτή η εντολή εξυπηρετεί πολλαπλούς σκοπούς - τη χρησιμοποιείτε για την παρακολούθηση νέων αρχείων, για τη σταδιοποίηση αρχείων και για να κάνουν και άλλες δουλειές όπως το να μαρκάρει συγχωνευμένα-συγκρουόμενα αρχεία ). Ας τρέξουμε την εντολή `git add`για να σταδιοποιήσουμε το `benchmarks.rb` αρχείο, και στη συνέχεια τρέξτε την `git status` ξανά.

	$ git add benchmarks.rb
	$ git status
	# On branch master
	# Changes to be committed:
	#   (use "git reset HEAD <file>..." to unstage)
	#
	#	new file:   README
	#	modified:   benchmarks.rb
	#

Και τα δύο αρχεία σταδιοποιήθηκαν και θα μπουν στο επόμενο σας commit. Σε αυτό το σημείο, υποθέτουμε ότι θυμηθήκατε μια μικρή αλλαγή που θα θέλατε να κάνετε στο `benchmarks.rb` πριν κάνετε το commit. Το ανοίγετε ξανά και κάνετε αυτήν την αλλαγή, και είστε έτοιμοι να προχωρήσετε στο commit. Παρόλα αυτά ας τρέξουμε την `git status` για άλλη μια φορά:

	$ vim benchmarks.rb
	$ git status
	# On branch master
	# Changes to be committed:
	#   (use "git reset HEAD <file>..." to unstage)
	#
	#	new file:   README
	#	modified:   benchmarks.rb
	#
	# Changed but not updated:
	#   (use "git add <file>..." to update what will be committed)
	#
	#	modified:   benchmarks.rb
	#

Τι στο καλό? τώρα το `benchmarks.rb` εμφανίζεται ταυτόχρονα σαν σταδιοποιημένο και σαν μη σταδιοποιημένο. Πως γενιν αυτο? Φαίνεται πως το Git Σταδιοποιεί ένα αρχείο ακριβώς όπως ήταν όταν τρέχατε την εντολή `git add`. Εάν κάνετε commit τώρα, η έκδοση του `benchmarks.rb` όπως ήταν την τελευταία φορά που τρέξαμε την `git add` εντολή είναι το πως ακριβώς θα μπει στο commit, όχι για την έκδοση του αρχείου όπως φαίνεται στον φάκελο εργασίας όταν τρέχουμε το `git commit`. Εάν τροποποιήσουμε ένα αρχείο μόλις τρέξουμε την εντολή `git add` πάλι για να σταδιοποιήσουμε την τελευταία έκδοση του αρχείου: 

	$ git add benchmarks.rb
	$ git status
	# On branch master
	# Changes to be committed:
	#   (use "git reset HEAD <file>..." to unstage)
	#
	#	new file:   README
	#	modified:   benchmarks.rb
	#

### Αγνοώντας Αρχεία ###

Συχνά, θα έχετε μια κλάση αρχείων τα οποία δε θέλετε το Git να προσθέτει αυτόματα ή ακόμα και το να σας δείχνει αν δεν παρακολουθούνται. Αυτές γενικά παράγωνται αυτόματα όπως τα αρχεία καταγραφής αλλαγών και τα αρχεία που παράγωνται μέσα στο build του συστήματος. Σε τέτοιες περιπτώσεις, μπορείτε να δημιουργήσετε ένα αρχείο με λίστες προτύπων και για να ταιριάζουν τα ονομάζουμε `.gitignore`. Παρακάτω υπάρχει παράδειγμα `.gitignore` αρχείου:

	$ cat .gitignore
	*.[oa]
	*~

Η πρώτη γραμμή λέει στο Git να αγνοήσει όλα τα αρχεία που τελειώνουν με `.o` ή `.a` — *αντικείμενο* και *φάκελος* αρχεία που μπορεί να έχουν παραχθεί από το χτίσιμο του κώδικα σας. Η δεύτερη γραμμή λέει στο Git να αγνοήσει όλα τα αρχεία που τελειώνουν με περισπωμένη (`~`), το οποίο χρησιμοποιείται από πολλούς επεξεργαστές κείμενου όπως τα Emacs για το μαρκάρισμα προσωρινών αρχείων. Μπορείτε να συμπεριλάβετε τα `log`, `tmp`, ή `pid` φάκελο, αυτόματη αρχειοθέτηση κλπ. Φτιάχνωντας ένα `.gitignore` αρχείο πριν ξεκινήσετε είναι μια καλή ιδέα για να μην κάνετε commit αρχεία που δεν θέλετε μέσα στο  Git repository σας.

Οι κανόνες για τα πρότυπα που θα μπουν στο `.gitignore` αρχείο είναι οι εξής:

*	Κενές γραμμές η γραμμές που ξεκινάνε με `#` αγνοούνται.
*	Τα στάνταρ glop πρότυπα δουλεύουν.
*	Μπορείτε επίσης να κλείσετε πρότυπα με (`/`) για να συγκεκριμενοποιήσετε έναν φάκελο.
*	Μπορείτε να αναιρέσετε ένα πρότυπο με το να το ξεκινάτε με θαυμαστικό (`!`).

Glob πρότυπα είναι σαν απλοποιημένες κανονικές εκφράσεις που χρησιμοποιούν στα shells. Ένας αστερίσκος (`*`) αντιστοιχίζει μηδέν ή και περισσότερους χαρακτήρες, το `[abc]` αντιστοιχεί σε όλους τους χαρακτήρες μέσα στις αγκύλες (στη περίπτωση αυτή `a`, `b`, ή `c`), ένα ερωτηματικό (`?`) αντιστοιχίζεται με έναν χαρακτήρα, και οι χαρακτήρες όταν κλείνουν αγκύλες χωρίζονται από ένα ενωτικο(`[0-9]`) αντιστοιχεί με όλους τους χαρακτήρες του πεδίου( στη περίπτωση αυτή από 0 εως 9) .
 

Άλλο ένα παράδειγμα `.gitignore` αρχείου:

	# a comment - this is ignored
	*.a       # no .a files
	!lib.a    # but do track lib.a, even though you're ignoring .a files above
	/TODO     # only ignore the root TODO file, not subdir/TODO
	build/    # ignore all files in the build/ directory
	doc/*.txt # ignore doc/notes.txt, but not doc/server/arch.txt

### Παρακολουθώντας τις Σταδιοποιημένες και τις Μη Σταδιοποιημένες Αλλαγές  ###

Εάν η `git status` εντολή είναι πολύ ασαφής για εσάς - θα θέλατε να ξέρετε ακριβώς τι αλλάξατε, όχι μόνο ποια αρχεία τροποποιήθηκαν - μπορείτε απλά να χρησιμοποιήσετε την εντολή `git diff`. Θα καλύψουμε την εντολή αυτή με περισσότερες ΄λεπτομέρειες αργότερα, αλλά πιθανότατα να τη χρησιμοποιείτε συχνά για να απαντήσετε σε αυτές τις δύο ερωτήσεις : Τι έχετε αλλάξει αλλα δεν έχετε σταδιοποιήσει ακόμα? Και τι έχετε σταδιοποιήσει και θέλετε να κάνετε commit? Παρόλαυτα η `git status` απαντάει αυτά τα ερωτήματα πολύ γενικά, η `git diff` σας δείχνει ακριβώς τις γραμμές που προστέθηκαν ή αφαιρέθηκαν - το patch, όπως ήταν.

Ας πούμε ότι τροποποιείτε και σταδιοποιείτε το αρχείο `README` ξανά και στη συνέχεια κάνετε το ίδιο στο αρχείο `benchmarks.rb` χωρίς τη σταδιοποίηση όμως. Τότε αν τρέξετε την εντολή `status`, θα δείτε ξανά κάτι παρόμοιο με τα παρακάτω: 

	$ git status
	# On branch master
	# Changes to be committed:
	#   (use "git reset HEAD <file>..." to unstage)
	#
	#	new file:   README
	#
	# Changed but not updated:
	#   (use "git add <file>..." to update what will be committed)
	#
	#	modified:   benchmarks.rb
	#

Για να δείτε τι αλλάξατε αλλά όχι ακόμα σταδιοποιήσει εισάγετε την εντολή `git diff` χωρίς άλλες προσθήκες:

	$ git diff
	diff --git a/benchmarks.rb b/benchmarks.rb
	index 3cb747f..da65585 100644
	--- a/benchmarks.rb
	+++ b/benchmarks.rb
	@@ -36,6 +36,10 @@ def main
	           @commit.parents[0].parents[0].parents[0]
	         end

	+        run_code(x, 'commits 1') do
	+          git.commits.size
	+        end
	+
	         run_code(x, 'commits 2') do
	           log = git.commits('master', 15)
	           log.size

Αυτή η εντολή συγκρίνει το τι βρίσκεται μέσα στον φάκελο που δουλεύετε με το τι υπάρχει στην σταδιοποιημένη σας περιοχή. Το αποτέλεσμα θα σας πει τις αλλαγές που έχετε κάνει και δεν έχετε σταδιοποιήσει ακόμα.

Εάν θέλετε να δείτε τι έχετε σταδιοποιήσει αυτό θα μπει στο επόμενο commit σας, μπορείτε να χρησιμοποιείσετε την εντολή  `git diff --cached`. ( Στις εκδόσεις Git 1.6.1 και επόμενες, μπορείτε επίσης να χρησιμοποιήσετε τη `git diff --staged`, που ίσως είναι πιο εύκολη να θυμάστε.) Αυτή η εντολή συγκρίνει τις σταδιποιημένες σας αλλαγές από το τελευταίο σας commit:

	$ git diff --cached
	diff --git a/README b/README
	new file mode 100644
	index 0000000..03902a1
	--- /dev/null
	+++ b/README2
	@@ -0,0 +1,5 @@
	+grit
	+ by Tom Preston-Werner, Chris Wanstrath
	+ http://github.com/mojombo/grit
	+
	+Grit is a Ruby library for extracting information from a Git repository

Είναι σημαντικό να σημειωθεί ότι η  `git diff` δεν δείχνει από μόνη της όλες τις αλλαγές που κάνατε στο τελευταίο σας commit αλλά μόνο αυτές που δεν έχουν σταδιοποιηθεί ακόμα. Αυτό μπορεί να σας μπερδέψει λίγο  επειδή εάν έχετε σταδιοποιήσει όλες τις αλλαγές σας, η `git diff` δε θα επιστρέψει τίποτα.

Ένα άλλο παράδειγμα, εάν σταδιοποιήσετε το αρχείο `benchmarks.rb`και μετά το τροποποιήσετε , μπορείτε με την `git diff` να δείτε τις αλλαγές που σταδιοποιήθηκαν και τις αλλαγές που δνε σταδιοποιήθηκαν:

	$ git add benchmarks.rb
	$ echo '# test line' >> benchmarks.rb
	$ git status
	# On branch master
	#
	# Changes to be committed:
	#
	#	modified:   benchmarks.rb
	#
	# Changed but not updated:
	#
	#	modified:   benchmarks.rb
	#

Tώρα μπορείτε να χρησιμοποιήσετε την `git diff` για να δείτε τι δεν είναι ακόμα σταδιοποιημένο

	$ git diff
	diff --git a/benchmarks.rb b/benchmarks.rb
	index e445e28..86b2f7c 100644
	--- a/benchmarks.rb
	+++ b/benchmarks.rb
	@@ -127,3 +127,4 @@ end
	 main()

	 ##pp Grit::GitRuby.cache_client.stats
	+# test line

και την `git diff --cached` για να δείτε τι έχετε σταδιοποιήσει μέχρι στιγμής:

	$ git diff --cached
	diff --git a/benchmarks.rb b/benchmarks.rb
	index 3cb747f..e445e28 100644
	--- a/benchmarks.rb
	+++ b/benchmarks.rb
	@@ -36,6 +36,10 @@ def main
	          @commit.parents[0].parents[0].parents[0]
	        end

	+        run_code(x, 'commits 1') do
	+          git.commits.size
	+        end
	+
	        run_code(x, 'commits 2') do
	          log = git.commits('master', 15)
	          log.size

### Κάνοντας Commit τις αλλαγές σας ###

Τώρα που έχουμε ετοιμάσει τη σταδιοποίησή μας όπως τη θέλουμε μπορούμε να κάνουμε commit στις αλλαγές μας. Να θυμάστε ότι οτιδήποτε δεν έχουμε σταδιποιήσει ακόμα — για όποια αρχεία που δεν δεν έχετε τρέξει την 'git add' από την στιγμή που τα επεξεργαστήκατε — δε θα μπουν σε αυτό το commit. Θα μείνουν σαν τροποποιημένα αρχεία στον δίσκο σας.
Σε αυτή την περίπτωση, την τελευταία φορά που χρησιμοποιήσατε την 'git status' , είδατε ότι όλα ήταν σταδιοποιημένα, οπότε είστε έτοιμοι να κάνετε commit τις αλλαγές σας. Ο πιο απλός τρόπος να κάνετε commit είναι η παρακάτω εντολή :

	$ git commit

Έτσι ανοίγει το πρόγραμμα επεξεργασίας που έχετε επιλέξει. (Αυτό γίνεται μέσα απο το Shell `$EDITOR` - συνήθως vim ή emacs, αν και παρόλαυτα μπορείτε να τα ρυθμίσετε με οτι θέλετε με την εντολή `git config --global core.editor` που είδαμε στο *Κεφάλαιο 1*).

Το πρόγραμμα επεξεργασίας προβάλει το παρακάτω κείμενο (στο παράδειγμα χρησιμοποιείται vim):

	# Please enter the commit message for your changes. Lines starting
	# with '#' will be ignored, and an empty message aborts the commit.
	# On branch master
	# Changes to be committed:
	#   (use "git reset HEAD <file>..." to unstage)
	#
	#       new file:   README
	#       modified:   benchmarks.rb
	~
	~
	~
	".git/COMMIT_EDITMSG" 10L, 283C

Μπορείτε να δείτε ότι το προκαθορισμένο μήνυμα commit περιέχει την παλαιότερη έξοδο του 'git status' καθώς και μια άδεια γραμμή στο πάνω μέρος. Μπορείτε να διαγράψετε αυτά τα σχόλεια και να πληκτρολογήσετε το δικό σας commit μήνυμα, ή μπορείτε να τα αφήσετε ως έχουν για να σας βοηθήσουν να θυμάστε τι κάνετε commit. (Για μια πιο συγκεκριμένη υπενθύμιση για τις αλλαγές σας μπορείτε να εισάγετε την '-v' επιλογή στο 'git commit'. Με αυτόν τον τρόπο προβάλονται όλες οι αλλαγές σας απο τον editor για να μπορείτε να δείτε ακριβώς τις αλλαγές που κάνατε.) Όταν κλείσετε τον editor, το Git θα δημιουργήσει ένα νέο commit με το νέο σχόλιο.

Εναλλακτικά, μπορείτε να γράψετε το μήνυμα του commit σας μαζί μέσα στην εντολή 'commit' βάζοντας το '-m' , κάπως έτσι:

	$ git commit -m "Story 182: Fix benchmarks for speed"
	[master]: created 463dc4f: "Fix benchmarks for speed"
	 2 files changed, 3 insertions(+), 0 deletions(-)
	 create mode 100644 README

Μόλις φτιάξατε το πρώτο σας commit! Μπορείτε να δείτε το commit σας έχει εξάγει κάποιες πληροφορίες για τον εαυτό του: ποιο branch έγινε commit στον ('master'), τι SHA-1 άθροισμα ελέγχου έχει το commit (`463dc4f`), πόσα αρχεία άλλαξαν, και στατιστικά για τις γραμμές που προστέθηκαν ή αφαιρέθηκαν από το commit.

Να θυμάστε ότι τα commit καταγράφουν ότι έχετε φτιάξει κατά την σταδιποίηση. Οτιδήποτε δεν σταδιοποιήθηκε είναι ακόμα εκεί τροποποιημένο. Μπορείτε να κάνετε άλλο ένα commit για να το προσθέσετε στο ιστορικό σας. Κάθε φορά που κάνετε ένα commit, καταγράφετε ένα στιγμιότυπο του project σας το οποίο μπορείτε να αναστρέψετε ή να συγκρίνετε αργότερα.

### Αποφεύγοντας την Σταδιποίηση ###

Αν και μπορεί να είναι πολύ χρήσιμη για την κατασκευή των commits όπως ακριβώς τα θέλουμε, η σταδιοποίηση είναι μερικές φορές λίγο πιο πολύπλοκη απ'όσο θέλουμε, βάση τη ροή που εργαζόμαστε. Εάν θέλετε να προσπελάσετε τη σταδιοποίηση, το Git προσφέρει μια απλή συντόμευση. Προσθέτοντας το '-a' στην εντολή 'git commit' κάνει το Git αυτόματα να σταδιοποιήσει όλα τα αρχεία που παρακολουθεί πριν να κάνει το commit, αφήνοντας σας να προσπελάσετε το 'git add':

	$ git status
	# On branch master
	#
	# Changed but not updated:
	#
	#	modified:   benchmarks.rb
	#
	$ git commit -a -m 'added new benchmarks'
	[master 83e38c7] added new benchmarks
	 1 files changed, 5 insertions(+), 0 deletions(-)

Παρατηρείτε το ότι δεν χρειάζεται να εισάγετε το 'git add' στο 'benchmarks.rb' αρχείο πριν το commit.

### Removing Files ###

To remove a file from Git, you have to remove it from your tracked files (more accurately, remove it from your staging area) and then commit. The `git rm` command does that and also removes the file from your working directory so you don’t see it as an untracked file next time around.

If you simply remove the file from your working directory, it shows up under the “Changed but not updated” (that is, _unstaged_) area of your `git status` output:

	$ rm grit.gemspec
	$ git status
	# On branch master
	#
	# Changed but not updated:
	#   (use "git add/rm <file>..." to update what will be committed)
	#
	#       deleted:    grit.gemspec
	#

Then, if you run `git rm`, it stages the file’s removal:

	$ git rm grit.gemspec
	rm 'grit.gemspec'
	$ git status
	# On branch master
	#
	# Changes to be committed:
	#   (use "git reset HEAD <file>..." to unstage)
	#
	#       deleted:    grit.gemspec
	#

The next time you commit, the file will be gone and no longer tracked. If you modified the file and added it to the index already, you must force the removal with the `-f` option. This is a safety feature to prevent accidental removal of data that hasn’t yet been recorded in a snapshot and that can’t be recovered from Git.

Another useful thing you may want to do is to keep the file in your working tree but remove it from your staging area. In other words, you may want to keep the file on your hard drive but not have Git track it anymore. This is particularly useful if you forgot to add something to your `.gitignore` file and accidentally added it, like a large log file or a bunch of `.a` compiled files. To do this, use the `--cached` option:

	$ git rm --cached readme.txt

You can pass files, directories, and file-glob patterns to the `git rm` command. That means you can do things such as

	$ git rm log/\*.log

Note the backslash (`\`) in front of the `*`. This is necessary because Git does its own filename expansion in addition to your shell’s filename expansion. This command removes all files that have the `.log` extension in the `log/` directory. Or, you can do something like this:

	$ git rm \*~

This command removes all files that end with `~`.

### Moving Files ###

Unlike many other VCS systems, Git doesn’t explicitly track file movement. If you rename a file in Git, no metadata is stored in Git that tells it you renamed the file. However, Git is pretty smart about figuring that out after the fact — we’ll deal with detecting file movement a bit later.

Thus it’s a bit confusing that Git has a `mv` command. If you want to rename a file in Git, you can run something like

	$ git mv file_from file_to

and it works fine. In fact, if you run something like this and look at the status, you’ll see that Git considers it a renamed file:

	$ git mv README.txt README
	$ git status
	# On branch master
	# Your branch is ahead of 'origin/master' by 1 commit.
	#
	# Changes to be committed:
	#   (use "git reset HEAD <file>..." to unstage)
	#
	#       renamed:    README.txt -> README
	#

However, this is equivalent to running something like this:

	$ mv README.txt README
	$ git rm README.txt
	$ git add README

Git figures out that it’s a rename implicitly, so it doesn’t matter if you rename a file that way or with the `mv` command. The only real difference is that `mv` is one command instead of three — it’s a convenience function. More important, you can use any tool you like to rename a file, and address the add/rm later, before you commit.

## Viewing the Commit History ##

After you have created several commits, or if you have cloned a repository with an existing commit history, you’ll probably want to look back to see what has happened. The most basic and powerful tool to do this is the `git log` command.

These examples use a very simple project called `simplegit` that I often use for demonstrations. To get the project, run

	git clone git://github.com/schacon/simplegit-progit.git

When you run `git log` in this project, you should get output that looks something like this:

	$ git log
	commit ca82a6dff817ec66f44342007202690a93763949
	Author: Scott Chacon <schacon@gee-mail.com>
	Date:   Mon Mar 17 21:52:11 2008 -0700

	    changed the version number

	commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
	Author: Scott Chacon <schacon@gee-mail.com>
	Date:   Sat Mar 15 16:40:33 2008 -0700

	    removed unnecessary test code

	commit a11bef06a3f659402fe7563abf99ad00de2209e6
	Author: Scott Chacon <schacon@gee-mail.com>
	Date:   Sat Mar 15 10:31:28 2008 -0700

	    first commit

By default, with no arguments, `git log` lists the commits made in that repository in reverse chronological order. That is, the most recent commits show up first. As you can see, this command lists each commit with its SHA-1 checksum, the author’s name and e-mail, the date written, and the commit message.

A huge number and variety of options to the `git log` command are available to show you exactly what you’re looking for. Here, we’ll show you some of the most-used options.

One of the more helpful options is `-p`, which shows the diff introduced in each commit. You can also use `-2`, which limits the output to only the last two entries:

	$ git log -p -2
	commit ca82a6dff817ec66f44342007202690a93763949
	Author: Scott Chacon <schacon@gee-mail.com>
	Date:   Mon Mar 17 21:52:11 2008 -0700

	    changed the version number

	diff --git a/Rakefile b/Rakefile
	index a874b73..8f94139 100644
	--- a/Rakefile
	+++ b/Rakefile
	@@ -5,7 +5,7 @@ require 'rake/gempackagetask'
	 spec = Gem::Specification.new do |s|
	-    s.version   =   "0.1.0"
	+    s.version   =   "0.1.1"
	     s.author    =   "Scott Chacon"

	commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
	Author: Scott Chacon <schacon@gee-mail.com>
	Date:   Sat Mar 15 16:40:33 2008 -0700

	    removed unnecessary test code

	diff --git a/lib/simplegit.rb b/lib/simplegit.rb
	index a0a60ae..47c6340 100644
	--- a/lib/simplegit.rb
	+++ b/lib/simplegit.rb
	@@ -18,8 +18,3 @@ class SimpleGit
	     end

	 end
	-
	-if $0 == __FILE__
	-  git = SimpleGit.new
	-  puts git.show
	-end
	\ No newline at end of file

This option displays the same information but with a diff directly following each entry. This is very helpful for code review or to quickly browse what happened during a series of commits that a collaborator has added.
You can also use a series of summarizing options with `git log`. For example, if you want to see some abbreviated stats for each commit, you can use the `--stat` option:

	$ git log --stat
	commit ca82a6dff817ec66f44342007202690a93763949
	Author: Scott Chacon <schacon@gee-mail.com>
	Date:   Mon Mar 17 21:52:11 2008 -0700

	    changed the version number

	 Rakefile |    2 +-
	 1 files changed, 1 insertions(+), 1 deletions(-)

	commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
	Author: Scott Chacon <schacon@gee-mail.com>
	Date:   Sat Mar 15 16:40:33 2008 -0700

	    removed unnecessary test code

	 lib/simplegit.rb |    5 -----
	 1 files changed, 0 insertions(+), 5 deletions(-)

	commit a11bef06a3f659402fe7563abf99ad00de2209e6
	Author: Scott Chacon <schacon@gee-mail.com>
	Date:   Sat Mar 15 10:31:28 2008 -0700

	    first commit

	 README           |    6 ++++++
	 Rakefile         |   23 +++++++++++++++++++++++
	 lib/simplegit.rb |   25 +++++++++++++++++++++++++
	 3 files changed, 54 insertions(+), 0 deletions(-)

As you can see, the `--stat` option prints below each commit entry a list of modified files, how many files were changed, and how many lines in those files were added and removed. It also puts a summary of the information at the end.
Another really useful option is `--pretty`. This option changes the log output to formats other than the default. A few prebuilt options are available for you to use. The `oneline` option prints each commit on a single line, which is useful if you’re looking at a lot of commits. In addition, the `short`, `full`, and `fuller` options show the output in roughly the same format but with less or more information, respectively:

	$ git log --pretty=oneline
	ca82a6dff817ec66f44342007202690a93763949 changed the version number
	085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7 removed unnecessary test code
	a11bef06a3f659402fe7563abf99ad00de2209e6 first commit

The most interesting option is `format`, which allows you to specify your own log output format. This is especially useful when you’re generating output for machine parsing — because you specify the format explicitly, you know it won’t change with updates to Git:

	$ git log --pretty=format:"%h - %an, %ar : %s"
	ca82a6d - Scott Chacon, 11 months ago : changed the version number
	085bb3b - Scott Chacon, 11 months ago : removed unnecessary test code
	a11bef0 - Scott Chacon, 11 months ago : first commit

Table 2-1 lists some of the more useful options that format takes.

	Option	Description of Output
	%H	Commit hash
	%h	Abbreviated commit hash
	%T	Tree hash
	%t	Abbreviated tree hash
	%P	Parent hashes
	%p	Abbreviated parent hashes
	%an	Author name
	%ae	Author e-mail
	%ad	Author date (format respects the --date= option)
	%ar	Author date, relative
	%cn	Committer name
	%ce	Committer email
	%cd	Committer date
	%cr	Committer date, relative
	%s	Subject

You may be wondering what the difference is between _author_ and _committer_. The _author_ is the person who originally wrote the patch, whereas the _committer_ is the person who last applied the patch. So, if you send in a patch to a project and one of the core members applies the patch, both of you get credit — you as the author and the core member as the committer. We’ll cover this distinction a bit more in *Chapter 5*.

The `oneline` and `format` options are particularly useful with another `log` option called `--graph`. This option adds a nice little ASCII graph showing your branch and merge history, which we can see our copy of the Grit project repository:

	$ git log --pretty=format:"%h %s" --graph
	* 2d3acf9 ignore errors from SIGCHLD on trap
	*  5e3ee11 Merge branch 'master' of git://github.com/dustin/grit
	|\
	| * 420eac9 Added a method for getting the current branch.
	* | 30e367c timeout code and tests
	* | 5a09431 add timeout protection to grit
	* | e1193f8 support for heads with slashes in them
	|/
	* d6016bc require time for xmlschema
	*  11d191e Merge branch 'defunkt' into local

Those are only some simple output-formatting options to `git log` — there are many more. Table 2-2 lists the options we’ve covered so far and some other common formatting options that may be useful, along with how they change the output of the `log` command.

	Option	Description
	-p	Show the patch introduced with each commit.
	--stat	Show statistics for files modified in each commit.
	--shortstat	Display only the changed/insertions/deletions line from the --stat command.
	--name-only	Show the list of files modified after the commit information.
	--name-status	Show the list of files affected with added/modified/deleted information as well.
	--abbrev-commit	Show only the first few characters of the SHA-1 checksum instead of all 40.
	--relative-date	Display the date in a relative format (for example, “2 weeks ago”) instead of using the full date format.
	--graph	Display an ASCII graph of the branch and merge history beside the log output.
	--pretty	Show commits in an alternate format. Options include oneline, short, full, fuller, and format (where you specify your own format).

### Limiting Log Output ###

In addition to output-formatting options, `git log` takes a number of useful limiting options — that is, options that let you show only a subset of commits. You’ve seen one such option already — the `-2` option, which show only the last two commits. In fact, you can do `-<n>`, where `n` is any integer to show the last `n` commits. In reality, you’re unlikely to use that often, because Git by default pipes all output through a pager so you see only one page of log output at a time.

However, the time-limiting options such as `--since` and `--until` are very useful. For example, this command gets the list of commits made in the last two weeks:

	$ git log --since=2.weeks

This command works with lots of formats — you can specify a specific date (“2008-01-15”) or a relative date such as “2 years 1 day 3 minutes ago”.

You can also filter the list to commits that match some search criteria. The `--author` option allows you to filter on a specific author, and the `--grep` option lets you search for keywords in the commit messages. (Note that if you want to specify both author and grep options, you have to add `--all-match` or the command will match commits with either.)

The last really useful option to pass to `git log` as a filter is a path. If you specify a directory or file name, you can limit the log output to commits that introduced a change to those files. This is always the last option and is generally preceded by double dashes (`--`) to separate the paths from the options.

In Table 2-3 we’ll list these and a few other common options for your reference.

	Option	Description
	-(n)	Show only the last n commits
	--since, --after	Limit the commits to those made after the specified date.
	--until, --before	Limit the commits to those made before the specified date.
	--author	Only show commits in which the author entry matches the specified string.
	--committer	Only show commits in which the committer entry matches the specified string.

For example, if you want to see which commits modifying test files in the Git source code history were committed by Junio Hamano and were not merges in the month of October 2008, you can run something like this:

	$ git log --pretty="%h - %s" --author=gitster --since="2008-10-01" \
	   --before="2008-11-01" --no-merges -- t/
	5610e3b - Fix testcase failure when extended attribute
	acd3b9e - Enhance hold_lock_file_for_{update,append}()
	f563754 - demonstrate breakage of detached checkout wi
	d1a43f2 - reset --hard/read-tree --reset -u: remove un
	51a94af - Fix "checkout --track -b newbranch" on detac
	b0ad11e - pull: allow "git pull origin $something:$cur

Of the nearly 20,000 commits in the Git source code history, this command shows the 6 that match those criteria.

### Using a GUI to Visualize History ###

If you like to use a more graphical tool to visualize your commit history, you may want to take a look at a Tcl/Tk program called `gitk` that is distributed with Git. Gitk is basically a visual `git log` tool, and it accepts nearly all the filtering options that `git log` does. If you type `gitk` on the command line in your project, you should see something like Figure 2-2.

Insert 18333fig0202.png
Figure 2-2. The gitk history visualizer.

You can see the commit history in the top half of the window along with a nice ancestry graph. The diff viewer in the bottom half of the window shows you the changes introduced at any commit you click.

## Undoing Things ##

At any stage, you may want to undo something. Here, we’ll review a few basic tools for undoing changes that you’ve made. Be careful, because you can’t always revert some of these undos. This is one of the few areas in Git where you may lose some work if you do it wrong.

### Changing Your Last Commit ###

One of the common undos takes place when you commit too early and possibly forget to add some files, or you mess up your commit message. If you want to try that commit again, you can run commit with the `--amend` option:

	$ git commit --amend

This command takes your staging area and uses it for the commit. If you’ve made no changes since your last commit (for instance, you run this command immediately after your previous commit), then your snapshot will look exactly the same and all you’ll change is your commit message.

The same commit-message editor fires up, but it already contains the message of your previous commit. You can edit the message the same as always, but it overwrites your previous commit.

As an example, if you commit and then realize you forgot to stage the changes in a file you wanted to add to this commit, you can do something like this:

	$ git commit -m 'initial commit'
	$ git add forgotten_file
	$ git commit --amend

After these three commands, you end up with a single commit — the second commit replaces the results of the first.

### Unstaging a Staged File ###

The next two sections demonstrate how to wrangle your staging area and working directory changes. The nice part is that the command you use to determine the state of those two areas also reminds you how to undo changes to them. For example, let’s say you’ve changed two files and want to commit them as two separate changes, but you accidentally type `git add *` and stage them both. How can you unstage one of the two? The `git status` command reminds you:

	$ git add .
	$ git status
	# On branch master
	# Changes to be committed:
	#   (use "git reset HEAD <file>..." to unstage)
	#
	#       modified:   README.txt
	#       modified:   benchmarks.rb
	#

Right below the “Changes to be committed” text, it says "use `git reset HEAD <file>...` to unstage". So, let’s use that advice to unstage the `benchmarks.rb` file:

	$ git reset HEAD benchmarks.rb
	benchmarks.rb: locally modified
	$ git status
	# On branch master
	# Changes to be committed:
	#   (use "git reset HEAD <file>..." to unstage)
	#
	#       modified:   README.txt
	#
	# Changed but not updated:
	#   (use "git add <file>..." to update what will be committed)
	#   (use "git checkout -- <file>..." to discard changes in working directory)
	#
	#       modified:   benchmarks.rb
	#

The command is a bit strange, but it works. The `benchmarks.rb` file is modified but once again unstaged.

### Unmodifying a Modified File ###

What if you realize that you don’t want to keep your changes to the `benchmarks.rb` file? How can you easily unmodify it — revert it back to what it looked like when you last committed (or initially cloned, or however you got it into your working directory)? Luckily, `git status` tells you how to do that, too. In the last example output, the unstaged area looks like this:

	# Changed but not updated:
	#   (use "git add <file>..." to update what will be committed)
	#   (use "git checkout -- <file>..." to discard changes in working directory)
	#
	#       modified:   benchmarks.rb
	#

It tells you pretty explicitly how to discard the changes you’ve made (at least, the newer versions of Git, 1.6.1 and later, do this — if you have an older version, we highly recommend upgrading it to get some of these nicer usability features). Let’s do what it says:

	$ git checkout -- benchmarks.rb
	$ git status
	# On branch master
	# Changes to be committed:
	#   (use "git reset HEAD <file>..." to unstage)
	#
	#       modified:   README.txt
	#

You can see that the changes have been reverted. You should also realize that this is a dangerous command: any changes you made to that file are gone — you just copied another file over it. Don’t ever use this command unless you absolutely know that you don’t want the file. If you just need to get it out of the way, we’ll go over stashing and branching in the next chapter; these are generally better ways to go.

Remember, anything that is committed in Git can almost always be recovered. Even commits that were on branches that were deleted or commits that were overwritten with an `--amend` commit can be recovered (see *Chapter 9* for data recovery). However, anything you lose that was never committed is likely never to be seen again.

## Working with Remotes ##

To be able to collaborate on any Git project, you need to know how to manage your remote repositories. Remote repositories are versions of your project that are hosted on the Internet or network somewhere. You can have several of them, each of which generally is either read-only or read/write for you. Collaborating with others involves managing these remote repositories and pushing and pulling data to and from them when you need to share work.
Managing remote repositories includes knowing how to add remote repositories, remove remotes that are no longer valid, manage various remote branches and define them as being tracked or not, and more. In this section, we’ll cover these remote-management skills.

### Showing Your Remotes ###

To see which remote servers you have configured, you can run the `git remote` command. It lists the shortnames of each remote handle you’ve specified. If you’ve cloned your repository, you should at least see *origin* — that is the default name Git gives to the server you cloned from:

	$ git clone git://github.com/schacon/ticgit.git
	Initialized empty Git repository in /private/tmp/ticgit/.git/
	remote: Counting objects: 595, done.
	remote: Compressing objects: 100% (269/269), done.
	remote: Total 595 (delta 255), reused 589 (delta 253)
	Receiving objects: 100% (595/595), 73.31 KiB | 1 KiB/s, done.
	Resolving deltas: 100% (255/255), done.
	$ cd ticgit
	$ git remote
	origin

You can also specify `-v`, which shows you the URL that Git has stored for the shortname to be expanded to:

	$ git remote -v
	origin  git://github.com/schacon/ticgit.git (fetch)
	origin  git://github.com/schacon/ticgit.git (push)

If you have more than one remote, the command lists them all. For example, my Grit repository looks something like this.

	$ cd grit
	$ git remote -v
	bakkdoor  git://github.com/bakkdoor/grit.git
	cho45     git://github.com/cho45/grit.git
	defunkt   git://github.com/defunkt/grit.git
	koke      git://github.com/koke/grit.git
	origin    git@github.com:mojombo/grit.git

This means we can pull contributions from any of these users pretty easily. But notice that only the origin remote is an SSH URL, so it’s the only one I can push to (we’ll cover why this is in *Chapter 4*).

### Adding Remote Repositories ###

I’ve mentioned and given some demonstrations of adding remote repositories in previous sections, but here is how to do it explicitly. To add a new remote Git repository as a shortname you can reference easily, run `git remote add [shortname] [url]`:

	$ git remote
	origin
	$ git remote add pb git://github.com/paulboone/ticgit.git
	$ git remote -v
	origin	git://github.com/schacon/ticgit.git
	pb	git://github.com/paulboone/ticgit.git

Now you can use the string `pb` on the command line in lieu of the whole URL. For example, if you want to fetch all the information that Paul has but that you don’t yet have in your repository, you can run git fetch pb:

	$ git fetch pb
	remote: Counting objects: 58, done.
	remote: Compressing objects: 100% (41/41), done.
	remote: Total 44 (delta 24), reused 1 (delta 0)
	Unpacking objects: 100% (44/44), done.
	From git://github.com/paulboone/ticgit
	 * [new branch]      master     -> pb/master
	 * [new branch]      ticgit     -> pb/ticgit

Paul’s master branch is accessible locally as `pb/master` — you can merge it into one of your branches, or you can check out a local branch at that point if you want to inspect it.

### Fetching and Pulling from Your Remotes ###

As you just saw, to get data from your remote projects, you can run:

	$ git fetch [remote-name]

The command goes out to that remote project and pulls down all the data from that remote project that you don’t have yet. After you do this, you should have references to all the branches from that remote, which you can merge in or inspect at any time. (We’ll go over what branches are and how to use them in much more detail in *Chapter 3*.)

If you clone a repository, the command automatically adds that remote repository under the name *origin*. So, `git fetch origin` fetches any new work that has been pushed to that server since you cloned (or last fetched from) it. It’s important to note that the `fetch` command pulls the data to your local repository — it doesn’t automatically merge it with any of your work or modify what you’re currently working on. You have to merge it manually into your work when you’re ready.

If you have a branch set up to track a remote branch (see the next section and *Chapter 3* for more information), you can use the `git pull` command to automatically fetch and then merge a remote branch into your current branch. This may be an easier or more comfortable workflow for you; and by default, the `git clone` command automatically sets up your local master branch to track the remote master branch on the server you cloned from (assuming the remote has a master branch). Running `git pull` generally fetches data from the server you originally cloned from and automatically tries to merge it into the code you’re currently working on.

### Pushing to Your Remotes ###

When you have your project at a point that you want to share, you have to push it upstream. The command for this is simple: `git push [remote-name] [branch-name]`. If you want to push your master branch to your `origin` server (again, cloning generally sets up both of those names for you automatically), then you can run this to push your work back up to the server:

	$ git push origin master

This command works only if you cloned from a server to which you have write access and if nobody has pushed in the meantime. If you and someone else clone at the same time and they push upstream and then you push upstream, your push will rightly be rejected. You’ll have to pull down their work first and incorporate it into yours before you’ll be allowed to push. See *Chapter 3* for more detailed information on how to push to remote servers.

### Inspecting a Remote ###

If you want to see more information about a particular remote, you can use the `git remote show [remote-name]` command. If you run this command with a particular shortname, such as `origin`, you get something like this:

	$ git remote show origin
	* remote origin
	  URL: git://github.com/schacon/ticgit.git
	  Remote branch merged with 'git pull' while on branch master
	    master
	  Tracked remote branches
	    master
	    ticgit

It lists the URL for the remote repository as well as the tracking branch information. The command helpfully tells you that if you’re on the master branch and you run `git pull`, it will automatically merge in the master branch on the remote after it fetches all the remote references. It also lists all the remote references it has pulled down.

That is a simple example you’re likely to encounter. When you’re using Git more heavily, however, you may see much more information from `git remote show`:

	$ git remote show origin
	* remote origin
	  URL: git@github.com:defunkt/github.git
	  Remote branch merged with 'git pull' while on branch issues
	    issues
	  Remote branch merged with 'git pull' while on branch master
	    master
	  New remote branches (next fetch will store in remotes/origin)
	    caching
	  Stale tracking branches (use 'git remote prune')
	    libwalker
	    walker2
	  Tracked remote branches
	    acl
	    apiv2
	    dashboard2
	    issues
	    master
	    postgres
	  Local branch pushed with 'git push'
	    master:master

This command shows which branch is automatically pushed when you run `git push` on certain branches. It also shows you which remote branches on the server you don’t yet have, which remote branches you have that have been removed from the server, and multiple branches that are automatically merged when you run `git pull`.

### Removing and Renaming Remotes ###

If you want to rename a reference, in newer versions of Git you can run `git remote rename` to change a remote’s shortname. For instance, if you want to rename `pb` to `paul`, you can do so with `git remote rename`:

	$ git remote rename pb paul
	$ git remote
	origin
	paul

It’s worth mentioning that this changes your remote branch names, too. What used to be referenced at `pb/master` is now at `paul/master`.

If you want to remove a reference for some reason — you’ve moved the server or are no longer using a particular mirror, or perhaps a contributor isn’t contributing anymore — you can use `git remote rm`:

	$ git remote rm paul
	$ git remote
	origin

## Tagging ##

Like most VCSs, Git has the ability to tag specific points in history as being important. Generally, people use this functionality to mark release points (`v1.0`, and so on). In this section, you’ll learn how to list the available tags, how to create new tags, and what the different types of tags are.

### Listing Your Tags ###

Listing the available tags in Git is straightforward. Just type `git tag`:

	$ git tag
	v0.1
	v1.3

This command lists the tags in alphabetical order; the order in which they appear has no real importance.

You can also search for tags with a particular pattern. The Git source repo, for instance, contains more than 240 tags. If you’re only interested in looking at the 1.4.2 series, you can run this:

	$ git tag -l 'v1.4.2.*'
	v1.4.2.1
	v1.4.2.2
	v1.4.2.3
	v1.4.2.4

### Creating Tags ###

Git uses two main types of tags: lightweight and annotated. A lightweight tag is very much like a branch that doesn’t change — it’s just a pointer to a specific commit. Annotated tags, however, are stored as full objects in the Git database. They’re checksummed; contain the tagger name, e-mail, and date; have a tagging message; and can be signed and verified with GNU Privacy Guard (GPG). It’s generally recommended that you create annotated tags so you can have all this information; but if you want a temporary tag or for some reason don’t want to keep the other information, lightweight tags are available too.

### Annotated Tags ###

Creating an annotated tag in Git is simple. The easiest way is to specify `-a` when you run the `tag` command:

	$ git tag -a v1.4 -m 'my version 1.4'
	$ git tag
	v0.1
	v1.3
	v1.4

The `-m` specifies a tagging message, which is stored with the tag. If you don’t specify a message for an annotated tag, Git launches your editor so you can type it in.

You can see the tag data along with the commit that was tagged by using the `git show` command:

	$ git show v1.4
	tag v1.4
	Tagger: Scott Chacon <schacon@gee-mail.com>
	Date:   Mon Feb 9 14:45:11 2009 -0800

	my version 1.4
	commit 15027957951b64cf874c3557a0f3547bd83b3ff6
	Merge: 4a447f7... a6b4c97...
	Author: Scott Chacon <schacon@gee-mail.com>
	Date:   Sun Feb 8 19:02:46 2009 -0800

	    Merge branch 'experiment'

That shows the tagger information, the date the commit was tagged, and the annotation message before showing the commit information.

### Signed Tags ###

You can also sign your tags with GPG, assuming you have a private key. All you have to do is use `-s` instead of `-a`:

	$ git tag -s v1.5 -m 'my signed 1.5 tag'
	You need a passphrase to unlock the secret key for
	user: "Scott Chacon <schacon@gee-mail.com>"
	1024-bit DSA key, ID F721C45A, created 2009-02-09

If you run `git show` on that tag, you can see your GPG signature attached to it:

	$ git show v1.5
	tag v1.5
	Tagger: Scott Chacon <schacon@gee-mail.com>
	Date:   Mon Feb 9 15:22:20 2009 -0800

	my signed 1.5 tag
	-----BEGIN PGP SIGNATURE-----
	Version: GnuPG v1.4.8 (Darwin)

	iEYEABECAAYFAkmQurIACgkQON3DxfchxFr5cACeIMN+ZxLKggJQf0QYiQBwgySN
	Ki0An2JeAVUCAiJ7Ox6ZEtK+NvZAj82/
	=WryJ
	-----END PGP SIGNATURE-----
	commit 15027957951b64cf874c3557a0f3547bd83b3ff6
	Merge: 4a447f7... a6b4c97...
	Author: Scott Chacon <schacon@gee-mail.com>
	Date:   Sun Feb 8 19:02:46 2009 -0800

	    Merge branch 'experiment'

A bit later, you’ll learn how to verify signed tags.

### Lightweight Tags ###

Another way to tag commits is with a lightweight tag. This is basically the commit checksum stored in a file — no other information is kept. To create a lightweight tag, don’t supply the `-a`, `-s`, or `-m` option:

	$ git tag v1.4-lw
	$ git tag
	v0.1
	v1.3
	v1.4
	v1.4-lw
	v1.5

This time, if you run `git show` on the tag, you don’t see the extra tag information. The command just shows the commit:

	$ git show v1.4-lw
	commit 15027957951b64cf874c3557a0f3547bd83b3ff6
	Merge: 4a447f7... a6b4c97...
	Author: Scott Chacon <schacon@gee-mail.com>
	Date:   Sun Feb 8 19:02:46 2009 -0800

	    Merge branch 'experiment'

### Verifying Tags ###

To verify a signed tag, you use `git tag -v [tag-name]`. This command uses GPG to verify the signature. You need the signer’s public key in your keyring for this to work properly:

	$ git tag -v v1.4.2.1
	object 883653babd8ee7ea23e6a5c392bb739348b1eb61
	type commit
	tag v1.4.2.1
	tagger Junio C Hamano <junkio@cox.net> 1158138501 -0700

	GIT 1.4.2.1

	Minor fixes since 1.4.2, including git-mv and git-http with alternates.
	gpg: Signature made Wed Sep 13 02:08:25 2006 PDT using DSA key ID F3119B9A
	gpg: Good signature from "Junio C Hamano <junkio@cox.net>"
	gpg:                 aka "[jpeg image of size 1513]"
	Primary key fingerprint: 3565 2A26 2040 E066 C9A7  4A7D C0C6 D9A4 F311 9B9A

If you don’t have the signer’s public key, you get something like this instead:

	gpg: Signature made Wed Sep 13 02:08:25 2006 PDT using DSA key ID F3119B9A
	gpg: Can't check signature: public key not found
	error: could not verify the tag 'v1.4.2.1'

### Tagging Later ###

You can also tag commits after you’ve moved past them. Suppose your commit history looks like this:

	$ git log --pretty=oneline
	15027957951b64cf874c3557a0f3547bd83b3ff6 Merge branch 'experiment'
	a6b4c97498bd301d84096da251c98a07c7723e65 beginning write support
	0d52aaab4479697da7686c15f77a3d64d9165190 one more thing
	6d52a271eda8725415634dd79daabbc4d9b6008e Merge branch 'experiment'
	0b7434d86859cc7b8c3d5e1dddfed66ff742fcbc added a commit function
	4682c3261057305bdd616e23b64b0857d832627b added a todo file
	166ae0c4d3f420721acbb115cc33848dfcc2121a started write support
	9fceb02d0ae598e95dc970b74767f19372d61af8 updated rakefile
	964f16d36dfccde844893cac5b347e7b3d44abbc commit the todo
	8a5cbc430f1a9c3d00faaeffd07798508422908a updated readme

Now, suppose you forgot to tag the project at `v1.2`, which was at the "updated rakefile" commit. You can add it after the fact. To tag that commit, you specify the commit checksum (or part of it) at the end of the command:

	$ git tag -a v1.2 9fceb02

You can see that you’ve tagged the commit:

	$ git tag
	v0.1
	v1.2
	v1.3
	v1.4
	v1.4-lw
	v1.5

	$ git show v1.2
	tag v1.2
	Tagger: Scott Chacon <schacon@gee-mail.com>
	Date:   Mon Feb 9 15:32:16 2009 -0800

	version 1.2
	commit 9fceb02d0ae598e95dc970b74767f19372d61af8
	Author: Magnus Chacon <mchacon@gee-mail.com>
	Date:   Sun Apr 27 20:43:35 2008 -0700

	    updated rakefile
	...

### Sharing Tags ###

By default, the `git push` command doesn’t transfer tags to remote servers. You will have to explicitly push tags to a shared server after you have created them.  This process is just like sharing remote branches — you can run `git push origin [tagname]`.

	$ git push origin v1.5
	Counting objects: 50, done.
	Compressing objects: 100% (38/38), done.
	Writing objects: 100% (44/44), 4.56 KiB, done.
	Total 44 (delta 18), reused 8 (delta 1)
	To git@github.com:schacon/simplegit.git
	* [new tag]         v1.5 -> v1.5

If you have a lot of tags that you want to push up at once, you can also use the `--tags` option to the `git push` command.  This will transfer all of your tags to the remote server that are not already there.

	$ git push origin --tags
	Counting objects: 50, done.
	Compressing objects: 100% (38/38), done.
	Writing objects: 100% (44/44), 4.56 KiB, done.
	Total 44 (delta 18), reused 8 (delta 1)
	To git@github.com:schacon/simplegit.git
	 * [new tag]         v0.1 -> v0.1
	 * [new tag]         v1.2 -> v1.2
	 * [new tag]         v1.4 -> v1.4
	 * [new tag]         v1.4-lw -> v1.4-lw
	 * [new tag]         v1.5 -> v1.5

Now, when someone else clones or pulls from your repository, they will get all your tags as well.

## Tips and Tricks ##

Before we finish this chapter on basic Git, a few little tips and tricks may make your Git experience a bit simpler, easier, or more familiar. Many people use Git without using any of these tips, and we won’t refer to them or assume you’ve used them later in the book; but you should probably know how to do them.

### Auto-Completion ###

If you use the Bash shell, Git comes with a nice auto-completion script you can enable. Download the Git source code, and look in the `contrib/completion` directory; there should be a file called `git-completion.bash`. Copy this file to your home directory, and add this to your `.bashrc` file:

	source ~/.git-completion.bash

If you want to set up Git to automatically have Bash shell completion for all users, copy this script to the `/opt/local/etc/bash_completion.d` directory on Mac systems or to the `/etc/bash_completion.d/` directory on Linux systems. This is a directory of scripts that Bash will automatically load to provide shell completions.

If you’re using Windows with Git Bash, which is the default when installing Git on Windows with msysGit, auto-completion should be preconfigured.

Press the Tab key when you’re writing a Git command, and it should return a set of suggestions for you to pick from:

	$ git co<tab><tab>
	commit config

In this case, typing `git co` and then pressing the Tab key twice suggests commit and config. Adding `m<tab>` completes `git commit` automatically.

This also works with options, which is probably more useful. For instance, if you’re running a `git log` command and can’t remember one of the options, you can start typing it and press Tab to see what matches:

	$ git log --s<tab>
	--shortstat  --since=  --src-prefix=  --stat   --summary

That’s a pretty nice trick and may save you some time and documentation reading.

### Git Aliases ###

Git doesn’t infer your command if you type it in partially. If you don’t want to type the entire text of each of the Git commands, you can easily set up an alias for each command using `git config`. Here are a couple of examples you may want to set up:

	$ git config --global alias.co checkout
	$ git config --global alias.br branch
	$ git config --global alias.ci commit
	$ git config --global alias.st status

This means that, for example, instead of typing `git commit`, you just need to type `git ci`. As you go on using Git, you’ll probably use other commands frequently as well; in this case, don’t hesitate to create new aliases.

This technique can also be very useful in creating commands that you think should exist. For example, to correct the usability problem you encountered with unstaging a file, you can add your own unstage alias to Git:

	$ git config --global alias.unstage 'reset HEAD --'

This makes the following two commands equivalent:

	$ git unstage fileA
	$ git reset HEAD fileA

This seems a bit clearer. It’s also common to add a `last` command, like this:

	$ git config --global alias.last 'log -1 HEAD'

This way, you can see the last commit easily:

	$ git last
	commit 66938dae3329c7aebe598c2246a8e6af90d04646
	Author: Josh Goebel <dreamer3@example.com>
	Date:   Tue Aug 26 19:48:51 2008 +0800

	    test for current head

	    Signed-off-by: Scott Chacon <schacon@example.com>

As you can tell, Git simply replaces the new command with whatever you alias it to. However, maybe you want to run an external command, rather than a Git subcommand. In that case, you start the command with a `!` character. This is useful if you write your own tools that work with a Git repository. We can demonstrate by aliasing `git visual` to run `gitk`:

	$ git config --global alias.visual "!gitk"

## Summary ##

At this point, you can do all the basic local Git operations — creating or cloning a repository, making changes, staging and committing those changes, and viewing the history of all the changes the repository has been through. Next, we’ll cover Git’s killer feature: its branching model.
