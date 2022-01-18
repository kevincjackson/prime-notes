# Primes 

## Integrate Into Task List
- 1. Prime Niche / Community
- 2. Calculate Primorials, Save Primorials
  - def: product of first n primes 
  - fields: Id, Primes, Product, Bytes
- 3. Go Server Hello World
- 4. Elixir Language - quick
- 5. Elixir Server Hello World - quick
- 6. Go Server Small Primes
- 7. Go Server Primescan
- 8. Elixir Server Small Primes
- 9. Elixir Server Primescan
- 10. Go Concurrency
- 11. Elixir Concurrency
- 12. Concurrency Blog

## Smallprimes Tasks
1. DONE Generate list of small primes.
2. DONE Define Data
  - Expanded
    - prime int
    - position int
  - Compressed
    - billion int
3. DONE Define API: smallprimes.io
  - api/between/?a=100&b=200        -> [int]
  - api/is/101                      -> bool
  - api/upto/101                    -> [int]
4. DONE How to Make Your Own Binary Format
  - x Ruby, TODO Go, TODO Elixir
5. DONE Data Storage
  - x For read based file compression, store 4 x 1B range of 1,3,7,9's. -> 50MB files.
6. Try Databases for best speed size. MAXNUMBER: 1B
    - Generating 1B fresh
      - x NO Ruby: minutes
      - x Go: 1B: 10.2s, 100M: 0.7s, 10M: 0.04s
      - Elixir: ?
    - X Binary File: Use 4 bin files `primes_0B.bin` (pdat taken)
      - Ruby: C1379: File.read: 0.01s, File.read & Unpack: 0.37 seconds
      - Go: C1379: ioutil.ReadFile: 25ms
      - Go: Unpack C1379 400M bools / 50M bytes: 685ms
      - Go: Read C13790 50M bytes: 485ms
      - TODO Speed Tests: 
    - SQLite: `smallprimes.db`
      - No bueno! 
      - TODO
      - number & pos
        - Non-Indexed DB Size: 4000MB with 4B numbers, Multirow query: 6s
        - Non-Indexed DB Size:  900MB with 1B numbers, Multirow query: 2s
        -     Indexed DB Size: 2300MB with 1B numbers, Multirow query: 0.3s
        - Non-Indexed DB Size:    1MB with 1M numbers, Multirow query: 0.3s
      - number only
        - 1B primes only, no INDEX:     632M    
        - 1B primes only, with INDEX:   1.3G    Query All: Real: 4m 39s, User: 31s, Sys: 22s
    - Redis `?`
      - Speed Tests: Milliseconds
      - Size: ???
7. API: DONE
  - CONSTANT: MAXNUMBER: 10**9 // YES - Storage
  - Web: smallprimes.dev  `between/?a=1&b=100`, `is/n`, `upto/n`
  - CLI: sprimes          `between a b`, `is n`, `upto n`, `-json`
  - Go:  smallprimes      `Is(n)`, `Between(a,b)`, `Upto(n)`


## API Notes
- When in doubt leave it out
- Reduce the need for boiler plate code
- Spend time on good names
- Names should not be cryptic
- Easy to learn and use
- Hard to misuse
- Don't transliterate from another language


## File Transfer Speeds
- From Harddrive: small (4k) files take the longest
  - 7200 RPM drive: 80-160 MB/s
  - SSD: 25-300 MB/s
  - USB 2.0: 25-30 MB/s
  - USB 3.0: 25-300 MB/s
- From Internet:  
  - Unit: Mbps (Mega bits / second)
  - Mbps:  8 Mb = 1 MB, divide Mbps by 8 to get MBps 
  - By state: Slowest 59 Mbps, Avg 127 mbps. => 7 - 15 MB / s
- Reference: A file with 1B c1379 primes is 50MB.
- Analysis: 
  - Inital Download 200MB download -> ~ 15-30/s
  - Read file(s) from disk 200MB -> 1-6 
    - From my SSD drive: 1.4s
  - Regenerate: ? TODO: Create benchmarks.


