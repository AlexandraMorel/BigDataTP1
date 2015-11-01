# Bash command

## Maven on local machine:
        mvn archetype:generate -DarchetypeArtifactId=maven-archetype-quickstart -DgroupId=org.bigdata.tp1_2 -DartifactId=BankingAccount -DinteractiveMode=false

        cd ./Users/alexandra/BankingAccount
        mvn eclipse:eclipse

Add to POM.xml:
```xml
        <dependency>
                <groupId>org.apache.hadoop</groupId>
                <artifactId>hadoop-core</artifactId>
                <version>1.2.1</version>
        </dependency>
```

Then re-run
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
        git add FriendsMean-1.0-SNAPSHOT.jar
        git commit -m "Add .jar"
        kinit
        hadoop jar BankingAccount-1.0-SNAPSHOT.jar org.bigdata.tp1_2.BankAccount /res/mapred_assignment /home/amorel/output
        

Problem when we try to put files of the git on the Github: 
```
        git remote add origin git@github.com:AlexandraMorel/BigDataTP1.git
        git push origin master
```
We obtain "Permission denied (publickey)." so we create a SSH key to identify our local machine as a trusted computer.
```
        ssh-keygen -t rsa -b 4096 -C "amorel@edu.ece.fr"
        eval $(ssh-agent -s)
        ssh-add ~/.ssh/id_rsa
        clip < ~/.ssh/id_rsa.pub
```
We add .jar for each exercises.
```
        git add ./BankingAccount-1.0-SNAPSHOT.jar
        git commit -m "add bankingaccount files"
        git push --set-upstream git@github.com:AlexandraMorel/BigData_TP1.git master
        git pull git@github.com:AlexandraMorel/BigData_TP1.git
        git add ./FriendsMean-1.0-SNAPSHOT.jar
        git commit -m "add friendsmean files"
        git push --set-upstream git@github.com:AlexandraMorel/BigData_TP1.git master
        git pull git@github.com:AlexandraMorel/BigData_TP1.git
```

### II. Practice 1
Question
> It is useful to use the Reducer Class as a Combiner because it's an addition function (it would not be useful for a mean function). It can be used because the function is both commutative and associative.
