# CS136
## 4/4/2023 Week 1 Tuesday Lec 1
* Security is necessary
    * Malicious people
* Malicious code attacks
* DDOS
* Vulnerabilities in Commonly Used Systems
* SolarWinds
    * SupplyChain attack
* Electronic Commerce Attacks
* Log4j Vulnerability
    * A programming flaw in a popular package for Java program logging
    * Allows attacker to force a server to execute arbitrary remote code
* Why aren't all computer systems secure?
* Legacy and Retrofitting
    * Retrofitting security works poorly
        * Consider the history of patching
* Problems with patching
    * Usually done under pressure
* Some important definitions
    * Security, Protection, Vulnerabilities, Exploits, Trust
* Security is a policy
* Protection is a method for achieving a policy
* Vulnerability is a weakness that can allow an attacker to cause problems
* An exploit is an actual incident of taking advantage of a vulnerability
* Trust is doing certain things for those you trust
    * How do you express trust?
* Transitive trust
* Examples of transitive trust
    * Chains of certificates
* What are our security goals?
    * CIA (acronym)
    * Confidentiality
    * Integrity
    * Availability
* What are the Threats?
    * Theft (of data)
    * Privacy
    * Destruction
    * Interruption or interference with computer-controlled services
* Active Threats Vs. Passive Threats
    * Passive threats are forms of eavesdropping
        * No modification, injections of requests, etc.
* Social Engineering and Security
* Why isn't security easy?
    * Security is different than most other problems in CS
* Security is Actually Even Harder
## 4/6/2023 Week 1 Thursday Lec 2
* Security Principles, Policies, and Tools
* Design Principles for Secure Systems
    * Economy, complete mediation, open design, ...
* Economy in Security Design
* Complete Mediation
* Open Design
    * Doesn't work
* Separation of Privileges
    * different passwords
* Least Privilege
    * require user to login to purchase items
* Least Common Mechanism
    * don't share code among parts
* Acceptability
    * mechanism must be simple to use
    * least atonishment
        * people aren't surprised to provide maiden's name
* Fail-Safe Designs
    * Default to lack of access
    * Hackers send garbage at system to see what happens when they get an error message
* Security Policies
    * Security policies describe how a secure system should behave
    * Policy says what should happen, not how you achieve it
    * Generally, if you don't have a clear policy, you don't have a secure system
* Informal Security Policies
* Formal Security Policies
    * Typically expressed in a mathematical security policy language
    * Often matched to a particular policy model
    * Hard to express many sensible policies in formal ways
* Some Important Security Policies
* Bell-La Padula Model
    * Probably best-known formal computer security model
    * Corresponds to military classifications
    * Combines mandatory and discretionary access control
    * Two parts:
        * Clearances
        * Classifications
* Clearances
    * Subjects (people, programs, etc.) have a clearance
    * Clearance describes how trusted the subject is
    * E.g., unclassified, confidential, secret, top secret
* Classifications
    * Each object (file, database entry, etc.) has a classification
    * The classifciation describes how sensitive the object is
    * Using same categories as clearances
    * Informally, only people with the same (or higher) clearance should be able to access objects of a particular classification
* Goal of Bell-La Padula Model
    * Prevent any subject from ever getting read access to data at higher classification levels than subject's clearance
        * i.e., don't let untrusted people see your secrets
* Bell-La Padula Simple Security Condition
    * Subject S can read object O iff l_O <= l_S
* Why aren't we done
    * We really care about the info in an object
* The Bell-La Padula *-Property
    * S can write O iff l_S <= l_O
    * Prevents write-down
    * Can be proven that a system meeting these properties is "secure"
* Bell-La Padula Example
* So how do you really use the system?
    * There have to be mechanisms for reclassification
        * Usually requiring explicit operation
    * Danger that reclassification process will be done incautiously
    * Real systems also use classes of information
        * Remember least common mechanism?
* Integrity Security Policies
    * Designed to ensure that information is not improperly changed
* Example: Biba Integrity Policy
    * Subject set S, object set O
    * Set of ordered integrity levels I
    * Subjects and objects have integrity levels
    * Subjects at high integrity levels are less likely to screw up data
    * Data at a high integrity level is less likely to be screwed up
* Biba Integrity Policy Rules
    * s can write to o iff i(o) <= i(s)
    * s_1 can execute s_2 iff i(s_2) <= i(s_1)
    * A subject s can read object o iff i(s) <= i(o)
    * Why do we need the read rule?
* Hybrid Models
* The Problems with Security Policies
* Tools for Security
* Physical Security
    * Lock up computer
* Access Controls
    * Only let authorized parties access the system
    * A lot trickier than it sounds
* Encryption
    * Algorithms to hide the content of data or communications
    * Only those knowing a secret can decrypt the protection
    * One of the most important tools in computer security
* Authentication
    * Methods of ensuring that someone is who they say they are
* Encapsulation
    * Methods of allowing outsiders limited access to your resources
        * Preferably making inaccessible things invisible
* Intrusion Detection
    * All security methods sometimes fail
* Common sense
    * A lot of problems arise because people don't like to think
* Access Control
    * Security could be easy
    * The trick is giving access to only the right people
    * How do we ensure a given resource can only be accessed when it should be?
* Goals for Access Control
    * Complete mediation
    * Least privilege
    * Useful in a networked environment
    * Scalability
    * Acceptable cost and usability
* Access Control Mechanisms
    * Access control lists
    * Capabilities
    * Access control matrices
* Language of Access Control
    * Subjects are active entities (users or programs)
    * Objects represents things that can be accessed (files, devices, database records)
    * Access is any form of interaction with an object
    * An entity can be both subject and object
* Mandatory vs. Discretionary Access Control
    * Mandatory access control is dictated by the underlying system
    * Discretionary access control is under command of the user
* Realities of Discretionary Access Control
    * Most users never change the defaults on anything
    * Most users don't think about or understand access control
    * Proably not wise to rely on it to protect information you care about
* Access Control Lists
    * For each protected resource, maintain a single list
    * Each list entry specifies a user who can access the resoiurce
    * When a user requests access to a resource, check the access control list (ACL)
* ACL Example
* An ACL Protecting a File
* Issues for Access Control Lists
* Pros and Cons of ACLs
* Capabilities
    * Each subject keeps a set of data items that specify his allowable accesses
    * Essentially, a set of tickets
    * Possession of the capability for an object implies that access is allowed
* Properties of Capabilities
    * Must be unforgeable
    * In most systems, some capabilities allow creation of other capabilities
* Capabilities Protecting a File
* Options for Revoking Capabilities
    * Destroy the capability
    * Revoke on use
    * Generation numbers
* Pros and Cons of Capabilities
## 4/7/2023 Week 1 Friday Dis 1
* Specific naming format
* Submit tarball and also deter
## 4/11/2023 Week 2 Tuesday Lec 3
* Pros and Cons of Capabilities
* Distributed Access Control
    * ACLs still work ok
    * Capabilities are more problematic
* Role Based Access Control
* A Simple Example
* Changing Roles
    * Role based access control only helps if changing roles isn't trivial
* Practical Limitations on Role Based Access Control
* Reference Monitors
    * Whatever form it takes, access control must be instantiated in actual code
    * called reference monitor
* Desirable Properties of Reference Monitors
* Cryptography
    * Outline
        * What is data encryption?
        * Cryptanalysis
        * Basic encryption methods
* Introduction to Encryption
    * Much of computer security is about keeping secrets
* Encryption
    * Process of hiding information in plain sight
* Encryption and Data Transformations
    * One bit or byte pattern is transformed to another bit or byte pattern
* Encryption Terminology
    * Encryption is typically described in terms of sending a message
