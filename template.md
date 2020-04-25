GO

Authors
Robert Griesemer 
Rob Pike– Google employer, member of Unix team, co-creator of UTF-8, Involved in the creation of “Plan 9”
Ken Thompson- Design and implement Unix, one of the creator and developer of “Plan 9”, Known for UTF-8 encoding , he gained
Turing Award in 1983


Designers
Charles Bigelow – He is a type designer and he designed Go Language fonts with Kris Holmes.
Kris Holmes – She is a typeface designer, calligrapher and animator. She and Charles Bigelow is the co-creator of the Lucida and
Wingdings font family.


History of Language
Go was designed at Google in 2007 and first appeared in November 10, 2009. Go is widely used in production at Google and in many
other organizations for improve programming productivity. 
Go is statically-typed and compiled language having syntax similar to C. The designers of the Go thinks that, code should be
simple to understand for other developers who works with each other. So in Go there is no classes but packages. Go is not allow
inheritance for simplicity. In the end of this rules Go provides you high performance like C and efficiency like Java.


When/Why Shall We Use It?
Most of the modern programming languages(Java, Python etc.) are from the ’90s single threaded environment. Most of those
programming languages supports multi-threading. But the real problem comes with concurrent execution, threading-locking and
deadlocks. Those things make it hard to create a multi-threading application on those languages. Go has goroutines( lightweight
thread managed by the Go runtime) instead of threads. They consume almost 2KB memory from the heap. So, you can spin billions of
goroutines at any time.
And this goroutines makes go special and spesific.

Popular Applications Developed by Go
Openshift
Kubernetes
Dropbox(migrated some critical components from Python to Go)
Netflix(for server architecture)
InfluxDB

Companies That are Using Go
Facebook
Twitter
YouTube
Apple
Soundcloud
Mozilla Firefox
Medium
Github
UBER

How To Download Go Windows
First go to -> https://golang.org/dl/ page
And choose your OS and click -> download
And create folder on or drive, give a name you want
Under your created folder make 3 sub folder
  src(Where you will write your code)
  pkg(Where library or third party packages will go)
  bin(Where your will be execution file from you compiled code)
And then, go to Control Pane -> System and Security -> System -> Advanced System Settings
On Advanced tab click -> Environment Variable
Under User Variables for (your account name) add a new variable
  variable name: GOPATH
  variable value: (your chosen drive name C,D,E e.g):\(your created folder's given name) (This will be your development environment
  path)
Then click -> Path and edit it and add -> (your chosen drive name C,D,E e.g):\(your created folder's given name)\bin  
Then open cmd and type -> go version and then type (for start coding) -> go env

How To Download Go Ubuntu
Type terminal -> wget -q https://storage.googleapis.com/golang/getgo/installer_linux
              -> chmod +x installer_linux
              ->  ./installer_linux
              -> source /root/.bach_profile
 
How To Download Mac OS
First go to -> https://golang.org/dl/ page
And choose your OS and click -> download
And then run downloaded file
Create new file in your drive and inside that folder create new folder which name is src
Then go terminal and write -> export GOROOT=/usr/local/go
                           -> export GOPATH=/(your first created file path)(e.g export GOPATH=/Users/ece/ece/go/
                           ->export PATH=$PATH:$GOROOT/bin:$GOPATH/bin


Examples
package main
import "fmt"
func sum(s []int, c chan int) {
	sum := 0
	for _, v := range s {
		sum += v
}
	c <- sum // send sum to c
}
func main() {
	s := []int{7, 2, 8, -9, 4, 0}
	c := make(chan int)
	go sum(s[:len(s)/2], c)
	go sum(s[len(s)/2:], c)
	x, y := <-c, <-c // receive from c and assign value to v
	fmt.Println(x, y, x+y)
}


Fibonacci Example
package main

import (
	"fmt"
)

func fibonacci(n int, c chan int) {
	x, y := 0, 1
	for i := 0; i < n; i++ {
		c <- x
		x, y = y, x+y
	}
	close(c)
}

func main() {
	c := make(chan int, 10)
	go fibonacci(cap(c), c)
	for i := range c {
		fmt.Println(i)
	}
}


Gorountine Example
package main 
import(
“fmt”
“time”
)
func f(from string){
for a := 0; a <3; a++{
fmt.Println(from, a)
}}
func main(){
f(“direct”)
go f(“gorountine”)
go func(msg string){
ftm.Println(msg)
}(“going”)
Time.Sleep(time.Second)
Fmt.Println(“done”)
}