## SQLite, Put into Separate Note
- Basics: File based, serverless, configuration free.
- Usage: your app is the database engine! Do not separate by a network.
- Myth: Toy Database, Truth: Local Storage DB, used in phones to airplanes.
- Most controversial feature: Duck typing (Manifest typing), No Strong Typing. Flexible Typing comes from TCL.
- File based. 'yourfile.db'. You can use as your own filetype.
- Competes with `fopen` not enterprise dabases. Benefit: faster than `fopen` for blobs < 100k.
- Use case: 1 db total, 1 concurrent writer, 1 file data. Example testing, local caches, embedded data such as phones, cars, TV's.
- Use `VACUUM;` after deleting lots of data. Sqllite does not automatically defragment data.
- Inserting a blob / binary file: 
  - `sqlite> CREATE TABLE images(name TEXT, type TEXT, img BLOB);`
  - `sqlite> INSERT INTO images(name,type,img) VALUES('icon','jpeg',readfile('icon.jpg'));`


## Data Storage Options
- Dropbox: 100GB file size, 2GB Free, limits on heavy transfer
- Github: 100MB file limit, 5GB repo soft limit, not intended for data storage!
- AWS: DynamoDB (Key Value): 25GB free
- Media Fire: 10GB Free, no limits on transfer
- SQLite blob storage: no limit, but faster than filesystem under 100KB


## Data formats
- String file of "01"s.: 1M -> 1MB file 
- String file of "01"s using 1379 compression: 1M -> 0.4MB file 
- String file of "01"s.: 1B -> 1G file, 400MB compressed
- Binary file: 1M bits -> 0.125M or 125KB
- Binary file: 1M bits, 1379 compression -> 0.05M or 50KB
- Binary file: 1B bits -> 125MB, 50MB compressed
- App usage: in Go init 1B < 1s, 1T > 1s
  

## Explanation of the Projects
  - What did I learn
    - x Learn bit array storage and manipulation
    - x Learn Marshalling vs Serialization
    - x Learned hexdump
    - x Decompressing a Billion bytes took 2.5 minutes in Ruby! Slow
  - Project: Finding Prime Numbers
    - Challenges: 
      - x Learn basic Go.
      - x Learn Go modules.
      - x Learn Go Big Numbers.
      - x Learn Go Persistance.
      - x Learn Go Writing a Command Line App 
      - x Learn Prime Search methods.
      - Confusing parts of Go
        - Strings, bytes/uint8, runes
      - Make a chart of bits to digits
      - Learning Bit Programming and Bit Sets
    - Mistakes: ?
      - Predicted 1 month project: Start April 1st.
    - Enjoyed:
      - Designing API.
    - Leadership: Personal Project
    - Conflicts: ?
    - Do Differently: ?
      - Making realizable stepping stones.


## THIS WEEK
- 1wk: Learn remaining prime methods:   
    - Sundar
    - Atkins
- Live with Smallprimes API. Release when it's stable.


## AFTER THIS WEEK
- 3-9d: Hunt for big primes on one machine
- 1wk: Websockets - watch it all go! 
- 1-3m: Try to break bitcoin
- 1-3wk: Make a Web Front End
- 2-6wk: Report findings
- 2wk: Paper with Dan on computing
- Cloud App <-> Web Service <-> Cloud Db
- Distributed App - Many Apps, Many Databases


## COMPLETED TASKS
- x Concretize API.
- x Concretize storage.
  - x Lookup avg architecture, target GB inmemory?
  - x Postgres, Mongo DB Free tier.
- x Concretize how many numbers: 4B, keeps searches ~0.4s
  x Don't do competition #'s
- x Local App <-> Local Db
- x Efficiency: Compare storing by bits, ints, varchar's.
- x Performance: Try fully SQL Sieve of Atkins, + Sieve only w/ 1,3,7,9's
- x Storage: Try storing as bits, ints, varchars

## Haskell
- <https://hackage.haskell.org/package/primes-0.2.1.0/docs/Data-Numbers-Primes.html>


## UI Queries
- `IS PRIME`
- `GET PRIMES FROM TO`
- `GET NTH PRIME`
- `GET NTH PRIMES FROM TO`
- `GET RANDOM PRIME`
- `GET RANDOM PRIME MIN MAX`


## Web
- Url's don't by standard have any limit, due to search engine and browser limits (IE) are 2000.
- Api needs to use POST


## Arbitrary Precision Programming Language Support
- <https://en.wikipedia.org/wiki/List_of_arbitrary-precision_arithmetic_software>
- C#: System.Numerics.BigInteger
- Go: math/big (Int type)
- Haskell: Built-in Integer, 
- Haskell Package: Data.Number.Primes
- Javascript: gwt-math library
- Python: Built-in int
- Ruby: Bignum


