# Architecture

### FRONTEND:
TAILWIND CSS
React stuff
Typescript 
Feather Icons

### Backend => Custom WebServer made with Vert.x
Tools:
    Vert.x
    mySQL
    Yarn
#### Notes:
    A WebServer?
        Software that serves web content. Anything that can be on the web and be transferred on the web.
        Uses the HTTP protocol
        Uses Static; bland content and Dynamic; responsive and highly changable tings. Content
        Used to Host web pages
    How does a web server work?
        The client device makes a request to wherever the server is running (AWS) and it the server processes that request and return what its supossed to.
    What does a web server do?
        1. Listens
            waits for requests. Does nothing until we get a request
        2. On a port
            http port 80
        3. For a request
            literelly a request like post, get etc. 
            HTTP request lol
            HTTP and FTP are collective meaning you cant mix them up
        4. Transport protocol
             TCP protocol a shipper kinda service.
        5. Response
            We get on abck from the server.
            Suppose we have a button to show us a numebr one.
            Once we press the button... we send a request GJ
            then the server gets that and goes to its code and handles the task it supposed to do when the button is pressed: in this case to show the nnumber 1.
        6. Resource
            Routing
            /LOL/stoopid/dank/dum-dum
            Static routing is basically just like a file system <== this is boring doe this is used when we have stuff were data doesnt change often.
            Dynamic routing is when we have data that often changes like a users feed or profile
                You cant do this statically so you woukld save the current state of that to a database and update it dynamically.
                A place where our app can start and then based on requests we can make a collective redirect to the server that the user wants to go to.

    What is a database?
    
        Basically its an organized collection of data.
        mySQL is a relational database
            It is filled with tables that have rows and columns

## Backend Notes

#### Event Loop/Multi Reactor
The Event Loop is like a reactor design pattern copy.

It’s goal is to continuously check for new events, and each time a new event comes in, to quickly dispatch it to someone who knows how to handle it.

But by using only one thread to consume all the events, we’re basically not making the best use of our hardware. Node.js applications, for example, often spawn multiple processes to address that issue.

While providing good isolation, processes are expensive. Vert.x uses multiple threads instead, which are cheaper in terms of system resources.



What is Vert.X :

    Eclipse Vert.x and reactive in just a few words
    Eclipse Vert.x is a tool-​kit for build­ing re­ac­tive ap­pli­ca­tions on the JVM. Re­ac­tive ap­pli­ca­tions are both scal­able as work­loads grow, and re­silient when fail­ures arise. A re­ac­tive ap­pli­ca­tion is re­spon­sive as it keeps la­tency under con­trol by mak­ing ef­fi­cient usage of sys­tem re­sources, and by pro­tect­ing it­self from er­rors.

    Microservices
    Vert.x is backed by a large ecosys­tem of re­ac­tive mod­ules with just any­thing you need when writ­ing mod­ern ser­vices: a com­pre­hen­sive web stack, re­ac­tive data­base dri­vers, mes­sag­ing, event streams, clus­ter­ing, met­rics, dis­trib­uted trac­ing and more.

    Vert.x is a tool-​kit and not a frame­work that ships with black magic: what you write is ac­tu­ally what you get to ex­e­cute, as sim­ple as that.

    So what makes Vert.x a great op­tion for writ­ing your next cloud-​native or twelve-​factor app?

    In the beginning, there were threads…
    The clas­sic ap­proach to con­cur­rency is to use threads. Mul­ti­ple threads can live within a sin­gle process, per­form con­cur­rent work, and share the same mem­ory space.

    Threads
    Most ap­pli­ca­tion and ser­vice de­vel­op­ment frame­works are based on multi-​threading. On the sur­face, the model of hav­ing 1 thread per con­nec­tion is re­as­sur­ing be­cause de­vel­op­ers can rely on tra­di­tional im­per­a­tive style code.

    This is fine, es­pe­cially if you for­get about those silly mis­takes you can make with multi-​threading and mem­ory ac­cess …

    Multi-threading is “simple” but limited
    What hap­pens as the work­load grows be­yond mod­er­ate work­loads? (see the C10k prob­lem)

    The an­swer is sim­ple: you start mak­ing your op­er­at­ing sys­tem ker­nel suf­fer be­cause there is too much con­text switch­ing work with in-​flight re­quests.

    Blocking I/O
    Some of your threads will be blocked be­cause they are wait­ing on I/O op­er­a­tions to com­plete, some will be ready to han­dle I/O re­sults, and some will be in the mid­dle of doing CPU-​intensive tasks.

    Mod­ern ker­nels have very good sched­ulers, but you can­not ex­pect them to deal with 50 000 threads as eas­ily as they would do with 5 000. Also, threads aren’t cheap: cre­at­ing a thread takes a few mil­lisec­onds, and a new thread eats about 1MB of mem­ory.

    Asynchronous programming: scalability and resource efficiency
    Pro­cess­ing more con­cur­rent con­nec­tions with less threads is pos­si­ble when you use asyn­chro­nous I/O. In­stead of block­ing a thread when an I/O op­er­a­tion oc­curs, we move on to an­other task which is ready to progress, and re­sume the ini­tial task later when it is ready.

    Vert.x mul­ti­plexes con­cur­rent work­loads using event loops.

    Event loop
    Code that runs on event loops should not per­form block­ing I/O or lengthy pro­cess­ing. But don’t worry if you have such code: Vert.x has worker threads and APIs to process events back on an event loop.

    Pick the best asynchronous programming model for your problem domain
    We know that asyn­chro­nous pro­gram­ming re­quires more ef­forts. At the core of Vert.x, we sup­port call­backs and promises/fu­tures, the lat­ter being a sim­ple and el­e­gant model for chain­ing asyn­chro­nous op­er­a­tions.

    Ad­vanced re­ac­tive pro­gram­ming is pos­si­ble with Rx­Java, and if you pre­fer some­thing closer to tra­di­tional im­per­a­tive pro­gram­ming, then we are happy to pro­vide you with first-​class sup­port of Kotlin corou­tines.

    Asynchronous programming
    Vert.x sup­ports many asyn­chro­nous pro­gram­ming mod­els: choose what works best for each prob­lem you need to solve!

    Don’t let failures ruin responsiveness
    Fail­ures hap­pen all the time. A data­base will go down, the net­work will go down, or some ser­vice you de­pend on will be­come un­re­spon­sive.

    Failures
    Vert.x of­fers tools to keep la­tency under con­trol, in­clud­ing a sim­ple and ef­fi­cient cir­cuit breaker.

    A rich ecosystem
    The Eclipse Vert.x stack con­tains mod­ules for build­ing mod­ern, end-​to-end re­ac­tive ser­vices. From ef­fi­cient re­ac­tive data­base clients to event stream­ing, mes­sag­ing and web stacks, the Eclipse Vert.x project has you cov­ered:

    Ecosystem
    Can’t find what you are look­ing for?

    The Re­ac­ti­verse is a larger com­mu­nity around the re­ac­tive ecosys­tems where you can find more client and mod­ules.
    The Vert.x Awe­some repos­i­tory pro­vides links to even more in­ter­est­ing projects from the larger open-​source com­mu­nity!


        