* More Terminology
    * Encryption
    * Decryption
    * A system for performing these transformations is a cryptosystem
        * Rules for transformation sometimes called a cipher
* Plaintext and Ciphertext
    * Plaintext is the original form of the emssage (often refferred to as P)
    * Ciphertext is the encrypted form of the message 
* Very basics of encryptions algorithms
    * Most algorithms use Keys to perform encryption and decryption
    * Without key, decryption is hard
    * With key, decryption is easy
* Terminology for Encryption Algorithms
    * The encryption algorithm E()
    * C = E(K, P)
    * Description algorithm D()
* Symmetric and Asymmetric Encryption Systems
    * Symmetric systems use the same keys for E and D
    * Asymmetric systems use different keys for E and D
* Characteristics of Keyed Encryption Systems
* Desirable Characteristics of Ciphers
* More Characteristics
* Yet More Characteristics
* Cryptanalysis
    * Process of trying to break a cryptosystem
    * Finding the meaning of an encrypted message without being given the key
    * To build a strong crypotsystem, you must understand cryptanalysis
* Forms of Cryptanalysis
* Breaking Cryptosystems
    * Most cryptosystems are breakable
    * Some just cost more to break than others
    * The job of the cryptosystem designer is to make the cost infeasible
* Types of Attacks on Cryptosystems
    * Ciphertext only, etc.
* Ciphertext only
* Known plaintext
    * Full or partial
* Chosen Plaintext
    * submit chosen samples
* Algorithm and Ciphertext
* Timing Attacks
* Basic Encryption Methods
    * Substitutions
        * Monoalphabetic
        * Polyalphabetic
    * Permutations
* Substitution Ciphers
    * Substitute one or more characters in a message with one or more different characters
    * Using some set of rules
    * Decryption is performed by reversing the substitutions
* Example of a Simple Substitution Cipher
* Caesar Ciphers
    * A simple substitution cipher like the previous example
* Is Caesar Cipher a Good Cipher?
    * It's simple
    * Fails to conceal many important characteristics of the message
    * Which makes cryptanalysis easier
    * Limited number of useful keys
* How would cryptanalysis attack a caesa cipher
    * Letter frequencies
    * In english, some letters occur more frequently than others
    * Caesar ciphers translate all occurences of a given plaintext letter
* More on frequency distributions
* Cryptanalysis and Frequency Distribution
    * Especially for Caesar ciphers
* Breaking Caesar Ciphers
* Applying frequencies to our example
* More Complex Substitutions
    * Monoalphabetic substitutions
* Are These Monoalphabetic Ciphers Better?
* Polyalphabetic Ciphers
    * Ciphers that don't always a translate a character into same ciphertext
* Example of Simple Polyalphabetic Cipher
* Are Polyalphabetic Ciphers Better?
* Cryptanalysis of Our Example
* How about for more complex patterns
* Methods of Attacking Polyalphabetic Ciphers
* How does the Cryptanalyst "know" when he's succeeded?
* Consider a Caesar Cipher
* The Unbreakable Cipher
* One-Time Pads
    * A new substitution alphabet for every character
    * Substitution alphabets chosen purely at random
    * Provably unbreakable without knowing this key
* Example of One Time Pads
* One Time Pads at Work
* What's so secure about that
* Security of One-Time Pads
* One-time pads and cryptographic snake oil
* Permutation Ciphers
* Characteristics of Permutation Ciphers
* Columnar Transpositions
* Attacking Columnar Transformations
* Double Transpositions
* Generalized Transpositions
* Which is Better, Transposition or Substitution?
* Quantum Cryptography
* Quantum Cryptanalysis
## 4/14/2023 Week 2 Thursday Lec 4
* Outline
* Stream and Block Ciphers
* Stream Ciphers
* Keys for Stream Ciphers
* Advantages of Stream Ciphers
* ... video didn't let me take notes
## 4/18/2023 Week 3 Tuesday Lec 5
* Key Management
* Outline
* Introduction
* Properties of Keys
* Key Length
* Are There Real Costs for Key Length?
* Key Randomness
* Generating Random Keys
* Cryptographic Methods
* Is This Method Secure?
* Perfect Forward Secrecy
* Random Noise
* On Users and Randomness
* Don't Go Crazy on Randomness
* Key Lifetime
* Why Change Keys?
    * A secret that cannot be readily changed should be regarded as a vulnerability
* Practicalities of Key Lifetimes
* Key Storage
    * Symmetric session keys
    * Long term symmetric keys
    * Private asymmetric keys
* Storing a User's Keys
* Destroying Old Keys
* Key Secrecy
* Some Problems with Key Sharing
* Why Do People Do This?
* TO make it clear
    * PRIVATE KEYS ARE PRIVATE
    * single user
* Key Generation
* Shared Session Key Problem
* Key Exchange Protocols
* Diffie/Hellman Key Exchange
* Exchanging a Key in Diffie/Hellman
* Why Can't Others Get the Secret?
    * discrete logarithm to obtain x or y
* A Snake in Diffie/Hellman's Grass
* The Core of the Problem
    * Diffie/Hellman does not authenticate the parties
* The Ubiquity of the Problem
* Authentication for Key Distribution
* Basic Approaches
* Key Servers
* Certificates
    * Server-less authentication
    * What is a certificate?
    * A signed electronic document proving you are who you claim to be
    * Most often used to solve key distribution problem
* Public Key Certificates
* Implementation of Public Key Certificates
* Checking a Certificate
* Does no one use Diffy-Helman then??
* Certificates and Diffie-Helman
    * Certificates are used to solve the Diffie-Hellman authentication problem
* Well, Sort Of
    * Big servers do but ordinary users don't have certificate
* Scaling Issues of Certificates
    * If there are 1-2 billion Internet users needing certificates, can one authority serve them all?
* Certification Hierarchies
    * Arrange certification authorities hierarchically
* Using Certificates From Hierarchies
* Extracting the Authentication
* A Example
* Certification Hierarchies Reality
* Certificates and Trust
* Potential Problems in the Certification Process
* Trustworthiness of Certificate Authority
* What Does a Certificate Really Tell Me?
* Showing a problem using an example
* Another Big Problem
* Revocation
* Revisiting Our Example
* Realities of Certificates
* An Example
* Firefox Preconfigured Certificate Authorities
* The Upshot
* The Problem in the Real World
* Effects of DigiNotar Compromise
* How Did the Compromise Occur?
* Another Practicality
* Reality of Expired Certificates
* Core Problem with Certificates
* Should we worry about Certificate Validity
* One Approach
## 4/20/2023 Week 3 Thursday Lec 6
* Outline
* Basics of Security Protocols
* Security Protocols
    * Series of steps involving two or more parties designed to accomplish a task with suitable security
* Types of Security Protocols
    * Arbitrated
    * Adjudicated
    * Self-enforced
* Participants in Security Protocols
    * Alice and Bob
* And the bad guys
    * Eve
        * passive
    * Mallory
        * malicious
    * Sometimes Alice or Bob might cheat
* Trusted Arbitrator
    * Trent
        * A disinterested third party trusted by all legitimate participates
* Goals of Security Protocols
* Key Exchange Protocols
* Key Exchange with Symmetric Encryption and an Arbitrator
    * Alice and Bob want to talk securely with a new key
* Step One, Step Two, Step Three
* What the Protocol Achieved?
* Problems with the Protocol
* The Man-in-the-Middle Attack
* Trent Does His Job
* How can Mallory prevent the message from being sent? I can see intercepting it????
* Really Getting in the Middle
* Mallory Plays Man-in-the-Middle
* Defeating the Main in the Middle
* Applying the First Fix
* But there's another problem
    * A replay attack
