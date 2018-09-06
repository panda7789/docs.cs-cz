---
title: Příklady serializace XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML serialization, examples
- arrays, serializing
- ICollection interface, serializing
- XmlSerializer class, serializing
- serialization, examples
- DataSet class, serializing
- XML Schema, serializing
ms.assetid: eec46337-9696-435b-a375-dc5effae6992
ms.openlocfilehash: bd79008275f3c0176d8ffea9e5de3b53eae3ad2b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777948"
---
# <a name="examples-of-xml-serialization"></a><span data-ttu-id="ac46a-102">Příklady serializace XML</span><span class="sxs-lookup"><span data-stu-id="ac46a-102">Examples of XML Serialization</span></span>
<span data-ttu-id="ac46a-103">Serializace XML může trvat více než jeden formulář z snadno komplexní.</span><span class="sxs-lookup"><span data-stu-id="ac46a-103">XML serialization can take more than one form, from simple to complex.</span></span> <span data-ttu-id="ac46a-104">Například může serializovat třídu, která jednoduše se skládá z veřejných polí a vlastností, jak je znázorněno v [představení serializace XML](../../../docs/standard/serialization/introducing-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="ac46a-104">For example, you can serialize a class that simply consists of public fields and properties, as shown in [Introducing XML Serialization](../../../docs/standard/serialization/introducing-xml-serialization.md).</span></span> <span data-ttu-id="ac46a-105">Následující příklady kódu adresa různých pokročilé scénáře, včetně použití serializace XML ke generování datový proud XML, který odpovídá určitého dokumentu schématu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="ac46a-105">The following code examples address various advanced scenarios, including how to use XML serialization to generate an XML stream that conforms to a specific XML Schema (XSD) document.</span></span>  
  
## <a name="serializing-a-dataset"></a><span data-ttu-id="ac46a-106">Serializace na sadu dat</span><span class="sxs-lookup"><span data-stu-id="ac46a-106">Serializing a DataSet</span></span>  
 <span data-ttu-id="ac46a-107">Kromě serializaci instancí veřejnou třídu instance <xref:System.Data.DataSet> lze také serializovat, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="ac46a-107">Besides serializing an instance of a public class, an instance of a <xref:System.Data.DataSet> can also be serialized, as shown in the following code example.</span></span>  
  
```vb  
Private Sub SerializeDataSet(filename As String)  
    Dim ser As XmlSerializer = new XmlSerializer(GetType(DataSet))  
    ' Creates a DataSet; adds a table, column, and ten rows.  
    Dim ds As DataSet = new DataSet("myDataSet")  
    Dim t As DataTable = new DataTable("table1")  
    Dim c As DataColumn = new DataColumn("thing")  
    t.Columns.Add(c)  
    ds.Tables.Add(t)  
    Dim r As DataRow  
    Dim i As Integer  
    for i = 0 to 10  
        r = t.NewRow()  
        r(0) = "Thing " &  i  
        t.Rows.Add(r)  
    Next  
    Dim writer As TextWriter = new StreamWriter(filename)  
    ser.Serialize(writer, ds)  
    writer.Close()  
End Sub  
```  
  
```csharp  
private void SerializeDataSet(string filename){  
    XmlSerializer ser = new XmlSerializer(typeof(DataSet));  
  
    // Creates a DataSet; adds a table, column, and ten rows.  
    DataSet ds = new DataSet("myDataSet");  
    DataTable t = new DataTable("table1");  
    DataColumn c = new DataColumn("thing");  
    t.Columns.Add(c);  
    ds.Tables.Add(t);  
    DataRow r;  
    for(int i = 0; i<10;i++){  
        r = t.NewRow();  
        r[0] = "Thing " + i;  
        t.Rows.Add(r);  
    }  
    TextWriter writer = new StreamWriter(filename);  
    ser.Serialize(writer, ds);  
    writer.Close();  
}  
```  
  
## <a name="serializing-an-xmlelement-and-xmlnode"></a><span data-ttu-id="ac46a-108">Serializace XmlElement a XmlNode</span><span class="sxs-lookup"><span data-stu-id="ac46a-108">Serializing an XmlElement and XmlNode</span></span>  
 <span data-ttu-id="ac46a-109">Můžete také serializovat instance <xref:System.Xml.XmlElement> nebo <xref:System.Xml.XmlNode> třídy, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="ac46a-109">You can also serialize instances of a <xref:System.Xml.XmlElement> or <xref:System.Xml.XmlNode> class, as shown in the following code example.</span></span>  
  
```vb  
private Sub SerializeElement(filename As String)  
    Dim ser As XmlSerializer = new XmlSerializer(GetType(XmlElement))  
    Dim myElement As XmlElement = _  
    new XmlDocument().CreateElement("MyElement", "ns")  
    myElement.InnerText = "Hello World"  
    Dim writer As TextWriter = new StreamWriter(filename)  
    ser.Serialize(writer, myElement)  
    writer.Close()  
End Sub  
  
Private Sub SerializeNode(filename As String)  
    Dim ser As XmlSerializer = _  
    new XmlSerializer(GetType(XmlNode))  
    Dim myNode As XmlNode = new XmlDocument(). _  
    CreateNode(XmlNodeType.Element, "MyNode", "ns")  
    myNode.InnerText = "Hello Node"  
    Dim writer As TextWriter = new StreamWriter(filename)  
    ser.Serialize(writer, myNode)  
    writer.Close()  
End Sub  
```  
  
```csharp  
private void SerializeElement(string filename){  
    XmlSerializer ser = new XmlSerializer(typeof(XmlElement));  
    XmlElement myElement=   
    new XmlDocument().CreateElement("MyElement", "ns");  
    myElement.InnerText = "Hello World";  
    TextWriter writer = new StreamWriter(filename);  
    ser.Serialize(writer, myElement);  
    writer.Close();  
}  
  
private void SerializeNode(string filename){  
    XmlSerializer ser = new XmlSerializer(typeof(XmlNode));  
    XmlNode myNode= new XmlDocument().  
    CreateNode(XmlNodeType.Element, "MyNode", "ns");  
    myNode.InnerText = "Hello Node";  
    TextWriter writer = new StreamWriter(filename);  
    ser.Serialize(writer, myNode);  
    writer.Close();  
}  
```  
  
## <a name="serializing-a-class-that-contains-a-field-returning-a-complex-object"></a><span data-ttu-id="ac46a-110">Serializace třídu, která obsahuje pole vrácení komplexního objektu</span><span class="sxs-lookup"><span data-stu-id="ac46a-110">Serializing a Class that Contains a Field Returning a Complex Object</span></span>  
 <span data-ttu-id="ac46a-111">Pokud vlastnost nebo pole vrátí komplexního objektu (například pole nebo instanci třídy), [XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx) převede ho na prvek vnořené hlavní dokument XML.</span><span class="sxs-lookup"><span data-stu-id="ac46a-111">If a property or field returns a complex object (such as an array or a class instance), the [XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx) converts it to an element nested within the main XML document.</span></span> <span data-ttu-id="ac46a-112">Můžete například první třídou v následujícím příkladu vrací instanci třídy sekundu.</span><span class="sxs-lookup"><span data-stu-id="ac46a-112">For example, the first class in the following code example returns an instance of the second class.</span></span>  
  
```vb  
Public Class PurchaseOrder  
    Public MyAdress As Address  
End Class  
  
Public Class Address  
    Public FirstName As String  
End Class  
```  
  
```csharp  
public class PurchaseOrder  
{  
    public Address MyAddress;  
}  
public class Address  
{  
    public string FirstName;  
}  
```  
  
 <span data-ttu-id="ac46a-113">Serializovaná výstupu XML může vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="ac46a-113">The serialized XML output might resemble the following.</span></span>  
  
```xml  
<PurchaseOrder>  
    <Address>  
        <FirstName>George</FirstName>  
    </Address>  
</PurchaseOrder>  
```  
  
## <a name="serializing-an-array-of-objects"></a><span data-ttu-id="ac46a-114">Serializace pole objektů</span><span class="sxs-lookup"><span data-stu-id="ac46a-114">Serializing an Array of Objects</span></span>  
 <span data-ttu-id="ac46a-115">Můžete také serializovat pole, které vrací pole objektů, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="ac46a-115">You can also serialize a field that returns an array of objects, as shown in the following code example.</span></span>  
  
```vb  
Public Class PurchaseOrder  
    public ItemsOrders () As Item  
End Class  
  
Public Class Item  
    Public ItemID As String  
    Public ItemPrice As decimal  
End Class  
```  
  
```csharp  
public class PurchaseOrder  
{  
    public Item [] ItemsOrders  
}  
  
public class Item  
{  
    public string ItemID  
    public decimal ItemPrice  
}  
```  
  
 <span data-ttu-id="ac46a-116">Instance třídy serializovaná může vypadat podobně, pokud jsou řazeny dvě položky.</span><span class="sxs-lookup"><span data-stu-id="ac46a-116">The serialized class instance might resemble the following, if two items are ordered.</span></span>  
  
```xml  
<PurchaseOrder xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <Items>  
        <Item>  
            <ItemID>aaa111</ItemID>  
            <ItemPrice>34.22</ItemPrice>  
        <Item>  
        <Item>  
            <ItemID>bbb222</ItemID>  
            <ItemPrice>2.89</ItemPrice>  
        <Item>  
    </Items>  
</PurchaseOrder>  
```  
  
## <a name="serializing-a-class-that-implements-the-icollection-interface"></a><span data-ttu-id="ac46a-117">Serializace třídu tohoto implementuje rozhraní ICollection</span><span class="sxs-lookup"><span data-stu-id="ac46a-117">Serializing a Class that Implements the ICollection Interface</span></span>  
 <span data-ttu-id="ac46a-118">Můžete vytvořit vlastní třídy kolekce implementující <xref:System.Collections.ICollection> rozhraní a používat <xref:System.Xml.Serialization.XmlSerializer> k serializaci instance těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="ac46a-118">You can create your own collection classes by implementing the <xref:System.Collections.ICollection> interface, and use the <xref:System.Xml.Serialization.XmlSerializer> to serialize instances of these classes.</span></span> <span data-ttu-id="ac46a-119">Všimněte si, že při implementuje třídu <xref:System.Collections.ICollection> rozhraní, pouze kolekce obsažené třídou je serializována.</span><span class="sxs-lookup"><span data-stu-id="ac46a-119">Note that when a class implements the <xref:System.Collections.ICollection> interface, only the collection contained by the class is serialized.</span></span> <span data-ttu-id="ac46a-120">Všechny veřejné vlastnosti nebo pole přidán do třídy nesmí být serializován.</span><span class="sxs-lookup"><span data-stu-id="ac46a-120">Any public properties or fields added to the class will not be serialized.</span></span> <span data-ttu-id="ac46a-121">Třída musí obsahovat **přidat** metoda a **položky** vlastnost (indexeru C#) k serializaci.</span><span class="sxs-lookup"><span data-stu-id="ac46a-121">The class must include an **Add** method and an **Item** property (C# indexer) to be serialized.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Collections  
Imports System.Xml.Serialization  
  
Public Class Test  
    Shared Sub Main()  
        Dim t As Test= new Test()  
        t.SerializeCollection("coll.xml")  
    End Sub  
  
    Private Sub SerializeCollection(filename As String)  
        Dim Emps As Employees  = new Employees()  
        ' Note that only the collection is serialized -- not the   
        ' CollectionName or any other public property of the class.  
        Emps.CollectionName = "Employees"  
        Dim John100 As Employee = new Employee("John", "100xxx")  
        Emps.Add(John100)  
        Dim x As XmlSerializer = new XmlSerializer(GetType(Employees))  
        Dim writer As TextWriter = new StreamWriter(filename)  
        x.Serialize(writer, Emps)  
        writer.Close()  
    End Sub  
End Class  
  
Public Class Employees  
    Implements ICollection  
    Public CollectionName As String   
    Private empArray As ArrayList = new ArrayList()   
  
    Public ReadOnly Default Overloads _  
    Property Item(index As Integer) As Employee  
        get  
        return CType (empArray(index), Employee)  
        End Get  
    End Property  
  
    Public Sub CopyTo(a As Array, index As Integer) _  
    Implements ICollection.CopyTo  
        empArray.CopyTo(a, index)  
    End Sub  
  
    Public ReadOnly Property Count () As integer Implements _  
    ICollection.Count  
        get   
            Count = empArray.Count  
        End Get  
  
    End Property  
  
    Public ReadOnly Property SyncRoot ()As Object _  
    Implements ICollection.SyncRoot  
        get  
        return me  
        End Get  
    End Property  
  
    Public ReadOnly Property IsSynchronized () As Boolean _  
    Implements ICollection.IsSynchronized  
        get   
        return false  
        End Get  
    End Property  
  
    Public Function GetEnumerator() As IEnumerator _  
    Implements IEnumerable.GetEnumerator  
  
        return empArray.GetEnumerator()  
    End Function   
  
    Public Function Add(newEmployee As Employee) As Integer  
        empArray.Add(newEmployee)  
        return empArray.Count  
    End Function  
End Class  
  
Public Class Employee  
    Public EmpName As String   
    Public EmpID As String   
  
    Public Sub New ()  
    End Sub  
  
    Public Sub New (newName As String , newID As String )   
        EmpName = newName  
        EmpID = newID  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Collections;  
using System.Xml.Serialization;  
  
public class Test {  
    static void Main(){  
        Test t = new Test();  
        t.SerializeCollection("coll.xml");  
    }  
  
    private void SerializeCollection(string filename){  
        Employees Emps = new Employees();  
        // Note that only the collection is serialized -- not the   
        // CollectionName or any other public property of the class.  
        Emps.CollectionName = "Employees";  
        Employee John100 = new Employee("John", "100xxx");  
        Emps.Add(John100);  
        XmlSerializer x = new XmlSerializer(typeof(Employees));  
        TextWriter writer = new StreamWriter(filename);  
        x.Serialize(writer, Emps);  
    }  
}  
public class Employees:ICollection {  
    public string CollectionName;  
    private ArrayList empArray = new ArrayList();   
  
    public Employee this[int index]{  
        get{return (Employee) empArray[index];}  
    }  
  
    public void CopyTo(Array a, int index){  
        empArray.CopyTo(a, index);  
    }  
    public int Count{  
        get{return empArray.Count;}  
    }  
    public object SyncRoot{  
        get{return this;}  
    }  
    public bool IsSynchronized{  
        get{return false;}  
    }  
    public IEnumerator GetEnumerator(){  
        return empArray.GetEnumerator();  
    }  
  
    public void Add(Employee newEmployee){  
        empArray.Add(newEmployee);  
    }  
}  
  
public class Employee {  
    public string EmpName;  
    public string EmpID;  
    public Employee(){}  
    public Employee(string empName, string empID){  
        EmpName = empName;  
        EmpID = empID;  
    }  
}  
```  
  
## <a name="purchase-order-example"></a><span data-ttu-id="ac46a-122">Příklad pořadí nákupu</span><span class="sxs-lookup"><span data-stu-id="ac46a-122">Purchase Order Example</span></span>  
 <span data-ttu-id="ac46a-123">Můžete vyjmout a vložit následující příklad kódu do textového souboru přejmenován s cs nebo VB příponu názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="ac46a-123">You can cut and paste the following example code into a text file renamed with a .cs or .vb file name extension.</span></span> <span data-ttu-id="ac46a-124">Použijte kompilátor jazyka C# nebo Visual Basic pro kompilaci souboru.</span><span class="sxs-lookup"><span data-stu-id="ac46a-124">Use the C# or Visual Basic compiler to compile the file.</span></span> <span data-ttu-id="ac46a-125">Spusťte ji pomocí názvu spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="ac46a-125">Then run it using the name of the executable.</span></span>  
  
 <span data-ttu-id="ac46a-126">V tomto příkladu je jednoduché scénáře k předvedení jak instance objektu je vytvořena a serializován do souboru pomocí datového proudu <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ac46a-126">This example uses a simple scenario to demonstrate how an instance of an object is created and serialized into a file stream using the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method.</span></span> <span data-ttu-id="ac46a-127">Datový proud XML je uložen na soubor a stejný soubor je poté číst zpět a znovu vytvořena do kopii původní objekt pomocí <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ac46a-127">The XML stream is saved to a file, and the same file is then read back and reconstructed into a copy of the original object using the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> method.</span></span>  
  
 <span data-ttu-id="ac46a-128">V tomto příkladu třída s názvem `PurchaseOrder` je serializaci a potom deserializaci.</span><span class="sxs-lookup"><span data-stu-id="ac46a-128">In this example, a class named `PurchaseOrder` is serialized and then deserialized.</span></span> <span data-ttu-id="ac46a-129">Druhé třídu s názvem `Address` je rovněž obsažena, protože veřejné pole s názvem `ShipTo` musí být nastavena na `Address`.</span><span class="sxs-lookup"><span data-stu-id="ac46a-129">A second class named `Address` is also included because the public field named `ShipTo` must be set to an `Address`.</span></span> <span data-ttu-id="ac46a-130">Podobně `OrderedItem` třída je zahrnuta, protože pole `OrderedItem` objekty musí být nastaven na `OrderedItems` pole.</span><span class="sxs-lookup"><span data-stu-id="ac46a-130">Similarly, an `OrderedItem` class is included because an array of `OrderedItem` objects must be set to the `OrderedItems` field.</span></span> <span data-ttu-id="ac46a-131">Na závěr třída s názvem `Test` obsahuje kód, který serializuje a deserializuje třídy.</span><span class="sxs-lookup"><span data-stu-id="ac46a-131">Finally, a class named `Test` contains the code that serializes and deserializes the classes.</span></span>  
  
 <span data-ttu-id="ac46a-132">`CreatePO` Metoda vytvoří `PurchaseOrder`, `Address`, a `OrderedItem` objekty třídy a nastaví hodnoty veřejného polí.</span><span class="sxs-lookup"><span data-stu-id="ac46a-132">The `CreatePO` method creates the `PurchaseOrder`, `Address`, and `OrderedItem` class objects, and sets the public field values.</span></span> <span data-ttu-id="ac46a-133">Metoda také vytvoří instanci objektu <xref:System.Xml.Serialization.XmlSerializer> třídu, která se používá k serializaci a deserializaci `PurchaseOrder`.</span><span class="sxs-lookup"><span data-stu-id="ac46a-133">The method also constructs an instance of the <xref:System.Xml.Serialization.XmlSerializer> class that is used to serialize and deserialize the `PurchaseOrder`.</span></span> <span data-ttu-id="ac46a-134">Všimněte si, že kód předá konstruktoru typu třídy, která bude serializována.</span><span class="sxs-lookup"><span data-stu-id="ac46a-134">Note that the code passes the type of the class that will be serialized to the constructor.</span></span> <span data-ttu-id="ac46a-135">Kód vytvoří také `FileStream` , který se používá k zápisu do dokumentu XML datový proud XML.</span><span class="sxs-lookup"><span data-stu-id="ac46a-135">The code also creates a `FileStream` that is used to write the XML stream to an XML document.</span></span>  
  
 <span data-ttu-id="ac46a-136">`ReadPo` Metoda je o něco jednodušší.</span><span class="sxs-lookup"><span data-stu-id="ac46a-136">The `ReadPo` method is a little simpler.</span></span> <span data-ttu-id="ac46a-137">Stačí vytvoří objekty k deserializaci a přečte jejich hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ac46a-137">It just creates objects to deserialize and reads out their values.</span></span> <span data-ttu-id="ac46a-138">Stejně jako u `CreatePo` metody, je nutné nejprve vytvořit <xref:System.Xml.Serialization.XmlSerializer>, předejte typ třídy k deserializaci do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="ac46a-138">As with the `CreatePo` method, you must first construct a <xref:System.Xml.Serialization.XmlSerializer>, passing the type of the class to be deserialized to the constructor.</span></span> <span data-ttu-id="ac46a-139">Také <xref:System.IO.FileStream> je vyžadována pro čtení dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ac46a-139">Also, a <xref:System.IO.FileStream> is required to read the XML document.</span></span> <span data-ttu-id="ac46a-140">K deserializaci objektů, zavolejte <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> metodu se <xref:System.IO.FileStream> jako argument.</span><span class="sxs-lookup"><span data-stu-id="ac46a-140">To deserialize the objects, call the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> method with the <xref:System.IO.FileStream> as an argument.</span></span> <span data-ttu-id="ac46a-141">Deserializovaný objekt musí být přetypovat na proměnné objektu typu `PurchaseOrder`.</span><span class="sxs-lookup"><span data-stu-id="ac46a-141">The deserialized object must be cast to an object variable of type `PurchaseOrder`.</span></span> <span data-ttu-id="ac46a-142">Kód poté načte hodnoty deserializovat `PurchaseOrder`.</span><span class="sxs-lookup"><span data-stu-id="ac46a-142">The code then reads the values of the deserialized `PurchaseOrder`.</span></span> <span data-ttu-id="ac46a-143">Všimněte si, můžete si také přečíst soubor PO.xml, který je vytvořen zobrazíte skutečný XML výstupu.</span><span class="sxs-lookup"><span data-stu-id="ac46a-143">Note that you can also read the PO.xml file that is created to see the actual XML output.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Serialization  
Imports System.IO  
Imports Microsoft.VisualBasic  
  
' The XmlRoot attribute allows you to set an alternate name  
' (PurchaseOrder) for the XML element and its namespace. By  
' default, the XmlSerializer uses the class name. The attribute  
' also allows you to set the XML namespace for the element. Lastly,  
' the attribute sets the IsNullable property, which specifies whether  
' the xsi:null attribute appears if the class instance is set to  
' a null reference.   
<XmlRoot("PurchaseOrder", _  
 Namespace := "http://www.cpandl.com", IsNullable := False)> _  
Public Class PurchaseOrder  
    Public ShipTo As Address  
    Public OrderDate As String  
    ' The XmlArrayAttribute changes the XML element name  
    ' from the default of "OrderedItems" to "Items".   
    <XmlArray("Items")> _  
    Public OrderedItems() As OrderedItem  
    Public SubTotal As Decimal  
    Public ShipCost As Decimal  
    Public TotalCost As Decimal  
End Class   
  
Public Class Address  
    ' The XmlAttribute attribute instructs the XmlSerializer to serialize the   
    ' Name field as an XML attribute instead of an XML element (the   
    ' default behavior).   
    <XmlAttribute()> _  
    Public Name As String  
    Public Line1 As String  
  
    ' Setting the IsNullable property to false instructs the  
    ' XmlSerializer that the XML attribute will not appear if  
    ' the City field is set to a null reference.   
    <XmlElement(IsNullable := False)> _  
    Public City As String  
    Public State As String  
    Public Zip As String  
End Class   
  
Public Class OrderedItem  
    Public ItemName As String  
    Public Description As String  
    Public UnitPrice As Decimal  
    Public Quantity As Integer  
    Public LineTotal As Decimal  
  
    ' Calculate is a custom method that calculates the price per item  
    ' and stores the value in a field.   
    Public Sub Calculate()  
    LineTotal = UnitPrice * Quantity  
    End Sub   
End Class   
  
Public Class Test  
        Public Shared Sub Main()  
    ' Read and write purchase orders.  
    Dim t As New Test()  
    t.CreatePO("po.xml")  
    t.ReadPO("po.xml")  
    End Sub   
  
    Private Sub CreatePO(filename As String)  
        ' Creates an instance of the XmlSerializer class;  
        ' specifies the type of object to serialize.  
        Dim serializer As New XmlSerializer(GetType(PurchaseOrder))  
        Dim writer As New StreamWriter(filename)  
        Dim po As New PurchaseOrder()  
  
        ' Creates an address to ship and bill to.  
        Dim billAddress As New Address()  
        billAddress.Name = "Teresa Atkinson"  
        billAddress.Line1 = "1 Main St."  
        billAddress.City = "AnyTown"  
        billAddress.State = "WA"  
        billAddress.Zip = "00000"  
        ' Set ShipTo and BillTo to the same addressee.  
        po.ShipTo = billAddress  
        po.OrderDate = System.DateTime.Now.ToLongDateString()  
  
        ' Creates an OrderedItem.  
        Dim i1 As New OrderedItem()  
        i1.ItemName = "Widget S"  
        i1.Description = "Small widget"  
        i1.UnitPrice = CDec(5.23)  
        i1.Quantity = 3  
        i1.Calculate()  
  
        ' Inserts the item into the array.  
        Dim items(0) As OrderedItem  
        items(0) = i1  
        po.OrderedItems = items  
        ' Calculates the total cost.  
        Dim subTotal As New Decimal()  
        Dim oi As OrderedItem  
        For Each oi In  items  
            subTotal += oi.LineTotal  
        Next oi  
        po.SubTotal = subTotal  
        po.ShipCost = CDec(12.51)  
        po.TotalCost = po.SubTotal + po.ShipCost  
        ' Serializes the purchase order, and close the TextWriter.  
        serializer.Serialize(writer, po)  
        writer.Close()  
    End Sub   
  
    Protected Sub ReadPO(filename As String)  
        ' Creates an instance of the XmlSerializer class;  
        ' specifies the type of object to be deserialized.  
        Dim serializer As New XmlSerializer(GetType(PurchaseOrder))  
        ' If the XML document has been altered with unknown  
        ' nodes or attributes, handles them with the  
        ' UnknownNode and UnknownAttribute events.  
        AddHandler serializer.UnknownNode, AddressOf serializer_UnknownNode  
        AddHandler serializer.UnknownAttribute, AddressOf _  
        serializer_UnknownAttribute  
  
        ' A FileStream is needed to read the XML document.  
        Dim fs As New FileStream(filename, FileMode.Open)  
        ' Declare an object variable of the type to be deserialized.  
        Dim po As PurchaseOrder  
        ' Uses the Deserialize method to restore the object's state   
        ' with data from the XML document.   
        po = CType(serializer.Deserialize(fs), PurchaseOrder)  
        ' Reads the order date.  
        Console.WriteLine(("OrderDate: " & po.OrderDate))  
  
        ' Reads the shipping address.  
        Dim shipTo As Address = po.ShipTo  
        ReadAddress(shipTo, "Ship To:")  
        ' Reads the list of ordered items.  
        Dim items As OrderedItem() = po.OrderedItems  
        Console.WriteLine("Items to be shipped:")  
        Dim oi As OrderedItem  
        For Each oi In items  
            Console.WriteLine((ControlChars.Tab & oi.ItemName & _  
            ControlChars.Tab & _  
                oi.Description & ControlChars.Tab & oi.UnitPrice & _  
                ControlChars.Tab & _  
                oi.Quantity & ControlChars.Tab & oi.LineTotal))  
        Next oi  
        ' Reads the subtotal, shipping cost, and total cost.  
        Console.WriteLine((ControlChars.Cr & New String _  
        (ControlChars.Tab, 5) & _  
        " Subtotal" & ControlChars.Tab & po.SubTotal & ControlChars.Cr & _  
        New String(ControlChars.Tab, 5) & " Shipping" & ControlChars.Tab & _  
        po.ShipCost & ControlChars.Cr &  New String(ControlChars.Tab, 5) & _  
        " Total" & New String(ControlChars.Tab, 2) & po.TotalCost))  
    End Sub   
  
    Protected Sub ReadAddress(a As Address, label As String)  
        ' Reads the fields of the Address.  
        Console.WriteLine(label)  
        Console.Write((ControlChars.Tab & a.Name & ControlChars.Cr & _  
        ControlChars.Tab & a.Line1 & ControlChars.Cr & ControlChars.Tab & _  
        a.City & ControlChars.Tab & a.State & ControlChars.Cr & _  
        ControlChars.Tab & a.Zip & ControlChars.Cr))  
    End Sub   
  
    Protected Sub serializer_UnknownNode(sender As Object, e As _  
    XmlNodeEventArgs)  
        Console.WriteLine(("Unknown Node:" & e.Name & _  
        ControlChars.Tab & e.Text))  
    End Sub   
  
    Protected Sub serializer_UnknownAttribute(sender As Object, _  
    e As XmlAttributeEventArgs)  
        Dim attr As System.Xml.XmlAttribute = e.Attr  
        Console.WriteLine(("Unknown attribute " & attr.Name & "='" & _  
        attr.Value & "'"))  
    End Sub 'serializer_UnknownAttribute  
End Class 'Test  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Serialization;  
using System.IO;  
  
// The XmlRoot attribute allows you to set an alternate name   
// (PurchaseOrder) for the XML element and its namespace. By   
// default, the XmlSerializer uses the class name. The attribute   
// also allows you to set the XML namespace for the element. Lastly,  
// the attribute sets the IsNullable property, which specifies whether   
// the xsi:null attribute appears if the class instance is set to   
// a null reference.  
[XmlRoot("PurchaseOrder", Namespace="http://www.cpandl.com",   
IsNullable = false)]  
public class PurchaseOrder  
{  
    public Address ShipTo;  
    public string OrderDate;   
    // The XmlArray attribute changes the XML element name  
    // from the default of "OrderedItems" to "Items".  
    [XmlArray("Items")]  
    public OrderedItem[] OrderedItems;  
    public decimal SubTotal;  
    public decimal ShipCost;  
    public decimal TotalCost;     
}  
  
public class Address  
{  
    // The XmlAttribute attribute instructs the XmlSerializer to serialize the   
    // Name field as an XML attribute instead of an XML element (the   
    // default behavior).  
    [XmlAttribute]  
    public string Name;  
    public string Line1;  
  
    // Setting the IsNullable property to false instructs the   
    // XmlSerializer that the XML attribute will not appear if   
    // the City field is set to a null reference.  
    [XmlElement(IsNullable = false)]  
    public string City;  
    public string State;  
    public string Zip;  
}  
  
public class OrderedItem  
{  
    public string ItemName;  
    public string Description;  
    public decimal UnitPrice;  
    public int Quantity;  
    public decimal LineTotal;  
  
    // Calculate is a custom method that calculates the price per item  
    // and stores the value in a field.  
    public void Calculate()  
    {  
        LineTotal = UnitPrice * Quantity;  
    }  
}  
  
public class Test  
{  
    public static void Main()  
    {  
        // Read and write purchase orders.  
        Test t = new Test();  
        t.CreatePO("po.xml");  
        t.ReadPO("po.xml");  
    }  
  
    private void CreatePO(string filename)  
    {  
        // Creates an instance of the XmlSerializer class;  
        // specifies the type of object to serialize.  
        XmlSerializer serializer =   
        new XmlSerializer(typeof(PurchaseOrder));  
        TextWriter writer = new StreamWriter(filename);  
        PurchaseOrder po=new PurchaseOrder();  
  
        // Creates an address to ship and bill to.  
        Address billAddress = new Address();  
        billAddress.Name = "Teresa Atkinson";  
        billAddress.Line1 = "1 Main St.";  
        billAddress.City = "AnyTown";  
        billAddress.State = "WA";  
        billAddress.Zip = "00000";  
        // Sets ShipTo and BillTo to the same addressee.  
        po.ShipTo = billAddress;  
        po.OrderDate = System.DateTime.Now.ToLongDateString();  
  
        // Creates an OrderedItem.  
        OrderedItem i1 = new OrderedItem();  
        i1.ItemName = "Widget S";  
        i1.Description = "Small widget";  
        i1.UnitPrice = (decimal) 5.23;  
        i1.Quantity = 3;  
        i1.Calculate();  
  
        // Inserts the item into the array.  
        OrderedItem [] items = {i1};  
        po.OrderedItems = items;  
        // Calculate the total cost.  
        decimal subTotal = new decimal();  
        foreach(OrderedItem oi in items)  
        {  
            subTotal += oi.LineTotal;  
        }  
        po.SubTotal = subTotal;  
        po.ShipCost = (decimal) 12.51;   
        po.TotalCost = po.SubTotal + po.ShipCost;   
        // Serializes the purchase order, and closes the TextWriter.  
        serializer.Serialize(writer, po);  
        writer.Close();  
    }  
  
    protected void ReadPO(string filename)  
    {  
        // Creates an instance of the XmlSerializer class;  
        // specifies the type of object to be deserialized.  
        XmlSerializer serializer = new XmlSerializer(typeof(PurchaseOrder));  
        // If the XML document has been altered with unknown   
        // nodes or attributes, handles them with the   
        // UnknownNode and UnknownAttribute events.  
        serializer.UnknownNode+= new   
        XmlNodeEventHandler(serializer_UnknownNode);  
        serializer.UnknownAttribute+= new   
        XmlAttributeEventHandler(serializer_UnknownAttribute);  
  
        // A FileStream is needed to read the XML document.  
        FileStream fs = new FileStream(filename, FileMode.Open);  
        // Declares an object variable of the type to be deserialized.  
        PurchaseOrder po;  
        // Uses the Deserialize method to restore the object's state   
        // with data from the XML document. */  
        po = (PurchaseOrder) serializer.Deserialize(fs);  
        // Reads the order date.  
        Console.WriteLine ("OrderDate: " + po.OrderDate);  
  
        // Reads the shipping address.  
        Address shipTo = po.ShipTo;  
        ReadAddress(shipTo, "Ship To:");  
        // Reads the list of ordered items.  
        OrderedItem [] items = po.OrderedItems;  
        Console.WriteLine("Items to be shipped:");  
        foreach(OrderedItem oi in items)  
        {  
            Console.WriteLine("\t"+  
            oi.ItemName + "\t" +   
            oi.Description + "\t" +  
            oi.UnitPrice + "\t" +  
            oi.Quantity + "\t" +  
            oi.LineTotal);  
        }  
        // Reads the subtotal, shipping cost, and total cost.  
        Console.WriteLine(  
        "\n\t\t\t\t\t Subtotal\t" + po.SubTotal +   
        "\n\t\t\t\t\t Shipping\t" + po.ShipCost +   
        "\n\t\t\t\t\t Total\t\t" + po.TotalCost  
        );  
    }  
  
    protected void ReadAddress(Address a, string label)  
    {  
        // Reads the fields of the Address.  
        Console.WriteLine(label);  
        Console.Write("\t"+  
        a.Name +"\n\t" +  
        a.Line1 +"\n\t" +  
        a.City +"\t" +  
        a.State +"\n\t" +  
        a.Zip +"\n");  
    }  
  
    protected void serializer_UnknownNode  
    (object sender, XmlNodeEventArgs e)  
    {  
        Console.WriteLine("Unknown Node:" +   e.Name + "\t" + e.Text);  
    }  
  
    protected void serializer_UnknownAttribute  
    (object sender, XmlAttributeEventArgs e)  
    {  
        System.Xml.XmlAttribute attr = e.Attr;  
        Console.WriteLine("Unknown attribute " +   
        attr.Name + "='" + attr.Value + "'");  
    }  
}  
```  
  
 <span data-ttu-id="ac46a-144">Výstup XML může vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="ac46a-144">The XML output might resemble the following.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<PurchaseOrder xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://www.cpandl.com">  
    <ShipTo Name="Teresa Atkinson">  
        <Line1>1 Main St.</Line1>  
        <City>AnyTown</City>  
        <State>WA</State>  
        <Zip>00000</Zip>  
    </ShipTo>  
    <OrderDate>Wednesday, June 27, 2001</OrderDate>  
    <Items>  
        <OrderedItem>  
            <ItemName>Widget S</ItemName>  
            <Description>Small widget</Description>  
            <UnitPrice>5.23</UnitPrice>  
            <Quantity>3</Quantity>  
            <LineTotal>15.69</LineTotal>  
        </OrderedItem>  
    </Items>  
    <SubTotal>15.69</SubTotal>  
    <ShipCost>12.51</ShipCost>  
    <TotalCost>28.2</TotalCost>  
</PurchaseOrder>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac46a-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac46a-145">See Also</span></span>  
 [<span data-ttu-id="ac46a-146">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="ac46a-146">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="ac46a-147">Řízení serializace XML pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="ac46a-147">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [<span data-ttu-id="ac46a-148">Seznam atributů řídících serializaci XML</span><span class="sxs-lookup"><span data-stu-id="ac46a-148">Attributes That Control XML Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 [<span data-ttu-id="ac46a-149">Třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="ac46a-149">XmlSerializer Class</span></span>](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx)  
 [<span data-ttu-id="ac46a-150">Postupy: Serializace objektu</span><span class="sxs-lookup"><span data-stu-id="ac46a-150">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="ac46a-151">Postupy: Deserializace objektu</span><span class="sxs-lookup"><span data-stu-id="ac46a-151">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
