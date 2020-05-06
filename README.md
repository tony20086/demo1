1. package main

import (
	"fmt"
)

func main() {
	a := []int{10, 40, 5, 280}
	b := []int{234, 5, 2, 148, 23}

	v := 8
	res := check(a, b, v)
	fmt.Println(res)

}

func check(a, b []int, target int) bool {
	cache := make(map[int]int, 64)
	for _, i := range a {
		cache[target-i] = 0
	}
	for _, j := range b {
		_, ok := cache[j]
		if ok {
			return true
		}
	}
	return false
}
2. package main

import (
	"github.com/satori/go.uuid"
	"fmt"
	"strings"
	"strconv"
)

func main() {

	fmt.Println("user"+strconv.FormatInt(genNum(8),10))
}
// l 生成数字长度
func genNum(l int) int64 {
	u1 := uuid.Must(uuid.NewV4())
	s1 := strings.Replace(u1.String(), "-", "", -1)
	var ret string
	for _, s := range s1 {
		if 65 <= s || s <= 122 {
			ret = ret + strconv.Itoa(int(s))
		} else {
			ret = ret + string(s)
		}
		if len(ret) == l {
			break
		}else if len(ret) > l {
			ret = ret[:l]
		}
	}
	result,_ := strconv.ParseInt(ret,10,64)

	return result
}

4. 
