###Introduction
* An object passes through different stages in life cycle. - save(), load(), update(), merge()
* Interceptor interface provides methods which can be called at different stage to perform different tasks.
* These methods are callbacks from session to application, allowing application to inspect and/or manipulate properties of a persistent object before it is saved, updated, deleted or loaded.

###Steps to add Interceptors
* Created an Interceptor class by extending EmptyInterceptor
* Implement the functions wherever you want to tap & read object's information.
* And, when creating session factory, call setInterceptor() and pass Interceptor class object.