* Key Exchange with Public Key Cryptography
* Basic Key Exchange using PK
* Man-in-the-Middle with Public Keys
* Alice Chooses a Session Key
* Combined Key Distribution and Authentication
* Needham-Schroeder Key Exchange
* What's the Point of R_A
    * Random number chosen by Alice 
        * Helps defend against replay
* What's All This Extra Stuff For?
* Mallory Causes Problems
* What will Alice do now?
* So what's the problem?
* How do the random numbers help?
    * Why subtract one from R_A??? Also why is R_A stop replay attack??
* So, Everything's Fine, Right
* Mallory Cracks an Old Key
* Timestamps in Security Protocols
* Using Timestamps in the Needham-Schroeder Protocol
* Using Timestamps to Defeat Mallory
* Problems With Using Timestamps
    * Synchronized clocks
        * Attackers
    * Window of vulnerability
* Suppress-Replay Attack
    * Two participants in a security protocol
* Handling Clock Problems
    1. Rely on clocks fairly synchronized and hard to tamper with
        * Perhaps GPS signals
    2. Make all comparisons against the same clock
        * No two clocks need to be synchronized
* IS this overkill
    * Some attacks are specialized
* Why should we care?
    * Vulnerabilities leave room for exploits
* Something to Bear in Mind
    * These vulnerabilities aren't specific to just these protocols
## 4/25/2023 Week 4 Tuesday Lec 7
* Outline
* Introduction
    * Much of security is based on good access control
    * Access control only works if you have good authentication
    * What is authenication?
* Authentication
    * Determining the identity of some entity
        * Process, machine, human user
    * Requires notion of identity
* Authentication vs. Authorization
    * Authentication is determining who you are
    * Authorization is determining what someone is allowed to do
    * Can't authorize properly without authenication
* Proving identity in the physical world
    * Most frequently done by physical recognition
        * I recognize your face, your voice, your body
    * What about identifying those we don't already know
* Other Physical Identification Methods
    * Identification by credentials
    * Identification by recommendation
    * Identification by knowledge
    * Identification by location
        * You're behind the counter at the DMV
    * These all have cyber analogs
* Differences in Cyber Identification
    * Usually the identifying entity isn't human
    * Often the identified entity isn't human, either
    * Often no physical presence required
    * Often no later rechecks of identity
* Identifying with a computer
    * Not as smart as a human
    * Can't do certain things as well
    * But lightning fast on computations and less prone to simple errors
        * Mathematical methods are acceptable
* Identifying Computers and Programs
    * No physical characteristics
    * Generally easy to duplicate programs
    * Not smart enough to be flexible
    * Again, good at computations
* Physical Presence Optional
    * Often authenication required over a network or cale
    * Even if the party to be identified is human
    * So authenication mechanism must work in face of network characteristics
        * Active wiretapping
        * Everything is converted to digital signal
* Identity Might Not Be Rechecked
    * Human beings can make identification mistakes
    * But they often recover from them
        * Often quite easily
    * Based on observing behavior that suggests identification was wrong
    * Computers and programs rarely have that capability
        * if they identify something, they believe it
* Authenication Mechanisms
    * Something you know
    * Something you have
    * Something you are
    * Somewhere you are
* Passwords
    * Authenication by what you know
    * One of the oldest and most commonly used security mechanisms
    * Authenticate the user by requiring him to produce a secret
* Problems with Passwords
    * They have to be unguessable
    * If networks connect remote devices to computers, susceptible to password sniffers
    * Unless quite long, brute force attacks often work on them
* Proper use of passwords
    * Passwords should be sufficiently long
    * Passwords should be unguessable
    * Passwords should never be written down
    * Passwords should never be shared
    * Hard to achieve all this simultanneously
* Passwords and Single Sign-On
    * Many systems ask for password once
        * Resulting authentication lasts for an entire "session"
    * Used on its own, complete mediation definitely not achieved
    * Trading security for convnience
    * Especially if others can use the authenicated machine
* Handling Passwords
    * The OS must be able to check passwords when users log in
    * So must the OS store passwords?
    * Not really
        * Store encrypted version
    * Encrypt the offered password
        * Using a one-way function
    * And compare it to the stored version
* One Way Functions
    * Functions that convert data A into data B
    * But it's hard to convert data B back into data A
        * Hard for anyone
    * Often done as a particular type of cryptographic operation
    * Depend on particular use, simple hashing might be enough
* Standard Password Handling
* Is Encrypting the Password File Enough?
    * What if an attacker gets a copy of your password file?
* Dictionary attacks on an encrypted password file
* Attack Dictionaries
    * Real dictionary attacks don't use Webster's
    * Dictionary based on probability of words being used as passwords
    * Partly set up as procedures
    * Check common names, proper nouns, etc. early in the process
    * Tend to evolve to match user trends
* A Serious Issue
    * All Linux machines use the same one-way function to encrypt passwords
    * If someone runs the entire dictionary through that function
* Illustrating the Problem
* The Real Problem
    * Not just that Darwin and Marx chose the same password
    * But that anyone who chose that password got the same encrypted result
    * So the attacker need only encrypt every possible password once
* Salted Passwords
    * Combine the plaintext password with a random number
        * Then run it through the one-way function
    * The random number need not be secret
    * It just has to be different for different users
* What is this salt, really?
    * An integer that is combined with the password before hashing
* Modern Dictionary Attacks
    * Modern machines are very fast
    * Even with salting, huge dictionaries can be checked against encrypted passwords quickly
* GPU Password Cracking
    * GPUs are great for password cracking
        * Highly parallelizable task
        * 200x faster than CPU
    * Possible to build cheap, powerful GPU unit for this purpose (less than $2000)
    * Prototypes crack 20-50% of passwords in example files in a few minutes
* Password Management
* Limit Login Attempts
    * Don't allow dictionary attacks "over the wire"
    * After some reasonable number of failed login attempts, do something
        * Lock account
        * Slow down
            * iPhone does this, Android doesn't
        * Watch more closely
* Encrypt Your Passwords
    * Using the techniques we just covered
    * One would think this advice isn't necessary but
        * GoDaddy lost 1.2 million unecrypted passwords in 2021
    * Encryption is more expensive and less convenient
* Protecting the Password File
    * So it's OK to leave the encrypted version of the password file around?
    * No it isn't
    * Why make it easy for attackers?
    * Dictionary attacks on single accounts still work
    * And there are "popular" passwords, leading to easy dictionary attacks
* Other Issues for Proper Handling of User's Passwords
    * Sites should store unencrypted passwords as briefly as possible
        * Partly issue of how they store the file
        * Partly issue of good programming
    * Don't leave passwords in temp files or elsewhere
    * Should not be possible to print or save someone's unencrypted password
* Handling Forgotten Passwords
    * Users frequently forget passwords
    * How should your site deal with it?
    * Bad idea
        * Store plaintext passwords and send them on request
    * Better idea
        * Generate new passwords when old ones forgotten
    * Example of common security theme
        * Security often at odds with usability
* Generating New Passwords
    * Easy enough to generate a random one
    * But you need to get it to the user
* Transporting New Passwords
    * The engineering solution is usually to send it in email
    * Often fine for practical purposes
    * But there are very serious vulnerabilites
        * E.g., unecrypted wireless networks
    * If you really care, use something else
        * E.g. surface mail
* User Issues with Passwords
    * Password profileration
* Password Proliferation
    * Practically every web site you visit wants you to enter a password
* Using the Same Password
    * Easier to remember
    * Much less secure
        * One password guesser gets all your authenication info
        * Do you trust all the sites you visit equally
        * Compromise in one place compromises you everywhere
        * Real attacks are based on this vulnerability
