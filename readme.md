# C  Style Guide

The guidelines in this article are adopted from the .NET Runtime,
Microsoft 's .NET Framework, C  Coding Style guidelines. This C  style
guide recommends best practices for C  programmers to improve their
code. This style guide evolves over time as additional conventions are
identified and past conventions are rendered obsolete by changes in C 
itself.

## Introduction:

One of the component-oriented, object-oriented, and type-safe
programming language is C  (pronounced  "See Sharp ") which enables
developers to create many types of secure and robust applications that
run on .NET. C  has its roots inside the C circle of relatives of
languages ​​and might be immediately familiar to C, C++, Java, and
JavaScript programmers.

### Guiding Principles:

The principal goal is readability, conciseness, and simplicity. Also,
this guide is written to keep .Net in mind. components of C  design
which have been immediately encouraged by using versioning concerns
consist of separate virtual and override modifiers, guidelines for
managing approach overloading, and assist for specific declarations of
interface individuals.

Below are some of the best practices which all the .Net Developers
should follow:

### Nomenclature

Overall, naming should follow C  standards.

### **Pascal case**:

To be consistent with the Microsoft 's .NET Framework guidlines, the
PascalCasing is used for naming classes, records, structures and
methods.

    public class EmployeeDepartment

    {

        public void FinalStatistics()

        {

        }

        public void AnalyzeStatistics()

        {


        }

    }



### **Interface Naming convention**:
When naming an interface, use pascal casing in addition to prefixing the
name with an I. This clearly indicates to consumers that it 's an
interface.

    public interface IEmployeeDepartment

    {

    }

    
When naming public members of types, such as fields, properties, events,
methods, and local functions, use pascal casing.

    public class EmployeeDepartment

    {

    // An init-only property given below

    public IEmployeeDepartment EmployeeDepartment { get; init; }

    // An event shown below

    public event Action EventsProcessing;

    // Method

    public void EventsStartProcessing()

    {

    // Local function

    static int TotalNumberOfEmployees() = > EmployeeDepartment.Count;

    //  ...

    }

    }

Use pascal casing for writing positional records because it uses
parameters.   

    public record ContactAddress(

    string City,

    string ZipCode,

    string StateOrProvince,

    string HouseNumber

    );

    
### **Camel case:**

Camel casing is used when naming internal or private fields and use
prefix with them  _.

    public class EmployeeDepartment

    {

    private I EmployeeDepartment  _ employeeDepartment;

    }  

When writing method parameters, use camel casing.    

    public T RandomMethod<T>(int anyNumber, bool isValid)

    {

    }

### Additional naming conventions:

If qualified names are too long for a single line it can be broken down
after a dot (.), as shown in the example below.  

    var overallEmployeeAttendanceChart = new
    System.Diagnostics.EmployeeAttendanceChart ();    

### One responsibility:

The method or function should have only single responsibility (one job).
Don't try to combine multiple functionalities into single function.

    **Correct**:    

    public void UpdateAddress(Address address) {}

    public void InsertAddress(Address address) {}    

    **Avoid**:  

    public void SaveAddress(Address address) {

    if (address.AddressId == 0) {} else {}

    }    

### Controller Actions:

Controller Actions in MVC should have meaningful names and each action
have single responsibility only.

    **Correct**:    

    public class EmployeeController: Controller {

    public ActionResult Index() {}

    public ActionResult Create() {}

    [HttpPost]

    public ActionResult Create(EmployeeModel employee) {}

    public ActionResult Edit(int id) {}

     [HttpPut ]

    public ActionResult Update(EmployeeModel employee) {}

     [HttpDelete ]

    public JsonResult Delete(int id) {}

    }  

    **Avoid**:

    public class EmployeeController: Controller {

    public ActionResult GetAll() {}

    public ActionResult CreateEmployee() {}

    [HttpPost]

    public ActionResult CreateEmployee(EmployeeModel employee) {}

    public ActionResult EditEmployee(int id) {}

    [HttpPut]

    public ActionResult UpdateEmployee(EmployeeModel employee) {}

    [HttpDelete]

    public JsonResult EmployeeDelete(int id) {}

    }    

### Common Type System:

Avoid using common type system. Use the language specific aliases

    **Correct:  **

    int age;  

    string firstName;  

    object addressInfo; 

    ** Avoid:  **

    System.Int32 age; String firstName;  

    Object addressInfo; 

While comparing string, convert string variables into Upper or Lower
case

    **Correct**:

    if (firstName.ToLower() ==  "yogesh ") {}

    if (firstName.ToUpper() == "YOGESH") {}

    ** Avoid**:

    if (firstName == "rohit") {}

Use String.Empty instead of ""

    **Correct**:     if (firstName == String.Empty) {}      

    **Avoid**:      **if** (firstName == "") {}      

Use enums wherever required. Don't use numbers or strings to indicate
discrete values.

    ** Correct**:

    public enum LoggerType {

    Event,

    File,

    Database

    }

    public void LogException(string message, LoggerType loggerType) {

    switch (loggerType) {

    case LoggerType.Event:

    // Do something break;

    case LoggerType.File:

    // Do something break;

    case LoggerType.Database:

    // Do something break;

    default:

    // Do something break;

    }

    }

    ** Avoid**:

    public void LogException(string message, LoggerType loggerType) {

    switch (loggerType) {

    case  "Event ":

    // Do something break;

    case  "File ":

    // Do something break;

    case  "Database ":

    // Do something break;

    default:

    // Do something break;

    }

    }

Always do null check for objects and complex objects before accessing
them.

    ** Correct**:

    public Contact GetContactDetails(Address address) {

    if (address != null && address.Contact != null) {

    return address.Contact;

    }

    }

    ** Avoid**:

    public Contact GetContactDetails(Address address) {

    return address.Contact;

    }

Error message to end use should be user friendly and self-explanatory
but log the actual exception details using logger. Create constants for
this and use them in application.

    ** Correct**:

    "Error occurred while connecting to database. Please contact
    administrator." "Your session has been expired. Please login again."
    
    ** Avoid**:

    "Error in Application."

    "There is an error in application."     

Avoid passing many parameters to function. If you have more than 4-5
parameters use class or structure to pass it.

    ** Correct**:

    public void UpdateAddress(Address address) {}

    ** Avoid**:

    public void UpdateAddress(int addressId, string country, string state,
    string phoneNumber, string pinCode, string address1, string address2) {}

Use object initializers to simplify object creation.

    ** Correct**:

    var employee = new Employee {

    FirstName = "ABC", LastName = "PQR", Manager = "XYZ", Salary = 12346.25

    };

    ** Avoid**:

    var employee = new Employee();

    employee.FirstName = "ABC";

    employee.LastName = "PQR";

    employee.Manager = "XYZ";

    employee.Salary = 12346.25;

The using statements should be sort by framework namespaces first and
then application namespaces in ascending order

    using System;

    using System.Collections.Generic; using System.IO;

    using System.Text;

    using Company.Product.BusinessLayer;  

Simplify your code by using the C  using statement. If you have a
try-finally statement in which the only code in the finally block is a
call to the Dispose method, use a using statement instead.

    ** Correct**:

    using(var fileToOpen = new FileInfo(fileName)) {

    // File operation

    }

    ** Avoid**:

    var fileInfo = new FileInfo(fileName);

    try {

    // File operation

    } finally {

    if (fileInfo != null) {

    fileInfo.Delete();

    }

    }

Always catch only the specific exception instead of catching generic
exception.

    ** Correct:**

    void ReadFile(string fileName) {  

    try{  

    // read from file.  

    } catch (System.IO.IOException fileException) {  

    // log the error. Re-throw exception throw fileException;  

    } finally {}  

    }

    ** Avoid:**

       

    void ReadFile(string fileName) {  

    try {  

    // read from file.  

    } catch (Exception ex) {  

    // catching general exception  

    } finally {}  

    }

### Constants: 

To Avoid grasping too much attention don't use Screaming Caps for
constants or read-only variables as they.

    **  Correct**

    public static const string EmployeeDepartment =  "CourrierServices ";

    **  Avoid**

        public static const string EMPLOYEEDEPARTMENT =  "
    CourrierServices  ";    

### Identifiers:

According to Microsoft 's .NET Framework as well as the Visual Studio
IDE makes it very easy to determine the type of a variable (via
tooltips). It is best to avoid type indicators in identifiers.

    ** Correct**

    int age;

    string name;

    ** Avoid**

    int IAge;

    string strName;

### Abbreviations:  

It is best to avoid using abbreviations and contractions as a part of
identifiers. Don't use abbreviations as it cause trouble for other
developers. Except for few abbreviations that are pre-defined.

    **// Correct**

    EmployeeGroup employeeGroup;

    Department employeeDepartment;

    **// Avoid**

    EmployeeGroup emplyGrp;

    Department emplyDepartment;

    sp(smartPhone)

    lm(liveMode)

    WinXp(windowsXP)

    // Exceptions

    EmployeeId employeeId;

    XmlDocument xmlDocument;

For 2 or more characters abbreviation, use PascalCasing (2 chars are
both uppercase).
    
    HtmlHelper htmlHelper;

    FtpTransfer ftpTransfer;

    UIControl uiControl;

### Underscores:

It is best in identifiers, not to use Underscores or underlines for
improving the readability and chances of error. 
**Exclusion**: you can prefix private static variables with an
underscore.

    **// Correct**

    public TimeDate employeeGroup;

    public EmploymentTenure employmentTenure;

    **// Avoid**

    public TimeDate employee Group;

    public EmploymentTenure employment Tenure;

    **// Exception**

    private TimeDate  _employeeGroup;

### Noun Class Names:

It is best to make classes easy to remember so avoid using noun or noun
phrases while naming a class.

    public class Employees

    { //...}

    public class DepartmentLocation

    {//...}

    public class DocumentVerification

    {//... }

### Type Names:

Instead of using system type names like Int16, UInt64, Single, etc. use
predefined type names.

    ** Correct:**

    string employeeName;

    int age;

    bool isConfirmed;

    **  Avoid**

    String employeeName;

    Int32 age;

    Boolean isConfirmed;

### Implicit Types:

It is best to avoid using local variable declarations as implicit
type var . 
**Exclusion**: The primitive types like int, string, double, etc. use
predefined names.

    var stream = File.Create(path);

    var customers = new List();

    // Exceptions

    int age = 50;

    string timeTable;

    bool isConfirmed;

### Interfaces:

It is best use Prefix interfaces with the letter **I** as Interface
names are adjectives or noun.

    public interface IBadge

    {//..}

    public interface IBadge Collection

    {//..}

    public interface IGroupData

    {//..}

### File Names:

It is best to always name source file consistent with their main
classes.

Exception: file names with partial classes suggest their purpose or
source, such as trendy, created, etc. Files are alphabetically ordered
and keep partial classes adjacent.

    // Located in Employee.cs

    public partial class Employee

    {

    // ...

    }

    // Located in Employee. trendy.cs

    public partial class Employee

    {

    // ...

    }

### Namespaces:

We should arrange namespaces with a distinctly identified structure to
sustain better organization of code base.

**// Few Suggestions**

    namespace Company. Employee.Module.SubModule

    namespace Employee.Module.Component

    namespace Employee.Layer.Module.Group    

### Curly Brackets:

It is best to use vertically align curly brackets as developer prefers
although it is different than Microsoft's defined standards.

    ** Correct:**

    class Employee

    {

    static void trendy(string [ ] args)

    {//.... }

    }

### Member Variables: 

It is best to declare at the top of a class, all static and member
variables, in order to prevents the necessity to search for their
declarations.

    ** Correct:**

    public class Employee

    {

    public static string Employee Name;

    public static decimal Age;

    public string ContactNumber{get; set;}

    public DateTime DateOfJoining{get; set;}

    public DateTime DateOFAbsence {get; set;}

    public decimal Salary {get; set;}

    // Constructor

    public Employee ()

    {

    //  ...

    }

    }

### Enums:

It is best to use singular names for enums but can use flags for plural
because enum can grasp multiple values by utilizing  'OR ' bitwise.

     **Correct**

    public enum Language

    {

    Chinese,

    English,

    French,

    Italian,

    Spanish

    }

    // Exception

     [Flags ]

    public enum Placements

    {

    None = 0,

    Top = 2 ,

    Right = 3,

    Bottom = 2,

    Left = 8

    }  

### Enum Types:

It is best not to specify a type or values of enum or enums (except for
"bit fields") as it can create confusion when relying on actual types
and values.

     **Avoid**

    public enum Placement: far

    {

    Top = 1,

    Right = 2,

    Left = 3,

    Bottom = 4

    }

    **  Correct**

    public enum Placement

    {

    Top,

    Right,

    Left,

    Bottom

    }

### Enum Suffix:

It is best not to use suffix enum names with Enum to be consistent with
preceding rule of avoiding the type indicators in identifiers.

    ** Avoid**

    public enum NameEnum

    {

    Peter,

    Nicky,

    Damien,

    }

    ** Correct**

    public enum Name

    {

    Peter,

    Nicky,

    Damien,

    }

### Layout conventions:

Write only one statement, declaration per line.one blank line between
method definitions & parentheses to make clauses in an expression
apparent

    if ((val1  > val2) && (val1  > val3))

    {

    // Take appropriate action.

    }

### String data type:

Use string interpolation to concatenate short strings, as shown in the
following code.

    string employeeName =  $ "{nameList [n ].FirstName}, {nameList [n ].
    LastName } ";

To append strings in loops, especially when you 're working with large
amounts of text, use a StringBuilder object.

    var sentence =  "alkfhaldkhfadhflkadhfgahd ";

    var multiplesentaces = new StringBuilder();

    for (var i = 0; i  < 10000; i++)

    {

    multiplesentaces.Append(sentence);

    }

    //Console.WriteLine( "tra " + multiplesentaces);

### Implicitly typed local variables:

When the type of the variable is clear from the right side of the
assignment, it is important to use implicit typing for local variables.

    var var1 =  "Obviously! It's a string. ";

    var var2 = 12;

If the type is not obvious, then refrain from using var instead of
assuming the type from its method name.

    int var3 = EmployeeClass.PerformanceReview();

    int var4 = Convert.ToInt64(Console.ReadLine());

    var inputInt = Console.ReadLine();

    Console.WriteLine(inputInt);

To determine the type of the loop variable in for loops, it is best to
use implicit typing.

    var sentence =  "alkfhaldkhfadhflkadhfgahd ";

    var multiplesentaces = new StringBuilder();

    for (var i = 0; i  < 10000; i++)

    {

    multiplesentaces.Append(sentence);

    }

    //Console.WriteLine( "tra " + multiplesentaces);

The next example is a foreach statement using explicit typing.

    foreach (char en in lang)

    {

    if (en ==  'n ')

    Console.Write( "N ");

    else

    Console.Write(en);

    }

    Console.WriteLine();    

### Unsigned data types:

It is preferable to use int instead of using unsigned types as it is
easier to communicate with more libraries.

### Arrays:

While creating an array you can 't use var instead of string [ ], so use
the concise and neat syntax on the declaration line while initializing
arrays .

    string [ ] fruits1 = {  "apple ",  "Kiwi ",  "Tangerine ",  "Melon " };

    // you can use var, If you apply explicit instantiation,.

    var fruits2 = new string [ ] {  "apple ",  "Kiwi ",  "Tangerine ",
     "Melon " };

### Delegates:

To pass arguments of one method to another method it is best to use
delegates like event handlers.

    public delegate int WeightCalculator(int x, int y);

### Event handling:

The best practice is to use a lambda expression for defining an event
handler if you are not going to eliminate it later.

    public App()

    {

    this.Click += (a, e) = >

    {

    PerformanceHandlerShow(

    ((MouseEventArgs)e).Location.ToString());

    };

    }

The lambda expression shortens the following traditional definition.

    public App1 ()

    {

    this.Click += new EventHandler(App  _Click);

    }

    void App  _Click(object? sender, EventArgs e)

    {

    PerformanceHandler.
    PerformanceHandlerShow(((MouseEventArgs)e).Location.ToString());

    }

### Static members:

Avoid defining static member in a base class it may break the code in
the future

### LINQ queries:

Use meaningful names for query variables. For the declaration of range
variables and query variables use implicit typing.

     **Correct**:

    private void SaveAddress(Address address) {}

    ** Avoid**:

    // This method used to save address

    private void Save(Address address) {} 

It is best to use from clauses multiple times as an alternative of a join clause to retrieve innermost
collections.

### Keywords in C :

Reserved and predefined identifiers with special values used with @ as a
prefix to the compiling program are called as Keywords.

### Contextual keywords:

Contextual key phrases have special meaning only in a limited
application context and can be used as identifiers outside that context.

### Editing the current project:

You may set the version of your language for your current report.

     <PropertyGroup >

     <LangVersion >Hello </LangVersion >

     </PropertyGroup >

The value hello uses the latest C  language version supported by the
compiler.

### Set up multiple projects:

You can create a Directory.Build.props file containing the
 <LangVersion > element In order to setup multiple projects and placed
in the solution directory.

     <Project >

     <PropertyGroup >

     <LangVersion >preview </LangVersion >

     </PropertyGroup >

     </Project >   

### Value types:

A variable of a value type contains an instance of the type. With value
types, the variables each have their own copy and original instance.  

    using System;

    using System.Collections.Generic;

    public struct EmployeeAge

    {

    public int Age;

    private List <string > employees;

    public EmployeeAge(int n)

    {

    Age = n;

    employees = new List <string >();

    }

    public void AddEmployee (string employee) = > employees.Add(employee);

    public override string ToString() = >  $ "{Age}  [{string.Join( ",  ",
    employees)} ] ";

    }

    public class App

    {

    public static void Main()

    {

    var n1 = new EmployeeAge (0);

    n1. AddEmployee ( "A ");

    Console.WriteLine(n1); // output: 0  [A ]

    var n2 = n1;

    n2.Age = 7;

    n2. AddEmployee ( "B ");

    Console.WriteLine(n1); // output: 0  [A, B ]

    Console.WriteLine(n2); // output: 7  [A, B ]

    }

    }  

### Kinds of value types and type constraints:

There are two kinds of value type variables:

Structure Type (encapsulating object and its associated functionality)

Enumeration Type(described by a collection of selected constants and
embodies an option or a combination of options.).

## Built-in value types

### Integral numeric types 

All integral numeric types
support [arithmetic](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators), [bitwise
logical](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators), [comparison](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/comparison-operators),
and [equality](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/equality-operators) operators.The
default value of each integral type is zero, 0.
   
    int a = 123;

    System.Int32 b = 123;   

### Integer literals:   

    var decimalLiteral = 42;

    var hexLiteral = 0x2A;  

The value can be implicitly converted to sbyte, byte, short, ushort,
uint, ulong, nint or nuint:    

    byte a = 17;

    byte b = 300; // CS0031: Constant value  '300 ' cannot be converted to a
     'byte '  

Use a cast to convert the value of an integer literal to the other type:

    var signedByte = (sbyte)42;

    var longVariable = (long)42;   

### Native sized integers:

Their storage is determined by the natural integer size on the target
machine.

    // To get the size of a native-sized integer at run time

    Console.WriteLine( $ "size of nint = {sizeof(nint)} ");

    Console. WriteLine( $ "size of nuint = {sizeof(nuint)} ");     

To get the minimum and maximum values of native-sized integers at run
time:

    Console.WriteLine( $ "nint.MinValue = {nint.MinValue} ");

    Console.WriteLine( $ "nint.MaxValue = {nint.MaxValue} ");

    Console.WriteLine( $ "nuint.MinValue = {nuint.MinValue} ");

    Console.WriteLine( $ "nuint.MaxValue = {nuint.MaxValue} ")    

There 's no direct syntax for native-sized integer literals use implicit
or explicit casts of other integer values:

    nint a = 42

    nint a = (nint)42;

### Floating-point numeric types:

It represents real numbers, numeric types that support arithmetic,
comparison, and equality operators.

#### Characteristics:

The default value is zero, use double instead of decimal for optimizing
performance and ensuring accuracy.

    double a = 1.0;

    decimal b = 2.1m;

    Console.WriteLine(a + (double)b);

    Console.WriteLine((decimal)a + b);   

### Real literals:

The literal without suffix or with the d or D suffix is of type double,
with the f or F suffix is of type float and with the m or M suffix is of
type decimal.    

    double d = 3D;

    d = 4d;

    d = 3.934_001;

    float f = 3_000.5F;

    f = 5.4f;

    decimal myMoney = 3_000.5m;

    myMoney = 400.75M;   

**Built-in numeric conversions:**

There are no implicit conversions to the byte and sbyte, or double and
decimal, float or double types.

    byte a = 13;

    byte b = 300; // CS0031**: Constant value  '300 ' cannot be converted to
    a  'byte '**   

### Explicit numeric conversions:

If the source value is too small to be represented as a decimal, the
result becomes zero & if it is NaN an OverflowException is thrown.

### Bool:

Can be a controlling conditional expression in the if, do, while, and
for statements and default value is false.

    bool check = true;

    Console.WriteLine(check ?  "Checked " :  "Not checked "); // output:
    Checked

    Console.WriteLine(false **?  "Checked " :  "Not checked "); // output:
    Not checked**    

### Three-valued Boolean logic:

Use the nullable bool? type, for the three-valued logic, the predefined
& and  | operators

### Char:

The default value is   0, that is, U+0000, supports comparison,
equality, increment, and decrement operators.

    var chars = new [ ]

    {

     'j ',

     '  u006A ',

     '  x006A ',

    (char)106,

    };

    Console.WriteLine(string.Join( "  ", chars)); // output: j j j j    

### Enumeration types:

A set of named constants of the underlying integral numeric type, use
the enum keyword.

    enum Season

    {

    Spring,

    Summer,

    Autumn,

    Winter

    }    

enum members are of type int; they start with zero and increase by one
following the definition text order.    

    enum ErrorCode : ushort

    {

    None = 0,

    Unknown = 1,

    ConnectionLost = 100,

    OutlierReading = 200}    

You cannot define a method inside the definition of an enumeration type
should create an extension method.

### Enumeration types as bit flags:

To indicate that an enumeration type declares bit fields, apply the
Flags attribute to it.

     [Flags ]

    public enum Days

    {

    None = 0b_0000_0000, // 0

    Monday = 0b_0000_0001, // 1

    Tuesday = 0b_0000_0010, // 2

    Wednesday = 0b_0000_0100, // 4

    Thursday = 0b_0000_1000, // 8

    Friday = 0b_0001_0000, // 16

    Saturday = 0b_0010_0000, // 32

    Sunday = 0b_0100_0000, // 64

    Weekend = Saturday  | Sunday

    }   

### The System.Enum type and enum constraint:

The System.Enum type provides various methods to get information about
an enumeration type and its values.

### Structure types

A structure type (or struct type) is a value type that can encapsulate
data and related functionality.

    public struct Coords

    {

    public Coords(double x, double y)

    {

    X = x;

    Y = y;

    }

    public double X { get; }

    public double Y { get; }

    public override string ToString() = >  $ "({X}, {Y}) ";

    }    

### Readonly struct:

It is immutable any property even auto-implemented must be read-only &
can call a non-readonly member.

    public readonly struct Coords

    {

    public Coords(double x, double y)

    {

    X = x;

    Y = y;

    }

    public double X { get; init; }

    public double Y { get; init; }

    public override string ToString() = >  $ "({X}, {Y}) ";

    }   

You can also apply the readonly modifier to methods that override
methods declared in System.Object:    

    public readonly override string ToString() = >  $ "({X}, {Y}) ";

    properties and indexers:

    private int counter;

    public int Counter

    {

    readonly get = > counter;

    set = > counter = value;}    

To apply on both accessors of a property or indexer, apply it in the
declaration of the property or indexer.    

    public readonly double X { get; init; }    

### Nondestructive mutation:

Use object initializer syntax to modify members and their new values.   

    public readonly struct Coords

    {

    public Coords(double x, double y)

    {

    X = x;

    Y = y;

    }

    public double X { get; init; }

    public double Y { get; init; }

    public override string ToString() = >  $ "({X}, {Y}) ";

    }

    public static void Main()

    {

    var p1 = new Coords(0, 0);

    Console.WriteLine(p1); // output: (0, 0)

    var p2 = p1 with { X = 3 };

    Console.WriteLine(p2); // output: (3, 0)

    var p3 = p1 with { X = 1, Y = 4 };

    Console.WriteLine(p3); // output: (1, 4)

    }    

### Record struct:

It can define both record struct and readonly record struct types. A
record struct can 't be a ref struct.

### Struct initialization and default values:

It creates a distinction between an uninitialized struct with its
default value and an initialized struct, which stores values set by
constructing it.    

    public readonly struct Measurement

    {

    public Measurement()

    {

    Value = double.NaN;

    Description =  "Undefined ";

    }

    public Measurement(double value, string description)

    {

    Value = value;

    Description = description;

    }

    public double Value { get; init; }

    public string Description { get; init; }

    public override string ToString() = >  $ "{Value} ({Description}) ";

    }

    public static void Main()

    {

    var m1 = new Measurement();

    Console.WriteLine(m1); // output: NaN (Undefined)

    var m2 = default(Measurement);

    Console.WriteLine(m2); // output: 0 ()

    var ms = new Measurement [2 ];

    Console.WriteLine(string.Join( ",  ", ms)); // output: 0 (), 0 ()

    }   

### Limitations with the design of a structure type:

It can 't inherit from other class or structure type, implement
interfaces but can 't be the base of a class.

**Conversions**

Except ref struct types can convert to and from the System.ValueType and
System.Object types.

**ref structure types:**

Instances of a ref struct type are allocated on the stack and can 't be
used in iterators.

    public ref struct CustomRef

    {

    public bool IsValid;

    public Span <int > Inputs;

    public Span <int > Outputs;

    }    

A ref field may have the null value. Use the Unsafe.IsNullRef <T >(T)
method to determine if a ref field is null.

### readonly ref: 

Use ref reassign with the = ref operator only inside a constructor or an
init accessor.

### Tuple:

It provides concise syntax to group multiple data elements in a
lightweight data structure.    

    (double, int) t1 = (4.5, 3);

    Console.WriteLine( $ "Tuple with elements {t1.Item1} and {t1.Item2}. ");

    // Output:

    // Tuple with elements 4.5 and 3.

    (double Sum, int Count) t2 = (4.5, 3);

    Console.WriteLine( $ "Sum of {t2.Count} elements is {t2.Sum}. ");

    // Output:

    // Sum of 3 elements is 4.5.   

### Void:

The return type of a method (or a local function) to specify that the
method doesn 't return a value.    

    public static void Display(IEnumerable <int > numbers)

    {

    if (numbers is null)

    {

    return;

    }

    Console.WriteLine(string.Join( "  ", numbers));

    }   

### Default value expressions:

You can use the default literal to initialize a variable with the
default value of its type:

    int a = default;    

### Parameterless constructor of a value type:

The implicit parameterless constructor also produces the default value
of the type.

    var n = new System.Numerics.Complex();

    Console.WriteLine(n); // output: (0, 0)     

### C  operators and expressions

Many of them are supported by the built-in types and allow you to
perform basic operations with values.

#### Types of operators:

Those operators include the following groups:

- Arithmetic operators that perform arithmetic operations with numeric
operands

- Comparison operators that compare numeric operands

- Boolean logical operators that perform logical operations with bool
operands

- Bitwise and shift operators that perform bitwise or shift operations
with operands of the integral types

- Equality operators that check if their operands are equal or not. 

        int a, b, c;

        a = 7;

        b = a;

        c = b++;

        b = a + b  * c;

        c = a  >= 100 ? b : c / 10;

        a = (int)Math.Sqrt(b  * b + c  * c);

        string s =  "String literal ";

        char l = s [s.Length - 1 ];

        var numbers = new List <int >(new [ ] { 1, 2, 3 });

        b = numbers.FindLast(n = > n  > 1);     

Lambda expressions that allow you to create anonymous functions:

    int [ ] numbers = { 2, 3, 4, 5 };

    var maximumSquare = numbers.Max(x = > x  * x);

    Console.WriteLine(maximumSquare);

    // Output:

    // 25    

Query expressions that allow you to use query capabilities directly in
C :

    var scores = new [ ] { 90, 97, 78, 68, 85 };

    IEnumerable <int > highScoresQuery =

    from score in scores

    where score  > 80

    orderby score descending

    select score;

    Console.WriteLine(string.Join( "  ", highScoresQuery));

    // Output:

    // 97 90 85

### Operator precedence:

With multiple operators, the operators with higher precedence are
evaluated before the operators with lower precedence.

    var a = 2 + 2  * 2;

    Console.WriteLine(a); // output: 6

Use parentheses to change the order of evaluation imposed by operator
precedence:

    var a = (2 + 2)  * 2;

    Console.WriteLine(a); // output: 8

### User-defined conversion operators :

A user-defined type can define a custom implicit or explicit conversion
from or to another type.

    using System;

    public readonly struct Digit

    {

    private readonly byte digit;

    public Digit(byte digit)

    {

    if (digit  > 9)

    {throw new ArgumentOutOfRangeException(nameof(digit),  "Digit cannot be
    greater than nine. ");

    }

    this.digit = digit;

    }

    public static implicit operator byte(Digit d) = > d.digit;

    public static explicit operator Digit(byte b) = > new Digit(b);

    public override string ToString() = >  $ "{digit} ";

    }

    public static class UserDefinedConversions

    {

    public static void Main()

    {

    var d = new Digit(7);

    byte number = d;

    Console.WriteLine(number); // output: 7

    Digit digit = (Digit)number;

    Console.WriteLine(digit); // output: 7

    }

    }

### && and  | | operators

To avoid exceptions and increase performance use && instead of & and
 | | instead of  | for comparisons.

    Console.Write( "Enter a dividend:  ");

    int dividend = Convert.ToInt32(Console.ReadLine());

    Console.Write( "Enter a divisor:  ");

    int divisor = Convert.ToInt32(Console.ReadLine());

    if ((divisor != 0) && (dividend / divisor  > 0))

    {

    Console.WriteLine( "Quotient: {0} ", dividend / divisor);

    }

    else

    {

    Console.WriteLine( "Attempted division by 0 ends up here. ");

    }

### new operator

Use one of the concise forms of object instantiation.

    var instance1 = new ExampleClass();

    ExampleClass instance2 = new();

The preceding declarations are equivalent to the following declaration.

    ExampleClass instance2 = new ExampleClass();

Use object initializers to simplify object creation, as shown in the
following example.

    var instance3 = new ExampleClass { Name =  "Desktop ", ID = 37414,

    Location =  "Redmond ", Age = 2.3 };

The following example sets the same properties as the preceding example
but doesn 't use initializers.

    var instance4 = new ExampleClass();

    instance4.Name =  "Desktop ";

    instance4.ID = 37414;

    instance4.Location =  "Redmond ";

    instance4.Age = 2.3;

### Pointer related operators:

- Unary & (address-of) operator: to get the address of a variable

- Unary  * (pointer indirection) operator: to obtain the variable pointed
by a pointer

- The - > (member access) and  [ ] (element access) operators

- Arithmetic operators +, -, ++, and  --

- Comparison operators ==, !=,  <,  >,  <=, and  >=

### Address-of operator &

    unsafe

    {

    int number = 27;

    int * pointerToNumber = &number;

    Console.WriteLine( $ "Value of the variable: {number} ");

    Console.WriteLine( $ "Address of the variable:
    {(long)pointerToNumber:X} ");

    }

    // Output is similar to:

    // Value of the variable: 27

    // Address of the variable: 6C1457DBD4

### Pointer indirection operator  *:

The unary pointer indirection operator  * computes the product of its
numeric operands, obtains the variable to which its operand points,
cannot apply o an expression of type void *.

    unsafe

    {

    char letter =  'A ';

    char * pointerToLetter = &letter;

    Console.WriteLine( $ "Value of the  `letter ` variable: {letter} ");

    Console.WriteLine( $ "Address of the  `letter ` variable:
    {(long)pointerToLetter:X} ");

     *pointerToLetter =  'Z ';

    Console.WriteLine( $ "Value of the  `letter ` variable after update:
    {letter} ");

    }

    // Output is similar to:

    // Value of the  `letter ` variable: A

    // Address of the  `letter ` variable: DCB977DDF4

    // Value of the  `letter ` variable after update: Z

### Pointer member access operator - >:

The - > operator combines pointer indirection and member access.

    x- >y

    is equivalent to

    ( *x).y

### Assignment operators:

The assignment operator = assigns the value of its right-hand operand by
its left-hand operand.

    a = b = c

is evaluated as

    a = (b = c)     

### ref assignment:

Ref assignment = ref makes its left-hand operand an alias to the
right-hand operand. when you update its value with an ordinary
assignment operator =, the corresponding array element is also updated.

    void Display(double [ ] s) = > Console.WriteLine(string.Join( "  ", s));

    double [ ] arr = { 0.0, 0.0, 0.0 };

    Display(arr);

    ref double arrayElement = ref arr [0 ];

    arrayElement = 3.0;

    Display(arr);

    arrayElement = ref arr [arr.Length - 1 ];

    arrayElement = 5.0;

    Display(arr);

    // Output:

    // 0 0 0

    // 3 0 0

    // 3 0 5

### Compound assignment:

For a binary operator op, a compound assignment expression of the form

    x op= y

is equivalent to

    x = x op y

except that x is only evaluated once.

### Null-coalescing assignment:

You can use the ??= operator to assign the value of its right-hand
operand to its null left-hand operand.

### Expression lambdas:

A lambda expression with an expression on the right side of the = >
operator is called an expression lambda.

    (input-parameters) = > expression

### Statement lambdas:

A statement lambda resembles an expression lambda except that its
statements are enclosed in braces:

    (input-parameters) = > {  <sequence-of-statements > }

The body of a statement lambda can consist of any number of statements
can 't use create expression trees.

    Action <string > greet = name = >

    {

    string greeting =  $ "Hello {name}! ";

    Console.WriteLine(greeting);

    };

    greet( "World ");

    // Output:

    // Hello World!

### Input parameters of a lambda expression:

Enclose input parameters in parentheses. Specify zero input parameters
with empty parentheses:

    Action line = () = > Console.WriteLine();

If a lambda expression has only one input parameter, parentheses are
optional:

    Func <double, double > cube = x = > x  * x  * x;

Two or more input parameters are separated by commas:

    Func <int, int, bool > testForEquality = (x, y) = > x == y;

Sometimes the compiler can 't infer the types of input parameters use
explicit type in-case

    Func <int, string, bool > isTooLong = (int x, string s) = > s.Length  >
x;

Input parameter types must be all explicit or all implicit; otherwise, a
CS0748 compiler error occurs.

    Func <int, int, int > constant = ( _,  _) = > 42;

Lambda discard parameters may be useful when you use a lambda expression
to provide an event handler.

### Async lambdas:

For lambda expressions and statements for asynchronous processing use
the async and await keywords.

    public partial class Form1 : Form

    {

    public Form1()

    {

    InitializeComponent();

    button1.Click += button1_Click;

    }

    private async void button1_Click(object sender, EventArgs e)

    {

    await ExampleMethodAsync();

    textBox1.Text +=  "  r  nControl returned to Click event handler.  n ";

    }

    private async Task ExampleMethodAsync()

    {

    // The following line simulates a task-returning asynchronous process.

    await Task.Delay(1000);

    }

    }

### Lambda expressions and tuples

You can provide a tuple as an argument to a lambda expression, and it
will also return a tuple.

    Func <(int, int, int), (int, int, int) > doubleThem = ns = > (2  *
    ns.Item1, 2  * ns.Item2, 2  * ns.Item3);

    var numbers = (2, 3, 4);

    var doubledNumbers = doubleThem(numbers);

    Console.WriteLine( $ "The set {numbers} doubled: {doubledNumbers} ");

    // Output:

    // The set (2, 3, 4) doubled: (4, 6, 8)

Ordinarily, the fields of a tuple are named Item1, Item2, or you can
define a tuple with named components.

    Func <(int n1, int n2, int n3), (int, int, int) > doubleThem = ns
    = > (2  * ns.n1, 2  * ns.n2, 2  * ns.n3);

    var numbers = (2, 3, 4);

    var doubledNumbers = doubleThem(numbers);

    Console.WriteLine( $ "The set {numbers} doubled: {doubledNumbers} ");

### Lambdas with the standard query operators

LINQ to Objects, an input parameter whose type is one of the
Func <TResult > family of generic delegates.

    public delegate TResult Func <in T, out TResult >(T arg)

The delegate can be instantiated as a Func <int, bool > instance where
int is an input parameter and bool is the return value.

    Func <int, bool > equalsFive = x = > x == 5;

    bool result = equalsFive(4);

    Console.WriteLine(result); // False

The following example specifies multiple input parameters by enclosing
them in parentheses.

    int [ ] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };

    var firstSmallNumbers = numbers.TakeWhile((n, index) = > n  >= index);

    Console.WriteLine(string.Join( "  ", firstSmallNumbers));

    // Output:

    // 5 4

Don't use lambda expressions directly in query expressions, rather use
them in method calls within query expressions.

    var numberSets = new List <int [ ] >

    {

    new [ ] { 1, 2, 3, 4, 5 },

    new [ ] { 0, 0, 0 },

    new [ ] { 9, 8 },

    new [ ] { 1, 0, 1, 0, 1, 0, 1, 0 }

    };

    var setsWithManyPositives =

    from numberSet in numberSets

    where numberSet.Count(n = > n  > 0)  > 3

    select numberSet;

    foreach (var numberSet in setsWithManyPositives)

    {

    Console.WriteLine(string.Join( "  ", numberSet));

    }

    // Output:

    // 1 2 3 4 5

    // 1 0 1 0 1 0 1 0

### Type inference in lambda expressions

- The lambda must contain the same number of parameters as the delegate
type.

- Each input parameter in the lambda must be implicitly convertible to its
corresponding delegate parameter.

- The return value of the lambda (if any) must be implicitly convertible
to the delegate 's return type.

    customers.Where(c = > c.City ==  "London ");

### Natural type of a lambda expression:

A lambda expression in itself doesn 't have a type because the common
type system has no intrinsic concept of  "lambda expression.

    var parse = (string s) = > int.Parse(s);

The compiler chooses an available Func or Action delegate, if a suitable
one exists. Otherwise, it synthesizes a delegate type. 

    object parse = (string s) = > int.Parse(s); // Func <string, int >

    Delegate parse = (string s) = > int.Parse(s); // Func <string, int >

Method groups (that is, method names without parameter lists) with
exactly one overload have a natural type:

    var read = Console.Read; // Just one overload; Func <int > inferred

    var write = Console.Write; // ERROR: Multiple overloads, can 't choose
  
If you assign a lambda expression to
System.Linq.Expressions.LambdaExpression, or
System.Linq.Expressions.Expression, and the lambda has a natural
delegate type, the expression has a natural type of
System.Linq.Expressions.Expression <TDelegate >, with the natural
delegate type used as the argument for the type parameter:

    LambdaExpression parseExpr = (string s) = > int.Parse(s); //
    Expression <Func <string, int > >

    Expression parseExpr = (string s) = > int.Parse(s); //
    Expression <Func <string, int > >

Not all lambda expressions have a natural type. Consider the following
declaration:

    var parse = s = > int.Parse(s); // ERROR: Not enough type info in the
    lambda

The compiler can 't infer a parameter type for s. When the compiler
can 't infer a natural type, you must declare the type:
 
    Func <string, int > parse = s = > int.Parse(s);

### Explicit return type:

The return type of a lambda expression is obvious and inferred.

    var choose = (bool b) = > b ? 1 :  "two "; // ERROR: Can 't infer
return type    

When you specify an explicit return type, you must parenthesize the
input parameters:

    var choose = object (bool b) = > b ? 1 :  "two "; // Func <bool,
object >    

### Attributes:

You can add attributes to a lambda expression, input parameters, return
value and its parameters.

    Func <string, int > parse =  [Example(1) ] (s) = > int.Parse(s);

    var choose =  [Example(2) ] [Example(3) ] object (bool b) = > b ? 1 :
     "two ";

    var sum = ( [Example(1) ] int a,  [Example(2), Example(3) ] int b) = > a
  + b;

    var inc =  [return: Example(1) ] (int s) = > s++;   

### Static modifier:

You can apply it to a lambda expression to prevent unintentional capture
of local variables or instance state.
    
    Func <double, double > square = static x = > x  * x;

### Patterns:

The following C  expressions and statements support pattern matching:

### is expression

**switch** statement

### switch expression

In those constructs, you can match an input expression against any of
the following patterns:

    public double CalculateAreaSwitchExpression(T shape)

    {

    return shape switch

    {

    null = > throw new ArgumentNullException(nameof(shape)),

    Square { Length: var l } = > l  * l,

    Circle { Radius: var r } = > r  * r  * Math.PI,

    Rectangle { Height: var h, Length: var l } = > h  * l,

    Triangle { Base: var b, Height: var h } = > b  * h / 2,

     _ = > throw new NotSupportedException()

    };

    }

### Declaration pattern:

To check the run-time type of an expression and, if a match succeeds,
assign an expression result to a declared variable.

    object shape = new Square { Length = 5 };

    public void IsShapeSquare(object shape)

    {

    if (shape is Square square)

    {

    Console.WriteLine( $ "Shape is a square with a side of length
    {square.Length} ");

    }

    else

    {

    Console.WriteLine( $ "{shape} is not a square ");

    }

    }

### Type pattern:

To check the run-time type of an expression.

    object shape = new Square { Length = 5 };

    public void IsShapeSquare(object shape)

    {

    if (shape is Square)

    {

    Console.WriteLine( $ "{shape} is a square ");

    }

    else

    {

    Console.WriteLine( $ "{shape} is not a square ");

    }

    }

### Constant pattern:

To test if an expression result equals a specified constant.

    Rectangle rectangle = new Rectangle { Height = 7, Length = 3 };

    public void IsShapeNull(Rectangle rectangle)

    {

    if (rectangle is null)

    {

    throw new ArgumentNullException(nameof(rectangle));

    }

    }

### Relational patterns: 

To compare an expression result with a specified constant.

    object shape = new Circle {Radius = 110};

    public void IsBigCircle(object shape)

    {

    if (shape is Circle { Radius:  >= 100 })

    {

    Console.WriteLine( $ "This is a big circle ");

    }

    }

### Logical patterns: 

To test if an expression matches a logical combination of patterns.

    object shape = new Circle {Radius = 110};

    public void IsBigCircleRange(object shape)

    {

    if (shape is Circle { Radius:  >= 100 and  <= 200 })

    {

    Console.WriteLine( $ "This is a big circle ");

    }

    }    

### Property pattern:

To test if an expression 's properties or fields match nested patterns.

    Triangle triangle = new Triangle { Base = 4, Height = 6 };

    public void IsSpecificTriangle(Triangle triangle)

    {

    if (triangle is Triangle { Base: 4, Height: 6 } specificTriangle)

    {

    Console.WriteLine( $ "Shape is a triangle wih a base of
    {specificTriangle.Base} and a height of {specificTriangle.Height} ");

    }

    }

### Positional pattern:

To deconstruct an expression result and test if the resulting values
match nested patterns.

    public struct Rectangle

    {

    public double Length { get; init; }

    public double Height {get; init; }

    public void Deconstruct(out double length, out double height)

    {

    length = Length;

    height = Height;

    }

    }

### var pattern: 

To match any expression and assign its result to a declared variable.

    object shape = new Rectangle { Length = 9, Height = 4};

    public void IsLengthMultipleOfThree(object shape)

    {

    if (shape is Rectangle { Length: var length } rect && length % 3 == 0)

    {

    Console.WriteLine( "This shape is a rectangle with a length which is a
    multiple of 3 ");

    }

    }

### Tuple pattern:

The tuple pattern is a particular way of using the positional pattern,
but the object we match on is not deconstructed as it is already a
tuple.

    public string ReturnDescriptionOfShape(string shape, int length, int
    height)

    {

    return (shape, length, height) switch

    {

    ( "Rectangle ", 2, 1) = >  "This is a small rectangle ",

    ( "Circle ", 4, 2) = >  "This is a medium circle ",

    ( "Square ", 8, 4) = >  "This is a large square ",

    ( _, _, _) = >  "This not a valid input "

    };

    }

### Discard pattern: 

### Discards are equivalent to unassigned variables; they don 't have a value. 

    ( _,  _, area) = city.GetCityInformation(cityName);    

### List patterns: 

To test if sequence elements match corresponding nested patterns.

    list_pattern_clause

    :  ' [ ' (pattern ( ', ' pattern) *  ', '?)?  ' ] '

    ;

    list_pattern

    : list_pattern_clause simple_designation?

    ;

    slice_pattern

    :  '.. ' pattern?

    ;

    primary_pattern

    : list_pattern

     | slice_pattern

     | // all of the pattern forms previously defined

    ;

Logical, property, positional, and list patterns are recursive patterns.
That is, they can contain nested patterns.

### Declaration and type patterns:

You use declaration and type patterns to check the compatibility with a
given type and declare new local variable.

    object greeting =  "Hello, World! ";

    if (greeting is string message)

    {

    Console.WriteLine(message.ToLower()); // output: hello, world!}

The run-time type of an expression result is T.

    // A declaration pattern with type T matches an expression when an
    expression result is non-null and any of the following conditions are
    true:

    var numbers = new int [ ] { 10, 20, 30 };

    Console.WriteLine(GetSourceLabel(numbers)); // output: 1

    var letters = new List <char > {  'a ',  'b ',  'c ',  'd ' };

    Console.WriteLine(GetSourceLabel(letters)); // output: 2

    static int GetSourceLabel <T >(IEnumerable <T > source) = > source
    switch

    {

    Array array = > 1,

    ICollection <T > collection = > 2,

     _ = > 3,

    };

A boxing or unboxing conversion exists from the run-time type of an
expression result to type T.

    int? xNullable = 7;

    int y = 23;

    object yBoxed = y;

    if (xNullable is int a && yBoxed is int b)

    {

    Console.WriteLine(a + b); // output: 30

    }

If you want to check only the type of an expression, you can use a
discard  _ in place of a variable 's name.

    public abstract class Vehicle {}

    public class Car : Vehicle {}

    public class Truck : Vehicle {}

    public static class TollCalculator

    {

    public static decimal CalculateToll(this Vehicle vehicle) = > vehicle
    switch

    {

    Car  _ = > 2.00m,

    Truck  _ = > 7.50m,

    null = > throw new ArgumentNullException(nameof(vehicle)),

     _ = > throw new ArgumentException( "Unknown type of a vehicle ",
    nameof(vehicle)),

    };

    }

You can use a type pattern, as the following example shows:

    public static decimal CalculateToll(this Vehicle vehicle) = > vehicle
    switch

    {

    Car = > 2.00m,

    Truck = > 7.50m,

    null = > throw new ArgumentNullException(nameof(vehicle)),

     _ = > throw new ArgumentException( "Unknown type of a vehicle ",
    nameof(vehicle)),

    };

To check for non-null, you can use a negated null constant pattern, as
the following example shows:

    if (input is not null)

    {

    //  ...

    }

### Constant pattern"

You use a constant pattern to test if an expression result equals a
specified constant, as the following example shows:

    public static decimal GetGroupTicketPrice(int visitorCount) = >
    visitorCount switch

    {

    1 = > 12.0m,

    2 = > 20.0m,

    3 = > 27.0m,

    4 = > 32.0m,

    0 = > 0.0m,

     _ = > throw new ArgumentException( $ "Not supported number of visitors:
    {visitorCount} ", nameof(visitorCount)),

    };    

### Constant Pattern:

In a constant pattern, you can use any constant expression, such as:

- an integer or floating-point numerical literal

- a char

- a string literal.

- a Boolean value true or false

- an enum value

- the name of a declared const field or local

- null

The expression must be a type that is convertible to the constant type,
with one exception: An expression whose type is Span <char > or
ReadOnlySpan <char > can be matched against constant strings in C  11
and later versions.

Use a constant pattern to check for null, as the following example
shows:

    if (input is null)

    {

    return;

    }

### Relational patterns:

Use any of the relational operators  <,  >,  <=, or  >= to compare an
expression result with a constant.

    Console.WriteLine(Classify(13)); // output: Too high

    Console.WriteLine(Classify(double.NaN)); // output: Unknown

    Console.WriteLine(Classify(2.4)); // output: Acceptable

    static string Classify(double measurement) = > measurement switch

    {

     < -4.0 = >  "Too low ",

    10.0 = >  "Too high ",

    double.NaN = >  "Unknown ",

     _ = >  "Acceptable ",

    };

In a relational pattern, The right-hand part of a relational pattern
must be a constant expression.

    Console.WriteLine(GetCalendarSeason(new DateTime(2021, 3, 14))); //
    output: spring

    Console.WriteLine(GetCalendarSeason(new DateTime(2021, 7, 19))); //
    output: summer

    Console.WriteLine(GetCalendarSeason(new DateTime(2021, 2, 17))); //
    output: winter

    static string GetCalendarSeason(DateTime date) = > date.Month switch

    {

     >= 3 and  < 6 = >  "spring ",

     >= 6 and  < 9 = >  "summer ",

     >= 9 and  < 12 = >  "autumn ",

    12 or ( >= 1 and  < 3) = >  "winter ",

     _ = > throw new ArgumentOutOfRangeException(nameof(date),  $ "Date with
    unexpected month: {date.Month}. "),

    };    

### **Conjunctive and pattern** that matches an expression when both patterns match the expression. 

    Console.WriteLine(Classify(13)); // output: High

    Console.WriteLine(Classify(-100)); // output: Too low

    Console.WriteLine(Classify(5.7)); // output: Acceptable

    static string Classify(double measurement) = > measurement switch

    {

     < -40.0 = >  "Too low ",

     >= -40.0 and  < 0 = >  "Low ",

     >= 0 and  < 10.0 = >  "Acceptable ",

     >= 10.0 and  < 20.0 = >  "High ",

     >= 20.0 = >  "Too high ",

    double.NaN = >  "Unknown ",

    };

Disjunctive or pattern that matches an expression when either pattern
matches the expression

    Console.WriteLine(GetCalendarSeason(new DateTime(2021, 1, 19))); //
    output: winter

    Console.WriteLine(GetCalendarSeason(new DateTime(2021, 10, 9))); //
    output: autumn

    Console.WriteLine(GetCalendarSeason(new DateTime(2021, 5, 11))); //
    output: spring

    static string GetCalendarSeason(DateTime date) = > date.Month switch

    {

    3 or 4 or 5 = >  "spring ",

    6 or 7 or 8 = >  "summer ",

    9 or 10 or 11 = >  "autumn ",

    12 or 1 or 2 = >  "winter ",

     _ = > throw new ArgumentOutOfRangeException(nameof(date),  $ "Date with
    unexpected month: {date.Month}. "),

    };

### Precedence and order of checking:

The following list orders pattern combinators starting from the highest
precedence to the lowest:

**not**

**and**

**or**

To explicitly specify the precedence, use parentheses, as the following
example shows:

    static bool IsLetter(char c) = > c is ( >=  'a ' and  <=  'z ') or ( >=
     'A ' and  <=  'Z ');

### Property pattern

You use a property pattern to match an expression 's properties or
fields against nested patterns.

    static bool IsConferenceDay(DateTime date) = > date is { Year: 2020,
    Month: 5, Day: 19 or 20 or 21 };

### Positional pattern:

Use to deconstruct an expression result and match the resulting values
against the subsequent nested patterns.

    public readonly struct Point

    {

    public int X { get; }

    public int Y { get; }

    public Point(int x, int y) = > (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) = > (x, y) = (X, Y);

    }

    static string Classify(Point point) = > point switch

    {

    (0, 0) = >  "Origin ",

    (1, 0) = >  "positive X basis end ",

    (0, 1) = >  "positive Y basis end ",

     _ = >  "Just a point ",

    };

You can also match expressions of tuple types against positional
pattern.

    static decimal GetGroupTicketPriceDiscount(int groupSize, DateTime
    visitDate)

    (groupSize, visitDate.DayOfWeek) switch

    {

    ( <= 0,  _) = > throw new ArgumentException( "Group size must be
    positive. "),

    ( _, DayOfWeek.Saturday or DayOfWeek.Sunday) = > 0.0m,

    ( >= 5 and  < 10, DayOfWeek.Monday) = > 20.0m,

    ( >= 10, DayOfWeek.Monday) = > 30.0m,

    ( >= 5 and  < 10,  _) = > 12.0m,

    ( >= 10,  _) = > 15.0m,

     _ = > 0.0m,

    };

### var pattern:

You use a var pattern to match any expression, including null, and
assign its result to a new local variable.
    static bool IsAcceptable(int id, int absLimit) = >

    SimulateDataFetch(id) is var results

    && results.Min()  >= -absLimit

    && results.Max()  <= absLimit;

    static int [ ] SimulateDataFetch(int id)

    {

    var rand = new Random();

    return Enumerable

    .Range(start: 0, count: 5)

    .Select(s = > rand.Next(minValue: -10, maxValue: 11))

    .ToArray();

    }

You can use a temporary variable within a Boolean expression or for a
switch expression or statement.

    public record Point(int X, int Y);

    static Point Transform(Point point) = > point switch

    {

    var (x, y) when x  < y = > new Point(-x, y),

    var (x, y) when x  > y = > new Point(x, -y),

    var (x, y) = > new Point(x, y),

    };

    static void TestTransform()

    {

    Console.WriteLine(Transform(new Point(1, 2))); // output: Point { X =
    -1, Y = 2 }

    Console.WriteLine(Transform(new Point(5, 2))); // output: Point { X = 5,
    Y = -2 }

    }

### Discard pattern:

You use a discard pattern  _ to match any expression, including null,
and any integer value handles all possible input values.

    Console.WriteLine(GetDiscountInPercent(DayOfWeek.Friday)); // output:
    5.0

    Console.WriteLine(GetDiscountInPercent(null)); // output: 0.0

    Console.WriteLine(GetDiscountInPercent((DayOfWeek)10)); // output: 0.0

    static decimal GetDiscountInPercent(DayOfWeek? dayOfWeek) = > dayOfWeek
    switch

    {

    DayOfWeek.Monday = > 0.5m,

    DayOfWeek.Tuesday = > 12.5m,

    DayOfWeek.Wednesday = > 7.5m,

    DayOfWeek.Thursday = > 12.5m,

    DayOfWeek.Friday = > 5.0m,

    DayOfWeek.Saturday = > 2.5m,

    DayOfWeek.Sunday = > 2.0m,

     _ = > 0.0m,

    };

### Parenthesized pattern:

you can put parentheses to emphasize or change the precedence in logical
patterns.

    if (input is not (float or double))

    {

    return;

    }

### List patterns:

You can match an array or a list against a sequence of patterns.

    int [ ] numbers = { 1, 2, 3 };

    Console.WriteLine(numbers is  [1, 2, 3 ]); // True

    Console.WriteLine(numbers is  [1, 2, 4 ]); // False

    Console.WriteLine(numbers is  [1, 2, 3, 4 ]); // False

    Console.WriteLine(numbers is  [0 or 1,  <= 2,  >= 3 ]); // True

To match any element, use the discard pattern or, if you also want to
capture the element, the var pattern.

    List <int > numbers = new() { 1, 2, 3 };

    if (numbers is  [var first,  _,  _ ])

    {

    Console.WriteLine( $ "The first element of a three-item list is
    {first}. ");

    }

    // Output:

    // The first element of a three-item list is 1.     

The preceding examples match a whole input sequence against a list
pattern. To match elements only at the start or/and the end of an input
sequence, use the slice pattern .. within a list pattern, as the
following example shows:

    Console.WriteLine(new [ ] { 1, 2, 3, 4, 5 } is  [ > 0,  > 0,
    .. ]); // True

    Console.WriteLine(new [ ] { 1, 1 } is  [ _,  _, .. ]); // True

    Console.WriteLine(new [ ] { 0, 1, 2, 3, 4 } is  [ > 0,  > 0, .. ]); //
    False

    Console.WriteLine(new [ ] { 1 } is  [1, 2, .. ]); // False

    Console.WriteLine(new [ ] { 1, 2, 3, 4 } is  [..,  > 0,  > 0 ]); // True

    Console.WriteLine(new [ ] { 2, 4 } is  [..,  > 0, 2, 4 ]); // False

    Console.WriteLine(new [ ] { 2, 4 } is  [.., 2, 4 ]); // True

    Console.WriteLine(new [ ] { 1, 2, 3, 4 } is  [ >= 0, .., 2 or 4 ]); //
    True

    Console.WriteLine(new [ ] { 1, 0, 0, 1 } is  [1, 0, .., 0, 1 ]); // True

    Console.WriteLine(new [ ] { 1, 0, 1 } is  [1, 0, .., 0, 1 ]); // False 

You can also nest a subpattern within a slice pattern. 

    void MatchMessage(string message)

    {

    var result = message is  [ 'a ' or  'A ', .. var s,  'a ' or  'A ' ]

    ?  $ "Message {message} matches; inner part is {s}. "

    :  $ "Message {message} doesn 't match. ";

    Console.WriteLine(result);

    }

    MatchMessage( "aBBA "); // output: Message aBBA matches; inner part is
    BB.

    MatchMessage( "apron "); // output: Message apron doesn 't match.

    void Validate(int [ ] numbers)

    {

    var result = numbers is  [ < 0, .. { Length: 2 or 4 },  > 0 ] ?
     "valid " :  "not valid ";

    Console.WriteLine(result);

    }

    Validate(new [ ] { -1, 0, 1 }); // output: not valid

    Validate(new [ ] { -1, 0, 0, 1 }); // output: valid

### String concatenation:

When one or both operands are of type string, the + operator
concatenates the string representations.

    Console.WriteLine( "Forgot " +  "white space ");

    Console.WriteLine( "Probably the oldest constant:  " + Math.PI);

### Delegate combination:

For operands of the same delegate type, the + operator returns a new
delegate instance.

    Action a = () = > Console.Write( "a ");

    Action b = () = > Console.Write( "b ");

    Action ab = a + b;

    ab(); // output: ab    

### + and += operators:

The + and += operators are supported by the built-in integral and
floating-point numeric types, the string type, and delegate types. To
combine delegates, use the + operator.

    let a = 2;

    let b =  'hello ';

    console.log(a += 3); // addition

    // expected output: 5

    console.log(b +=  ' world '); // concatenation

    // expected output:  "hello world "

### async function expression:

The async function keywords can be used to define an async function
inside an expression.

    async function (param0) {

    statements

    }

    async function (param0, param1) {

    statements

    }

    async function (param0, param1, / * ... , */ paramN) {

    statements

    }

    async function name(param0) {

    statements

    }

    async function name(param0, param1) {

    statements

    }

    async function name(param0, param1, / * ... , */ paramN) {

    statements

    }

### Bitwise AND assignment (&=):

It uses the binary representation of both operands.

    let a = 5;

    a &= 2; // 0    

### Bitwise OR assignment ( |=):

It uses the binary representation of both operands, does a bitwise OR
operation on them and assigns the result to the variable.

    let a = 5;

    a  |= 3

    console.log(a);

### Logical OR ( | |):

It is typically used with boolean (logical) values or a set of operands
is true if and only if one or more of its operands is true.

    const a = 3;

    const b = -2;

    console.log(a  > 0  | | b  > 0);

### Multiplication assignment ( *=):

### The multiplication assignment ( *=) operator multiplies a variable by the value of the right operand and assigns the result to the variable.

    let a = 2;

    console.log(a  *= 3);

    // expected output: 6

    console.log(a  *=  'hello ');    

### Optional chaining (?.):

It accesses an object 's property or calls a function. If the object is
undefined or null, it returns undefined instead of throwing an error.

    const adventurer = {

    name:  'Alice ',

    cat: {

    name:  'Dinah '

    }

    };

    const dogName = adventurer.dog?.name;

    console.log(dogName);

    // expected output: undefined

    console.log(adventurer.someNonExistentMethod?.());

### Remainder (%):

### It returns the remainder left over when one operand is divided by a second operand. It always takes the sign of the dividend.

    console.log(13 % 5);

    // expected output: 3

    console.log(-13 % 5);

    // expected output: -3

    console.log(4 % 2);

    // expected output: 0

    console.log(-4 % 2);

    // expected output: -0

### Nullish coalescing assignment (??=):

### The nullish coalescing assignment (x ??= y) operator only assigns if x is nullish (null or undefined).

    const a = { duration: 50 };

    a.duration ??= 10;

    console.log(a.duration);

    // expected output: 50

    a.speed ??= 25;

    console.log(a.speed);

    // expected output: 25

### Multiplication assignment ( *=):

It multiplies a variable by the value of the right operand and assigns
the result to the variable.

    let a = 2;

    console.log(a  *= 3);

    // expected output: 6

    console.log(a  *=  'hello ');

    // expected output: NaN

### Subtraction assignment (-=):

It subtracts the value of the right operand from a variable and assigns
the result to the variable.

    let a = 2;

    console.log(a -= 3);

    // expected output: -1

    console.log(a -=  'Hello ');

    // expected output: NaN    

### Delegate removal:

For operands of the same delegate type, the - operator returns a
delegate instance that is calculated as follows:

### non-null operands

**?? and ??= operators:**

- The ?? operator doesn 't evaluate its right-hand operand if the left-hand operand evaluates to non-null. 

- The ??= operator doesn 't evaluate its right-hand operand if the left-hand operand evaluates to non-null. 

    List <int > numbers = null;

    int? a = null;

    (numbers ??= new List <int >()).Add(5);

    Console.WriteLine(string.Join( "  ", numbers)); // output: 5

    numbers.Add(a ??= 0);

    Console.WriteLine(string.Join( "  ", numbers)); // output: 5 0

    Console.WriteLine(a); // output: 0

#### Case2:

If the right-hand operand 's list matches multiple contiguous sublists
in the left-hand operand 's list, only the right-most matching sublist
is removed. If removal results in an empty list, the result is null.

    Action a = () = > Console.Write( "a ");

    Action b = () = > Console.Write( "b ");

    var abbaab = a + b + b + a + a + b;

    abbaab(); // output: abbaab

    Console.WriteLine();

    var ab = a + b;

    var abba = abbaab - ab;

    abba(); // output: abba

    Console.WriteLine();

    var nihil = abbaab - abbaab;

    Console.WriteLine(nihil is null); // output: True

#### Case3:

If the invocation list of the right-hand operand is not a proper
contiguous sublist of the invocation list of the left-hand operand, the
result of the operation is the left-hand operand.

    Action a = () = > Console.Write( "a ");

    Action b = () = > Console.Write( "b ");

    var abbaab = a + b + b + a + a + b;

    var aba = a + b + a;

    var first = abbaab - aba;

    first(); // output: abbaab

    Console.WriteLine();

    Console.WriteLine(object.ReferenceEquals(abbaab, first)); // output:
    True

    Action a2 = () = > Console.Write( "a ");

    var changed = aba - a;

    changed(); // output: ab

    Console.WriteLine();

    var unchanged = aba - a2;

    unchanged(); // output: aba

    Console.WriteLine();

    Console.WriteLine(object.ReferenceEquals(aba, unchanged)); // output:
    True

#### Case4:

If the left-hand operand is null, the result of the operation is null.
If the right-hand operand is null, the result of the operation is the
left-hand operand.

    Action a = () = > Console.Write( "a ");

    var nothing = null - a;

    Console.WriteLine(nothing is null); // output: True

    var first = a - null;

    a(); // output: a

    Console.WriteLine();

    Console.WriteLine(object.ReferenceEquals(first, a)); // output: True

### Operator overloadability:

A user-defined type can overload the -- operator but cannot explicitly
overload the -= operator.

### ?: operator:

The conditional operator ?:, also known as the ternary conditional
operator, evaluates a Boolean expression

    string GetWeatherDisplay(double tempInCelsius) = > tempInCelsius
     < 20.0 ?  "Cold. " :  "Perfect! ";

    Console.WriteLine(GetWeatherDisplay(15)); // output: Cold.
    
    Console.WriteLine(GetWeatherDisplay(27)); // output: Perfect!     

### ! (null-forgiving) operator:

The unary postfix ! operator is used to declare that expression isn 't
null: x!. Ithas no effect at run time

     nullable enable

    public class Person

    {

    public Person(string name) = > Name = name ?? throw new
    ArgumentNullException(nameof(name));

    public string Name { get; }

    }

Using the MSTest test framework, you can create the following test for
the validation logic in the constructor:

      [TestMethod, ExpectedException(typeof(ArgumentNullException)) ]

    public void NullNameShouldThrowTest()

    {

    var person = new Person(null!);

    }    

### operator:

The = > token is supported in two forms: as the lambda operator and as a
separator of a member name

### Lambda operator:

The lambda operator = > separates the input parameters on the left side
from the right side.

    string [ ] words = {  "bot ",  "apple ",  "apricot " };

    int minimalLength = words

    .Where(w = > w.StartsWith( "a "))

    .Min(w = > w.Length);

    Console.WriteLine(minimalLength); // output: 5

    int [ ] numbers = { 4, 7, 10 };

    int product = numbers.Aggregate(1, (interim, next) = > interim  * next);

    Console.WriteLine(product); // output: 280

### Expression body definition:

The return type of expression must be implicitly convertible to the
member 's return type. If the member:

    member = > expression;

Expression must be a statement expression, the return type of that
expression can be any type.

    public override string ToString() = >  $ "{fname} {lname} ".Trim();

**:: operator:**

Use the namespace alias qualifier :: to access a member of an aliased
namespace. You can use the :: qualifier only between two identifiers.

    using forwinforms = System.Drawing;

    using forwpf = System.Windows;

    public class Converters

    {

    public static forwpf::Point Convert(forwinforms::Point point) = > new
    forwpf::Point(point.X, point.Y);

    }

### await operator:

It suspends evaluation of the enclosing async method until the
asynchronous operation is complete.

    using System;

    using System.Net.Http;

    using System.Threading.Tasks;

    public class AwaitOperator

    {

    public static async Task Main()

    {

    Task <int > downloading = DownloadDocsMainPageAsync();

    Console.WriteLine( $ "{nameof(Main)}: Launched downloading. ");

    int bytesLoaded = await downloading;

    Console.WriteLine( $ "{nameof(Main)}: Downloaded {bytesLoaded}
    bytes. ");

    }

    private static async Task <int > DownloadDocsMainPageAsync()

    {

    Console.WriteLine( $ "{nameof(DownloadDocsMainPageAsync)}: About to
    start downloading. ");

    var client = new HttpClient();

    byte [ ] content = await
    client.GetByteArrayAsync( "https://docs.microsoft.com/en-us/ ");

    Console.WriteLine( $ "{nameof(DownloadDocsMainPageAsync)}: Finished
    downloading. ");

    return content.Length;

    }

    }

    // Output similar to:

    // DownloadDocsMainPageAsync: About to start downloading.

    // Main: Launched downloading.

    // DownloadDocsMainPageAsync: Finished downloading.

    // Main: Downloaded 27700 bytes.

### default value expressions:

There are two kinds of default value expressions: the default operator
call and a default literal.

### default operator:

The argument to the default operator must be the name of a type or a
type parameter.

    Console.WriteLine(default(int)); // output: 0

    Console.WriteLine(default(object) is null); // output: True

    void DisplayDefaultOf <T >()

    {

    var val = default(T);

    Console.WriteLine( $ "Default value of {typeof(T)} is {(val == null ?
     "null " : val.ToString())}. ");

    }

    DisplayDefaultOf <int? >();

    DisplayDefaultOf <System.Numerics.Complex >();

    DisplayDefaultOf <System.Collections.Generic.List <int > >();

    // Output:

    // Default value of System.Nullable `1 [System.Int32 ] is null.

    // Default value of System.Numerics.Complex is (0, 0).

    // Default value of System.Collections.Generic.List `1 [System.Int32 ]
    is null.

### default literal:

It is used to produce the default value of a type when the compiler can
infer the expression type

    T [ ] InitializeArray <T >(int length, T initialValue = default)

    {

    if (length  < 0)

    {

    throw new ArgumentOutOfRangeException(nameof(length),  "Array length
    must be nonnegative. ");

    }

    var array = new T [length ];

    for (var i = 0; i  < length; i++)

    {

    array [i ] = initialValue;

    }

    return array;

    }

    void Display <T >(T [ ] values) = > Console.WriteLine( $ " [
    {string.Join( ",  ", values)}  ] ");

    Display(InitializeArray <int >(3)); // output:  [ 0, 0, 0  ]

    Display(InitializeArray <bool >(4, default)); // output:  [ False,
    False, False, False  ]

    System.Numerics.Complex fillValue = default;

    Display(InitializeArray(3, fillValue)); // output:  [ (0, 0), (0, 0),
    (0, 0)  ]

### is operator:

The is operator checks if the result of an expression is compatible with
a given type.

    static bool IsFirstFridayOfOctober(DateTime date) = >

    date is { Month: 10, Day:  <=7, DayOfWeek: DayOfWeek.Friday };    

### nameof expression:

You can use a nameof expression to make the argument-checking code more
maintainable:

    public string Name

    {

    get = > name;

    set = > name = value ?? throw new ArgumentNullException(nameof(value),
     $ "{nameof(Name)} cannot be null ");

    }     

### new operator:

You can use an object or collection initializer with the new operator to
instantiate and initialize an object in one statement.

    var dict = new Dictionary <string, int >

    {

     [ "first " ] = 10,

     [ "second " ] = 20,

     [ "third " ] = 30

    };

    Console.WriteLine(string.Join( ";  ", dict.Select(entry = >
     $ "{entry.Key}: {entry.Value} ")));

    // Output:

    // first: 10; second: 20; third: 30

### sizeof operator:

The argument to the sizeof operator must be the name of an unmanaged
type and it returns the number of bytes occupied by a variable.

### stackalloc expression:

A stackalloc expression allocates a block of memory on the stack and is
automatically discarded when that method returns.

    int length = 3;

    Span <int > numbers = stackalloc int [length ];

    for (var i = 0; i  < length; i++)

    {

    numbers [i ] = i;

    }

### switch expression:

It is used to evaluate a single expression from a list of candidate
expressions based on a pattern match with an input expression

    public static class SwitchExample

    {

    public enum Direction

    {

    Up,

    Down,

    Right,

    Left

    }

    public enum Orientation

    {

    North,

    South,

    East,

    West

    }

    public static Orientation ToOrientation(Direction direction) = >
    direction switch

    {

    Direction.Up = > Orientation.North,

    Direction.Right = > Orientation.East,

    Direction.Down = > Orientation.South,

    Direction.Left = > Orientation.West,

     _ = > throw new ArgumentOutOfRangeException(nameof(direction),  $ "Not
    expected direction value: {direction} "),

    };

    public static void Main()

    {

    var direction = Direction.Right;

    Console.WriteLine( $ "Map view direction is {direction} ");

    Console.WriteLine( $ "Cardinal orientation is
    {ToOrientation(direction)} ");

    // Output:

    // Map view direction is Right

    // Cardinal orientation is East

    }

    }

### true and false operators:

Use the bool? type, if you need to support the three-valued logic. The
true and false operators are not guaranteed to complement each other.

### with expression:

A left-hand operand of a with expression must be of a record type.

    using System;

    public class InheritanceExample

    {

    public record Point(int X, int Y);

    public record NamedPoint(string Name, int X, int Y) : Point(X, Y);

    public static void Main()

    {

    Point p1 = new NamedPoint( "A ", 0, 0);

    Point p2 = p1 with { X = 5, Y = 3 };

    Console.WriteLine(p2 is NamedPoint); // output: True

    Console.WriteLine(p2); // output: NamedPoint { X = 5, Y = 3, Name = A }

    }

    }

### scoped ref:

The scoped modifier restricts the ref-safe-to-escape or safe-to-escape
lifetime, asserts that your code won 't extend the lifetime of the
variable.

### Iteration statements:

The following statements repeatedly execute a statement or a block of
statements:

- The **for** statement executes its body while a specified Boolean
expression evaluates to true.

- The **foreach** statement enumerates the elements of a collection and
executes its body for each element of the collection.

- The **do** statement conditionally executes its body one or more times.

- The **while** statement conditionally executes its body zero or more
times.

- The **break** statement to break out of the loop.

- The **continue** statement to step to the next iteration in the loop.

### for statement:

It executes a statement or a block of statements while a specified
Boolean expression evaluates to true.

    for (int i = 0; i  < 3; i++)

    {

    Console.Write(i);

    }

    // Output:

    // 012

### foreach statement:

It executes a statement or a block of statements for each element in an
instance of the type that implements the System.Collections.IEnumerable
or System.Collections.Generic.IEnumerable <T > interface.

    var fibNumbers = new List <int > { 0, 1, 1, 2, 3, 5, 8, 13 };

    foreach (int element in fibNumbers)

    {

    Console.Write( $ "{element}  ");

    }

    // Output:

    // 0 1 1 2 3 5 8 13    

### await foreach:

You can use it to consume an asynchronous stream of data. Each iteration
of the loop may be suspended while the next element is retrieved
asynchronously.

    await foreach (var item in GenerateSequenceAsync())

    {

    Console.WriteLine(item);

    }

### Type of an iteration variable

You can use the var keyword to let the compiler infer the type of an
iteration variable in the foreach statement.

    foreach (var item in collection) { }

You can also explicitly specify the type of an iteration variable, as
the following code shows:

    

    IEnumerable <T > collection = new T [5 ];

 ### do statement:

A do loop executes one or more times. This differs from a while loop,
which executes zero or more times.

    int n = 0;

    do

    {

    Console.Write(n);

    n++;

    } while (n  < 5);

    // Output:

    // 01234

### try-finally statement:

You have a try-finally statement in which the only code in the finally
block is a call to the Dispose method, use a using statement instead.

    Font font1 = new Font( "Arial ", 10.0f);

    try

    {

    byte charset = font1.GdiCharSet;

    }

    finally

    {

    if (font1 != null)

    {

    ((IDisposable)font1).Dispose();

    }

    }

You can do the same thing with a **using** statement.

    using (Font font2 = new Font( "Arial ", 10.0f))

    {

    byte charset2 = font2.GdiCharSet;

    }

Use the **new** using syntax that doesn 't require braces:

    using Font font3 = new Font( "Arial ", 10.0f);

    byte charset3 = font3.GdiCharSet;

### while statement:

It executes a statement or a block of statements while a specified
Boolean expression evaluates to true and executes zero or more times.

    int n = 0;

    while (n  < 5)

    {

    Console.Write(n);

    n++;

    }

    // Output:

    // 01234

### Selection statements:

The following statements select statements to execute from a number of
possible statements based on the value of an expression:

- The **if statement:** selects a statement to execute based on the value
of a Boolean expression.

- The **switch statement**: selects a statement list to execute based on a
pattern match with an expression.

### if statement:

An if statement with an else part selects one of the two statements to
execute based on the value of a Boolean expression.

    DisplayWeatherReport(15.0); // Output: Cold.

    DisplayWeatherReport(24.0); // Output: Perfect!

    void DisplayWeatherReport(double tempInCelsius)

    {

    if (tempInCelsius  < 20.0)

    {

    Console.WriteLine( "Cold. ");

    }

    else

    {

    Console.WriteLine( "Perfect! ");

    }

    }    

### switch statement:

The switch statement selects a statement list to execute based on a
pattern match with a match expression.

    DisplayMeasurement(-4); // Output: Measured value is -4; too low.

    DisplayMeasurement(5); // Output: Measured value is 5.

    DisplayMeasurement(30); // Output: Measured value is 30; too high.

    DisplayMeasurement(double.NaN); // Output: Failed measurement.

    void DisplayMeasurement(double measurement)

    {

    switch (measurement)

    {

    case  < 0.0:

    Console.WriteLine( $ "Measured value is {measurement}; too low. ");

    break;

    case  > 15.0:

    Console.WriteLine( $ "Measured value is {measurement}; too high. ");

    break;

    case double.NaN:

    Console.WriteLine( "Failed measurement. ");

    break;

    default:

    Console.WriteLine( $ "Measured value is {measurement}. ");

    break;

    }

    }

### Jump statements:

#### The break statement:

It terminates the closest enclosing iteration statement (that is, for,
foreach, while, or do loop) or switch statement.

    int [ ] numbers = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };

    foreach (int number in numbers)

    {

    if (number == 3)

    {

    break;

    }

    Console.Write( $ "{number}  ");

    }

    Console.WriteLine();

    Console.WriteLine( "End of the example. ");

    // Output:

    // 0 1 2

    // End of the example.

#### The continue statement:

It starts a new iteration of the closest enclosing iteration statement
(that is, for, foreach, while, or do loop).

    for (int i = 0; i  < 5; i++)

    {

    Console.Write( $ "Iteration {i}:  ");

    if (i  < 3)

    {

    Console.WriteLine( "skip ");

    continue;

    }

    Console.WriteLine( "done ");

    }

#### The return statement:

It terminates execution of the function in which it appears and returns
control and the function 's result, if any, to the caller.

    Console.WriteLine( "First call: ");

    DisplayIfNecessary(6);

    Console.WriteLine( "Second call: ");

    DisplayIfNecessary(5);

    void DisplayIfNecessary(int number)

    {

    if (number % 2 == 0)

    {

    return;

    }

    Console.WriteLine(number);

    }    

#### Ref returns:

It means that a method returns a reference (or an alias) to some
variable and it must include the method.

    public ref Person GetContactInformation(string fname, string lname)

    {

    //  ...method implementation ...

    return ref p;

    }

    using System;

    public enum CoffeChoice

    {

    Plain,

    WithMilk,

    WithIceCream,

    }

    public class GotoInSwitchExample

    {

    public static void Main()

    {

    Console.WriteLine(CalculatePrice(CoffeChoice.Plain)); // output: 10.0

    Console.WriteLine(CalculatePrice(CoffeChoice.WithMilk)); // output: 15.0

    Console.WriteLine(CalculatePrice(CoffeChoice.WithIceCream)); // output:
    17.0

    }

    private static decimal CalculatePrice(CoffeChoice choice)

    {

    decimal price = 0;

    switch (choice)

    {

    case CoffeChoice.Plain:

    price += 10.0m;

    break;

    case CoffeChoice.WithMilk:

    price += 5.0m;

    goto case CoffeChoice.Plain;

    case CoffeChoice.WithIceCream:

    price += 7.0m;

    goto case CoffeChoice.Plain;

    }

    return price;

    }

    }

#### goto statement:

Within the switch statement, you can also use the statement goto
default; to transfer control to the switch section with the default
label.

### checked and unchecked statements:

The checked and unchecked statements specify the overflow-checking
context for integral-type arithmetic operations and conversions.

    uint a = uint.MaxValue;

    nchecked

    {

    Console.WriteLine(a + 1); // output: 0

    }

    try

    {

    checked

    {

    Console.WriteLine(a + 1);

    }

    }

    catch (OverflowException e)

    {

    Console.WriteLine(e.Message); // output: Arithmetic operation resulted
    in an overflow.

    }

In a checked context, a System.OverflowException is thrown; if overflow
happens in a constant expression, a compile-time error occurs.

In an unchecked context, the operation result is truncated by discarding
any high-order bits that don 't fit in the destination type

### fixed statement:

It prevents the garbage collector from relocating a moveable variable
and declares a pointer to that variable:

    unsafe

    {

    byte [ ] bytes = { 1, 2, 3 };

    fixed (byte * pointerToFirst = bytes)

    {

    Console.WriteLine( $ "The address of the first array element:
    {(long)pointerToFirst:X}. ");

    Console.WriteLine( $ "The value of the first array element:
    { *pointerToFirst}. ");

    }

    }

### lock statement:

It acquires the mutual-exclusion lock for a given object, executes a
statement block, and then releases the lock.

    lock (x)

    {

    // Your code ...

    }

### yield statement:

You use the yield statement in an iterator in two following forms:

**yield return:** to provide the next value in iteration, as the
following example shows:

    foreach (int i in ProduceEvenNumbers(9))

    {

    Console.Write(i);

    Console.Write( "  ");

    }

    // Output: 0 2 4 6 8

    IEnumerable <int > ProduceEvenNumbers(int upto)

    {

    for (int i = 0; i  <= upto; i += 2)

    {

    yield return i;

    }

    }

###  $ - string interpolation:

When an interpolated string is resolved to a result string, items with
interpolation expressions are replaced by the string representations of
the expression results.

    string name =  "Mark ";

    var date = DateTime.Now;

    // Composite formatting:

    Console.WriteLine( "Hello, {0}! Today is {1}, it 's {2:HH:mm} now. ",
    name, date.DayOfWeek, date);

    // String interpolation:

    Console.WriteLine( $ "Hello, {name}! Today is {date.DayOfWeek}, it 's
    {date:HH:mm} now. ");

    @ verbatim identifier:

    string [ ]  @for = {  "John ",  "James ",  "Joan ",  "Jamie " };

    for (int ctr = 0; ctr  <  @for.Length; ctr++)

    {

    Console.WriteLine( $ "Here is your gift, { @for [ctr ]}! ");

    }

### Assembly level attributes interpreted by the C  compiler

Most attributes are applied to specific language elements such as
classes or methods; however, some attributes are global---they apply to
an entire assembly or module.

     [assembly: AssemblyVersion( "1.0.0.0 ") ]

**Global attributes** appear in the source code after any top level
using directives and before any type, module, or namespace declarations
& can appear in multiple source files.

### Unsafe code, pointer types, and function pointers:

In an unsafe context, code may use pointers, allocate and free blocks of
memory, and call methods using function pointers.

### Pointer types:

Pointer types don 't inherit from object and no conversions exist
between pointer types and object. Also, boxing and unboxing don 't
support pointers.

    type * identifier;

    void * identifier; //allowed but not recommended

### Fixed-size buffers:

They are useful when you write methods that interoperate with data
sources from other languages or platforms & can take any attributes or
modifiers that are allowed for regular struct members.

    private fixed char name [30 ];

### preprocessor directives:

Although the compiler doesn 't have a separate preprocessor, the
directives described in this section are processed as if there were one.
You use them to help in conditional compilation.

### Nullable context:

his directive controls whether nullable annotations have effect, and
whether nullability warnings are given. Each context is either disabled
or enabled.

### Conditional compilation:

You use four preprocessor directives to control conditional compilation:

###  if:

Opens a conditional compilation, where code is compiled only if the
specified symbol is defined.

     if preprocessor-expression

    code to compile

     endif `

###  elif: 

Closes the preceding conditional compilation and opens a new conditional
compilation based on if the specified symbol is defined.

     if preprocessor-expression-1

    code to compile

     elif preprocessor-expression-2

    code to compile

     endif `

###  else: 

Closes the preceding conditional compilation and opens a new conditional
compilation if the previous specified symbol isn 't defined.

     if preprocessor-expression-1

    code to compile

     else

    code to compile    

###  endif: 

Closes the preceding conditional compilation.

     if preprocessor-expression

    code to compile

     endif `

### Defining symbols:

You use the following two preprocessor directives to define or undefine
symbols for conditional compilation:

     define SYMBOL

        

     define: Define a symbol.

###  warning:

Allows us to generate level 1 warning from our code

     warning warning-message    

###  error:

Allows us to generate error from our code

     error error-message

###  line:

Allows us to modify the compiler 's line number and filename to display
errors and warnings

     line line-number file-name

###  region:

Allows us to create a region that can be expanded or collapsed when
using a Visual Studio Code Edi

     region region-description

codes

     endregion

###  endregion 

Indicates the end of a region

     region region-description

    codes

     endregion

###  define directive:

The  define directive allows us to define a symbol that are defined
when used along with  if directive will evaluate to true.

     define SYMBOL

###  undef directive:

The  undef directive allows us to undefine a symbol when used along
with  if directive will evaluate to false.

     undef SYMBOL
