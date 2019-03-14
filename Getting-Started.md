![StoreKeeper Logo](https://i.imgur.com/SXTH2r0.png)

## Todo

- [ ] Finish introduction
- [ ] Document the different authentication methods
- [ ] Add example code of how to authenticate to the StoreKeeper api
- [ ] Show example of basic usage (listing customers for example)

## Getting started

The StoreKeeper API allows programmatic access to all of the features that are available within the StoreKeeper backoffice. Usage of the API will allow you to fully integrate the StoreKeeper system*s* with your own system*s*.

Before you can start communicating with the StoreKeeper backend using the available API, you'll need an active StoreKeeper account and the neccesary credentials to sign-in into the StoreKeeper API Explorer. The API Explorer provides an easy way to make calls to the backend.

Using the API Explorer, it's possible to generate the code, which is needed to reproduce the result you got using the explorer. The code generation is currently only available for ++javascript++ and ++php++

## Important urls
| System | Url |
|--------|--------|
| backoffice | https://{account_name}.storekeeper.cloud |
| api explorer | https://explorer-{account_name}.storekeeper.cloud |

## Authentication methods

There are multiple ways to authenticate against a StoreKeeper backend. You can authenticate using a ++hash++, ++password++, or an ++api_key++.

### 1. Api Keys

Api keys are generated against a certain user. With this in mind you could create a system user for the service you want to use the API key for or just use an existing user to create the API key agaist.

#### 1.1 Getting sub user data

Generating an API key is easy and can be done using the API explorer. You start with login in the API explorer, and search for the `listSubusers` function in the `ManagementModule`. Here you can list all Users in your system, this includes also customer and contacts. So to be sure you have the correct account I recommend filtering on the email of the user you want to have.

Once you have the correct subuser, you need to save its `id` and `subaccount_id` for later use.

#### 1.2 Getting the API key

So firstly I would suggest checking if there already exists an API key for that user by using the `listSubuserApikeys` function of the `ManagementModule` with the subuser_id and subaccount_id filter set to the once we got before.

**Note: the `hash` you get back with the `listSubuserApikeys` function is this API key.**

If you want to generate the API key you go to the `newSubuserApikey` function in the `ManagementModule`, Where you are required to fill in the `subuser_id`, `subaccount_id` and a name for that API key and execute that, where you get the `id` back for that API key.

With that ID you can use  the `listSubuserApikeys` function again with that id as filter to get your hash which is the API key. 

### 2. Hash

// TODO: Write hash

### 3. Password

// TODO: Write password