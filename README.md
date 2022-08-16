# Coding-Rubbish
<p align="center"> <img src="meme.jpg"> </p>

## Java CheatSheet

### ***String, char, Integer conversion***
[String to int]:     Integer.parseInt(s);        // return int primitive  <br />
[String to Integer]: Integer.valueOf(s); 	     // return an Integer Object <br />
[int to String]:     String.valueOf(int) <br />
[char[] to String]:  String str = new String(chArray); <br />
[list to array]:     String[] arr = list.toArray(new String[list.size()]); <br />
[array to list]:     List<String> list = Arrays.asList(arr); <br /> 可以直接罗列array的元素，比如：Arrays.asList("first", "second"); <br />
                                                              非常适合于 convert single element to list <br />
 注意 Arrays.asList 返回的list形式的数组，可以修改某个element，但不能 add 或 remove elements <br />

### ***String***
String s = “a*b*c”; <br />
s.charAt(i);<br />
s.length();<br />
s.substring(0, 1);            // [0, 1)<br />
s.substring(1);               //[1, s.length)<br />
s.equals(“b”);<br />
s.compareTo(“b*c*d”);         // return -1 because s comes first in lexicographical order<br />
s.trim(); 	                  // remove tailing and padding spaces<br />
s.indexOf(“a”);               // return first index of substring “a”   indexOf(substring)<br />
s.indexOf(‘a’, 2);            // indexOf(int ch, fromIndex), indexOf(String str, fromIndex)<br />
s.lastIndexOf(‘a’);           // also we can use s.lastIndexOf(String str)<br />
s.replaceAll(substr, target); // replace all substr to target in s<br />

char[] arr = s.toCharArray();<br />
String[] arr = s.split("\\*") // when delimiter is '*'<br />
String[] arr = s.split("\\.") // when delimiter is '.'<br />
String res = String.join(String delimiter, List<String> data); // use the delimiter to concatenate the string in data.<br /><br />
Objects.equals(Object a, Object b); // (1)if both parameters are null return true<br />
                                    // (2)if exactly one parameter is null return false<br />
                                    // (3)return the result of invoking the equals() method of the first parameter passing it the second parameter<br />
                                    // This behaviour means it is "null safe".<br />
                                    
### ***StringBuilder***
StringBuilder sb = new StringBuilder();<br />
sb.append(“a”);<br />
sb.insert(0, “a”);            // sb.insert(int offset, char c) or sb.insert(offset, str)<br />
sb.deleteCharAt(int index);<br />
sb.reverse();<br />
sb.toString();<br />
sb.length();                  // return the number of characters in sb, similar to str.length()<br />

### ***Array***
int[] arr = new int[10];<br />
Arrays.sort(arr);<br />
Arrays.fill(arr, -1);           // initialize all array elements with value -1<br />
public void helper(int[] nums);<br />
helper(new int[]{1, 2});        // initialize array in method<br />

### ***HashMap (TreeMap), HashSet (TreeSet)***
HashMap<Character, Integer> map = new HashMap<Character, Integer>();<br />
map.put('c', 1);<br />
map.get('c');<br />
map.getOrDefault(key, defaultValue);                         // if key exists return value, else return default value<br />
map.remove(‘c’);                                             // remove key and its value<br />
map.computeIfAbsent(key, mappingFunction);                   // if key exists return value, else create a value by mappingFunction<br />
map.computeIfAbsent(key, k -> new HashSet<>()).add(val);<br />
map.computeIfAbsent(key, k -> new ArrayList<>()).add(val);   // RECOMMENDED !!!<br />
if (map.containsKey('c')) {                                  // check if key exists<br />
}<br />
if (map.containsValue(1)) {                                  // check if value exists<br />
}<br />
for (Character d : map.keySet()) {                           // traverse key set<br />
}<br />
for (Integer i : map.values()) {                             // traverse value set<br />
}<br />
for(Map.Entry<Character, Integer> entry : map.entrySet()){   // traverse key-value pair<br />
    entry.getKey();<br />
    entry.getValue();<br />
}<br />
map.forEach((k,v) -> System.out.println("key: "+k+" value:"+v)); // traverse key-value pair using lamda expression to print out info<br />
<br />
map.isEmpty();<br />
map.size();<br />
HashSet<Integer> set = new HashSet<Integer>();<br />
set.add(10);<br />
set.remove(10);<br />
if(set.contains(10)){<br />
}<br />
set.size();<br />
set.isEmpty();<br />
setA.retainAll(setB); // setA keeps the intersection of original setA and setB;<br />
setB.removeAll(setC); // Removes from this set all of its elements that are contained in the specified collection (setB - setC)<br />
setC.addAll(setD);    // union two sets of setC and setD<br />
setC.containsAll(setD); // Returns true if this set contains all of the elements of specified collection<br />
Object[] arr = setA.toArray(); // Returns an array containing all of the elements in this set.<br />

