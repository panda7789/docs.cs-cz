---
title: Generování datových sad silného typu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: 9accfb68c57384e12a59bae40ebe30a2d3e22877
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43489718"
---
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="56506-102">Generování datových sad silného typu</span><span class="sxs-lookup"><span data-stu-id="56506-102">Generating Strongly Typed DataSets</span></span>
<span data-ttu-id="56506-103">Zadané schéma XML, který vyhovuje schématu XML definice jazyk (XSD) standard, můžete vygenerovat silného typu <xref:System.Data.DataSet> nástrojem XSD.exe, opatřeného [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56506-103">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].</span></span>  
  
 <span data-ttu-id="56506-104">(Vytvoření xsd z tabulky databáze najdete v tématu <xref:System.Data.DataSet.WriteXmlSchema%2A> nebo [práce s datovými sadami v sadě Visual Studio](https://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span><span class="sxs-lookup"><span data-stu-id="56506-104">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](https://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span></span>  
  
 <span data-ttu-id="56506-105">Následující kód ukazuje syntaxi pro generování **datovou sadu** pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="56506-105">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="56506-106">V této syntaxe `/d` směrnice instruuje nástroj v režimu generování **datovou sadu**a `/l:` instruuje nástroj jaký jazyk se má použít (například C# nebo Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="56506-106">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="56506-107">Volitelný `/eld` direktiva Určuje, které můžete použít [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] k dotazu vůči generované **datové sady.**</span><span class="sxs-lookup"><span data-stu-id="56506-107">The optional `/eld` directive specifies that you can use [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] to query against the generated **DataSet.**</span></span> <span data-ttu-id="56506-108">Tato možnost se používá při `/d` je také zadán.</span><span class="sxs-lookup"><span data-stu-id="56506-108">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="56506-109">Další informace najdete v tématu [dotazování typované datové sady](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="56506-109">For more information, see [Querying Typed DataSets](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="56506-110">Volitelný `/n:` – direktiva Určuje nástroj, který také generovat obor názvů pro **datovou sadu** volá **XSDSchema.Namespace**.</span><span class="sxs-lookup"><span data-stu-id="56506-110">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="56506-111">Výstup příkazu je XSDSchemaFileName.cs, které je možné zkompilovat a použít v aplikaci ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="56506-111">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="56506-112">Generovaný kód lze zkompilovat jako knihovny nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="56506-112">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="56506-113">Následující kód ukazuje syntaxi pro kompilaci vygenerovaného kódu jako knihovny pomocí kompilátoru jazyka C# (csc.exe).</span><span class="sxs-lookup"><span data-stu-id="56506-113">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="56506-114">`/t:` Směrnice instruuje nástroj pro kompilaci do knihovny a `/r:` direktivy zadat závislé knihovny požadovaných pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="56506-114">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="56506-115">Výstup příkazu je XSDSchemaFileName.dll, které mohou být předána do kompilátor při kompilaci aplikace pomocí technologie ADO.NET `/r:` směrnice.</span><span class="sxs-lookup"><span data-stu-id="56506-115">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="56506-116">Následující kód ukazuje syntaxi pro přístup k oboru názvů předán XSD.exe v aplikaci ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="56506-116">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="56506-117">Následující příklad kódu používá typovaného **datovou sadu** s názvem **CustomerDataSet** načíst seznam zákazníků **Northwind** databáze.</span><span class="sxs-lookup"><span data-stu-id="56506-117">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="56506-118">Po načtení dat pomocí **vyplnit** metody v příkladu prochází každého zákazníka v **zákazníkům** tabulky pomocí zadaného **CustomersRow** ( **Objekt DataRow**) objektu.</span><span class="sxs-lookup"><span data-stu-id="56506-118">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="56506-119">To poskytuje přímý přístup k **CustomerID** sloupců, nikoli až **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="56506-119">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
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
  
 <span data-ttu-id="56506-120">Následuje schéma XML pro příklad.</span><span class="sxs-lookup"><span data-stu-id="56506-120">Following is the XML Schema used for the example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="56506-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="56506-121">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="56506-122">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="56506-122">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="56506-123">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="56506-123">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="56506-124">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="56506-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
