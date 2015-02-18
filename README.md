# Lockdown Full Control Authorization
A plugin for Jenkins providing an authorization strategy named "Logged-in users can do anything (lockdown)"

## What is it good for
As per [my blog post](http://blog.backslasher.net/locking-down-jenkins-authentication.html), the authentication strategy "Logged-in users can do anything" (`FullControlOnceLoggedInAuthorizationStrategy`) grants read access to anonymous users, meaning that if your Jenkins contains private code / configuration and it's exposed by an unauthorized user, it's no longer private.  
My plugin provides an alternative strategy, identical to the original except for that anonymous privillage.

![](http://blog.backslasher.net/images/locking-down-jenkins-authentication/myauth.png)

## Building
Standard maven build.

1. Install Maven and JDK on your Machine/VM. Ubuntu users: `sudo apt-get install maven openjdk-7-jdk`
2. Build by `cd`ing to the project dir and running `mvn`
3. Install resulting `hpi` file

## Using
### Via GUI
After installing, select my strategy `Logged-in users can do anything (lockdown)` under "Manage Jenkins>Configure Global Security"
### Via CLI
Execute this Groovy script (optionally via "Manage Jenkins>Script Console"):
```groovy
def instance = Jenkins.getInstance()
def strategy = new net.backslasher.jenkins.LockdownFullControlOnceLoggedInAuthorizationStrategy()
instance.setAuthorizationStrategy(strategy)
instance.save()
```

## Contributing
Please submit PRs or issues! I hope I can help.  
Also, please drop me a line if you find my script useful.