## Software Support
- Unix: `bc` (by default)
- Openssl: `openssl prime`, OpenSSL is a robust, commercial-grade, and full-featured toolkit for the Transport Layer Security (TLS) and Secure Sockets Layer (SSL) protocols. It is also a general-purpose cryptography library. 


## Names of Large Numbers
- <https://en.wikipedia.org/wiki/Names_of_large_numbers>
- Go's uint64 = 8 bytes = 64 bits = 18,446,744,073,709,551,615 ~= 18 quintillion (18 zeroes)
- Centillion: 303 zeroes


## Number of Primes
| nth prime | number | % of primes |
| - | - | - |
|       100 |          541 | 18 |
|     1_000 |        7_919 | 12 |
|    10_000 |      104_729 | 9.5 |
|   100_000 |    1_299_709 | 7.7 |
| 1_000_000 |   15_485_863 | 6.5 |


## Prime Websites
- <https://www.mersenne.org/>
- <https://www.bigprimes.net/archive/prime/10000>
- <https://primes.utm.edu/>


## Bounties
- <https://www.mersenne.org/>
- <https://www.eff.org/awards/coop>
  - $150,000 to the first individual or group who discovers a prime number with at least 100M decimal digits
    - sqrt(100Mdigits) = 50M digits
  - $250,000 to the first individual or group who discovers a prime number with at least 1B decimal digits
    - sqrt(1Bdigits) = 500M digits


## Largest Known Prime
- 2^82,589,933 − 1, 24M digits


## Prime Search Methods, Scan 10^6 Test
- Trial division
    1. Naive: 264s
    2. 1 to Square Root n optimization, 2.81s
    3. Above only using primes, calculating prime each n, 7.8
- Wheel Factorization / Sieve: ?
    - A pre-culling method to feed into Eratosthenes
    - Pick n amount of the primes series, so you can loop them. Example) 2 * 3 * 5 * 7 = 210
    - Cross off all the multiples of 2, 3,5, and 7.
    - The remaining numbers are the ones you have to check. Saves minimum 50% of the work, and for 210 saves 76%.
    - Coprime: numbers that only have 1 has a common factor
- Sieve of Eratosthanes: Make a range 2..n, foreach n delete multiples.
    - Bit array: 
        - 10^6: 48ms
	    - 10^7: 1.16s
        - 10^8: 9s
        - 10^9: 1m39s
- Sieve of Sundar
- Sieve of Atkins
- Optimizations
  - Preculling 2,3,5 multiples


## Prime Storage
- Int64, etc. Wasteful
- bit, masks, seek 


## Standard Representation of Exponents
1. `2^8 = 256` Works in bc, wolfram alpha, haskell


## Prime Factors
2: yes, 2
3: yes, 3
4: no, 2^2
5: yes, 5
6: no, 2, 3
7: yes, 7
8: no 2^3
9: no 3^2
10: no 2, 5


## Prime Algo
- n
- square root n
- floor square root n
- get list of primes below above
- check the primes
    - if match, add a to factors, get factors of b
    - if not keep going


## Simple Database
- `primes: prime, position, digits`
- `config: largest_sequential_prime_checked`
- `composites: composite, first_factor, opposite_factor` 


## Distributed App Database
- Keep track of `highest_checked`
- Keep track of `in_progress`?


## API
graphql
```
primes.io/
    number/ <- int
            -> json
            -> csv?
        is_prime: bool
        prime_factors: string
        hex: string
        bits: int
        digits: int
    filters/  <- max result int 
              <- min result int 
              <- position min #
              <- position max #
              -> json hash 
              -> csv file?
```


## Postgres Limitations
- `smallint`: 2 bytes, -32,768 to 32,767
- `integer`: 4 bytes, -2,147,483,648 to +2,147,483,647, ~2B
- `bigint`: 8 bytes, -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807, ~9 x 10^18
- `numeric` / `decimal`: variable user-specified precision, exact up to `131,072` digits before the decimal point; up to `16,383` digits after the decimal point
- `varchar`: Max size: 10,485,760
- Laurel's idea: Use multiple columns for large numbers!


## Go Limitations
- `int`, maybe `int32` or `int64`
- `int32`: ~2 x 10**9
- `int64`: ~9 x 10**18
- `uint32`: ~4 x 10**9
- `uint64`: ~18 x 10**18
- `big.Int`: no limit


## Small Prime Database (SPD)
- numbers
  - id
  - first_factor
  - is_prime 
