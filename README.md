# PlistReadWrite

## Plist Read And Write ##
```
override func viewDidLoad() {
        super.viewDidLoad()
        
        let bundlePath = Bundle.main.path(forResource: "CustomPlist", ofType: "plist")
        do{
            let documentdirectory = try FileManager.default.url(for: .documentDirectory, in: .userDomainMask, appropriateFor: nil, create: false)
            let url = documentdirectory.appendingPathComponent("CustomPlist.plist")
            print(url)
            if !FileManager.default.fileExists(atPath: url.path)
            {
                do{
                    try FileManager.default.copyItem(at: URL.init(fileURLWithPath: bundlePath!), to: url)
                    let data : NSMutableDictionary = NSMutableDictionary.init(contentsOfFile: url.path)!
                    data.setObject("Vishal",forKey: "Username" as NSCopying)
                    data.setObject("k",forKey: "Password" as NSCopying)
                    data.write(toFile: url.path, atomically: true)
                }catch{
                    print("File not copy")
                }
            }
            else{
                print("file already exist")
                let data : NSMutableDictionary = NSMutableDictionary.init(contentsOfFile: url.path)!
                data.setObject("kalola",forKey: "Username" as NSCopying)
                data.setObject("patel",forKey: "Password" as NSCopying)
                data.write(toFile: url.path, atomically: true)
            }
        }catch{
            print("Error to get document directory")
        }
    }
    
    func readPlist() throws -> Void {
        let documentdirectory = try FileManager.default.url(for: .documentDirectory, in: .userDomainMask, appropriateFor: nil, create: false)
        let url = documentdirectory.appendingPathComponent("CustomPlist.plist")
        print(url)
        if !FileManager.default.fileExists(atPath: url.path)
        {
            // FromURL Get the Plist and FetchData From Plist.
        }
    }
```