TreeMap<Integer, String> map = new TreeMap<>();             // key’s ascending order (default)<br />
map.put(2, “b”);<br />
map.put(1, “a”);<br />
map.put(3, “c”);<br />
for(String str : map.values())                              // traverse in “a” “b” “c” order<br />
for(Integer num : map.keySet())			                    // traverse in  1, 2, 3 order<br />

TreeMap<String, Integer> treeMap = new TreeMap<>();             // sorted in lexicographical order<br />
TreeMap<Integer, Integer> treeMap = new TreeMap<>(Collections.reverseOrder()); // descending order<br />

treeMap.lowerKey(k);                                        // return the greatest key strictly less than the given key, <br />
treeMap.floorKey(k);                                        // return the greatest key less than or equal to key<br />
treeMap.higherKey(k);                                       // return the greatest key strictly larger than the given key, <br />
treeMap.ceilingKey(k);                                      // return the greatest key larger than or equal to key<br />
treeMap.firstKey();                                         // returns the first (lowest) key currently in this map.<br />
SortedMap<K,V> portionOfTreeMap = treeMap.headMap(K toKey); // Returns a view of the portion of this map whose keys are strictly less than toKey.<br />
NavigableMap<K,V> map = treeMap.headMap(toKey, true);       // Returns a view of the portion of this map whose keys are less than or equal to toKey.<br />

Set<Integer> treeSet = new TreeSet<>();                     // sort in ascending order by default<br />
treeSet.lower(Integer e);	                                // return greatest element that is < e, or null if no such element<br />
treeSet.floor(Integer e);	                                // return greatest element that is <= e, or null if no such element<br />
treeSet.ceiling(Integer e);                                 // return smallest element that is >= e, or null if no such element<br />
treeSet.higher(Integer e);                                  // return smallest element that is > e, or null if no such element<br />
treeSet.first();                                            // return the first element in the treeset (if min set, return minimum element)<br />
treeSet.last();                                             // return the last element in the treeset<br />

### ***LinkedHashMap, LinkedHashSet***
Map<Integer,String> map = new LinkedHashMap<>();<br />
map.put(1, "first");<br />
map.put(2, "second");<br />
map.put(3, "third");           <br />
for(Map.Entry<Integer,String> entry : map.entrySet())<br />
    System.out.println(entry.getKey<br />(), entry.getValue());   // print order: 1, 2, 3<br />
Set<Integer> set = new LinkedHashSet<>();<br />