* Using Different Passwords
    * Much more secure
    * But how many passwords can you actually rememeber?
    * And you might "solve" this problem by choosing crummy passwords
    * Or by altering one good password
* Other options
    * Use a few passwords
    * Write down your passwords
        * Several diadvantages
        * Could write down hints
    * Use algorithm customized to site
    * Password vaults
* Password Vaults
    * Also known as key chains and password managers
    * Store a lot of passwords in encrypted form
    * Require another password to decrypt them
    * Typically integrated with web passwords
    * Single sign-on issue
* Choosing Passwords
    * Typically a compromise between
        * Sufficient security
        * Remembering it
    * Major issues
* How Long Should Passwords Be?
    * Generally a function of how easy it is for attackers to attack them
    * Changes as speed of processors increase
    * Nowadays, 15 character password are pretty safe
        * If they aren't guessable
    * Old sites may demand shorter ones
* Some Password Choice Strategies
    * Use first letters from a phrase you remember (or entire phrase, if allowed)
    * Use several randomly chosen words
    * Replace letters with numbers and symbols
* Challenge/Response Authenication
    * Authenication by what questions you can answer correctly
        * Again, by what you know
    * The system asks the user to provide some information
    * If it's provided correctly, the user is authenticated
* Differences from Passwords
    * Challenge/response systems ask for differnet information every time
    * Or at least the questions come from a large set
    * Best security achieved by requiring what amounts to encryption of the challenge
        * But that requires special hardware
        * Essentially a smart card
* Identification Devices
    * Authenication by what you have
    * A smart card or other hardware device that is readable by the computer
* Simple Use of Authenication Tokens
    * If you have the token, you are identified
* Authenication with Smart Cards
    * How can the server be sure of the remote user's identity
* Some Details on Smart Cards
    * Cryptography performed only on smart card
        * So compromised client machine can't steal keys
    * Often user must enter password to activate card
        * Should it be entered to the card or the computer?
* Problems with Identification Devices
    * If lost or stolen, you can't authenicate yourself
        * And maybe someone else can
        * Often combined with passwords to avoid this problem (two factor authenication)
    * Unless cleverly done, suspectible to sniffing attacks
    * Requires special hardware
* Authenication Through Biometrics
    * Authenication based on who you are
    * Things like fingerprints, voice patterns, retinal patterns, etc.
    * To authenticate to the system, allow system to measure the appropriate the physical characterstics
* Problems with Biometric Authenication
    * Requires very special hardware
        * Except systems that use typing patterns
    * May not be as foolproof as you think
    * What happens when it's cracked?
* When do Biometrics (maybe) work well?
    * When you use them for authenication
    * When biometric readers are themselves secure
    * When attacks are rare or difficult
    * In conjunction with other authenication
* When do Biometrics (Definitely) work poorly
    * Finding "needles in haystacks"
        * Terrorists in airports
    * When working off low-quality readings
    * When the biometric reader is easy to bypass or spoof
        * Anything across a network is suspect
    * When the biometric is "noisy"
        * Too many false negatives
* Characterizing Biometric Accuracy
    * How many false positives?
        * Match made when it shouldn't have been
    * Versus how many false negatives?
        * Match not made when it should have been
    * Crossover Error Rate (CER)
        * When false positive meets false negative
* Some Typical Crossover Error Rates
* Biometrics and Usability
    * Always a tradeoff between false positive and false negatives
    * For consumer devices, false negatives are very, very bad
        * People discard devices that won't let the legitimate user in
    * Can you maek the false positive rate non-trivial with almost no false negs?
* Didn't Carnegie Mellon Perfect Facial Recognition
* Authentication by where you are
    * Soemtimes useful in ubiquitous computing
    * The issue is where the message in question is coming from the machine that's nearby
    * Less important who owns that machine
* Multi-Factor Authenication
    * Try more than one type of authenication
    * Unless all work, don't authenticate
* Recommendations for password managers?? White paper for how they don't actually know the password themselves??
* Could I throw away the private key for storing passwords???
## 4/27/2023 Week 4 Thursday Lec 8
* Multi-Factor Authentication
    * More than one type of authenication
    * Unless all work, don't authenticate
* Practical Multifactor Authentication
    * Something you know + something you have
    * E.g. password and smart phone
    * Provide the password and respond to a probe of your phone
    * ATMs have used this idea for years
        * Your PIN and ATM card
    * Vital that at least one factor be non-replayable
* Is This Better?
    * Now two things need to go wrong for false authenication
    * Are factors really orthogonal
    * Are both factors non-trivial
    * Is one factor likely to suffer a catastrophic break
* Multifactor Authentication and Users
    * Users generally don't like it
    * Only works when they're motivated
    * They might get over it...
* Regardless, It's State-of-the-Art
    * All expert security advice says to use multi-factor authentication
* Passkeys
    * A new authentication industry standard
* Passkey Advantages
    * No secret password
    * No replayable secrets
    * Secret info only stored in trusted place
* Operating System Security
* Outline
    * Waht does the OS protect?
    * Authentication for operating systems
    * Memory protection
        * Buffer overflows
    * IPC protection
        * Covert channels
    * Stored data protection
        * Full disk encryption
* Introduction
    * Operating systems provide the lowest layer of software visible to users
    * Operating systems are close to the hardware
    * If the operating system isn't protected, the machine isn't protected
    * Flaws in the OS generally compromise all security at higher levels
* Why is OS Security So Important?
    * OS controls access to application memory
    * OS controls scheduling of the processor
    * OS ensures that users receive the resources they ask for
    * OS isn't oding these things securely, practically anything can go wrong
    * So almost all other security systems must assume a secure OS at the bottom
* Single User vs Multiple User Machines
    * Majority of today's computers usually support a single user
    * Some computers are still multi-user
    * Single user machines often run multiple processes, though
    * Increasing numbers of embedded machines
* Trusted Computing
    * Since OS security is vital, how can we be sure out OS is secure?
    * Partly a question of building in good security mechanisms
    * But also a question of making sure you're running the right OS
    * That's called trusted computing
* How Do Achieve Trusted Computing?
    * From the bottom up
    * We need hardware we can count on
    * It can ensure the boot program behaves
    * The boot can make sure we run the right OS
* TPM and Bootstrap Security
    * Trusted Platform Module
        * Special hardware designed to improve OS security
    * Proves OF was booted with a particular bootstrap loader
        * Using tamperproof HW and cryptographic techniques
    * Also provides secure key storage and crypto support
* TPM and OS itself
    * Once the bootstrap loader is operating, it uses TPM to check the OS
    * Essentially, ensures that expected OS was what got booted
* Trust vs. Security
    * TPM doesn't guarantee security
    * It doesn't mean the OS and app are secure, or even non-malicious
    * It just verifies that they are versions you have said you trust
    * Offers some protection against tampering with software
    * But doesn't prevent other bad behavior
* Status of TPM
    * Hardware widely installed
    * Microsoft Bitlocker uses it
    * A secure Linux boot loader and OS work with it
    * Some specialized software uses TPM
* SecureBoot
    * A somewhat different approach to ensuring you boot the right thing
    * Built into the boot hardware and SW
    * Designed by Microsoft
    * Essentially only allows booting of particular OS versions
* Some Details of SecureBoot
    * Part of the Unified Extensible Firmware Interface (UEFI)
        * Replacement for BIOS
    * Microsoft insists on HW supporting these features
    * Only boots systems with pre-arranged digital signatures
    * Some issues of who can set those