- size: 1GB database for 2**32 (up to ~2B)
- primes bitarray up to 2**32 (~2B) => 268MB (no compression)


## Database Search
- SQLite is a single user, file based, serverless RDMS
- Redis, Remote Dictionary Store, an in memory (blazing fast) key value (hash) store.
- Test a conventional DB like Postgres for primes and composites, until it runs out of room
- Test a mongodb for primes and composities, until it you hit the limit.
- For 300 digits numbers+ store only prime as the index
- Cassandra - Available, Partition Tolerant Key-Value Store. Key Index is limited to -2^63 to 2^63
- CouchDB - Available, Partition Tolerant Document DB.


## Ideas
- Past 7 Only possible primes are numbers ending 1, 3, 7, 9
- For huge numbers, use the add up all the digits trick to eliminate 3, and 9. Compare it to the remainder method.
- Try converting numbers to different bases to see patterns. It worked for 0, 2, 4, 5, 7, 8, and 10 in decimals.
- Look at other sieves.


## Database 
- Start with Postgres
- Switch to Mongodb if needed.


## Algo - Improved Sieving
- You can gain any desired amount of improvement in sieving by selecting a high enough level of primes to get the desired efficiency. Example the first n numbers have p primes; 10 - 4 -  40%, 100 - 25 - 25%, 1000 - 168 - 17%, 10,000 - 1229 - 13%,  100000 - 9592 - 10%. Subtracting the last percentage from 100 yields the numbers you don't need to check. For example, with the 100000, you don't have to do 90% of the work! This is effectively getting rid of the low hanging fruit.  Getting the lowest common denominator for the threshold, allows you to start your sieve wherever you need - essential for searching huge numbers. When you do the trial division, you can also skip all the primes under the threshold - more savings!  This does use a computer, and not a formula, but for a computer tracking 10,000 numbers for an add matrix is trivial.
- I was very excited about this idea, and learned this has a name! Wheel sieving, discovered in ???
- Implementation
  - Data
    - ```fs
      type Wheel = { 
        Id : int
        Complete : bool
        Primes : int list
        Size : int
        WheelNumbers : WheelNumber list
      }
      type WheelNumber = { 
        IsBlocking : bool
        IsPrime: bool option 
      }
      ```
  - Function
    - Wheel.next :: wheel -> wheel
    - Wheel.addRow :: wheel -> wheel
    - Wheel.eratosthenes :: wheel -> wheel 
    - Wheel.primes :: wheel -> int list
    - Big.sqrt :: bigint -> bigint
  - Actions


## Algo - Searching for Mercidian Primes
- Searching for Mercidian primes, you can ignore every 2^n where n is a multiple of 4. They're always divisible by 5.


## Good Docs on Go <-> Strings
- <https://medium.com/orbs-network/big-integers-in-go-14534d0e490d>
- New big.Int, Default of 0: `var big1 *big.Int = new(big.Int)` or `big.NewInt(0)`
- String -> big.Int: `var big1, _ = new(big.Int).SetString("111", 10)`
- big.Int -> String: `var str1 string = big1.Text(10)` or `big1.String()`
- Add two big.Ints
```go
	var sum := new(big.Int)
	var big1, _ := new(big.Int).SetString("111", 10)
	var big2, _ := new(big.Int).SetString("222", 10)
	sum.Add(big1, big2)
```


## Go DB Functions
- `Open` / `Close`: manage the connection
- `Query`: for selects, returns rows, which you must iterate over w Next
- `Exec`: for insert, update, delete
- `Context`:there's Context versions which allow you to cancel commands
  

## Architecture
```
UI:         primeWeb - Main
UI:         primeCon - Main
Service:    primeApi - Main
Logic:      prime
                LargestChecked,
                IsPrime(n), diff methods
                Get(?)
                GetBig(?)
                GetNth(p)
                GetNext(p)
                GetRandom(?)
                Scan(?)
Data:       primeDB
```


## Troubleshooting Performance
Too many DB Connections ?
```go
// smallprimes Scan to 1M 45ms 
// smallprimes Print to 1M 90ms 
// smallprimes Scan to 1B: 24s, 
// smallprimes Print to 1B: 1min 1s
prime.ScanUptoNoDb(int(math.Pow10(6))) // -> 1.4s
prime.ScanUpto(int(math.Pow10(6))) // -> 6ms
prime.ScanNext(int(math.Pow10(6))) // -> 1h43m # SLOW DATA ACCESS ISSUE
prime.ScanUptoWithDb(4000000) // Check 
prime.ScanUptoNoDb(4000000) // 8 seconds
prime.ScanUptoNoDb(int(math.Pow10(6))) // 1.64s
prime.ScanUptoNoDb(int(math.Pow10(7))) // 24s
prime.ScanUptoNoDb(int(math.Pow10(8))) // 8m35s FAN ON
```


