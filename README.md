## Introduction

PantherDB is a <b>Simple</b>, <b>FileBase</b> and <b>Document Oriented</b> database that you can use it in your projects.

### Features:
- Document Oriented
- Easy to use
- Written in pure Python +3.11 based on standard type hints
- 85% Test coverage


## Usage

### Database:
- #### Create database:
    ```python
    db: PantherDB = PantherDB('database.json')
    ```

- #### Access to a collection:
    ```python
    user_collection: PantherCollection = db.collection('User')
    ```

- #### Delete a collection:
    ```python
    db.collection('User').drop()
    ```
### Create:
- #### Insert document:
    ```python
    user: PantherDocument = db.collection('User').insert_one(first_name='Ali', last_name='Rn')
    ```

### Get:
- #### Find first document:
    ```python
    user: PantherDocument = db.collection('User').first(first_name='Ali', last_name='Rn')
    ```
    or
    ```python
    user: PantherDocument = db.collection('User').first()
    ```

- #### Find last document:
    ```python
    user: PantherDocument = db.collection('User').last(last_name='Rn')
    ```
    or
    ```python
    user: PantherDocument = db.collection('User').last()
    ```

- #### Find documents:
    ```python
    user: PantherDocument = db.collection('User').find(last_name='Rn')
    ```

- #### All documents:
    ```python
    users: list[PantherDocument] = db.collection('User').all()
    ```

- #### Count documents:
    ```python
    users_count: int = db.collection('User').count(first_name='Ali')
    ```

### Update:
- #### Update documents:
  ```python
  user: PantherDocument = db.collection('User').get(first_name='Ali', last_name='Rn')
  user.update(name='Saba')
  ```

- #### Find and Update one:
  ```python
  _filter = {'first_name': 'Ali', 'last_name': 'Rn'}
  is_updated: bool = db.collection('User').update_one(_filter, first_name='Saba')
  ```

- #### Filter and Update many:
  ```python
  _filter = {'first_name': 'Ali'}
  updated_count: int = db.collection('User').update_many(_filter, first_name='Saba')
  ```
  
### Delete:
- #### Delete documents:
  ```python
  user: PantherDocument = db.collection('User').first(first_name='Ali', last_name='Rn')
  user.delete()
  ```

- #### Filter and Delete documents:
  ```python
  is_deleted: bool = db.collection('User').delete_one(first_name='Ali', last_name='Rn')
  ```

- #### Filter and Delete many:
  ```python
  deleted_count: int = db.collection('User').delete_many(last_name='Rn')
  ```