* Authentication and Authorization in Operating Systems
    * The OS must authenticate all user requests
        * Otherwise, can't control access to critical resources
    * Humans users log in
    * Processes run on their behalf
    * Once authenticated, requests must be authorized
* In-Person User Authentication
    * Authenticating the physically present user
    * Most frequently using password techniques
    * Sometimes biometrics
    * To verify that a particular person is sitting in front of keyboard and screen
* Remote User Authentication
    * Many users access machines remotely
    * How are they authenicated?
    * Most typically by password
    * Sometimes via public key crypto
    * Sometimes at OS level, sometimes by a particular process
        * In latter case, what is their OS identity
        * What does that imply for security?
* Process Authentication
    * Successful login creates a primal process
        * Under ID of user who logged in
    * OS securely ties a process control block to the process
    * Processes can fork off more processes
    * Usually special system calls can change a process' ID
* For example
    * Process X wants to open file Y for read
    * File Y has read permissions set for user Bill
    * If process X belongs to user Bill, system ties the oepn call to that user
    * And file system checks ID in open system call to file system permissions
    * Other syscalls (e.g., RPC) similar
* Authorization in Operating Systems
    * Operating systems allow user processes to perform system calls
        * Which generally do things that not all users/processors do
* Authorization and Reference Monitors
    * If an operation requires authorization, it should pass through a reference monitor
    * Reference monitors add overhead
        * So we don't want to use them unnecessarily
* Protecting Memory
    * What is there to protect in memory?
    * Page tables and virtual memory protection
* What Is In Memory?
    * Executable code
    * Copies of permanently stored data
    * Temporary process data
* Mechanisms for Memory Protection
    * Most general purpose systems provide some memory protection
    * Usually through virtual memory methods
    * Originally arose mostly for error containment, not security
* Paging and Security
    * Main memory is divided into page frames
    * Every process has an address space divided into logical pages
    * For a process to use a page, it must reside in a page frame
    * If multiple processes are running, how do we protect their frames?
* Protection of Pages
    * Each process is given a page table
        * Translation of logical addresses into physical locations
    * All addressing goes through page table
        * At unavoidable hardware level
    * If the OS is careful about filling in the page tables, a process can't even name other processes' pages
* Page Tables and Physical Pages
    * Process Page Tables
    * Physical Page Frames
* Security Issues of Page Frame Reuse
    * A common set of page frames is shared by all processes
    * The OS switches ownership of page frames as necessary
    * When a process acquires a new page frame, it used to belong to another process
        * Can the new process read the old data?
* Strategies for Cleaning PAges
    * Don't bother
    * Zero on deallocation
    * Zero on reallocation
        * The basic Linux strategy
    * Zero on use
    * Clean pages in the background
        * Windows strategy
* Special Interfaces to Memory
    * Some systems provide a special interface to memory
    * If the interface accesses physical memory
        * And doesn't go through page table protections
        * Then attackers can read the physical memory
        * Letting them figure out what's there and find what they're looking for
* Buffer Overflows
    * One of the most common causes for compromises of operating systems
    * Due to a flaw in how operating systems handle process inputs
* What is a Buffer Overflow?
    * A program requests input from a user
    * It allocates a temporary buffer to hold the input data
    * It then reads all the data the user provides into the buffer, but ...
    * It doesn't check how much data was provided
* For example
* Well, What If the User Does?
    * Code continues reading data into memory
    * First 32 bytes go into name buffer
        * Allocated on the stack
        * Close to record of current function
    * The remaining bytes go onto the stack
        * Right after name buffer
        * Overwriting current function record
        * Including the instruction pointer
* Why is This a Security Problem?
    * The attacker can cause the function to "return" to an arbitrary address
    * But all attacker can do is run different code than was expected
    * He hasn't gotten into anyone els'e data
* Is That So Bad?
    * Well yes
    * That's why a media player can write configuration and data files
    * Unless roles and access permissions set up very carefully, a typical program can write all its user's files
* The Core Buffer Overflow Security Issue
    * Programs often run on behalf of others
    * Maybe OK for you to access some data
    * But is it OK for someone who you're running a program for to access it?
        * Downloaded programs
        * Users of web servers
        * Many other cases
* Using Buffer Overflows to Compromise Security
    * Carefully choose what gets written into the instruction pointer
    * So that the program jumps to something you want to do
    * Such as execute shell
* Effects of Buffer Overflows
    * A remote or unprivileged local user runs a program with greater privileges
* Stack overflows
    * The most common kind of buffer overflow
    * Intended to alter the contents of the stack
    * Usually by overflowing a dynamic variable
    * Usually with intention of jumping to exploit code
* What Can you Do with Heap Overflows?
    * Alter variable values
    * "Edit" linked lists or other data structures
* Some Recent Buffer Overflows
    * Nginx web server
* Fixing Buffer Overflows
    * Write better code
    * Use programming languages that prevent them
    * Add OS controls that prevent overwriting the stack
    * Windows ASLR
    * Windows DEP
* Protecting Interprocess Communications
    * Operating systems provide various kinds of interprocess communications
        * Messages, sempahores, shared memory, sockets
    * How can we be sure they're used properly?
* IPC Protection Issues
    * How hard it is depends on what you're worried about
* Message Security
* How Can B Get the Secret?
    * He can convince the system he's A
    * He can break into A's memory
    * He can forge a message from someone else to get the secret
    * He can "eavesdrop" on someone else who gets the secret
* Can an Attacker Really Eavesdrop on IPC Message?
    * On a single machine, what is a message send, really?
    * A copy from a process buffer to an OS buffer
* Other Forms of IPC
    * Semaphores, sockets, shared memory, RPC
    * Pretty much all the smae
* So When Is It Hard?
    1. When there's a bug in the OS
        * E.g., not always checking authorization
        * Allows masquerading, ...
    2. What if it's not a single machine?
    * ...
* Distributed System Issues
    * What if your RPC is really remote?
    * RPC tries to make remote access look "just like" local access
    * The hard part is authentication
        * The call didn't come from your OS
        * How do you authenticate its origin
* The Other Hard Case
    * Process A wants to tell the secret to process B
    * But the OS has been instructed to prevent that 
        * A necessary part of Bell-La Padula
* OS Control of Interactions
    * OS can "understand" the security policy
    * Can maintain labels
* Covert Channels
    * Tricky ways to pass information
    * Requires cooperation of sender and receiver
        * Generally in active attempt to decieve
    * Use something not ordinarily regarded as a communications mechanism
* Covert Channels in Computers
    * Generally, one process "sends" a covert message to another
    * How?
        * Disk activity, Page swapping, Time slice behavior, Use of a peripheral device, Limited only by imagination
* Handling Covert Channels
    * Relative easy if you know details of how the channel is used
        * Put noise
    * Hard to impossible if you don't know what the channel is
    * Not most people's problem
* Stored Data Protection
    * Files are a common exmaple of a typically shared resource
    * If an OS supports multiple users, it needs to address the question of file protection
    * Simple read/write access control
    * What else do we need to do?
    * Protect the raw disk or SSD
* Encrypted File Systems
    * Data stored on disk is subject to many risks
        * Impromper access through OS flaws
* An Example of an Encrypted File System
    * Issues for encrypted file systems
    * When does the cryptography occur?
    * Where does the key come from?
    * What is the granularity of cryptography?
* When does cryptography occur?
    * Transparently when a user opens a file?
    * By explicit user command
    * How long is the data decrypted
    * Where does it exist in decrypted form?
* Where does the key come from?
    * Provided by human user?
    * Stored somewhere in file system
    * Stored on a smart card?
    * Stored in the disk hardware?
    * Stored on another computer?
* What is the Granularity of Cryptography?
    * An entire disk?
