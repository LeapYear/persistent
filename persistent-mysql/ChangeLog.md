## 2.6.2.1

* Fix haddock documentation [#725](https://github.com/yesodweb/persistent/pull/725)

## 2.6.2

* Extend the `SomeField` type to allow `insertManyOnDuplicateKeyUpdate` to conditionally copy values.
* Depend on `mysql-simple >= 0.4.3` to fix encoding and decoding of date/time values with fractional seconds (when a column is specified using something like `sqltype=TIME(6)`).  See also [#705](https://github.com/yesodweb/persistent/issues/705)
* Fix behavior of `insertManyOnDuplicateKeyUpdate` to ignore duplicate key exceptions when no updates specified.

## 2.6.1

* Add functions `insertOnDuplicateKeyUpdate`, `insertManyOnDuplicateKeyUpdate` to `Database.Persist.MySQL` module.

## 2.6.0.2

Prevent spurious no-op migrations when `default=NULL` is specified - revised version [#672](https://github.com/yesodweb/persistent/pull/672) (which fixes bug [#671](https://github.com/yesodweb/persistent/issues/671) introduced by the earlier attempt [#641](https://github.com/yesodweb/persistent/pull/641))

## 2.6

Compatibility for backend-specific upsert functionality.
A lucky contributor could add upsert to the MySQL backend now, i.e.:
INSERT ... ON DUPICATE ...

## 2.5

* changes for read/write typeclass split

## 2.3.0.1

Support usign default= for changing the id field type

## 2.3

* Distinguish between binary and non-binary strings in MySQL [#451](https://github.com/yesodweb/persistent/pull/451)
	* Previously all string columns (VARCHAR, TEXT, etc.) were being returned from Persistent as `PersistByteString`s (i.e. as binary data). Persistent now checks character set information to determine if the value should be returned as `PersistText` or `PersistByteString`.
	* This is a **breaking change** if your code is relying on a `PersistByteString` being returned for string-like MySQL values; persistent-mysql itself had several runtime errors that needed to be fixed because of this patch. High-level code dealing purely with `PersistEntities` should be unaffected.

## 2.2

* Update to persistent 2.2

## 2.1.3

* Added a `Show` instance for `MySQLConf`.

## 2.1.2.1

Documentation typo fix

## 2.1.2

Provide a `FromJSON` instance for `MySQLConf`.