### ***List, ArrayList, LinkedList***
List<Integer> list = new ArrayList<>();<br />
list.add(14);<br />
list.add(0, 10);                			            // list.add(int index, int value);<br />
list.get(int index);
list.remove(list.size() - 1);<br />
list.set(int index, int val);                     // replaces element at index and returns original<br />
list.indexOf(Object o);                           // return first index of occurrence of specified element in the list; -1 if not found<br />
list.subList(int fromIndex, int toIndex);         // return a sublist within range [fromIndex, toIndex)<br />
Collections.sort(list);				                    // ascending order by default<br />
Collections.sort(list, Collections.reverseOrder());         // descending order<br />
Collections.sort(list, new Comparator<Integer>() {<br />
   @Override<br />
   public int compare(Integer o1, Integer o2) {             // the Integer can be any Object instead<br />
   return o1 ‐ o2;// 0‐>1<br />
   // return o2‐o1; 1‐>0<br />
   }<br />
});<br />
list.forEach(num -> system.out.println(num));   // traverse the list and print out by using lamda function<br />
list.stream().mapToInt(i -> i).toArray(); -> arraylist to array<br />
  
  
### ***Stack, Queue, PriorityQueue, Deque***
Stack<Integer> stack = new Stack<Integer>();<br />
stack.push(10);<br />
stack.pop();<br />
stack.peek();<br />
stack.isEmpty();<br />
stack.size();<br />
Queue<Integer> q = new LinkedList<Integer>();<br />
q.offer(10);    					                                          // q.add() is also acceptable<br />
q.poll();<br />
q.peek();<br />
q.isEmpty();<br />
q.size();<br />
PriorityQueue<Integer> pq = new PriorityQueue<>();                            // minimum Heap by default<br />
PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());  // change to maximum Heap<br />
pq.add(10);<br />
pq.poll();<br />
pq.peek();<br />
pq.isEmpty();<br />
pq.size();<br />
class Node implements Comparable<Node>{<br />
    int x;<br />
    int y;<br />
    public Node(int x, int y){<br />
        this.x = x;<br />
        this.y = y;<br />
    }<br />
    @Override<br />
    public int compareTo(Node that){<br />
        return this.x - that.x;                            // ascending order / minimum Heap<br />
        // return that.x - this.x;			               // descending order / maximum Heap<br />
    }<br />
}<br />
PriorityQueue<Node> pq = new PriorityQueue<>();<br />

import java.util.Deque; <br />
Deque<Integer> dq = new LinkedList<Integer>();    // Deque is usually used to implement monotone queue<br />
dq.addFirst();  //  dq.offerFirst();<br />
dq.addLast();   //  dq.offerLast();<br />
dq.peekFirst(); // <br />
dq.peekLast();<br />
dq.pollFirst(); //  dq.removeFirst();<br />
dq.pollLast();  //  dq.removeLast();<br />
<br />
### ***Enum***
set1 = EnumSet.of(Gfg.QUIZ, Gfg.CONTRIBUTE,  Gfg.LEARN, Gfg.CODE); <br />
set2 = EnumSet.complementOf(set1);              // initially containing all the elements of this type that are not contained in the specified set<br />
set3 = EnumSet.allOf(Gfg.class);                <br />
set4 = EnumSet.range(Gfg.CODE, Gfg.CONTRIBUTE); // contains all of the elements in the range defined by the two specified endpoints.<br />

### ***Random method***
Random rand =new Random();    // initialize Random object<br />
int i = rand.nextInt(100);    // generate random number in [0, 100)<br />
float f = rand.nextFloat();   // generate float value in [0, 1)<br />
double d = rand.nextDouble(); // generate double value in [0.0, 1.0)<br />

### ***Math***
Math.pow(double x, double y); // return x^y <br />
Math.round(float a);          // returns the closest int to the argument<br />
Math.abs(int/float/doubld val);<br />
Math.sqrt();<br />
<br />Math.sin(double rad);         // input is rad not angle<br />
Math.PI;<br />
Math.E;<br />
<br />
### ***Collections/Object***
Collections.nCopies(100, new Object[]{true});// return an immutable list which contains n copies of given object<br />
getClass()                                   // Returns the runtime class of this {@code Object}<br />
Collections.singletonList()                  // use it to replace Arrays.asList() when there is only one element<br />
Collections.unmodifiableSet(new HashSet<>()) // returns an unmodifiable view of the specified set. Note that, changes in specified set will be reflected in unmodifieable set.<br /> 
                                             // Also, any modification on unmodifiableSet is not allowed, which triggers exception.<br />