## Troubleshooting Databases 
- SQL Server, Insert 1M int Rows of value(1): 10m 5s! Disk Usage 13.6M Reserved, 13.5M Data
- Postgres, Insert 1M int Rows of value(1): 6s5ms! Disk Usage, Total Bytes: 36.2M, Table TextClear-Content: 35M


## Bits to Digits
- Write a function for this
| Bits / 2**e | Digits | Compute Time |
| - | - | - |
| 32 | 10 |
| 64 | 20 |
| 128 | 39 |
| 256 | 78 |
| 512 | 155 |
| 1,024 | 309 |
| 2,048 | 617 |
| 4,096 | 1,234 |
| 8,192 | 2,467 |
| 16,384 | 4,933 |
| 32,768 | 9,865 |
| 65,536 | 19,729 |
| 131,072 | 39,457 |
| 262,144 | 78,914 |
| 524,288 | 157,827 |
| 1,048,576 | 315,653 |
| 2,097,152 | 631,306 |
| 4,194,304 | 1,262,612 |
| 8,388,608 | 2,525,223 | 5m |
| 16,777,216 | 5,050,446 | 22m |
| ~32M | ~10M | 
| ~64M | ~20M | 
| ~128M | ~40M | 
| ~256M | ~80M | 
| ~512M | ~160M | 
| ~1B | ~320M | 
| ~2B | ~640M | 
| ~4B | ~1.2B | 


## Storage
| Bits | Name | Compression |
| - | - | - |
| 2^10 | KiB / kibibyte / KB / 	kilobyte |
| 2^20 | MiB / mebibyte / MB / megabyte |
| 2^30 | GiB / gibibyte / GB / gigabyte |
| 2^32 | 537 MB ? | 40% Wheel Savings -> 214MB |
| 2^40 | TiB / tebibyte |
| 2^50 | PiB / pebibyte |
| 2^60 | EiB / exbibyte |
| 2^64 | 1000 EiB? | 10 Pb? |
| 2^70 | ZiB / zebibyte |
| 2^80 | YiB / yobibyte |


## Wheel Factor Savings
Need to write a program for this.
| Primorial | Primes | Primorial / Bits | Bytes | Work Saved % |
| - | - | - | - | - |
| 1 | 2,3 | 6 | ~1B | 3 / 6 = 50% |
| 2 | 2-5 | 30 | ~3B | 22 / 30 = 73% |
| 3 | 2-7 | 210 | ~26B | 52 / 210 = 76% |
| 4 | 2-11 | 2,310 | ~288B | ? |
| 5 | 2-13 | 30,030 | ~4KB | ? |
| 6 | 2-17 | 510,510 | ~63KB | ? |
| 7 | 2-19 | 9,699,690 | ~1.2MB | ? |
| 8 | 2-23 | 223,092,870 | ~28MB | ? |
| 9 | 2-29 | 6,469,693,230 | ~808MB | ? |
| 10 | 2-31 | 200,560,490,130 | ~25GB | ? |


## KJ Simple Storage Saver
! Apply This Idea to a Wheel. How???
| Only Do Numbers Ending In | Storage Saved
| - | - | 
| 1,3,7,9 | 60% |


## Prime Finding Algorithm
- Use Eratosthenes to find the primes in a primorial 2x3=6, 2x3x5=30, etc
  - Optimization, only search from 2 to sqrt of max.
- Use Wheel Factor to limit what you have to check for the next primoral.
- Check Using Eratosthenes.
- Repeat
- ! Need to make tables for this in action.


## Serialization vs Marshal
- Basic understanding:
  - Serialization: freeze drying data. JSON, XML, binary, YAML, etc for transport.  For example, Han Solo, was captured by ???, and needing to be frozen for transport to Jabba.  So serialization is freeze drying, and deserialization is rehydrating.
  - Marshalling: freeze drying data *and context* for use in a different environment. For example, the data may be moving between different language versions, different runtimes. Marshalling often involves serialization, but serialization may or may not indicate it's being marshalled.  
