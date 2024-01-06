---
title : Testing in Java Part 1
date: 2024-01-06
categories: [Java, Tutorial]
tags: [aws, learning]
toc: true
---

# Overview

[Testing using JUnit5 & Mockito framework](https://www.youtube.com/watch?v=H-3oYLLPvMM)

In addition to JUnit 5 and Mockito, there are a number of other testing frameworks available for Java, including TestNG and Selenium. Each framework has its own strengths and weaknesses, and the choice of which one to use will depend on the specific requirements of your project. It is also important to consider factors such as ease of use, community support, and documentation when selecting a testing framework.

[Testing using Junit5 & Mockito framework part 2 this is the main one](https://www.youtube.com/watch?v=_2fs_qjc0RQ)

This tutorial covers the basics of testing in Java using JUnit 5 and the Mockito framework. It includes examples of how to write test cases and use Mockito to mock dependencies. The second part focuses on more advanced topics such as testing Spring Boot applications and using MockMvc for testing REST APIs.

## Basics of Testing

- you need to create a class file for the tests that you are going to write
- then in the class you need to add the following dependencies

```java
@ContextConfiguration(classes = {RMAPIsServiceImp.class})
@ExtendWith(SpringExtension.class)
```

you can also do the same with the following annotations

> @ExtendWith(MockitoExtension.class)
> @DisplayName("AccordFintechServiceImp tests")

The next step involves us to mock all the different services or repos or whatever weâ€™re calling in the mocked file

something like this : 

```java
@Mock
AccordFintechService accordFintechService;
```

Next we need to add the actual service/repo or whatever to inject as a mock so we can later test it using assert equals

```java
@InjectMocks
AccordFintechServiceImp accordFintechServiceImp;
```

after that you just need to add @Test annotations to all the different test methods you create. Just make sure theyâ€™re imported as `org.junit.jupiter.api.Test;`

## When and Then

- this part tells us how to use the when and then return for mocking the returns of different methods that we call
- for example the following snippet of code will create a new object and return this specific object when the `getById` method is called

```java
UserOnboardCentral userOnboardCentral = new UserOnboardCentral();
        Organization organization = new Organization();
        OrganizationUserMapping organizationUserMapping = new OrganizationUserMapping();
        organizationUserMapping.setOrganization(organization);
        ClientDataMapping clientDataMapping = new ClientDataMapping();
        ClientDataCSV clientDataCSV = new ClientDataCSV();
        clientDataMapping.setClientDataCSV(clientDataCSV);
        clientDataMapping.setUserOnboardCentral(userOnboardCentral);
        userOnboardCentral.setClientDataMapping(clientDataMapping);
        organizationUserMapping.setUserOnboardCentral(userOnboardCentral);
        userOnboardCentral.setOrganizationUserMapping(organizationUserMapping);

        when(userOnboardCentralRepositoryImp.getById(anyString())).thenReturn(userOnboardCentral);
```

both when and then are from `import static org.mockito.Mockito`

- Finally you will need to actually test the method and see how things are working. For this you use assert equals like below

```java
assertEquals(rmClientMappingList.size(), rmapIsServiceImp.rmClientsList("000").size());
```