* What are you trying to protect against with crypto file systems
    * Unauthorized access by impromper users?
        * Why not just access control?
    * The OS itself?
        * What protection are you really getting?
    * Data transfers across a network?
    * Someone who accesses the device not using the OS?
        * A realistic threat in your environment
* Full Disk Encryption
    * All data on the disk is encrypted
    * Data is encrypted/decrypted
## 5/2/2023 Week 5 Tuesday Lec 9
* Introduction
* Some Important Network Characteristics for Security
* Degree of Locality
* Network Media
    * Some networks are wires, cables, or over telephone lines
        * Can be physically protected
    * Other networks are satellite links or other radio links
        * Physical protection possibilities more limited
* Protocol Types
    * TCP/IP is most used
    * In places, other protocols replace TCP/IP
    * And there are lots of supporting protocols
* Implications of Protocol Type
    * The protocol defines a set of rules that will always be followed
    * Specific attacks exist against specific protocols
* Threats To Network
    * Wiretapping
    * Impersonation
    * Attacks on message
        * Confidentiality
* Wiretapping
    * Passive wiretapping
    * Active wiretapping
    * Packet sniffers
    * Wiretapping on wireless often just a matter of putting up an antenna
* Impersonation
    * A packet comes in over the network
    * Often the action to be taken with the packet depends on the source
    * But attackers may be able to create packets with false sources
* Violations of Message Confidentiality
    * Other problems can cause messages to be inappropriately divulged
    * Misdelivery can send a message to the wrong place
    * Message can be read at an intermediate gateway or a router
    * Sometimes an intruder can get useful information just by traffic analysis
* Message Integrity
    * Even if the attacker can't create the packet he wants, sometimes he can alter proper packets
    * To change the effect of what they will do
    * Typically requires access to part of the path message takes
* Denial of Service
    * Attacks that prevent legitimate users from doing their work
    * By flooding the network
    * Or corrupting routing tables
    * Or flooding routes
    * Or destroying key packets
* How do Denial of Service Attacks Occur?
    * Basically, the attacker injects some form of traffic
    * Most current networks aren't built to throttle uncooperative parties very well
    * All-inclusive nature of the Internet makes basic access trivial
    * Universality of IP makes reaching most of the network easy
* An Example: SYN Flood
    * Based on vulnerability in TCP
    * Attacker uses initial request/response to start TCP session to fill a table at the server
    * Preventing new real TCP sessions
    * SYN cookies and firewalls with massive tables are possible defenses
* Normal SYN Behavior
    * Table of open TCP connections
* A SYN Flood
* SYN Cookies
    * SYN/ACK number is secret function of various information
    * Key Point: Server doesn't need to save cookies value
* General Network Denial of Service Attacks
    * Need not tickle any particular vulnerability
    * Can achieve success by mere volume of packets
    * If more packets sent than can be handled by target, service is denied
    * A hard problem to solve
* Distributed Denial of Service Attacks
    * Goal: Prevent a network site from doing its normal business
    * Method: Overwhelm the site with attack traffic
    * ?
* The Problem
* Why are these attacks made?
    * Annoy
    * Extortion
    * Prevent adversary from doing something important
    * If directed at infrastructure, might cripple parts of Internet
* Attack Methods
    * Pure flooding
    * Overwhelm some other resource
    * Direct or reflection
* Why "Distributed"?
    * Targets are often highly provisioned
    * A single machine usually cannot overwhelm such a server
    * So harness multiple machines
    * Makes defenses harder
* How to Defend?
    * A vital characteristic
        * Don't just stop a flood
        * Ensure Service to Legitimate Clients
    * If you deliver a manageable amount of garbage, you haven't solve the problem
* Complicating Factors
    * High availability of compromised machines
    * Internet is designed to deliver traffic
    * IP spoofing allows easy hiding
    * Distributed nature makes legal approaches hard
    * Attacker can choose all aspects of his attack packets
        * Can be a lot like good ones
* Basic Defense Approaches
    * Overprovisioning
    * Dynamic increase in provisioning
    * Hiding
    * Tracking attackers
    * Legal approaches
    * Reducing volume of attack
    * None of these are totally effective
* Traffic Control Mechanisms
    * Filtering
        * Source address filtering
        * Other forms of filtering
    * Rate limits
    * Protection against traffic analysis
* Source Address Filtering
    * Filtering out some packets because of their source address value
    * Often called ingress filtering
* Source Address Filtering for Address Assurance
    * Router "knows" what network it sits in front of
        * In particular, knows IP addresses of machines there
    * Filter outgoing packets with source addresses not in that range
    * Prevent your users from spoofing other nodes' addresses
        * But not from spoofing each other's
* Source Address Filtering Example
* Source Address Filtering in the Other Direction
    * Often called egress filtering
    * Occurs as packets leave the Internet and 
    * ...
* Filtering Incoming Packets
    * Packets with this source address should be going out, not coming in
* Other Forms of Filtering
    * One can filter on things other than source address
    * Also, there are unallocated IP addresses in IPv4 space
    * Some source addresses for local use only
* Realistic Limits on Filtering
    * Little filtering possible in Internet core
    * Filtering near edges has its own limits
* Another Filtrering Possibility
    * Redirect packets to a special filtering site on the edge of the network
    * They filter on any basis they want
    * ...
* Rate Limits
    * Many routers can place limits on the traffic they send to a destination
    * Ensuring that the destination isn't overloaded
    * Limits can be defined somewhat flexibly
    * ...
* Padding
    * Sometimes you don't want intruders to know what your traffic characteristics are
    * Padding adds extra traffic to hide the real stuff
    * Fake traffic must look like real traffic
    * Must be done carefully, or clever attackers can tell the good stuff from the noise
* Routing Control
    * Use ability to control message routing to conceal the traffic in the network
    * Used in onion routing to hide who is sending traffic to whom
    * Routing control also used in some network defense
* Firewalls
    * What is a firewall?
    * A machine to protect a network from malicious external attacks
    * Typically a machine that sits between a LAN/WAN and the Internet
    * ...
* Typical Use of a Firewall
* Firewalls and Perimeter Defense
    * Firewalls implement a form of security called perimeter defense
    * Protect the inside of something by defending the outside strongly
    * Control the entry and exit points
    * If nothing bad can get in, I'm safe, right?
* Weaknesses of Perimeter Defense Models
    * Breaching the perimeter compromises security
    * Generally hard to impossible to create a perfect perimeter
    * Perimeter defnse is part of the solution, not the entire solution
* Defense In Depth
    * An old principle in warfare
    * Don't rely on a single defensive mechanism or defense at a single point
    * Combine different denses
    * Defeating one defense doesn't defeat your entire plan
* So What Should Happen?
* Or, Better
* Or, Even Better
* So are firewalls any use?
    * Definitely
    * Aren't full solution, but they are part of it
    * ...
* Brass Tacks of Firewalls
    * What do they really do
    * Examine incoming packet
    * Decide to let the packet through or drop it
    * Perhaps log the decision
    * Maybe send rejected packets elsewhere
    * Pretty much all there is to it
* Types of Firewalls
    * Filtering gateways
        * AKA screening routers
    * Application level gatewyas
    * ...
* Filtering Gateways
    * Based on packet header information
    * Based on that info, either let the packet through or reject it
    * Stateless firewalls
* Example Use of Filtering Gateways
    * Allow particular external machines to telnet into specific internal machines
    * ...
* A Fundamental Problem
    * IP addresses can be spoofed
    * If your filtering firewall trusts packet headers, it offers little protection
    * Situation may be improved by IPsec
    * ...