- Intent: of Serialization is typically for transport, but is ultimately generally unknown. The data may be for storage, transport, or marshalling.
- Marshalling - I think of a troop who is in the middle of fighting on one battle field, only to be airlifted to another battlefield to continue fighting. Examples as going for client to server, oner thread to another thread, or from managed code to native code. John Skeet gives the example of ... get stackoverflow answer.
- A marshaller will do whatever it needs to do...it's about moving the data. <https://softwareengineering.stackexchange.com/questions/149493/whats-the-difference-between-a-marshaller-and-a-serializer>
- An accurate definition depends on the language.
  - C++: <https://docs.microsoft.com/en-us/cpp/dotnet/overview-of-marshaling-in-cpp?view=msvc-170>
  - Java: <https://tech.deepumohan.com/2011/11/marshalling-in-java.html>
  - Haskell: <https://wiki.haskell.org/Foreign_Function_Interface#Marshalling_data>
  - C#: Transform a type from managed to native code. <https://docs.microsoft.com/en-us/dotnet/standard/native-interop/type-marshaling>


  ## Serialization
  - Big Endian: "abcdefgh" is transported as "abcdefgh"
  - Little Endian: "abcdefgh" is transported as "cdabghef"


## OO in Golang (Need to create main document)

```go
// No complicated inheritance. Use composition / interface.
// No need to declare it on the concrete type.
type Greetable interface {
  Greet() string
}

// No classes. Use type <Name> struct.
type Person struct {
	id        int    // private
	FirstName string // public
	LastName  string
}

// Funny syntax for methods.
func (person Person) Greet(name string) string {
	return "Welcome, " + name + "! My name is " + person.FirstName + "."
}

// Public and private is called export, and unexported.
// Capital = public, Lowercase = private
func (person Person) SayHello() {
	fmt.Printf("Hi my name is %s %s.\n", person.FirstName, person.LastName)
}

//
func main() {
	p := Person{1, "John", "Jones"}
	p.SayHello()
	fmt.Println(p.Greet("Neighbor"))
}
```

## Write Bytes
- Use `hexdump` to look at a file. Hexdump shows you 16 hexes at a time. The last line it shows is empty. `hexdump -C` is often used with characters.
- `hexdump -v -e '1/1 "%02x"'` Shows pure hex with no formatting.
- In Ruby
  - Use Array.pack.
  - If baffled - checkout Perl's pack tutorial, which Ruby's is based on <https://perldoc.perl.org/perlpacktut>
  - `["1111111100000000"].pack("B*")` : Interpret everything as bits.Hexdump will yield "F0"
  - Export `File.write("tmp.bin", ["1111111100000000"].pack("B*"))`
  - Import `File.read("tmp.bin").unpack("B*").first`

## Ruby Oneliner
Is
```ruby
  def 
    is_prime(x) x < 2 ? false : 2.upto(Math.sqrt(x).to_i).all? { |y| x % y != 0 }
  end
```
With Output
```ruby
File.write("primes_to_1h.txt", (2..100).to_a.select { |n| is_prime(n) }.join("\n"))
```

## Primorial

