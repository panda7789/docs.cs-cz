---
title: Kopírování obsahu datové sady jako dat XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: dae044a9d7802e858f1f24dd4aa0f1de8f6cba7a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158948"
---
# <a name="writing-dataset-contents-as-xml-data"></a><span data-ttu-id="c7781-102">Kopírování obsahu datové sady jako dat XML</span><span class="sxs-lookup"><span data-stu-id="c7781-102">Writing DataSet Contents as XML Data</span></span>
<span data-ttu-id="c7781-103">Napište reprezentaci v jazyce XML v ADO.NET <xref:System.Data.DataSet>, s nebo bez jeho schématu.</span><span class="sxs-lookup"><span data-stu-id="c7781-103">In ADO.NET you can write an XML representation of a <xref:System.Data.DataSet>, with or without its schema.</span></span> <span data-ttu-id="c7781-104">Je-li informace o schématu zahrnuty vložené XML, je zapsán pomocí jazyka pro definici schématu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="c7781-104">If schema information is included inline with the XML, it is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="c7781-105">Schéma obsahuje definice tabulky <xref:System.Data.DataSet> a také definice relace a omezení.</span><span class="sxs-lookup"><span data-stu-id="c7781-105">The schema contains the table definitions of the <xref:System.Data.DataSet> as well as the relation and constraint definitions.</span></span>  
  
 <span data-ttu-id="c7781-106">Když <xref:System.Data.DataSet> je zapsán jako data XML, řádky v tabulce <xref:System.Data.DataSet> jsou napsané v jejich aktuálních verzí.</span><span class="sxs-lookup"><span data-stu-id="c7781-106">When a <xref:System.Data.DataSet> is written as XML data, the rows in the <xref:System.Data.DataSet> are written in their current versions.</span></span> <span data-ttu-id="c7781-107">Ale <xref:System.Data.DataSet> lze také zapsat jako formát DiffGram tak, aby aktuální a původní hodnoty řádky budou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="c7781-107">However, the <xref:System.Data.DataSet> can also be written as a DiffGram so that both the current and the original values of the rows will be included.</span></span>  
  
 <span data-ttu-id="c7781-108">Reprezentace XML <xref:System.Data.DataSet> lze zapsat do souboru, datový proud **XmlWriter**, nebo řetězec.</span><span class="sxs-lookup"><span data-stu-id="c7781-108">The XML representation of the <xref:System.Data.DataSet> can be written to a file, a stream, an **XmlWriter**, or a string.</span></span> <span data-ttu-id="c7781-109">Tyto možnosti poskytují flexibilitu pro způsob přenosu reprezentace XML <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c7781-109">These choices provide great flexibility for how you transport the XML representation of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c7781-110">K získání reprezentace XML <xref:System.Data.DataSet> jako řetězec, použijte **getxml –** způsob, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c7781-110">To obtain the XML representation of the <xref:System.Data.DataSet> as a string, use the **GetXml** method as shown in the following example.</span></span>  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 <span data-ttu-id="c7781-111">**Getxml –** vrátí reprezentaci XML <xref:System.Data.DataSet> bez informací o schématu.</span><span class="sxs-lookup"><span data-stu-id="c7781-111">**GetXml** returns the XML representation of the <xref:System.Data.DataSet> without schema information.</span></span> <span data-ttu-id="c7781-112">Zápis informací o schématu z <xref:System.Data.DataSet> (jako schéma XML) na řetězec pomocí **GetXmlSchema**.</span><span class="sxs-lookup"><span data-stu-id="c7781-112">To write the schema information from the <xref:System.Data.DataSet> (as XML Schema) to a string, use **GetXmlSchema**.</span></span>  
  
 <span data-ttu-id="c7781-113">K zápisu <xref:System.Data.DataSet> do souboru datového proudu, nebo **XmlWriter**, použijte **WriteXml** – metoda.</span><span class="sxs-lookup"><span data-stu-id="c7781-113">To write a <xref:System.Data.DataSet> to a file, stream, or **XmlWriter**, use the **WriteXml** method.</span></span> <span data-ttu-id="c7781-114">První parametr předáte do **WriteXml** je cílem výstupu XML.</span><span class="sxs-lookup"><span data-stu-id="c7781-114">The first parameter you pass to **WriteXml** is the destination of the XML output.</span></span> <span data-ttu-id="c7781-115">Například řetězec obsahující název souboru, předejte **System.IO.TextWriter** objektu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c7781-115">For example, pass a string containing a file name, a **System.IO.TextWriter** object, and so on.</span></span> <span data-ttu-id="c7781-116">Můžete předat volitelný druhý parametr **XmlWriteMode** k určení, jak se výstup XML má být proveden zápis.</span><span class="sxs-lookup"><span data-stu-id="c7781-116">You can pass an optional second parameter of an **XmlWriteMode** to specify how the XML output is to be written.</span></span>  
  
 <span data-ttu-id="c7781-117">V následující tabulce jsou uvedeny možnosti **XmlWriteMode**.</span><span class="sxs-lookup"><span data-stu-id="c7781-117">The following table shows the options for **XmlWriteMode**.</span></span>  
  