Collections.swap(List, int i, int j);        // swap the ith and jth element in list <br />
### ***Lamda expression***
1. Functional interface: the interface contains exactly one abstract method<br />
   @FunctionalInterface <br />
   public interface Sprint {<br />
      public void sprint(Animal animal); <br />
   }<br />
2. lamda expression<br />
   a -> a.canHop()   等价于 (Animal a) -> { return a.canHop(); }<br />
   <br />
### ***std input/output  file read/write***
import java.io.*;<br />
import java.net.*;<br />
Scanner in = new Scanner(System.in);<br />
int n = in.nextInt();<br />
while(in.hasNext()){<br />
    String str = in.nextLine();<br />
}<br />
<br />
String inputfile="in.txt";<br />
String outputfile="out.txt";<br />
try<br />
{<br />
    BufferedReader in = new BufferedReader(new FileReader(inputfile));<br />
    line = in.readLine();<br />
    while (line!=null)<br />
    {<br />
        // do something with line<br />
        line=in.readLine();<br />
    }<br />
    in.close();              // close the file<br />
} catch (IOException e)<br />
{<br />
    e.printStackTrace();<br />
}<br />
<br />
try{<br />
    BufferedWriter out = new BufferedWriter(new FileWriter(outputfile));<br />
    for(String str : map.keySet()){<br />
         out.write(str + " " + map.get(str));<br />
         out.newLine();<br />
    }<br />
    out.close();           // close the file<br />
}catch (IOException e)<br />
{<br />
    e.printStackTrace();<br />
}<br />
<br />
URL wordlist = new URL("http://foo.com/wordlist.txt");<br />
BufferedReader in = new BufferedReader(new InputStreamReader(wordlist.OpenStream()));<br />
String inputLine = null;<br />
List<String> res = new ArrayList<>();<br />
while((inputLine = in.readLine()) != null){<br />
    res.add(inputLine);<br />
}<br />
<br />
### ***Atomic Class***
<br />
//an atomic operation is supposed to be completed wholly or not at all. Based on CAS theory<br />
AtomicInteger count = new AtomicInteger(0);<br />
count.getAndSet();<br />
count.incrementAndGet();<br />
count.getAndIncrement();<br />
count.decrementAndGet();<br />
count.getAndDecrement();<br />
<br />
AtomicBoolean enabled = new AtomicBoolean(initialValue: false);<br />
boolean result = enabled.compareAndSet(expect:true, update:false);  // if result = false, means actual value doesn't equal to expect one<br />
<br />
AtomicReference<AmbryClientException> exceptionInCallback = new AtomicReference<>(null); // an atomic object allowing method to perform atomic operations<br />
exceptionInCallback.get();<br />
exceptionInCallback.set();<br />
exceptionInCallback.compareAndSet(expected, update); // Atomically sets the value to the given updated value if the current value == the expected value.<br />
<br />
AtomicStampedReference<Person> s  = new AtomicStampedReference<Person>(new Person(20), stampVal);<br />
s.compareAndSet(s.getReference(), new Person(s.getReference().age+10), stampVal, ++stampVal); // s.compareAndSet(expected_reference, update_reference, expected_stamp, update_stamp);<br />
<br />
### ***ExecutorService(create and manage threads)***
  <br />
(1)Future: Think of a Future as an object that holds the result – it may not hold it right now, <br />
           but it will do so in the future (once the Callable returns). Thus, a Future is basically one way <br />
           the main thread can keep track of the progress and result from other threads.<br />
(2)Callable: is similar to Runnable, in that it encapsulates a task that is meant to run on another thread.<br />
(3)In the thread pool, instead of using execute(Runnable r), you use submit(Callable r), which returns a Future<V> object (declared in the ExecutorService interface). <br />
   When the result is required, you can use get() method on the Future object. If the result is ready, it is returned, <br />
   otherwise, the calling thread is blocked until the result is available.<br />