```go
// Product of first n primes
// Inputs above 15 overflow int64, return -1
func primorial(n int) int {

	if n < 1 || n > 15 {
		return -1
	}

	product := 1
	primes := []int{2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47}
	for i := 0; i < n; i++ {
		product *= primes[i]
	}
	return product
}

// Product of first n primes
// Inputs above 1000 return -1
func bigPrimorial(n int) *big.Int {

	if n < 1 || n > 1000 {
		return big.NewInt(-1)
	}

	product := big.NewInt(1)
	primes := []int{2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97, 101, 103, 107, 109, 113, 127, 131, 137, 139, 149, 151, 157, 163, 167, 173, 179, 181, 191, 193, 197, 199, 211, 223, 227, 229, 233, 239, 241, 251, 257, 263, 269, 271, 277, 281, 283, 293, 307, 311, 313, 317, 331, 337, 347, 349, 353, 359, 367, 373, 379, 383, 389, 397, 401, 409, 419, 421, 431, 433, 439, 443, 449, 457, 461, 463, 467, 479, 487, 491, 499, 503, 509, 521, 523, 541, 547, 557, 563, 569, 571, 577, 587, 593, 599, 601, 607, 613, 617, 619, 631, 641, 643, 647, 653, 659, 661, 673, 677, 683, 691, 701, 709, 719, 727, 733, 739, 743, 751, 757, 761, 769, 773, 787, 797, 809, 811, 821, 823, 827, 829, 839, 853, 857, 859, 863, 877, 881, 883, 887, 907, 911, 919, 929, 937, 941, 947, 953, 967, 971, 977, 983, 991, 997, 1009, 1013, 1019, 1021, 1031, 1033, 1039, 1049, 1051, 1061, 1063, 1069, 1087, 1091, 1093, 1097, 1103, 1109, 1117, 1123, 1129, 1151, 1153, 1163, 1171, 1181, 1187, 1193, 1201, 1213, 1217, 1223, 1229, 1231, 1237, 1249, 1259, 1277, 1279, 1283, 1289, 1291, 1297, 1301, 1303, 1307, 1319, 1321, 1327, 1361, 1367, 1373, 1381, 1399, 1409, 1423, 1427, 1429, 1433, 1439, 1447, 1451, 1453, 1459, 1471, 1481, 1483, 1487, 1489, 1493, 1499, 1511, 1523, 1531, 1543, 1549, 1553, 1559, 1567, 1571, 1579, 1583, 1597, 1601, 1607, 1609, 1613, 1619, 1621, 1627, 1637, 1657, 1663, 1667, 1669, 1693, 1697, 1699, 1709, 1721, 1723, 1733, 1741, 1747, 1753, 1759, 1777, 1783, 1787, 1789, 1801, 1811, 1823, 1831, 1847, 1861, 1867, 1871, 1873, 1877, 1879, 1889, 1901, 1907, 1913, 1931, 1933, 1949, 1951, 1973, 1979, 1987, 1993, 1997, 1999, 2003, 2011, 2017, 2027, 2029, 2039, 2053, 2063, 2069, 2081, 2083, 2087, 2089, 2099, 2111, 2113, 2129, 2131, 2137, 2141, 2143, 2153, 2161, 2179, 2203, 2207, 2213, 2221, 2237, 2239, 2243, 2251, 2267, 2269, 2273, 2281, 2287, 2293, 2297, 2309, 2311, 2333, 2339, 2341, 2347, 2351, 2357, 2371, 2377, 2381, 2383, 2389, 2393, 2399, 2411, 2417, 2423, 2437, 2441, 2447, 2459, 2467, 2473, 2477, 2503, 2521, 2531, 2539, 2543, 2549, 2551, 2557, 2579, 2591, 2593, 2609, 2617, 2621, 2633, 2647, 2657, 2659, 2663, 2671, 2677, 2683, 2687, 2689, 2693, 2699, 2707, 2711, 2713, 2719, 2729, 2731, 2741, 2749, 2753, 2767, 2777, 2789, 2791, 2797, 2801, 2803, 2819, 2833, 2837, 2843, 2851, 2857, 2861, 2879, 2887, 2897, 2903, 2909, 2917, 2927, 2939, 2953, 2957, 2963, 2969, 2971, 2999, 3001, 3011, 3019, 3023, 3037, 3041, 3049, 3061, 3067, 3079, 3083, 3089, 3109, 3119, 3121, 3137, 3163, 3167, 3169, 3181, 3187, 3191, 3203, 3209, 3217, 3221, 3229, 3251, 3253, 3257, 3259, 3271, 3299, 3301, 3307, 3313, 3319, 3323, 3329, 3331, 3343, 3347, 3359, 3361, 3371, 3373, 3389, 3391, 3407, 3413, 3433, 3449, 3457, 3461, 3463, 3467, 3469, 3491, 3499, 3511, 3517, 3527, 3529, 3533, 3539, 3541, 3547, 3557, 3559, 3571, 3581, 3583, 3593, 3607, 3613, 3617, 3623, 3631, 3637, 3643, 3659, 3671, 3673, 3677, 3691, 3697, 3701, 3709, 3719, 3727, 3733, 3739, 3761, 3767, 3769, 3779, 3793, 3797, 3803, 3821, 3823, 3833, 3847, 3851, 3853, 3863, 3877, 3881, 3889, 3907, 3911, 3917, 3919, 3923, 3929, 3931, 3943, 3947, 3967, 3989, 4001, 4003, 4007, 4013, 4019, 4021, 4027, 4049, 4051, 4057, 4073, 4079, 4091, 4093, 4099, 4111, 4127, 4129, 4133, 4139, 4153, 4157, 4159, 4177, 4201, 4211, 4217, 4219, 4229, 4231, 4241, 4243, 4253, 4259, 4261, 4271, 4273, 4283, 4289, 4297, 4327, 4337, 4339, 4349, 4357, 4363, 4373, 4391, 4397, 4409, 4421, 4423, 4441, 4447, 4451, 4457, 4463, 4481, 4483, 4493, 4507, 4513, 4517, 4519, 4523, 4547, 4549, 4561, 4567, 4583, 4591, 4597, 4603, 4621, 4637, 4639, 4643, 4649, 4651, 4657, 4663, 4673, 4679, 4691, 4703, 4721, 4723, 4729, 4733, 4751, 4759, 4783, 4787, 4789, 4793, 4799, 4801, 4813, 4817, 4831, 4861, 4871, 4877, 4889, 4903, 4909, 4919, 4931, 4933, 4937, 4943, 4951, 4957, 4967, 4969, 4973, 4987, 4993, 4999, 5003, 5009, 5011, 5021, 5023, 5039, 5051, 5059, 5077, 5081, 5087, 5099, 5101, 5107, 5113, 5119, 5147, 5153, 5167, 5171, 5179, 5189, 5197, 5209, 5227, 5231, 5233, 5237, 5261, 5273, 5279, 5281, 5297, 5303, 5309, 5323, 5333, 5347, 5351, 5381, 5387, 5393, 5399, 5407, 5413, 5417, 5419, 5431, 5437, 5441, 5443, 5449, 5471, 5477, 5479, 5483, 5501, 5503, 5507, 5519, 5521, 5527, 5531, 5557, 5563, 5569, 5573, 5581, 5591, 5623, 5639, 5641, 5647, 5651, 5653, 5657, 5659, 5669, 5683, 5689, 5693, 5701, 5711, 5717, 5737, 5741, 5743, 5749, 5779, 5783, 5791, 5801, 5807, 5813, 5821, 5827, 5839, 5843, 5849, 5851, 5857, 5861, 5867, 5869, 5879, 5881, 5897, 5903, 5923, 5927, 5939, 5953, 5981, 5987, 6007, 6011, 6029, 6037, 6043, 6047, 6053, 6067, 6073, 6079, 6089, 6091, 6101, 6113, 6121, 6131, 6133, 6143, 6151, 6163, 6173, 6197, 6199, 6203, 6211, 6217, 6221, 6229, 6247, 6257, 6263, 6269, 6271, 6277, 6287, 6299, 6301, 6311, 6317, 6323, 6329, 6337, 6343, 6353, 6359, 6361, 6367, 6373, 6379, 6389, 6397, 6421, 6427, 6449, 6451, 6469, 6473, 6481, 6491, 6521, 6529, 6547, 6551, 6553, 6563, 6569, 6571, 6577, 6581, 6599, 6607, 6619, 6637, 6653, 6659, 6661, 6673, 6679, 6689, 6691, 6701, 6703, 6709, 6719, 6733, 6737, 6761, 6763, 6779, 6781, 6791, 6793, 6803, 6823, 6827, 6829, 6833, 6841, 6857, 6863, 6869, 6871, 6883, 6899, 6907, 6911, 6917, 6947, 6949, 6959, 6961, 6967, 6971, 6977, 6983, 6991, 6997, 7001, 7013, 7019, 7027, 7039, 7043, 7057, 7069, 7079, 7103, 7109, 7121, 7127, 7129, 7151, 7159, 7177, 7187, 7193, 7207, 7211, 7213, 7219, 7229, 7237, 7243, 7247, 7253, 7283, 7297, 7307, 7309, 7321, 7331, 7333, 7349, 7351, 7369, 7393, 7411, 7417, 7433, 7451, 7457, 7459, 7477, 7481, 7487, 7489, 7499, 7507, 7517, 7523, 7529, 7537, 7541, 7547, 7549, 7559, 7561, 7573, 7577, 7583, 7589, 7591, 7603, 7607, 7621, 7639, 7643, 7649, 7669, 7673, 7681, 7687, 7691, 7699, 7703, 7717, 7723, 7727, 7741, 7753, 7757, 7759, 7789, 7793, 7817, 7823, 7829, 7841, 7853, 7867, 7873, 7877, 7879, 7883, 7901, 7907, 7919}

	for i := 0; i < n; i++ {
		product.Mul(product, big.NewInt(int64(primes[i])))
	}
	return product
}
```