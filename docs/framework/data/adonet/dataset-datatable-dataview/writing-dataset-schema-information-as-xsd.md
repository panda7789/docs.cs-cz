---
title: Zápis informací o schématu datové sady jako XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: f86e9100489ddf35d8ef5f98e386306a7dbfd4ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784176"
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="2ab7f-102">Zápis informací o schématu datové sady jako XSD</span><span class="sxs-lookup"><span data-stu-id="2ab7f-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="2ab7f-103">Schéma můžete zapsat <xref:System.Data.DataSet> jako schéma XML schématu definice jazyka (XSD), abyste ho mohli přenést s použitím nebo bez souvisejících dat v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="2ab7f-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="2ab7f-104">Schéma XML lze zapsat do souboru, datového proudu, <xref:System.Xml.XmlWriter>nebo řetězce; je užitečné pro vygenerování **datové sady**silného typu.</span><span class="sxs-lookup"><span data-stu-id="2ab7f-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="2ab7f-105">Další informace o objektech **DataSet** se silnými typy najdete v tématu [typové datové sady](typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="2ab7f-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](typed-datasets.md).</span></span>  
  
 <span data-ttu-id="2ab7f-106">Můžete určit způsob reprezentace sloupce tabulky ve schématu XML pomocí vlastnosti <xref:System.Data.DataColumn> **ColumnMapping** objektu.</span><span class="sxs-lookup"><span data-stu-id="2ab7f-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="2ab7f-107">Další informace naleznete v části "mapování sloupců na prvky XML, atributy a text" v článku [psaní obsahu datové sady jako XML data](writing-dataset-contents-as-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="2ab7f-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="2ab7f-108">Chcete-li zapsat schéma **datové sady** jako schématu XML, do souboru, datového proudu nebo **XmlWriter**, použijte metodu **WriteXmlSchema** **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="2ab7f-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="2ab7f-109">**WriteXmlSchema** přijímá jeden parametr, který určuje cíl výsledného schématu XML.</span><span class="sxs-lookup"><span data-stu-id="2ab7f-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="2ab7f-110">Následující příklady kódu ukazují, jak zapsat schéma XML **datové sady** do souboru předáním řetězce obsahujícího název souboru a <xref:System.IO.StreamWriter> objektu.</span><span class="sxs-lookup"><span data-stu-id="2ab7f-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
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
  
 <span data-ttu-id="2ab7f-111">Chcete-li získat schéma **datové sady** a zapsat je jako řetězec schématu XML, použijte metodu **GetXmlSchema** , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2ab7f-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ab7f-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ab7f-112">See also</span></span>

- [<span data-ttu-id="2ab7f-113">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="2ab7f-113">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="2ab7f-114">Kopírování obsahu datové sady jako dat XML</span><span class="sxs-lookup"><span data-stu-id="2ab7f-114">Writing DataSet Contents as XML Data</span></span>](writing-dataset-contents-as-xml-data.md)
- [<span data-ttu-id="2ab7f-115">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="2ab7f-115">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="2ab7f-116">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="2ab7f-116">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="2ab7f-117">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2ab7f-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