<br /><br />
ExecutorService service = new Executor.newSingleThreadExecutor();           // single thread executor<br />
ExecutorService service = new Executor.newSingleThreadScheduledExecutor();  // single thread can run after delay or periodically<br />
ExecutorService service = new Executor.newCachedThreadPool();               // if previous thread is available, reuse it. Otherwise, create new thread as needed<br />
ExecutorService service = new Executor.newFixedThreadPool(int nThreads);    // create a pool with fixed number of threads<br />
ExecutorService service = new Executor.newScheduledThreadPool(int nThreads);// a pool with fixed number of threads and threads execute after delay or periodically<br />
<br />
service.execute(Runnable Object);                 // or lamda expression;  Executes a Runnable task at some point in the future<br />
Future<?> future = service.submit(Runnable task); // Executes a Runnable task at some point in the future and returns a Future representing the task<br />
service.shutdown();                               // finish running tasks and then terminate<br />
service.shutdownNow();                            // stop all running tasks immediately<br />
<br />
Future<?> result = service.schedule(Callable<V> callable, long delay, TimeUnit unit);<br />
Future<?> result = service.schedule(Runnable command, long delay, TimeUnit unit);<br />
Future<?> result = service.scheduleAtFixedDelay(Runnable command, long initialDelay, long delay, TimeUnit unit); // periodic execution. A fixed delay after completion of last execution<br />
Future<?> result = service.submit(Callable<V> callableWorker);<br />
future.isDone();<br />
future.isCancelled();<br />
future.cancel();                                // Attempts to cancel execution of the task.<br />
future.get();                                   // Retrieves the result of a task, waiting endlessly if it is not yet available.<br />
future.get(long timeout, TimeUnit unit);        // Retrieves the result of a task, waiting the specified amount of time. <br />
<br />
### ***Synchronize Block/Method***
<br />
synchronized(object){}               // synchronized block (used at code snippet closest to the operation)<br />
private synchronized void update(){} // synchronized method<br />
List<Integer> list = Collections.synchronizedList( new ArrayList<>(Arrays.asList(4,3,52))); // used to wrap non-concurrent class<br />
<br />
### ***Concurrent Collection***
<br />
Map<String,Integer> map = new ConcurrentHashMap<>();<br />
Queue<Integer> queue = new ConcurrentLinkedQueue<>();<br />
Deque<Integer> deque = new ConcurrentLinkedDeque<>();<br />
<br />
BlockingQueue<Integer> blockingQueue = new LinkedBlockingQueue<>();<br />
blockingQueue.offer(E e, long timeout, TimeUnit unit);             //Adds item to the queue waiting the specified time, returning false if time elapses before space is available<br />
blockingQueue.poll(long timeout, TimeUnit unit);                   //Retrieves and removes an item from the queue, waiting the specified time, returning null if the time elapses before the item is available<br />
<br />
BlockingDeque<Integer> blockingDeque = new LinkedBlockingDeque<>();<br />
blockingDeque.offerFirst(E e, long timeout, TimeUnit unit);<br />
blockingDeque.offerLast(E e, long timeout, TimeUnit unit);<br />
blockingDeque.pollFirst(long timeout, TimeUnit unit);<br />
blockingDeque.pollLast(long timeout, TimeUnit unit);<br />
<br />
<br />
<br />
/* ----- Introduction on CopyOnWriteArrayList -------<br />
* When we’re calling the iterator() method on the CopyOnWriteArrayList, <br />
* we get back an Iterator backed up by the immutable snapshot of the content of the CopyOnWriteArrayList.<br />
* Its content is an exact copy of data that is inside an ArrayList from the time when the Iterator was created. <br />
* Even if in the meantime some other thread adds or removes an element from the list, <br />
* that modification is making a fresh copy of the data that will be used in any further data lookup from that list.<br />
* Because of the copying mechanism, the remove() operation on the returned Iterator is not permitted.<br />
*/
List<Integer> list = new CopyOnWriteArrayList<>(Arrays.asList(4,3,52));// use case: when we are iterating over it more often than we are modifying it. <br />
                                                                       // If adding elements is a common operation in our scenario, then CopyOnWriteArrayList won’t be a good choice <br />
                                                                       // – because the additional copies will definitely lead to sub-par performance.<br />
