# VNHCoreData
Demo project which shows how to deal in simple steps with core data operations such insert, fetch, delete.

## DB Operations
### Insert
```
    func insert() {
        
        let person = PersonData()
        person.name = "Vasant"
        person.email = "ios.app.developer@gmail.com"
        person.age = 26
        person.phone = "+919876543210"
        person.id = Int(Date().timeIntervalSince1970)
        
        let success = DBHelper.store.makeEntry(person)
        show("Stored: \(success)")
    }
```
### Fetch
```
    func fetch() {
        if let personList = DBHelper.fetch.personRecords() {
            show("Records found: \(personList.count)")
        }
        
        //-------------- or --------------
        if let personList = DBHelper.fetch.records("Person") {
            show("Records found: \(personList.count)")
        }
    }
    
    func fetchWithCondition() {
        if let personList = DBHelper.fetch.records("Person", key: "phone", value: "+919901882290") {
            show("Records found: \(personList.count)")
        }
    }
```
### Delete
```
    func delete() {
        if DBHelper.delete.entity("Person") {
            show("Person table has been deleted successfully!")
        }
    }
```
