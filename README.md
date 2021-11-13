# Primes 

## Smallprimes Tasks
1. DONE Generate list of small primes.
2. DONE Define Data
  - Expanded
    - prime int
    - position int
  - Compressed
    - billion int
3. DONE Define API: smallprimes.io
  - api/list/?q                   -> [int]
  - api/is/n                      -> bool
  - api/pos/i                     -> int | nil
  - api/rand/?q                   -> int | nil
  - api/info/n                    -> {} | nil
4. DONE How to Make Your Own Binary Format
  - x Ruby, TODO Go, TODO Elixir
5. Data Storage
  - x For read based file compression, store 4 x 1B range of 1,3,7,9's. -> 50MB files.
  - Create files.
6. Set Database for purpose?
  - Try
    - Binary File: Use `primes_0B.bin` (pdat taken)
    - SQLite: `smallprimes.db`
    - Redis `?`
7. API
  - Web:          `is n`, `info n`, `list`, `pos i`, `rand` 
  - CLI: sprimes  `is n`, `info n`, `list`, `pos i`, `rand`
  - Query:        `from`, `to`, `from-pos`, `to-pos`
  - Info:         -> `{ prime, position }` 


## SQLite, Put into Separate Note
- Basics: File based, serverless, configuration free.
- Usage: your app is the database engine! Do not separate by a network.
- Myth: Toy Database, Truth: Local Storage DB, used in phones to airplanes.
- Most controversial feature: Duck typing (Manifest typing), No Strong Typing. Flexible Typing comes from TCL.
- File based. 'yourfile.db'. You can use as your own filetype.
- Competes with `fopen` not enterprise dabases. Benefit: faster than `fopen` for blobs < 100k.
- Use case: 1 db total, 1 concurrent writer, 1 file data. Example testing, local caches, embedded data such as phones, cars, TV's.


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
  - Project: Finding Prime Numbers
    - Challenges: 
      - x Learn basic Go.
      - Learn Go modules.
      - Learn Go Big Numbers.
      - Learn Go Persistance.
      - Learn Go Writing a Command Line App 
      - Learn Prime Search methods.
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
- Concretize API.
- Concretize storage.
  - Lookup avg architecture, target GB inmemory?
  - Postgres, Mongo DB Free tier.
- Concretize how many numbers.
  - Don't do competition #'s
- Release app.


## AFTER THIS WEEK
- 3-9d Fill up primes db to 600 digits (2*2048), with prime and sequence.
- 3-9d: Make a table of composites up to 600 digits of prime factorization.
- 3-9d: Hunt for big primes on one machine
- 1wk: Websockets - watch it all go! 
- 1-3m: Try to break bitcoin
- 1-3wk: Make a Web Front End
- 2-6wk: Report findings
- 2wk: Paper with Dan on computing
- Local App <-> Local Db
- Cloud App <-> Web Service <-> Cloud Db
- Distributed App - Many Apps, Many Databases
- Efficiency: Compare storing by bits, ints, varchar's.
- Performance: Try SQL doing everything. No other "brain" language.
- Performance: Try fully SQL Sieve of Atkins, + Sieve only w/ 1,3,7,9's
- Storage: Try storing as bits, ints, varchars


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
```
prime.ScanUptoNoDb(int(math.Pow10(6))) // -> 1.4s
prime.ScanUpto(int(math.Pow10(6))) -> 6ms
prime.ScanNext(int(math.Pow10(6))) -> 1h43m # SLOW DATA ACCESS ISSUE
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
| Primes | Primorial / Bits | Bytes | Work Saved % |
| - | - | - | - |
| 2,3 | 6 | ~1B | 3 / 6 = 50% |
| 2-5 | 30 | ~3B | 22 / 30 = 73% |
| 2-7 | 210 | ~26B | 52 / 210 = 76% |
| 2-11 | 2,310 | ~288B | ? |
| 2-13 | 30,030 | ~4KB | ? |
| 2-17 | 510,510 | ~63KB | ? |
| 2-19 | 9,699,690 | ~1.2MB | ? |
| 2-23 | 223,092,870 | ~28MB | ? |
| 2-29 | 6,469,693,230 | ~808MB | ? |
| 2-31 | 200,560,490,130 | ~25GB | ? |
| 2-37 | ? | ? | ? |
| 2-41 | ? | ? | ? |
| 2-43 | ? | ? | ? |
| 2-47 | ? | ? | ? |
| 2-53 | ? | ? | ? |
| 2-59 | ? | ? | ? |
| 2-61 | ? | ? | ? |
| 2-67 | ? | ? | ? |
| 2-71 | ? | ? | ? |
| 2-73 | ? | ? | ? |
| 2-79 | ? | ? | ? |
| 2-83 | ? | ? | ? |
| 2-89 | ? | ? | ? |
| 2-97 | ? | ? | ? |


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