|<span data-ttu-id="c7781-118">Možnost XmlWriteMode</span><span class="sxs-lookup"><span data-stu-id="c7781-118">XmlWriteMode option</span></span>|<span data-ttu-id="c7781-119">Popis</span><span class="sxs-lookup"><span data-stu-id="c7781-119">Description</span></span>|  
|-------------------------|-----------------|  
|**<span data-ttu-id="c7781-120">IgnoreSchema</span><span class="sxs-lookup"><span data-stu-id="c7781-120">IgnoreSchema</span></span>**|<span data-ttu-id="c7781-121">Zapíše aktuální obsah <xref:System.Data.DataSet> jako data XML bez schématu XML.</span><span class="sxs-lookup"><span data-stu-id="c7781-121">Writes the current contents of the <xref:System.Data.DataSet> as XML data, without an XML Schema.</span></span> <span data-ttu-id="c7781-122">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="c7781-122">This is the default.</span></span>|  
|**<span data-ttu-id="c7781-123">WriteSchema</span><span class="sxs-lookup"><span data-stu-id="c7781-123">WriteSchema</span></span>**|<span data-ttu-id="c7781-124">Zapíše aktuální obsah <xref:System.Data.DataSet> jako dat XML pomocí relační struktury jako vložené schéma XML.</span><span class="sxs-lookup"><span data-stu-id="c7781-124">Writes the current contents of the <xref:System.Data.DataSet> as XML data with the relational structure as inline XML Schema.</span></span>|  
|**<span data-ttu-id="c7781-125">DiffGram</span><span class="sxs-lookup"><span data-stu-id="c7781-125">DiffGram</span></span>**|<span data-ttu-id="c7781-126">Zapíše celý <xref:System.Data.DataSet> jako formát DiffGram, včetně aktuální a původní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c7781-126">Writes the entire <xref:System.Data.DataSet> as a DiffGram, including original and current values.</span></span> <span data-ttu-id="c7781-127">Další informace najdete v tématu [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="c7781-127">For more information, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>|  
  
 <span data-ttu-id="c7781-128">Při zápisu reprezentaci v jazyce XML <xref:System.Data.DataSet> obsahující **DataRelation** objekty, bude pravděpodobně chcete, aby výsledný XML obsahuje podřízené řádky každá relace vnořené jejich souvisejících nadřazených prvků.</span><span class="sxs-lookup"><span data-stu-id="c7781-128">When writing an XML representation of a <xref:System.Data.DataSet> that contains **DataRelation** objects, you will most likely want the resulting XML to have the child rows of each relation nested within their related parent elements.</span></span> <span data-ttu-id="c7781-129">Chcete-li to provést, nastavte **vnořené** vlastnost **DataRelation** k **true** po přidání **DataRelation** k <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c7781-129">To accomplish this, set the **Nested** property of the **DataRelation** to **true** when you add the **DataRelation** to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c7781-130">Další informace najdete v tématu [vnoření datových relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="c7781-130">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
 <span data-ttu-id="c7781-131">Následují dva příklady toho, jak reprezentaci XML pro zápis <xref:System.Data.DataSet> do souboru.</span><span class="sxs-lookup"><span data-stu-id="c7781-131">Following are two examples of how to write the XML representation of a <xref:System.Data.DataSet> to a file.</span></span> <span data-ttu-id="c7781-132">První příklad předá název souboru pro výslednou XML jako řetězec do **WriteXml**.</span><span class="sxs-lookup"><span data-stu-id="c7781-132">The first example passes the file name for the resulting XML as a string to **WriteXml**.</span></span> <span data-ttu-id="c7781-133">Druhý příklad předává **System.IO.StreamWriter** objektu.</span><span class="sxs-lookup"><span data-stu-id="c7781-133">The second example passes a **System.IO.StreamWriter** object.</span></span>  
  
```vb  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema)  
```  
  
```csharp  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema);  
```  
  
```vb  
Dim xmlSW As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xml")  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema)  
xmlSW.Close()  
```  
  
```csharp  
System.IO.StreamWriter xmlSW = new System.IO.StreamWriter("Customers.xml");  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema);  
xmlSW.Close();  
```  
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a><span data-ttu-id="c7781-134">Mapování sloupců na XML elementů, atributů a Text</span><span class="sxs-lookup"><span data-stu-id="c7781-134">Mapping Columns to XML Elements, Attributes, and Text</span></span>  
 <span data-ttu-id="c7781-135">Můžete určit, jak je reprezentovaná sloupec tabulky v XML pomocí **ColumnMapping** vlastnost **DataColumn** objektu.</span><span class="sxs-lookup"><span data-stu-id="c7781-135">You can specify how a column of a table is represented in XML using the **ColumnMapping** property of the **DataColumn** object.</span></span> <span data-ttu-id="c7781-136">V následující tabulce jsou uvedeny různé **MappingType** hodnoty **ColumnMapping** vlastnost sloupec tabulky a výsledného kódu XML.</span><span class="sxs-lookup"><span data-stu-id="c7781-136">The following table shows the different **MappingType** values for the **ColumnMapping** property of a table column, and the resulting XML.</span></span>  
  
|<span data-ttu-id="c7781-137">Hodnota MappingType</span><span class="sxs-lookup"><span data-stu-id="c7781-137">MappingType value</span></span>|<span data-ttu-id="c7781-138">Popis</span><span class="sxs-lookup"><span data-stu-id="c7781-138">Description</span></span>|  
|-----------------------|-----------------|  
|**<span data-ttu-id="c7781-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="c7781-139">Element</span></span>**|<span data-ttu-id="c7781-140">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="c7781-140">This is the default.</span></span> <span data-ttu-id="c7781-141">Sloupec je zapsán jako element XML, kde vlastnost ColumnName je název elementu a obsah sloupce se zapisují jako text elementu.</span><span class="sxs-lookup"><span data-stu-id="c7781-141">The column is written as an XML element where the ColumnName is the name of the element and the contents of the column are written as the text of the element.</span></span> <span data-ttu-id="c7781-142">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c7781-142">For example:</span></span><br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**<span data-ttu-id="c7781-143">Atribut</span><span class="sxs-lookup"><span data-stu-id="c7781-143">Attribute</span></span>**|<span data-ttu-id="c7781-144">Sloupec je zapsán jako atribut XML elementu XML pro aktuální řádek, kde vlastnost ColumnName je název atributu a obsah sloupce se zapisují jako hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="c7781-144">The column is written as an XML attribute of the XML element for the current row where the ColumnName is the name of the attribute and the contents of the column are written as the value of the attribute.</span></span> <span data-ttu-id="c7781-145">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c7781-145">For example:</span></span><br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**<span data-ttu-id="c7781-146">SimpleContent</span><span class="sxs-lookup"><span data-stu-id="c7781-146">SimpleContent</span></span>**|<span data-ttu-id="c7781-147">Obsah sloupce se zapisují jako text v elementu jazyka XML pro aktuální řádek.</span><span class="sxs-lookup"><span data-stu-id="c7781-147">The contents of the column are written as text in the XML element for the current row.</span></span> <span data-ttu-id="c7781-148">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c7781-148">For example:</span></span><br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> <span data-ttu-id="c7781-149">Všimněte si, že **SimpleContent** nelze nastavit pro sloupec tabulky, který má **Element** sloupce nebo vnořené relace.</span><span class="sxs-lookup"><span data-stu-id="c7781-149">Note that **SimpleContent** cannot be set for a column of a table that has **Element** columns or nested relations.</span></span>|  
|**<span data-ttu-id="c7781-150">Hidden</span><span class="sxs-lookup"><span data-stu-id="c7781-150">Hidden</span></span>**|<span data-ttu-id="c7781-151">Sloupec není zapsán ve výstupu XML.</span><span class="sxs-lookup"><span data-stu-id="c7781-151">The column is not written in the XML output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7781-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7781-152">See also</span></span>

- [<span data-ttu-id="c7781-153">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="c7781-153">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="c7781-154">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="c7781-154">DiffGrams</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)
- [<span data-ttu-id="c7781-155">Vnoření datových relací</span><span class="sxs-lookup"><span data-stu-id="c7781-155">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)
- [<span data-ttu-id="c7781-156">Zápis informací o schématu datové sady jako XSD</span><span class="sxs-lookup"><span data-stu-id="c7781-156">Writing DataSet Schema Information as XSD</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)
- [<span data-ttu-id="c7781-157">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="c7781-157">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="c7781-158">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="c7781-158">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
