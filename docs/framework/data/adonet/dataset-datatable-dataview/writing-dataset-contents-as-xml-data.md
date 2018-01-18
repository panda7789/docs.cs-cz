---
title: "Zápis obsah datovou sadu jako XML Data"
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
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9b1250d616ad5835fccd1a3acbf0b8a759c34181
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="writing-dataset-contents-as-xml-data"></a><span data-ttu-id="19529-102">Zápis obsah datovou sadu jako XML Data</span><span class="sxs-lookup"><span data-stu-id="19529-102">Writing DataSet Contents as XML Data</span></span>
<span data-ttu-id="19529-103">V technologii ADO.NET můžete napsat reprezentaci XML <xref:System.Data.DataSet>, s nebo bez jeho schématu.</span><span class="sxs-lookup"><span data-stu-id="19529-103">In ADO.NET you can write an XML representation of a <xref:System.Data.DataSet>, with or without its schema.</span></span> <span data-ttu-id="19529-104">Pokud informace o schématu zahrnuty vložené se souborem XML, je zapsán pomocí jazyka definice schématu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="19529-104">If schema information is included inline with the XML, it is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="19529-105">Schéma obsahuje definice tabulky <xref:System.Data.DataSet> a také definice relace a omezení.</span><span class="sxs-lookup"><span data-stu-id="19529-105">The schema contains the table definitions of the <xref:System.Data.DataSet> as well as the relation and constraint definitions.</span></span>  
  
 <span data-ttu-id="19529-106">Když <xref:System.Data.DataSet> je zapsána jako data XML, řádky v <xref:System.Data.DataSet> jsou zapsány ve své aktuální verze.</span><span class="sxs-lookup"><span data-stu-id="19529-106">When a <xref:System.Data.DataSet> is written as XML data, the rows in the <xref:System.Data.DataSet> are written in their current versions.</span></span> <span data-ttu-id="19529-107">Ale <xref:System.Data.DataSet> lze zapsat také jako prvek formátu DiffGram tak, že budou zahrnuty aktuální a původní hodnoty řádků.</span><span class="sxs-lookup"><span data-stu-id="19529-107">However, the <xref:System.Data.DataSet> can also be written as a DiffGram so that both the current and the original values of the rows will be included.</span></span>  
  
 <span data-ttu-id="19529-108">Reprezentace XML <xref:System.Data.DataSet> lze zapisovat do souboru, datového proudu **XmlWriter**, nebo řetězec.</span><span class="sxs-lookup"><span data-stu-id="19529-108">The XML representation of the <xref:System.Data.DataSet> can be written to a file, a stream, an **XmlWriter**, or a string.</span></span> <span data-ttu-id="19529-109">Tyto možnosti poskytují flexibilitu pro způsob přenosu reprezentaci XML <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="19529-109">These choices provide great flexibility for how you transport the XML representation of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="19529-110">K získání reprezentaci XML <xref:System.Data.DataSet> jako řetězec, použijte **getxml –** metoda, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="19529-110">To obtain the XML representation of the <xref:System.Data.DataSet> as a string, use the **GetXml** method as shown in the following example.</span></span>  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 <span data-ttu-id="19529-111">**Getxml –** vrátí reprezentaci XML <xref:System.Data.DataSet> bez informace o schématu.</span><span class="sxs-lookup"><span data-stu-id="19529-111">**GetXml** returns the XML representation of the <xref:System.Data.DataSet> without schema information.</span></span> <span data-ttu-id="19529-112">Při zápisu informací schématu z <xref:System.Data.DataSet> (jako schématu XML) na řetězec, použijte **GetXmlSchema**.</span><span class="sxs-lookup"><span data-stu-id="19529-112">To write the schema information from the <xref:System.Data.DataSet> (as XML Schema) to a string, use **GetXmlSchema**.</span></span>  
  
 <span data-ttu-id="19529-113">Zápis <xref:System.Data.DataSet> do souboru, datového proudu, nebo **XmlWriter**, použijte **WriteXml** metoda.</span><span class="sxs-lookup"><span data-stu-id="19529-113">To write a <xref:System.Data.DataSet> to a file, stream, or **XmlWriter**, use the **WriteXml** method.</span></span> <span data-ttu-id="19529-114">První parametr je předat do **WriteXml** je cílem výstup XML.</span><span class="sxs-lookup"><span data-stu-id="19529-114">The first parameter you pass to **WriteXml** is the destination of the XML output.</span></span> <span data-ttu-id="19529-115">Například předat řetězec obsahující název souboru, **System.IO.TextWriter** objekt a tak dále.</span><span class="sxs-lookup"><span data-stu-id="19529-115">For example, pass a string containing a file name, a **System.IO.TextWriter** object, and so on.</span></span> <span data-ttu-id="19529-116">Abyste mohli předávat volitelný druhý parametr funkce **XmlWriteMode** k určení, jak je výstup XML k zapsání.</span><span class="sxs-lookup"><span data-stu-id="19529-116">You can pass an optional second parameter of an **XmlWriteMode** to specify how the XML output is to be written.</span></span>  
  
 <span data-ttu-id="19529-117">Následující tabulka znázorňuje možnosti pro **XmlWriteMode**.</span><span class="sxs-lookup"><span data-stu-id="19529-117">The following table shows the options for **XmlWriteMode**.</span></span>  
  
