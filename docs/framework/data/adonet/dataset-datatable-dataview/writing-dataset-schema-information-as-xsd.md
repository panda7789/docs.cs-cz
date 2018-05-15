---
title: Zápis informací o schématu datovou sadu jako XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: b2012b32b0751bc093b9b3267cbbfc2e1a408156
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="9066f-102">Zápis informací o schématu datovou sadu jako XSD</span><span class="sxs-lookup"><span data-stu-id="9066f-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="9066f-103">Můžete napsat schéma <xref:System.Data.DataSet> jako schématu XML definition language (XSD) schématu, tak, aby vám ho přenosu s nebo bez souvisejících dat v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="9066f-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="9066f-104">Schéma XML lze zapisovat do souboru, datového proudu <xref:System.Xml.XmlWriter>, nebo řetězec; je vhodné pro generování silného typu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="9066f-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="9066f-105">Další informace o silného typu **datovou sadu** objekty, najdete v části [typové datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="9066f-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 <span data-ttu-id="9066f-106">Můžete určit, jak jsou reprezentována sloupec tabulky ve schématu XML pomocí **ColumnMapping** vlastnost <xref:System.Data.DataColumn> objektu.</span><span class="sxs-lookup"><span data-stu-id="9066f-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="9066f-107">Další informace najdete v tématu "Mapování sloupců XML elementy, atributy a Text" v [zápis obsah datovou sadu jako XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="9066f-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="9066f-108">Zápis schéma **datovou sadu** jako schématu XML do souboru, datového proudu, nebo **XmlWriter**, použijte **WriteXmlSchema** metodu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="9066f-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="9066f-109">**WriteXmlSchema** přijímá jeden parametr, který určuje cíl výsledné schématu XML.</span><span class="sxs-lookup"><span data-stu-id="9066f-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="9066f-110">Následující příklady kódu ukazují, jak napsat schéma XML **datovou sadu** do souboru předáním řetězec obsahující název souboru a <xref:System.IO.StreamWriter> objektu.</span><span class="sxs-lookup"><span data-stu-id="9066f-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 <span data-ttu-id="9066f-111">K získání schématu **datovou sadu** a zapsat jako řetězec schématu XML, použijte **GetXmlSchema** metoda, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9066f-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="9066f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="9066f-112">See Also</span></span>  
 [<span data-ttu-id="9066f-113">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="9066f-113">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="9066f-114">Kopírování obsahu datové sady jako dat XML</span><span class="sxs-lookup"><span data-stu-id="9066f-114">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [<span data-ttu-id="9066f-115">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="9066f-115">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="9066f-116">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="9066f-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="9066f-117">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="9066f-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
