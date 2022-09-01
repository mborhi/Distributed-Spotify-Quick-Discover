# Work Process

This file describes the design decisions made during the building of this application.

## Table of Contents
* [Authentication Service](#authentication-service)
* [Retrieval Service](#retrieval-service)
    + [Category and Genre Retrieval](#category-and-genre-retrieval)
    + [Playlist Retrieval](#playlist-retrieval)
* [Playback Service](#playback-service)
* [API Gateway](#api-gateway)
* [Frontend Clinet](#frontend-client)

---

# Authentication Service

This section describes my work process for developing the authentication service.

## User Authentication

While designing a way for users to login to spoitfy and for my application to receive the access token, I ran into several problems.

1. Where should my application store this token?
2. How can this be fast, and provide a good UX?
3. How can it be stored securely?
4. Will the token be easily manageble?
5. Is this scalable?

__(1)__ Associating the token with a session id and storing it in a Redis cache offers the best solution to all of these. Having a separate service to handle this allows for every client request to only be sent with a unique session id, which is then used to retrieve the access token from the cache. __(2)__ Firstly, storing this inside a cache provides extremeley fast retrieval results. Although, it should be mentioned that this adds an extra step for the application to access the token, which wouldn't be needed if the token is sent directly with every request. __(3)__ A separate service witha cache conviniently separates the user's token from the exposed client. Keeping the token on the backend as opposed to storing the token in a browser cookie, provides excellent security against XSS attacks. ))__(4)__ Additionally, leaving the token to only be operated on by a micro service allows for much easier token management and abstraction. For example, refreshing, validating, and processing new tokens can be done all in the service, without any other components of the application having to verify these. __(5)__ Finally, this solution can be scaled the best. The cache can expand to handle large number of concurrent users, especially when coupled with a container orchestration like Kubernetes. Later on, to handle even more users, algorithms like Least-Frequently-Used can be implemented.

---

# Retreival Service

This section describes my work process for developing the retrieval service.

## Category and Genre Retrieval

## Playlist Retrieval

---

# Frontend Client 

This section describes my work process for developing the frontend