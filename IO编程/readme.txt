IO框架
    ：如何处理数据的输入输出问题
数据交换（文件、网络、数据库）
java.io.File代表磁盘上的文件/目录
文件对象和文件的关系与线程对象和线程的关系相同（从JVM->磁盘）
IO流：用于传输的流对象，用来在JVM和外部交换数据源之间传输数据（例如：管道）
流对象的三中分类
    按数据传输方向：输入流/输出流
    按传输数据单位：字符流和字节流
    按流的功能：节点流和过滤流
        节点流：实际传输数据的流
        过滤流：给节点流增强功能（不具有传输数据的作用，如：电线外层的塑料包皮）
字节中节点流的用法：节点流是基础，用来读写文件的流。
InputStream/OutputStream所有字节流输出/输出流的父类
    子类类名以父类类名作为引用
FileInputStream/FileOutputStream 文件字节输入/输出流
三个写方法：
    write(int a):把字节a写进文件中
    wirte(bye[] bs):把字节数组bs全部写出去
    *write(byte[] bs,int off,int lenght):把字节数组中的一段写进去，具体由后两个参数决定。
三个读方法：
    int read():从文件中度一个字节，返回-1结束
    int read(byte[] bs):从文件中读多个数组，直至读满。返回值为实际读到的字节数，以-1结束
    int read(byte[] bs,int off,int length):从文件中读多个字节，放入数组中，返回值为实际读到字节数，以-1为结束
IO编程的模式：
    1.创建节点流
    2.封装过滤流
    3.读/写数据
    4.关闭流
DataInputStream/DataOutputStream 可以直接读写8种基本类型和字符串  readUTF()/writeUTF()
BufferedInputStream/BufferedOutputStream作用：缓冲，提高IO的效率,主要用于输出上。
    PrintStream:能写8种基本类型，同时具有缓冲
    PiedInputStream:管道流，用于线程间传输数据
    RanddomAccessFile:随机访问文件
通过字符流可以处理字符的编解码问题
字符的编解码：
    当字符的解码方式和编码方式不统一时，会造成乱码
字符流：读写文本文件，只能处理文本
    Reader/Writer 字符流的父类
    FileReader/FileWriter  文件字符流 节点流
    BufferedReader/BufferedWriter=PrintWriter 缓冲流  过滤流
    InputStreamReader/OutputStreamWriter  桥转换  在桥转换的时候指定编解码方式
    readLine():阻塞方法，读到换行符结束
对象序列化：将对象通过流传输
    ObjectOutputStream/ObjectInputStream
    只有实现了Serializable接口的对象才能序列化
    不仅对象本身需要实现Serializable接口,对象的属性也需要实现该接口，因为存对象就是存属性。
    用transient修饰的属性为临时属性，不参与序列化(如：二者存其一)
属性发生修改：
    流：记录对象的状态
    clone()：对象的克隆，返回对象的属性