Set<Integer> set = new CopyOnWriteArraySet<>(); // copy all of their elements to a new underlying structure anytime an element is added, modified, or removed from the collection<br />
<br />
# The most notable pros of the ConcurrentSkipListMap are the methods that <br />
# can make an immutable snapshot of its data in a lock-free way. <br />

Map<String, Integer> map = new ConcurrentSkipListMap<>(); // concurrent version for sorted map like treemap, ascending order by default<br />
Set<String> set = new ConcurrentSkipListSet<>();          // concurrent version for sorted set like treeset, ascending order by default<br />
concurrentNavigableMap<K,V>.descendingMap();              // Returns a reverse order view of the mappings contained in this map<br />
<br />
### ***Generics - Get and Put rule***
Use an extends wildcard when you only get values out of a structure.<br />
Use a super wildcard when you only put values into a structure.<br />
And don't use a wildcard when you both want to get and put from/to a structure.<br />

Collection<? extends Fruit> // what we know is that the collection is one type of Fruit. We can get but cannot add into it in case that added fruit violates the current type<br />
Collection<? super Banana> // what we know is fruits in collection belong to parent class of banana. We can add fruit as long as we know the added fruit is parent class of banana. But we can't get one from it because we don't know what is excatly the type is.<br />

### ***CountDownLatch***
CountDownLatch是一个同步工具类，它允许一个或多个线程一直等待，直到其他线程的操作执行完后再执行.<br />
Background: 并发工具类还有CyclicBarrier、Semaphore、ConcurrentHashMap和BlockingQueue，它们都存在于java.util.concurrent包下。<br />
CountDownLatch是通过一个计数器来实现的，计数器的初始值为线程的数量。每当一个线程完成了自己的任务后，计数器的值就会减1。当计数器值到达0时，它表示所有的线程已经完成了任务，然后在闭锁上等待的线程就可以恢复执行任务。<br />
CountDownLatch use cases:<br />
    1.实现最大的并行性：有时我们想同时启动多个线程，实现最大程度的并行性。例如，我们想测试一个单例类。如果我们创建一个初始计数为1的CountDownLatch，并让所有线程都在这个锁上等待，那么我们可以很轻松地完成测试。<br />
                     我们只需调用 一次countDown()方法就可以让所有的等待线程同时恢复执行。<br />
    2.开始执行前等待n个线程完成各自任务：例如应用程序启动类要确保在处理用户请求前，所有N个外部系统已经启动和运行了。<br /><br />
    3.死锁检测：一个非常方便的使用场景是，你可以使用n个线程访问共享资源，在每次测试阶段的线程数目是不同的，并尝试产生死锁。<br />
<br />
### ***review in OOP***
在Java中, static修饰的成员（method、field）表明它属于这个类本身，而不是这个类的某个实例；<br />
在Java中, 不要使用对象去调用static修饰的成员变量、方法，而是要用类去调用static修饰的成员。<br />
static块,用于初始化静态变量, 例如：<br />
   static int num;<br />
   static String mystr;<br />
   static{
      num = 97;<br />
      mystr = "Static keyword in Java";
   }<br />
   //Static Block is used for initializing the static variables.<br />
   //This block gets executed when the class is loaded in the memory. <br />
   //A class can have multiple Static blocks, which will execute in the same sequence in which they have been written into the program.<br />
