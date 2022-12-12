# class 26

## Django REST Framework

### Permissions

Together with authentication and throttling, permissions determine whether a request should be granted or denied access.

Permission checks are always run at the very start of the view, before any other code is allowed to proceed. Permission checks will typically use the authentication information in the request.user and request.auth properties to determine if the incoming request should be permitted.

Permissions are used to grant or deny access for different classes of users to different parts of the API.

The simplest style of permission would be to allow access to any authenticated user, and deny access to any unauthenticated user. This corresponds to the IsAuthenticated class in REST framework.

A slightly less strict style of permission would be to allow full access to authenticated users, but allow read-only access to unauthenticated users. This corresponds to the IsAuthenticatedOrReadOnly class in REST framework.

## API Reference

### AllowAny

The AllowAny permission class will allow unrestricted access, regardless of if the request was authenticated or unauthenticated.

This permission is not strictly required, since you can achieve the same result by using an empty list or tuple for the permissions setting, but you may find it useful to specify this class because it makes the intention explicit.

### IsAuthenticated

The IsAuthenticated permission class will deny permission to any unauthenticated user, and allow permission otherwise.

This permission is suitable if you want your API to only be accessible to registered users.

### IsAdminUser

The IsAdminUser permission class will deny permission to any user, unless user.is_staff is True in which case permission will be allowed.

This permission is suitable if you want your API to only be accessible to a subset of trusted administrators.

### IsAuthenticatedOrReadOnly

The IsAuthenticatedOrReadOnly will allow authenticated users to perform any request. Requests for unauthorised users will only be permitted if the request method is one of the "safe" methods; GET, HEAD or OPTIONS.

This permission is suitable if you want to your API to allow read permissions to anonymous users, and only allow write permissions to authenticated users.

### DjangoModelPermissions

This permission class ties into Django's standard django.contrib.auth model permissions. This permission must only be applied to views that have a .queryset property or get_queryset() method. Authorization will only be granted if the user is authenticated and has the relevant model permissions assigned. The appropriate model is determined by checking get_queryset().model or queryset.model.

POST requests require the user to have the add permission on the model.
PUT and PATCH requests require the user to have the change permission on the model.
DELETE requests require the user to have the delete permission on the model.
The default behaviour can also be overridden to support custom model permissions. For example, you might want to include a view model permission for GET requests.

To use custom model permissions, override DjangoModelPermissions and set the .perms_map property. Refer to the source code for details.

### DjangoModelPermissionsOrAnonReadOnly

Similar to DjangoModelPermissions, but also allows unauthenticated users to have read-only access to the API.

### DjangoObjectPermissions

This permission class ties into Django's standard object permissions framework that allows per-object permissions on models. In order to use this permission class, you'll also need to add a permission backend that supports object-level permissions, such as django-guardian.

As with DjangoModelPermissions, this permission must only be applied to views that have a .queryset property or .get_queryset() method. Authorization will only be granted if the user is authenticated and has the relevant per-object permissions and relevant model permissions assigned.

POST requests require the user to have the add permission on the model instance.
PUT and PATCH requests require the user to have the change permission on the model instance.
DELETE requests require the user to have the delete permission on the model instance.
Note that DjangoObjectPermissions does not require the django-guardian package, and should support other object-level backends equally well.

As with DjangoModelPermissions you can use custom model permissions by overriding DjangoObjectPermissions and setting the .perms_map property. Refer to the source code for details.

## Third party packages

### DRF - Access Policy

The Django REST - Access Policy package provides a way to define complex access rules in declarative policy classes that are attached to view sets or function-based views. The policies are defined in JSON in a format similar to AWS' Identity & Access Management policies.

### Composed Permissions

The Composed Permissions package provides a simple way to define complex and multi-depth (with logic operators) permission objects, using small and reusable components.

### REST Condition

The REST Condition package is another extension for building complex permissions in a simple and convenient way. The extension allows you to combine permissions with logical operators.

### DRY Rest Permissions

The DRY Rest Permissions package provides the ability to define different permissions for individual default and custom actions. This package is made for apps with permissions that are derived from relationships defined in the app's data model. It also supports permission checks being returned to a client app through the API's serializer. Additionally it supports adding permissions to the default and custom list actions to restrict the data they retrieve per user.

### Django Rest Framework Roles

The Django Rest Framework Roles package makes it easier to parameterize your API over multiple types of users.

### Django REST Framework API Key

The Django REST Framework API Key package provides permissions classes, models and helpers to add API key authorization to your API. It can be used to authorize internal or third-party backends and services (i.e. machines) which do not have a user account. API keys are stored securely using Django's password hashing infrastructure, and they can be viewed, edited and revoked at anytime in the Django admin.

### Django Rest Framework Role Filters

The Django Rest Framework Role Filters package provides simple filtering over multiple types of roles.

### Django Rest Framework PSQ

The Django Rest Framework PSQ package is an extension that gives support for having action-based permission_classes, serializer_class, and queryset dependent on permission-based rules.