|<span data-ttu-id="19529-118">Možnost XmlWriteMode</span><span class="sxs-lookup"><span data-stu-id="19529-118">XmlWriteMode option</span></span>|<span data-ttu-id="19529-119">Popis</span><span class="sxs-lookup"><span data-stu-id="19529-119">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="19529-120">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="19529-120">**IgnoreSchema**</span></span>|<span data-ttu-id="19529-121">Zapíše aktuální obsah <xref:System.Data.DataSet> jako data XML bez schématu XML.</span><span class="sxs-lookup"><span data-stu-id="19529-121">Writes the current contents of the <xref:System.Data.DataSet> as XML data, without an XML Schema.</span></span> <span data-ttu-id="19529-122">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="19529-122">This is the default.</span></span>|  
|<span data-ttu-id="19529-123">**WriteSchema**</span><span class="sxs-lookup"><span data-stu-id="19529-123">**WriteSchema**</span></span>|<span data-ttu-id="19529-124">Zapíše aktuální obsah <xref:System.Data.DataSet> jako data XML s relační struktura jako vloženého schématu XML.</span><span class="sxs-lookup"><span data-stu-id="19529-124">Writes the current contents of the <xref:System.Data.DataSet> as XML data with the relational structure as inline XML Schema.</span></span>|  
|<span data-ttu-id="19529-125">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="19529-125">**DiffGram**</span></span>|<span data-ttu-id="19529-126">Zapíše celý <xref:System.Data.DataSet> jako formát DiffGram, včetně aktuální a původní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="19529-126">Writes the entire <xref:System.Data.DataSet> as a DiffGram, including original and current values.</span></span> <span data-ttu-id="19529-127">Další informace najdete v tématu [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="19529-127">For more information, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>|  
  
 <span data-ttu-id="19529-128">Při zápisu reprezentaci XML <xref:System.Data.DataSet> obsahující **DataRelation** objekty, pravděpodobně budete chtít výsledný kód XML má řádky podřízené každý vztah vnořených ve svých související nadřazené elementy.</span><span class="sxs-lookup"><span data-stu-id="19529-128">When writing an XML representation of a <xref:System.Data.DataSet> that contains **DataRelation** objects, you will most likely want the resulting XML to have the child rows of each relation nested within their related parent elements.</span></span> <span data-ttu-id="19529-129">K tomu, nastavte **vnořené** vlastnost **DataRelation** k **true** při přidání **DataRelation** k <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="19529-129">To accomplish this, set the **Nested** property of the **DataRelation** to **true** when you add the **DataRelation** to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="19529-130">Další informace najdete v tématu [vnoření DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="19529-130">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
 <span data-ttu-id="19529-131">Následují dva příklady, jak napsat reprezentaci XML <xref:System.Data.DataSet> do souboru.</span><span class="sxs-lookup"><span data-stu-id="19529-131">Following are two examples of how to write the XML representation of a <xref:System.Data.DataSet> to a file.</span></span> <span data-ttu-id="19529-132">V prvním příkladu předá název souboru pro výsledný soubor XML jako řetězec tak, aby **WriteXml**.</span><span class="sxs-lookup"><span data-stu-id="19529-132">The first example passes the file name for the resulting XML as a string to **WriteXml**.</span></span> <span data-ttu-id="19529-133">V druhém příkladu předá **System.IO.StreamWriter** objektu.</span><span class="sxs-lookup"><span data-stu-id="19529-133">The second example passes a **System.IO.StreamWriter** object.</span></span>  
  
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
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a><span data-ttu-id="19529-134">Mapování sloupce XML elementy, atributy a Text</span><span class="sxs-lookup"><span data-stu-id="19529-134">Mapping Columns to XML Elements, Attributes, and Text</span></span>  
 <span data-ttu-id="19529-135">Můžete určit, jak je reprezentována sloupec tabulky v kódu XML pomocí **ColumnMapping** vlastnost **DataColumn** objektu.</span><span class="sxs-lookup"><span data-stu-id="19529-135">You can specify how a column of a table is represented in XML using the **ColumnMapping** property of the **DataColumn** object.</span></span> <span data-ttu-id="19529-136">V následující tabulce jsou uvedeny rozdíly **MappingType** hodnoty **ColumnMapping** vlastnost sloupec tabulky a výsledný soubor XML.</span><span class="sxs-lookup"><span data-stu-id="19529-136">The following table shows the different **MappingType** values for the **ColumnMapping** property of a table column, and the resulting XML.</span></span>  
  
|<span data-ttu-id="19529-137">Hodnota MappingType</span><span class="sxs-lookup"><span data-stu-id="19529-137">MappingType value</span></span>|<span data-ttu-id="19529-138">Popis</span><span class="sxs-lookup"><span data-stu-id="19529-138">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="19529-139">**Element**</span><span class="sxs-lookup"><span data-stu-id="19529-139">**Element**</span></span>|<span data-ttu-id="19529-140">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="19529-140">This is the default.</span></span> <span data-ttu-id="19529-141">Sloupec je zapsána jako element XML, kde ColumnName je název elementu a obsah sloupce se zapisují jako text elementu.</span><span class="sxs-lookup"><span data-stu-id="19529-141">The column is written as an XML element where the ColumnName is the name of the element and the contents of the column are written as the text of the element.</span></span> <span data-ttu-id="19529-142">Příklad:</span><span class="sxs-lookup"><span data-stu-id="19529-142">For example:</span></span><br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|<span data-ttu-id="19529-143">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="19529-143">**Attribute**</span></span>|<span data-ttu-id="19529-144">Sloupec je zapsána jako atribut XML elementu XML pro aktuální řádek, kde ColumnName je název atributu, a obsah sloupce se zapisují jako hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="19529-144">The column is written as an XML attribute of the XML element for the current row where the ColumnName is the name of the attribute and the contents of the column are written as the value of the attribute.</span></span> <span data-ttu-id="19529-145">Příklad:</span><span class="sxs-lookup"><span data-stu-id="19529-145">For example:</span></span><br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|<span data-ttu-id="19529-146">**SimpleContent**</span><span class="sxs-lookup"><span data-stu-id="19529-146">**SimpleContent**</span></span>|<span data-ttu-id="19529-147">Obsah sloupce jsou zapsány jako text v elementu XML pro aktuální řádek.</span><span class="sxs-lookup"><span data-stu-id="19529-147">The contents of the column are written as text in the XML element for the current row.</span></span> <span data-ttu-id="19529-148">Příklad:</span><span class="sxs-lookup"><span data-stu-id="19529-148">For example:</span></span><br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> <span data-ttu-id="19529-149">Všimněte si, že **SimpleContent** nelze nastavit pro sloupec tabulky, který má **Element** sloupce nebo vnořené relace.</span><span class="sxs-lookup"><span data-stu-id="19529-149">Note that **SimpleContent** cannot be set for a column of a table that has **Element** columns or nested relations.</span></span>|  
|<span data-ttu-id="19529-150">**Hidden**</span><span class="sxs-lookup"><span data-stu-id="19529-150">**Hidden**</span></span>|<span data-ttu-id="19529-151">Sloupec není napsán v výstup XML.</span><span class="sxs-lookup"><span data-stu-id="19529-151">The column is not written in the XML output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19529-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="19529-152">See Also</span></span>  
 [<span data-ttu-id="19529-153">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="19529-153">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="19529-154">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="19529-154">DiffGrams</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [<span data-ttu-id="19529-155">Vnoření datových relací</span><span class="sxs-lookup"><span data-stu-id="19529-155">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [<span data-ttu-id="19529-156">Zápis informací o schématu datové sady jako XSD</span><span class="sxs-lookup"><span data-stu-id="19529-156">Writing DataSet Schema Information as XSD</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 [<span data-ttu-id="19529-157">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="19529-157">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="19529-158">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="19529-158">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
