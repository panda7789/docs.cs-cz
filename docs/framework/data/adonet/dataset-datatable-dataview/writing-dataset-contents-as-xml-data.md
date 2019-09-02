---
title: Kopírování obsahu datové sady jako dat XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: b8a8656bb68832a09490e656903fd68788bdeb1d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203109"
---
# <a name="writing-dataset-contents-as-xml-data"></a><span data-ttu-id="04137-102">Kopírování obsahu datové sady jako dat XML</span><span class="sxs-lookup"><span data-stu-id="04137-102">Writing DataSet Contents as XML Data</span></span>
<span data-ttu-id="04137-103">V ADO.NET můžete napsat reprezentace <xref:System.Data.DataSet>XML s, s jeho schématem nebo bez něj.</span><span class="sxs-lookup"><span data-stu-id="04137-103">In ADO.NET you can write an XML representation of a <xref:System.Data.DataSet>, with or without its schema.</span></span> <span data-ttu-id="04137-104">Pokud jsou informace o schématu zahrnuty do vloženého kódu XML, jsou zapsány pomocí jazyka XSD (XML Schema Definition Language).</span><span class="sxs-lookup"><span data-stu-id="04137-104">If schema information is included inline with the XML, it is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="04137-105">Schéma obsahuje definice <xref:System.Data.DataSet> tabulek a také definice vztahu a omezení.</span><span class="sxs-lookup"><span data-stu-id="04137-105">The schema contains the table definitions of the <xref:System.Data.DataSet> as well as the relation and constraint definitions.</span></span>  
  
 <span data-ttu-id="04137-106">Když je zapsán jako XML data, řádky <xref:System.Data.DataSet> v jsou zapsány v aktuálních verzích. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="04137-106">When a <xref:System.Data.DataSet> is written as XML data, the rows in the <xref:System.Data.DataSet> are written in their current versions.</span></span> <span data-ttu-id="04137-107"><xref:System.Data.DataSet> Lze však také zapsat jako formát formátu DiffGram, aby byly zahrnuty aktuální i původní hodnoty řádků.</span><span class="sxs-lookup"><span data-stu-id="04137-107">However, the <xref:System.Data.DataSet> can also be written as a DiffGram so that both the current and the original values of the rows will be included.</span></span>  
  
 <span data-ttu-id="04137-108">Reprezentace <xref:System.Data.DataSet> XML může být zapsána do souboru, datového proudu, **XmlWriter**nebo řetězce.</span><span class="sxs-lookup"><span data-stu-id="04137-108">The XML representation of the <xref:System.Data.DataSet> can be written to a file, a stream, an **XmlWriter**, or a string.</span></span> <span data-ttu-id="04137-109">Tyto možnosti poskytují skvělou flexibilitu při přenosu XML reprezentace <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="04137-109">These choices provide great flexibility for how you transport the XML representation of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="04137-110">Pro získání reprezentace <xref:System.Data.DataSet> XML jako řetězce použijte metodu **GetXml –** , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="04137-110">To obtain the XML representation of the <xref:System.Data.DataSet> as a string, use the **GetXml** method as shown in the following example.</span></span>  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 <span data-ttu-id="04137-111">**GetXml –** vrátí reprezentaci <xref:System.Data.DataSet> XML bez informací o schématu.</span><span class="sxs-lookup"><span data-stu-id="04137-111">**GetXml** returns the XML representation of the <xref:System.Data.DataSet> without schema information.</span></span> <span data-ttu-id="04137-112">Chcete-li zapsat informace o schématu <xref:System.Data.DataSet> ze schématu (jako schéma XML) do řetězce, použijte GetXmlSchema.</span><span class="sxs-lookup"><span data-stu-id="04137-112">To write the schema information from the <xref:System.Data.DataSet> (as XML Schema) to a string, use **GetXmlSchema**.</span></span>  
  
 <span data-ttu-id="04137-113">Chcete-li <xref:System.Data.DataSet> zapisovat do souboru, datového proudu nebo **XmlWriter**, použijte metodu **WriteXml** .</span><span class="sxs-lookup"><span data-stu-id="04137-113">To write a <xref:System.Data.DataSet> to a file, stream, or **XmlWriter**, use the **WriteXml** method.</span></span> <span data-ttu-id="04137-114">První parametr, který předáte metodě **WriteXml** , je cílem výstupu XML.</span><span class="sxs-lookup"><span data-stu-id="04137-114">The first parameter you pass to **WriteXml** is the destination of the XML output.</span></span> <span data-ttu-id="04137-115">Například předejte řetězec obsahující název souboru, **System. IO. TextWriter** a tak dále.</span><span class="sxs-lookup"><span data-stu-id="04137-115">For example, pass a string containing a file name, a **System.IO.TextWriter** object, and so on.</span></span> <span data-ttu-id="04137-116">Můžete předat volitelný druhý parametr **XmlWriteMode** , který určuje, jak se má zapsat výstup XML.</span><span class="sxs-lookup"><span data-stu-id="04137-116">You can pass an optional second parameter of an **XmlWriteMode** to specify how the XML output is to be written.</span></span>  
  
 <span data-ttu-id="04137-117">V následující tabulce jsou uvedeny možnosti pro **XmlWriteMode**.</span><span class="sxs-lookup"><span data-stu-id="04137-117">The following table shows the options for **XmlWriteMode**.</span></span>  
  
