objc-gitlab-api
===============

[![Build Status](https://travis-ci.org/Indatus/objc-gitlab-api.png?branch=master)](https://travis-ci.org/Indatus/objc-gitlab-api)

### An Objective-C Gitlab Wrapper

## Installation with CocoaPods

<hr/>

To include this library just add the following to your projects Podfile:

```
pod 'ObjcGitlabApi', '~> 1.0'
```

## Usage

<hr/>

All of the calls to the API are executed from the singleton `GLGitlabApi` which uses blocks for the callbacks on each request.  Each call returns the operation that it begins so that it maybe canceled if necessary.

### Login

Logging in will return the information for the user requesting the login. 

```objc
[[GLGitlabApi sharedInstance] loginToHost:@"http://gitlab.example.com"
								 username:@"exampleuser"
				 				 password:@"password"
				  				  success:^(GLUser *user) {
									  	// Perform additional work here
									}
								  failure:^(NSError *error) {
								  		// Handle login failure
				  					}];
```

### Fetching Projects

To get all projects for a user you would use the following method:

```objc
[[GLGitlabApi sharedInstance] getUsersProjectsSuccess:^(NSArray *projects) {
											// Process projects
										}
					       				       failure:^(NSError *error) {
											// Handle error
										}];
```

Fetch details about a project:

```objc
[[GLGitlabApi sharedInstance] getProjectWithId:1
  	                                   success:^(GLProject *project) {
		                                 // Perform additional work here
        		                     }
                	                   failure:^(NSError *error) {
                                 		// Handle error here
		                             }];
```

The remaining calls in the api follow a similar pattern.

### Model Objects

The library contains a collection of model objects to manage the data passed back and forth between the api and the library.  It includes the following objects:

- GLBranch
- GLCommit
- GLDiff
- GLEvent
- GLFile
- GLGroup
- GLIssue
- GLMergeRequest
- GLMilestone
- GLNamespace
- GLNote
- GLProject
- GLSnippet
- GLTag
- GLUser
