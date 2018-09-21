---
title: Zápis informací o schématu datové sady jako XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: 2a59a9fc1c3b2f52543f4cc69de22a5703fa9b8b
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46540843"
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="fe005-102">Zápis informací o schématu datové sady jako XSD</span><span class="sxs-lookup"><span data-stu-id="fe005-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="fe005-103">Lze zapsat schéma <xref:System.Data.DataSet> jako jazyk (XSD) schématu definice schématu XML, takže, mohou přenášet, s nebo bez souvisejících dat v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="fe005-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="fe005-104">Schéma XML lze zapsat do souboru, datový proud <xref:System.Xml.XmlWriter>, nebo řetězec; jde použít ke generování silného typu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="fe005-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="fe005-105">Další informace o silně typované **datovou sadu** objekty, najdete [typované datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="fe005-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 <span data-ttu-id="fe005-106">Můžete určit, jak je reprezentovaná sloupec tabulky ve schématu XML pomocí **ColumnMapping** vlastnost <xref:System.Data.DataColumn> objektu.</span><span class="sxs-lookup"><span data-stu-id="fe005-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="fe005-107">Další informace najdete v tématu "Mapování sloupců XML elementů, atributů a Text" [zápis obsahu datové sady jako dat XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="fe005-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="fe005-108">Chcete-li zapsat schéma **datovou sadu** jako schéma XML do souboru, datový proud, nebo **XmlWriter**, použít **WriteXmlSchema** metodu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="fe005-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="fe005-109">**WriteXmlSchema** přijímá jeden parametr, který určuje cíl výsledného schématu XML.</span><span class="sxs-lookup"><span data-stu-id="fe005-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="fe005-110">Následující příklady kódu ukazují, jak zapsat schéma XML **datovou sadu** do souboru tím, že předáte řetězec obsahující název souboru a <xref:System.IO.StreamWriter> objektu.</span><span class="sxs-lookup"><span data-stu-id="fe005-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
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
  
 <span data-ttu-id="fe005-111">Získat schéma **datovou sadu** a zapsat jako řetězec schématu XML, použijte **GetXmlSchema** způsob, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fe005-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe005-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe005-112">See Also</span></span>  
 [<span data-ttu-id="fe005-113">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="fe005-113">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="fe005-114">Kopírování obsahu datové sady jako dat XML</span><span class="sxs-lookup"><span data-stu-id="fe005-114">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [<span data-ttu-id="fe005-115">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="fe005-115">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="fe005-116">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="fe005-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="fe005-117">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="fe005-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