* Filtering Based on Ports
    * Most incoming traffic is destined for a particular machine and port
    * Only let through packets to select machines at specific ports
    * Makes it impossible to externally exploit flaws in little-used ports
* Pros and Cons of Filtering Gateways
    * Fast, Cheap, Flexible, Transparent
    * Limited capabilities, Dependent on header authentication, Generally poor logging, May rely on router security
* Application Level Gateways
    * Also known as proxy gateways
    * Firewalls that understand the application-level details of network traffic
    * Traffic is accepted or reject based on the probable results of accepting it
    * Stateful firewalls
* How Application Level Gateways Work
    * The firewall serves as a general framework
    * Various proxies are plugged into the framework
    * Incoming packets are examines
    * Proxy typically accepts or rejects
* Deep Packet Inspection
    * Another name for typically activity of application level firewalls
    * Looking into packets beyond their headers
        * Especially IP header
    * "Deep" sometimes also means deeper understanding of what's going on
    * It almost always means "expensive"
        * In terms of performance
* Firewall Proxies
    * Programs capable of understanding particular kinds of traffic
    * Proxies are specialized
    * A good proxy has deep understanding of the network application
    * Typically limited by complexity ...
* Pros and Cons of Application Level Gateways
    * Highly flexible, Good logging, Content-based filtering, Potentially transparent
    * Slower, More complex and expensive, Highly dependent on proxy quality
* Reverse Firewalls
    * Normal firewalls keep stuff from the outside from getting inside
    * Reverse firewalls keep stuff from the insider from getting outside
    * Often colocated with regular firewalls
    * Why do we need them?
* Possible USes of Reverse Firewalls
    * Concealing details of your network from attacks
    * Prevent compromised machines from sending things out
        * E.g., intercepting bot communications or stopping DDoS
        * Preventing data exfiltration
## 5/11/2023 Week 6 Wednesday Lec 10
* Outline
    * Intrusion
* Introduction
* Intrusion Detection
* Why Intrusion Detection?
    * If we can detect bad things, can't we simply prevent them
    * Possibly not
        * May be too expensive
* For Example
    * Your intrusion detection system regards setting uid on root executables as suspicious
    * If the system detects several such events, it becomes suspicious
* Couldn't the System just have stopped this?
* Intrusions
* Kinds of Intrusions
* External Intrusions
* Internal Intrusions
* Information from 2022 Verizon Report
* Basics of Intrusion Detection
* Intrusion Detection and Logging
* On-Line vs Off-Line Intrusion Detection
* Failures in Intrusion Detection
* Desired Characteristics in Intrusion Detection
* Host Intrusion Detection
* Advantages of the Host Approach
* Network Intrusion Detection
* Advantages of Network Approach
* Network Intrusion Detection and Data Volume
* Network Intrusion Detection and Sensors
* Network Intrusion Detection and Deep Packet Inspection
* Wireless IDS
* Application-Specific IDS
    * SQL
* Styles of Intrusion Detection
* Misuse Detection
    * signature detection
* Level of Misuse Detection
    * Specific attacks
        * SYN floods
* How is Misuse Detection?
* Pluses and Minuses of Misuse Detection
* Misuse Detection and Commercial Systems
* Anomaly Detection
* Methods of Anomaly Detection
* Pluses and Minuses of Anomaly Detection
* Anomaly Detection and Academic Systems
* Specification Detection
* How Does This Differ from Misuse and Anomaly Detection?
* Some Challenges
    * How much state do you have to look at?
* Protocol Anomaly Detection
* Pluses and Minuses of Specification Detection
* Customizing and Evolving Intrusion Detection
* How do Intrusion Detection Systems Evolve?
* A Problem with Manually Evolving Systems
* A Problem with Evolving Intrusion Detection Systems
* Intrusion Detection Tuning
* Practicalities of Operation
* Practicalities of Audit Logs for IDS
* What Does an IDS Do When It Detects an Attack?
* Consequences of the Choices
* How Good Does an IDS Have To Be?
* False Positives and IDS Systems
* Consider a Case for Manual Response
* What are your Choices?
* Intrusion Prevention Systems
* Sample Intrusion Detection Systems
* Snort
* Bro
* RealSecure ISS
* Is Intrusion Detection Useful?
    * widely criticized
* Which Type of Instrusion Detection System should I use?
* Future of Intrusion Detection?
* Conclusions
## 5/16/2023 Week 7 Tuesday Lec 11
* Malicious software
* Outline
* Introduction
* Where does Malicious code come from?
* Magnitude of the Problem
* Viruses
* How do viruses work?
* Before the Infected program runs
* Macro and Attachment Viruses
* Virus Toolkits
* How to Find Viruses
* Precautions to Avoid Viruses
* Other Precautionary Measures
* Containment
* Viruses and File Sizes
* Signature Scanning
* How to Scan for Signatures
* Weaknesses of Scanning for Signatures
* Polymorphic Viruses
* Polymorphism by Hand
* Stealth Viruses
* Combating Stealth Viruses
* Other Detection Methods
* Preventing Virus Infections
* How to Deal with Virus Infections
* Disinfecting Programs
* Trojan Horses
* Basic Trojan Horses
* Recent Trends in Trojan Horses
* RATs
* Trapdoors
* Trapdoors and Other Malware
* Logic Bombs
* Ransomware and Extortionware
* Pay?
* Or Don't Pay?
* Ransomware Impacts
* Worms
* Some Famous Worms
* Code Red
* Code Red Errors
* Code Red II
* Impact of Code Red and Code Red II
* Stuxnet
* Where did Stuxnet come from?
* Worm, Virus, or Trojan Horse?
* Botnets
* What are Botnets used for?
* Botnet Software
* Botnet Communications
* Botnet Spreading
* Characterizing Botnets
* Why Are Botnets Hard To Handle
* Approaches to Handling Botnets
* Spyware
* What is done with Spyware?
* Where does Spyware come from?
* RAM Scrapers
* Malware Components
* Droppers
* Rootkits
* Use of Rootkits
* Ongoing Rootkit Behavior
## 5/18/2023 Week 7 Thursday Lec 12
* Secure Programming
* Outline
* Introduction
* Designing for Security
* Defining Security Goals
* Security and Other Goals
* Managing Software Security Risk
* Risk Management and Software Development
* Incorporating Security into Spiral Model of SW Development
* But How Do I Determine Risk?
* Design and Security Experts
* Principles for Secure Software
* Secure the Weakest Link
* For Example
* Practice Defense in Depth
* For Example
* Fail Securely
* For Example
* Use Principle of Least Privilege
* For Example
* Compartmentalize
* For Example
* Value Simplicity
* For Example
* Especially Important When Human Users Involved
* Promote Privacy
* For Example
* Remember That Hiding Secrets is Hard
* For Example
* Be Reluctant to Trust
* For Example
* Use Your Community Resources
* For Example
* Choosing Technologies
* Choices and PRacticalities
* Operating System Choices
* Language Choices
* C and C++
    * Worse security choice
* Java
* Python
* Scripting Languages
* Scripting Language Security Issues
* Open Source vs. Closed Source
* Is the "Many Eyes" Argument Correct?
* The Flip Side Argument
* The Upshot?
    * No solid evidence that open source or closed source produces better security
