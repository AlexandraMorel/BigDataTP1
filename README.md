# Bash command

## Maven on local machine:
        mvn archetype:generate -DarchetypeArtifactId=maven-archetype-quickstart -DgroupId=org.bigdata.tp1_2 -DartifactId=BankingAccount -DinteractiveMode=false

        cd ./Users/alexandra/BankingAccount
        mvn eclipse:eclipse

> Add to POM.xml:
```xml
        <dependency>
                <groupId>org.apache.hadoop</groupId>
                <artifactId>hadoop-core</artifactId>
                <version>1.2.1</version>
        </dependency>
```

> Then re-run
        mvn eclipse:eclipse
        mvn jar:jar (create the snapshot we will import on the server)

> Same commands for FriendsMean

## Git Bash:
        scp ./Users/alexandra/BankingAccount/target/BankingAccount-1.0-SNAPSHOT.jar amorel@haddop-ece.tk:/home/amorel/BigDataTP1 (import the file on the server)
        ssh amorel@hadoop-ece.tk
        mkdir ./BigDataTP1
        cd ./BigDataTP1
        git init
        vim README.md
        vim AUTHORS
        git add README.md
        git add AUTHORS
        git commit -m "Add AUTHORS and README.md files"
        git add BankingAccount-1.0-SNAPSHOT.jar
        git FriendsMean-1.0-SNAPSHOT.jar
        git commit -m "Add .jar"
        kinit
        hadoop jar BankingAccount-1.0-SNAPSHOT.jar org.bigdata.tp1_2.BankAccount /res/mapred_assignment /home/amorel/output

> Problem when we try: 
```
        git remote add origin git@github.com:AlexandraMorel/BigDataTP1.git
        git push origin master
```
> We obtain "Permission denied (publickey)."
> So we copy files from the server and add them to this Github manually.
