---
title : Testing in Java Part 2
date : 2024-01-06
categories : [java, tutorial]
tags : [java, tutorial]
toc : true
---

# Other Links
- [Link to part 1]({% post_url 2024-01-06-Testing-in-Java-part-01 %})

## Using stubs in testing in Java
- This was first brought up by Anivesh when he was "reviewing our code" for clovek and he said that another way of bypassing the failed test cases or to test some models is to use stubs [[code-review-may-02 1]]
- the flow that I understood went something like this (in our terms)
	1. start out at service interface
	2. then create new stub class
	3. after creating our stub class we implement all the interface
	4. this means we override all the methods in the interface and re-write them one-by-one
	5. Now the interesting thing is that when we write the test case we want to test the stub class
	6. testing the stub class gives us the coverage of the actual service implementation
	7. (it is unclear how this works exactly but we can use this to test our models as well)

[LINK to Jacoco on maven repository](https://mvnrepository.com/artifact/org.jacoco/jacoco-maven-plugin/0.8.10)

[Link to Jenkov explanation of the above](https://mvnrepository.com/artifact/org.jacoco/jacoco-maven-plugin/0.8.10)

[Mocks aren't stubs](https://www.martinfowler.com/articles/mocksArentStubs.html)
> _The term 'Mock Objects' has become a popular one to describe special case objects that mimic real objects for testing. Most language environments now have frameworks that make it easy to create mock objects. What's often not realized, however, is that mock objects are but one form of special case test object, one that enables a different style of testing. In this article I'll explain how mock objects work, how they encourage testing based on behavior verification, and how the community around them uses them to develop a different style of testing._

[Spring.io article on stubs and mocks](https://spring.io/blog/2007/01/15/unit-testing-with-stubs-and-mocks)

using stubs in this way should help in reducing the need to write extra logic code in test cases but it needs some more research 


This article talks about how to exclude modules in jacoco's test coverage [Configuring Jacoco in a Maven Project | SNMADDULA](https://snmaddula.bitbucket.io/maven-jacoco-config/) 

it looks a little like the following : 
```XML
<plugin>  
    <groupId>org.jacoco</groupId>  
    <artifactId>jacoco-maven-plugin</artifactId>  
    <version>0.8.1</version>  
    <executions>  
            <execution>  
                <id>prepare-agent</id>  
                <goals>  
                    <goal>prepare-agent</goal>  
                </goals>  
            </execution>  
            <execution>  
                <id>report</id>  
                <phase>prepare-package</phase>  
                <goals>  
                    <goal>report</goal>  
                </goals>  
                <configuration>  
                    <!-- Sets the path to the file which contains the execution data. -->  
                    <dataFile>target/jacoco.exec</dataFile>  
                    <!-- Sets the output directory for the code coverage report. -->  
                    <outputDirectory>target/jacoco-ut</outputDirectory>  
                </configuration>  
            </execution>  
    </executions>  
    <configuration>  
        <systemPropertyVariables>  
            <jacoco-agent.destfile>target/jacoco.exec</jacoco-agent.destfile>  
        </systemPropertyVariables>  
        <excludes>  
            <exclude>snmaddula/app/domain/*.class</exclude>  
            <exclude>snmaddula/app/exception/*.class</exclude>  
            <exclude>snmaddula/app/filter/*.class</exclude>  
            <exclude>snmaddula/app/App.class</exclude>  
        </excludes>  
    </configuration>  
</plugin>
```