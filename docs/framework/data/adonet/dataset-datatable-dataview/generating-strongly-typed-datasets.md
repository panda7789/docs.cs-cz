---
title: Generování datových sad se silnými typy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: ce7e5ad53f7aa5dad457ca1aa6ab76716086c0c3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833993"
---
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="7c67b-102">Generování datových sad se silnými typy</span><span class="sxs-lookup"><span data-stu-id="7c67b-102">Generating Strongly Typed DataSets</span></span>
<span data-ttu-id="7c67b-103">Vzhledem ke schématu XML, které vyhovuje standardu XSD (XML Schema Definition Language), můžete vygenerovat silně typované <xref:System.Data.DataSet> pomocí nástroje XSD. exe, který je součástí sady Windows Software Development Kit (SDK).</span><span class="sxs-lookup"><span data-stu-id="7c67b-103">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the Windows Software Development Kit (SDK).</span></span>  
  
 <span data-ttu-id="7c67b-104">(Chcete-li vytvořit XSD z databázových tabulek, přečtěte si část <xref:System.Data.DataSet.WriteXmlSchema%2A> nebo [práce s datovými sadami v sadě Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span><span class="sxs-lookup"><span data-stu-id="7c67b-104">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span></span>  
  
 <span data-ttu-id="7c67b-105">Následující kód ukazuje syntaxi pro generování **datové sady** pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="7c67b-105">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="7c67b-106">V této syntaxi direktiva `/d` instruuje nástroj, že generuje **datovou sadu**, a `/l:` oznamuje nástroji, který jazyk má být použit (například C# nebo Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="7c67b-106">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="7c67b-107">Volitelná direktiva `/eld` určuje, že lze použít LINQ to DataSet k dotazování na vygenerovanou **datovou sadu.**</span><span class="sxs-lookup"><span data-stu-id="7c67b-107">The optional `/eld` directive specifies that you can use LINQ to DataSet to query against the generated **DataSet.**</span></span> <span data-ttu-id="7c67b-108">Tato možnost se používá, když je také zadána možnost `/d`.</span><span class="sxs-lookup"><span data-stu-id="7c67b-108">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="7c67b-109">Další informace najdete v tématu [dotazování na typové datové sady](../querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="7c67b-109">For more information, see [Querying Typed DataSets](../querying-typed-datasets.md).</span></span> <span data-ttu-id="7c67b-110">Volitelná direktiva `/n:` říká nástroji, aby vygenerovala obor názvů pro **datovou sadu** s názvem **xsdschema. Namespace**.</span><span class="sxs-lookup"><span data-stu-id="7c67b-110">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="7c67b-111">Výstup příkazu je XSDSchemaFileName.cs, který lze zkompilovat a použít v aplikaci ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="7c67b-111">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="7c67b-112">Vygenerovaný kód může být kompilován jako knihovna nebo modul.</span><span class="sxs-lookup"><span data-stu-id="7c67b-112">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="7c67b-113">Následující kód ukazuje syntaxi pro zkompilování generovaného kódu jako knihovny pomocí C# kompilátoru (CSc. exe).</span><span class="sxs-lookup"><span data-stu-id="7c67b-113">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="7c67b-114">Direktiva `/t:` instruuje nástroj, že má kompilovat do knihovny a direktivy `/r:` určují závislé knihovny vyžadované ke kompilaci.</span><span class="sxs-lookup"><span data-stu-id="7c67b-114">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="7c67b-115">Výstup příkazu je XSDSchemaFileName. dll, který může být předán kompilátoru při kompilování aplikace ADO.NET s direktivou `/r:`.</span><span class="sxs-lookup"><span data-stu-id="7c67b-115">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="7c67b-116">Následující kód ukazuje syntaxi pro přístup k oboru názvů předanému do souboru XSD. exe v aplikaci ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="7c67b-116">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="7c67b-117">Následující příklad kódu používá typovou **datovou sadu** s názvem **CustomerDataSet** k načtení seznamu zákazníků z databáze **Northwind** .</span><span class="sxs-lookup"><span data-stu-id="7c67b-117">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="7c67b-118">Jakmile se data načtou pomocí metody **Fill** , příklad projde každý zákazník v tabulce **Customers** pomocí typovaného objektu **CustomersRow** (**DataRow**).</span><span class="sxs-lookup"><span data-stu-id="7c67b-118">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="7c67b-119">To poskytuje přímý přístup k sloupci **KódZákazníka** , na rozdíl od přes **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="7c67b-119">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
```vb  
Dim customers As CustomerDataSet= New CustomerDataSet()  
Dim adapter As SqlDataAdapter New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers;", _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=Northwind")  
  
adapter.Fill(customers, "Customers")  
  
Dim customerRow As CustomerDataSet.CustomersRow  
For Each customerRow In customers.Customers  
  Console.WriteLine(customerRow.CustomerID)  
Next  
```  
  
```csharp  
CustomerDataSet customers = new CustomerDataSet();  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers;",  
  "Data Source=(local);Integrated " +  
  "Security=SSPI;Initial Catalog=Northwind");  
  
adapter.Fill(customers, "Customers");  
  
foreach(CustomerDataSet.CustomersRow customerRow in customers.Customers)  
  Console.WriteLine(customerRow.CustomerID);  
```  
  
 <span data-ttu-id="7c67b-120">Následuje schéma XML použité pro příklad:</span><span class="sxs-lookup"><span data-stu-id="7c67b-120">The following is the XML Schema used for the example:</span></span>
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet" xmlns="" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c67b-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c67b-121">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="7c67b-122">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="7c67b-122">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="7c67b-123">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="7c67b-123">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="7c67b-124">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7c67b-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