* One More Consideration
* Major Problem Areas for Secure Programming
* Example Problem Areas
* Buffer Overflows
* Preventing Buffer Overflows
* Which Syscalls are Problematic?
* What do you do instead?
* Is that all I have to do
* An Example
* Why is this an problem?
* How does that work?
* What is this result?
* Other Programming Tools for Buffer Overflow Prevention
* Data Execution Prevention (DEP)
* Randomizing Address Space (ASLR)
* Other Input Verification Problems
* The Heartbleed Bug
* SSL Heartbeat Messages
* The Security Flaw
* For Example
* Exploiting Heartbleed
* Fixing Heartbleed
* Impacts of Heartbleed
## 5/23/2023 Week 8 Tuesday Lec 13
* Error handling
* A Typical Error Handling Problem
* Some Examples
* Checking Return Codes
* Privilege Escalation
* An Example Problem
* A Real World Example
* What To Do About This?
* Virtualization Approaches
* Race Conditions
* What is a Race Condition
* Security Implications of Race Conditions
* The TOCTOU Issue
* A Short Detour
* Effective UID and Access Permissions
* An Example
* What's (Supposed to Be) Going on Here?
* What's Really Going On Here?
* How the Attack Works
* The Dynamics of the Attack
* How Likely Was That?
* Some Types of Race Conditions
* A Real Example
* Other Recent Race Conditions
* Preventing Race Conditions
* Randomness and Determinism
* Pseudorandom Number Generators
* Attacks on PRNGs
* A Recent Example
* How to Do Better?
* Proper Use of Cryptography
* Using Crypto Properly
* An Example
* What was happening?
* Another Example
* Why Did That Cause Problems?
* Variable Synchronization
* An Example
* The Problematic Code
* Variable Initalization
* A Little Code
* What's the Output
* Why is this Dangerous?
* Variable Cleanup
* Use-After-Free Bugs
* An Example Use-After-Free Bug
* What Was the Effect?
* Recent Examples of Use-After-Free Bugs
* Remote Code Execution Vulnerabilities
* Remote Code Execution and Middleware
* A Common Problem
* Recent Examples
* How to Avoid this Problem?
* Some other problem areas
* Yet More Problem Areas
* Why Should You Care?
* So ... ?
* That's What They Always Say
* But How to Balance Things?
* Some Good Coding Practices
## 5/25/2023 Week 8 Thursday Lec 14
* Web Security
* The Web Security Problem
* Aspects of the Web Problem
* Who are we protecting?
* Some real threats
* More threats
* Yet More Threats
* Compromise Threats
* Solution Approaches
* Compromising the Browser
* But My Browser Must Be Ok...
* The Lock Icon
* What Are the Implications
* Another Browser Security Issue
* Same Origin Policy
* Web Cookies
* Same Origin Policy and Cookies
* A Cookie Caveat
* SQL Injection Attacks
* An Example
* What Happens Then?
* Basis of SQL Injection Problem
* Some Example Attacks
* Solution Approaches
* Examining Input for SQL
* Avoid SQL in Web Interfaces
* Use Parameterized Variables
* Malicious Downloaded Code
* Types of Downloaded Code
* Drive-By Downloads
* Solution Approaches
* Disabling Scripts
* Use Secure Scripting Languages
* Isolation Mechanisms
* Signatures and Blacklists
* Cross-Site Scripting
* Effect of XSS
* Non-Persistent XSS
    * Embed a small script in a link poiting to a legitimate web page
* Persistent XSS
* Why is XSS Common
* Typical Effects of XSS Attack
* Solution Approaches
* Disallowing Data Uploading
* Don't Allow Script Uploading
* Protect the User's Web Browser
* Cross-Site Request Forgery
    * CSRF
* Issues for CSRF Attacks
* CSRF in the wild
* Exploiting Statelessness
* A Simple Example
* Why Is That A Problem?
* A Concrete Example
* What Went Wrong?
* The Core Problem
* Solution Approaches
* Data Transport Issues
* (Non-) Use of Data Encryption
* Why Web Sites Don't Use Encryption
* Problems with Not Using Encryption
* Using Encryption on the Web
* Increased Use of Web Encryption
* Sometimes Encryption Isn't Enough
* Conclusion
## 5/30/2023 Week 9 Tuesday Lec 15
* Course evaluations
* Evaluating System Security
* Outline
* Secure System Standards
* Some Security Standards
* U.S. Orange Book
* Purpose of the Orange Book
* Why did the Orange Book fail?
* The Common Criteria
* What's the Common Criteria About?
* How Does it Work?
* How Do You Know a Product Meets a Profile?
* Status of the Common Criteria
* Problems with Common Criteria
* Evaluating Existing Systems
* Two Different Kinds of Problems
* Evaluating System Design Security
* How Do You Evaluate a System's Security?
* Stages of Review
* Design Reviews
* Purpose of Design Review
    * Threat Modeling
* Attack Surfaces
* Threat Modeling
* Information Collection
* One Approach
* Sources of Information
* Application Architecture Modeling
* Modeling Tools for Design Review
* Threat Identification
* Attack Trees
* A Sample Attack Tree
* STRIDE Approach
* STRIDE Threats
* How to Apply STRIDE
* Documentation of Findings
* DREAD Risk Ratings
* Priortizing Implementation Review
* One Prioritization Approach
* Application Review
* Need to Define a Process
* Review Process Outline
* Reviewing the Application
* General Approaches to Design Reviews
* Code Auditing Strategies
* Some Example Strategies
* Guidelines for Auditing Code
* Useful Auditing Tools
* Evaluating Running Systems
* Logging
* The Basics of Logging
* Access Logs
* Other Typical Logging Actions
* Problems With Logging
* Log Security
* Local Logging vs Remote Logging
* Local Logging
* Remote Logging
* Desirable Characteristics of a Logging Machine
* Network Logging
* Logging and Privacy
* Some Examples
* Auditing
* Auditing Requirements
* When Should You Audit?
* Auditing and Logs
* What Does an Audit Cover?
* Does Auditing Really Occur?
* Conclusion
## 6/1/2023 Week 9 Thursday Lec 16
* Privacy
* What is Privacy?
* Privacy and Computers
* Privacy and Our Network Operations
* Threat to Computer Privacy
* Some Specific Privacy Problems
* Do Users Care About Privacy?
* Data Privacy Issues
* Privacy of Personal Data
* Protecting Data Sets
* Options for Protecting Data
* Data Mining and Privacy
* An Example of the Problem
* Insider Threats and Privacy
* Local Examples
* Encryption and Privacy
* Problems with Data Encryption for Privacy
* One Major Case
* A Recent Case
* Network Privacy
* Traffic Analysis Problems
* A Cautionary Example
* How Did They Do That?
* Location Privacy
* Cellphones and Location
* Other Electronic Communications and Location
* Implications of Location Privacy Problems
* Why Isn't the Internet Private?
* Privacy and Cryptocurrency
* A Recent Example
* Web Privacy
* Do Not Track
* The Problems with Do Not Track
* What Do Not Track Really Means
* Some Privacy Solutions
* Data Encryption for Privacy
* A Fundamental Issue
* Full Disk Encryption
* Anonymizers
* The Problem with Anonymizers
* An Early Example
* VPNs
* VPN Compromise
* VPNs and Traffic Analysis
* Onion Routing
* A Little More Detail
* Sending an Onion-Routed Packet
* In Diagram Form
* What's Really in the Packet
* Delivering the Message
* What's Been Achieved?
* Issues for Onion Routing
    * Proper use of keys
    * Traffic analysis
    * Overheads
        * Multiple hops
        * Multiple encryptions
* Tor
* Why Hasn't Tor Solved This Privacy Problem?
* Can't I Surreptitiously Run Tor?
* Another Problem With Tor?
* Privacy and End-to-End Cryptography
* Privacy-Preserving Data Mining
* Approaches to Privacy for Data Mining
* The NSA and Privacy
* Privacy Policies
* European Privacy Laws
* U.S. Privacy Laws
* Google's Privacy Announcement
* But...
* Conclusion