<br />
<br />
final修饰Collection 比如 List, Map 意味着不能修改这个reference指向别的，但是我们仍允许修改这个Collection (add/delet element, etc)<br />
final修饰class, 意味着这个class不能被继承（extends）<br />
<br />
### ***Java NIO***
<br />
Background: Java NIO使我们可以进行非阻塞IO操作。比如说，单线程中从Channel读取数据到buffer，同时可以继续做别的事情<br />，
            当数据读取到buffer中后，线程再继续处理数据。写数据也是一样的。<br />
NIO包含下面几个核心的组件：<br />
        Channels: 所有I/O都是从Channel开始的. 这些channel基于于UDP和TCP的网络I/O，以及文件I/O. 例如: FileChannel, ServerSocketChannel, DatagramChannel 等。<br />
        Buffers: Buffer涵盖了可以通过IO操作的基础类型。比如 ByteBuffer, IntBuffer etc. <br />
        Selectors: 选择器允许单线程操作多个通道。如果你的程序中有大量的链接，同时每个链接的I/O带宽不高的话，这个特性将会非常有帮助。比如聊天服务器。<br />
                  要使用Selector的话，我们必须把Channel注册到Selector上，然后就可以调用Selector的select()方法。<br />
                  这个方法会进入阻塞，直到有一个channel的状态符合条件。当方法返回后，线程可以处理这些事件<br />。
Channel的特点：<br />
    Channel可以读也可以写，stream一般来说是单向的（只能读或者写);<br />
    Channel可以异步读写;<br />
    Channel总是基于缓冲区Buffer来读写.<br />
Channel的实现:<br />
    FileChannel         用于文件的数据读写<br />
    DatagramChannel     用于UDP的数据读写<br />
    SocketChannel       用于TCP的数据读写<br />
    ServerSocketChannel 允许我们监听TCP链接请求，每个请求会创建会一个SocketChannel<br />
    <br />
Buffer: 本质上就是一块内存区，可以用来写入数据，并在稍后读取出来。这块内存被NIO Buffer包裹起来，对外提供一系列的读写方便开发的接口。<br />
Buffer读写步骤：<br />
    (1)把数据装入buffer;   例如  int bytesRead = inChannel.read(buf);     //read into buffer.<br />
    (2)调用flip();        把Buffer从写模式切换到读模式;<br />
    (3)从Buffer中导出数据; 例如  int bytesWritten = inChannel.write(buf); //read from buffer into channel.<br />
    (4)调用buffer.clear()或者buffer.compact();    clear方法会重置position为0, compact则只清空已读取的数据，保留未读数据;<br />
Buffer有三个属性:<br />
    <1>capacity容量: 作为一块内存，buffer有一个固定的大小。一旦buffer写满了就需要清空已读数据以便下次继续写入新的数据。<br />
    <2>position位置: 读/写buffer时的位置。<br />
    <3>limit限制: 一旦切换到读模式，limit则代表我们所能读取的最大数据量，他的值等于写模式下position的位置。<br />
    <4>mark标记: A remembered position. Calling mark() sets mark = position. Calling reset( ) sets position = mark. The mark is undefined until set.<br />
    这4个的关系：<br />
               0 <= mark <= position <= limit <= capacity<br />
Buffer的常用API:<br />
    buffer.flip()      // 先set limit = current position, 再 reset position = 0;<br />
    buffer.clear()     // set the limit = capacity, reset position = 0;<br />
    buffer.rewind()    // 用于重新读一遍数据  reset position = 0, 保持limit不变<br />
    buffer.remaining() // The number of elements remaining in this buffer, 其实就是  limit - current position<br />
    <br />
Scatter:<br />
    Scattering read指的是从通道读取的操作能把数据写入多个buffer，也就是sctters代表了数据从一个channel到多个buffer的过程。<br />
Gather:<br />
    gathering write则正好相反，表示的是从多个buffer把数据写入到一个channel中。<br />
