---
title: "Generování silného typu datové sady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1231413303b60eade96d989114372c4443bc67d4
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="f45be-102">Generování silného typu datové sady</span><span class="sxs-lookup"><span data-stu-id="f45be-102">Generating Strongly Typed DataSets</span></span>
<span data-ttu-id="f45be-103">Zadané schéma XML, který odpovídá schématu XML definice jazyka (XSD) standard, můžete vygenerovat silného typu <xref:System.Data.DataSet> pomocí nástroje XSD.exe součástí [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f45be-103">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].</span></span>  
  
 <span data-ttu-id="f45be-104">(Vytvoření xsd z tabulek databáze naleznete v tématu <xref:System.Data.DataSet.WriteXmlSchema%2A> nebo [práce s datovými sadami v sadě Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span><span class="sxs-lookup"><span data-stu-id="f45be-104">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span></span>  
  
 <span data-ttu-id="f45be-105">Následující kód ukazuje syntaxi pro generování **datovou sadu** pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="f45be-105">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="f45be-106">V této syntaxe `/d` – direktiva informuje nástroj pro generování **datovou sadu**a `/l:` informuje nástroj jaké jazyka (například C# nebo Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="f45be-106">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="f45be-107">Volitelné `/eld` – direktiva Určuje, které můžete použít [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] k dotazu vůči vygenerovaného **datovou sadu.**</span><span class="sxs-lookup"><span data-stu-id="f45be-107">The optional `/eld` directive specifies that you can use [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] to query against the generated **DataSet.**</span></span> <span data-ttu-id="f45be-108">Tato možnost se používá při `/d` také parametr.</span><span class="sxs-lookup"><span data-stu-id="f45be-108">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="f45be-109">Další informace najdete v tématu [dotazování typové datové sady](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="f45be-109">For more information, see [Querying Typed DataSets](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="f45be-110">Volitelné `/n:` – direktiva informuje nástroj, který taky obor názvů pro generování **datovou sadu** názvem **XSDSchema.Namespace**.</span><span class="sxs-lookup"><span data-stu-id="f45be-110">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="f45be-111">Výstup příkazu je XSDSchemaFileName.cs, které můžete zkompilovat a použít v aplikaci ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f45be-111">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="f45be-112">Generovaný kód mohou být zkompilovány jako modul nebo knihovny.</span><span class="sxs-lookup"><span data-stu-id="f45be-112">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="f45be-113">Následující kód ukazuje syntaxi pro kompilace generovaného kódu jako knihovny pomocí kompilátor jazyka C# (csc.exe).</span><span class="sxs-lookup"><span data-stu-id="f45be-113">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="f45be-114">`/t:` – Direktiva informuje nástroj zkompilovat do knihovny a `/r:` direktivy zadejte závislé knihovny potřebné ke kompilaci.</span><span class="sxs-lookup"><span data-stu-id="f45be-114">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="f45be-115">Výstup příkazu je XSDSchemaFileName.dll, který se dá předat do kompilátoru při kompilaci aplikace ADO.NET s `/r:` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="f45be-115">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="f45be-116">Následující kód ukazuje syntaxi pro přístup k oboru názvů předaný XSD.exe v aplikaci ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f45be-116">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="f45be-117">Následující příklad kódu používá zadaný **datovou sadu** s názvem **CustomerDataSet** načíst seznam zákazníků z **Northwind** databáze.</span><span class="sxs-lookup"><span data-stu-id="f45be-117">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="f45be-118">Po načtení dat pomocí **vyplnění** metody v příkladu prochází každého zákazníka a to v **zákazníci** tabulky pomocí zadaného objektu **CustomersRow** ( **DataRow**) objektu.</span><span class="sxs-lookup"><span data-stu-id="f45be-118">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="f45be-119">To poskytuje přímý přístup k **CustomerID** sloupců, nikoli pomocí **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="f45be-119">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
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
  
 <span data-ttu-id="f45be-120">Následuje schématu XML pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="f45be-120">Following is the XML Schema used for the example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f45be-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="f45be-121">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="f45be-122">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="f45be-122">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="f45be-123">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="f45be-123">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="f45be-124">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="f45be-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