|<span data-ttu-id="04137-118">XmlWriteMode – možnost</span><span class="sxs-lookup"><span data-stu-id="04137-118">XmlWriteMode option</span></span>|<span data-ttu-id="04137-119">Popis</span><span class="sxs-lookup"><span data-stu-id="04137-119">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="04137-120">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="04137-120">**IgnoreSchema**</span></span>|<span data-ttu-id="04137-121">Zapíše aktuální obsah <xref:System.Data.DataSet> dat as XML bez schématu XML.</span><span class="sxs-lookup"><span data-stu-id="04137-121">Writes the current contents of the <xref:System.Data.DataSet> as XML data, without an XML Schema.</span></span> <span data-ttu-id="04137-122">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="04137-122">This is the default.</span></span>|  
|<span data-ttu-id="04137-123">**WriteSchema**</span><span class="sxs-lookup"><span data-stu-id="04137-123">**WriteSchema**</span></span>|<span data-ttu-id="04137-124">Zapíše aktuální obsah <xref:System.Data.DataSet> dat as XML do relační struktury jako vložené schéma XML.</span><span class="sxs-lookup"><span data-stu-id="04137-124">Writes the current contents of the <xref:System.Data.DataSet> as XML data with the relational structure as inline XML Schema.</span></span>|  
|<span data-ttu-id="04137-125">**Formát**</span><span class="sxs-lookup"><span data-stu-id="04137-125">**DiffGram**</span></span>|<span data-ttu-id="04137-126">Zapíše celý <xref:System.Data.DataSet> formát DiffGram, včetně původní a aktuální hodnoty.</span><span class="sxs-lookup"><span data-stu-id="04137-126">Writes the entire <xref:System.Data.DataSet> as a DiffGram, including original and current values.</span></span> <span data-ttu-id="04137-127">Další informace najdete v tématu formát [DiffGram](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="04137-127">For more information, see [DiffGrams](diffgrams.md).</span></span>|  
  
 <span data-ttu-id="04137-128">Při psaní reprezentace <xref:System.Data.DataSet> XML obsahující objekty DataRelation budete pravděpodobně chtít, aby výsledný kód XML měl podřízené řádky jednotlivých vztahů vnořené v rámci svých souvisejících nadřazených prvků.</span><span class="sxs-lookup"><span data-stu-id="04137-128">When writing an XML representation of a <xref:System.Data.DataSet> that contains **DataRelation** objects, you will most likely want the resulting XML to have the child rows of each relation nested within their related parent elements.</span></span> <span data-ttu-id="04137-129">Chcete-li toho dosáhnout, nastavte vnořenou vlastnost **DataRelation** na **hodnotu true** , když přidáte **DataRelation** do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="04137-129">To accomplish this, set the **Nested** property of the **DataRelation** to **true** when you add the **DataRelation** to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="04137-130">Další informace najdete v tématu [vnořování datových vztahů](nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="04137-130">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
 <span data-ttu-id="04137-131">Níže jsou uvedeny dva příklady zápisu reprezentace <xref:System.Data.DataSet> XML do souboru.</span><span class="sxs-lookup"><span data-stu-id="04137-131">Following are two examples of how to write the XML representation of a <xref:System.Data.DataSet> to a file.</span></span> <span data-ttu-id="04137-132">První příklad předá název souboru pro výsledný kód XML jako řetězec pro **WriteXml**.</span><span class="sxs-lookup"><span data-stu-id="04137-132">The first example passes the file name for the resulting XML as a string to **WriteXml**.</span></span> <span data-ttu-id="04137-133">Druhý příklad předává objekt **System. IO. StreamWriter** .</span><span class="sxs-lookup"><span data-stu-id="04137-133">The second example passes a **System.IO.StreamWriter** object.</span></span>  
  
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
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a><span data-ttu-id="04137-134">Mapování sloupců na elementy XML, atributy a text</span><span class="sxs-lookup"><span data-stu-id="04137-134">Mapping Columns to XML Elements, Attributes, and Text</span></span>  
 <span data-ttu-id="04137-135">Můžete určit způsob reprezentace sloupce tabulky v XML pomocí vlastnosti **ColumnMapping** objektu DataColumn.</span><span class="sxs-lookup"><span data-stu-id="04137-135">You can specify how a column of a table is represented in XML using the **ColumnMapping** property of the **DataColumn** object.</span></span> <span data-ttu-id="04137-136">V následující tabulce jsou uvedeny různé hodnoty **MappingType** pro vlastnost **ColumnMapping** sloupce tabulky a výsledný kód XML.</span><span class="sxs-lookup"><span data-stu-id="04137-136">The following table shows the different **MappingType** values for the **ColumnMapping** property of a table column, and the resulting XML.</span></span>  
  
|<span data-ttu-id="04137-137">Hodnota MappingType</span><span class="sxs-lookup"><span data-stu-id="04137-137">MappingType value</span></span>|<span data-ttu-id="04137-138">Popis</span><span class="sxs-lookup"><span data-stu-id="04137-138">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="04137-139">**Element**</span><span class="sxs-lookup"><span data-stu-id="04137-139">**Element**</span></span>|<span data-ttu-id="04137-140">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="04137-140">This is the default.</span></span> <span data-ttu-id="04137-141">Sloupec je zapsán jako XML element, kde ColumnName je název elementu a obsah sloupce je zapsán jako text elementu.</span><span class="sxs-lookup"><span data-stu-id="04137-141">The column is written as an XML element where the ColumnName is the name of the element and the contents of the column are written as the text of the element.</span></span> <span data-ttu-id="04137-142">Příklad:</span><span class="sxs-lookup"><span data-stu-id="04137-142">For example:</span></span><br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|<span data-ttu-id="04137-143">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="04137-143">**Attribute**</span></span>|<span data-ttu-id="04137-144">Sloupec je zapsán jako atribut XML elementu XML pro aktuální řádek, kde ColumnName je název atributu a obsah sloupce je zapsán jako hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="04137-144">The column is written as an XML attribute of the XML element for the current row where the ColumnName is the name of the attribute and the contents of the column are written as the value of the attribute.</span></span> <span data-ttu-id="04137-145">Příklad:</span><span class="sxs-lookup"><span data-stu-id="04137-145">For example:</span></span><br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|<span data-ttu-id="04137-146">**SimpleContent**</span><span class="sxs-lookup"><span data-stu-id="04137-146">**SimpleContent**</span></span>|<span data-ttu-id="04137-147">Obsah sloupce je zapsán jako text v elementu XML pro aktuální řádek.</span><span class="sxs-lookup"><span data-stu-id="04137-147">The contents of the column are written as text in the XML element for the current row.</span></span> <span data-ttu-id="04137-148">Příklad:</span><span class="sxs-lookup"><span data-stu-id="04137-148">For example:</span></span><br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> <span data-ttu-id="04137-149">Všimněte si, že **element simpleContent** nelze nastavit pro sloupec tabulky, která má sloupce elementů nebo vnořené relace.</span><span class="sxs-lookup"><span data-stu-id="04137-149">Note that **SimpleContent** cannot be set for a column of a table that has **Element** columns or nested relations.</span></span>|  
|<span data-ttu-id="04137-150">**Hidden**</span><span class="sxs-lookup"><span data-stu-id="04137-150">**Hidden**</span></span>|<span data-ttu-id="04137-151">Sloupec není napsaný ve výstupu XML.</span><span class="sxs-lookup"><span data-stu-id="04137-151">The column is not written in the XML output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04137-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04137-152">See also</span></span>

- [<span data-ttu-id="04137-153">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="04137-153">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="04137-154">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="04137-154">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="04137-155">Vnoření datových relací</span><span class="sxs-lookup"><span data-stu-id="04137-155">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="04137-156">Zápis informací o schématu datové sady jako XSD</span><span class="sxs-lookup"><span data-stu-id="04137-156">Writing DataSet Schema Information as XSD</span></span>](writing-dataset-schema-information-as-xsd.md)
- [<span data-ttu-id="04137-157">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="04137-157">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="04137-158">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="04137-158">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