Scatter/gather在有些场景下会非常有用，比如需要处理多份分开传输的数据。举例来说，假设一个消息包含了header和body，我们可能会把header和body保存在不同独立buffer中，这种分开处理header与body的做法会使开发更简明。<br />
<br />
在Java NIO中如果一个channel是FileChannel类型的，那么它可以直接把数据传输到另一个channel。这个特性得益于FileChannel包含的transferTo和transferFrom两个方法<br />
FileChannel.transferFrom(fromChannel, position, count)方法: 目标通道pull数据<br />
FileChannel.transferTo(position, count, toChannel)方法:   源通道push数据<br />
<br />
Selector: 用于检查一个或多个NIO Channel的状态是否处于可读、可写。如此可以实现单线程管理多个channels,也就是可以管理多个网络链接.<br />
   好处是: 我可以用更少的线程来处理channel。实际上，你甚至可以用一个线程来处理所有的channels。从操作系统的角度来看，切换线程开销是比较昂贵的，并且每个线程都需要占用系统资源，因此暂用线程越少越好。<br />
注册Channel到Selector上:<br />
    channel.configureBlocking(false);      //Channel必须是非阻塞的。所以FileChannel不适用Selector，因为FileChannel不能切换为非阻塞模式<br />
    SelectionKey key = channel.register(selector, SelectionKey.OP_READ); //第二个参数是一个“关注集合”, 代表我们关注的channel状态<br />
Channel状态:<br />
     (1)Connect:  SelectionKey.OP_CONNECT<br />
     (2)Accept:   SelectionKey.OP_ACCEPT<br />
     (3)Read:     SelectionKey.OP_READ<br />
     (4)Write:    SelectionKey.OP_WRITE<br />
<br />
SelectionKey对象包含以下属性:<br />
    The interest set;<br />
    The ready set;<br />
    The Channel;<br />
    The Selector;<br />
    An attached object (optional);<br />
    <br />
  (1)interest set: is the set of events you are interested in "selecting".<br />
  (2)ready set:  is the set of operations the channel is ready for. 一般来说在调用了select方法后都会需要用到ready set<br />
  (3)channel:<br />
  (4)selector: Accessing the channel + selector from the SelectionKey is trivial. Like this: Selector selector = selectionKey.selector();<br />
  (5)attached object: You can attach an object to a SelectionKey this is a handy way of recognizing a given channel, <br />
                      or attaching further information to the channel.<br />
                      <br />
Selector 选择 channel的几个函数<br />
  select():              blocks until at least one channel is ready for the events you registered for.<br />
  select(long timeout):  does the same as select() except it blocks for a maximum of timeout milliseconds (the parameter).<br />
  selectNow():           doesn't block at all. It returns immediately with whatever channels are ready.<br />
注意：上述函数返回值是int, The int returned by the select() methods tells how many channels are ready.<br />
<br />
访问Ready的Channel<br />
You can access the ready channels via the "selected key set", by calling the selectors selectedKeys() method.<br />
Set<SelectionKey> selectedKeys = selector.selectedKeys(); <br />
<br />
Close()函数<br />
When you are finished with the Selector you call its close() method. <br />
This closes the Selector and invalidates all SelectionKey instances registered with this Selector. <br />
The channels themselves are not closed.<br />
<br />
Java NIO SocketChannel: a channel that is connected to a TCP network socket.<br />
You can set a SocketChannel into non-blocking mode. When you do so, you can call connect(), read() and write() in asynchronous mode.<br />
connect()<br />
write()<br />
read()<br />
<br />

### ***Java I/O***
<br />
1. int read(byte[], int offset, int length)<br />
   The read(byte[], int offset, int length) method reads bytes into a byte array, but starts at offset bytes into the array, <br />
and reads a maximum of length bytes into the array from that position. Again, the read(byte[], int offset, int length) method <br />
returns an int telling how many bytes were actually read into array, remember to check this value before processing the read bytes.
