---
title: Načtení datové sady z XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: c21ed3bb31add285d64272040680433fff4e16fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151062"
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="d7fbb-102">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="d7fbb-102">Loading a DataSet from XML</span></span>
<span data-ttu-id="d7fbb-103">Obsah ADO.NET <xref:System.Data.DataSet> lze vytvořit z datového proudu XML nebo dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-103">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="d7fbb-104">Kromě toho s rozhraním .NET Framework máte velkou flexibilitu nad tím, jaké informace jsou načteny z XML a jak <xref:System.Data.DataSet> je vytvořeno schéma nebo relační struktura.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-104">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="d7fbb-105">Chcete-li <xref:System.Data.DataSet> vyplnit data z XML, použijte <xref:System.Data.DataSet> metodu **ReadXml** objektu.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-105">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="d7fbb-106">Metoda **ReadXml** čte ze souboru, datového proudu nebo **xmlreaderu**a bere jako argumenty zdroj xml a volitelný argument **XmlReadMode.**</span><span class="sxs-lookup"><span data-stu-id="d7fbb-106">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="d7fbb-107">Další informace o **aplikaci XmlReader**naleznete v [tématu Čtení dat XML pomocí aplikace XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d7fbb-107">For more information about the **XmlReader**, see [Reading XML Data with XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span></span> <span data-ttu-id="d7fbb-108">Metoda **ReadXml** přečte obsah datového proudu XML <xref:System.Data.DataSet> nebo dokumentu a načte data.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-108">The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="d7fbb-109">Vytvoří také relační schéma <xref:System.Data.DataSet> v závislosti na zadaném **xmlreadmode** a zda již existuje relační schéma.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-109">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="d7fbb-110">Následující tabulka popisuje možnosti argumentu **XmlReadMode.**</span><span class="sxs-lookup"><span data-stu-id="d7fbb-110">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="d7fbb-111">Možnost</span><span class="sxs-lookup"><span data-stu-id="d7fbb-111">Option</span></span>|<span data-ttu-id="d7fbb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d7fbb-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d7fbb-113">**Automaticky**</span><span class="sxs-lookup"><span data-stu-id="d7fbb-113">**Auto**</span></span>|<span data-ttu-id="d7fbb-114">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-114">This is the default.</span></span> <span data-ttu-id="d7fbb-115">Zkontroluje XML a vybere nejvhodnější možnost v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="d7fbb-115">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="d7fbb-116">- Pokud je XML DiffGram, použije se **DiffGram.**</span><span class="sxs-lookup"><span data-stu-id="d7fbb-116">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="d7fbb-117">- Pokud <xref:System.Data.DataSet> obsahuje schéma nebo XML obsahuje inline schéma, **readschema** se používá.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-117">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="d7fbb-118">- Pokud <xref:System.Data.DataSet> neobsahuje schéma a XML neobsahuje inline schéma, **inferSchema** se používá.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-118">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="d7fbb-119">Pokud znáte formát přečteného jazyka XML, doporučujeme pro dosažení nejlepšího výkonu nastavit explicitní **režim XmlReadMode**, nikoli **přijmout výchozí hodnotu Automaticky.**</span><span class="sxs-lookup"><span data-stu-id="d7fbb-119">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="d7fbb-120">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="d7fbb-120">**ReadSchema**</span></span>|<span data-ttu-id="d7fbb-121">Přečte libovolné vložkové schéma a načte data a schéma.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-121">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="d7fbb-122">Pokud <xref:System.Data.DataSet> již obsahuje schéma, nové tabulky jsou přidány z inline schématu do existujícího schématu <xref:System.Data.DataSet>v .</span><span class="sxs-lookup"><span data-stu-id="d7fbb-122">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="d7fbb-123">Pokud všechny tabulky v inline schématu již <xref:System.Data.DataSet>existují v , je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-123">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="d7fbb-124">Schéma existující tabulky nebude možné upravit pomocí **souboru XmlReadMode.ReadSchema**.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-124">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="d7fbb-125">Pokud <xref:System.Data.DataSet> neobsahuje schéma a neexistuje žádné inline schéma, jsou přečtena žádná data.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-125">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="d7fbb-126">Inline schéma lze definovat pomocí schématu definice schématu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="d7fbb-126">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="d7fbb-127">Podrobnosti o zápisu vřádnického schématu jako schématu XML naleznete v [tématu Deriving DataSet Relační struktura ze schématu XML (XSD).](deriving-dataset-relational-structure-from-xml-schema-xsd.md)</span><span class="sxs-lookup"><span data-stu-id="d7fbb-127">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="d7fbb-128">**Ignorujíschema**</span><span class="sxs-lookup"><span data-stu-id="d7fbb-128">**IgnoreSchema**</span></span>|<span data-ttu-id="d7fbb-129">Ignoruje jakékoli vložkové schéma a načte <xref:System.Data.DataSet> data do existujícího schématu.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-129">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="d7fbb-130">Všechna data, která neodpovídá existujícímu schématu, jsou zahozena.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-130">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="d7fbb-131">Pokud v souboru <xref:System.Data.DataSet>neexistuje žádné schéma , nebudou načtena žádná data.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-131">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="d7fbb-132">Pokud data je DiffGram, **IgnoreSchema** má stejné funkce jako **DiffGram** *.*</span><span class="sxs-lookup"><span data-stu-id="d7fbb-132">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="d7fbb-133">**InferSchema**</span><span class="sxs-lookup"><span data-stu-id="d7fbb-133">**InferSchema**</span></span>|<span data-ttu-id="d7fbb-134">Ignoruje jakékoli vložkové schéma a odvodí schéma podle struktury dat XML a pak data načte.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-134">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="d7fbb-135">Pokud <xref:System.Data.DataSet> již obsahuje schéma, aktuální schéma je rozšířeno přidáním sloupců do existujících tabulek.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-135">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="d7fbb-136">Další tabulky nebudou přidány, pokud neexistují existující tabulky.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-136">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="d7fbb-137">Výjimka je vyvolána, pokud odvozená tabulka již existuje s jiným oborem názvů nebo pokud jsou odvozené sloupce v konfliktu s existujícími sloupci.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-137">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="d7fbb-138">Podrobnosti o tom, jak **ReadXmlSchema** odvozuje schéma z dokumentu XML, naleznete [v tématu Odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d7fbb-138">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="d7fbb-139">**Diffgram**</span><span class="sxs-lookup"><span data-stu-id="d7fbb-139">**DiffGram**</span></span>|<span data-ttu-id="d7fbb-140">Přečte DiffGram a přidá data do aktuálního schématu.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-140">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="d7fbb-141">**DiffGram** sloučí nové řádky s existujícími řádky, kde se shodovat hodnoty jedinečného identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-141">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="d7fbb-142">Viz "Sloučení dat z XML" na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-142">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="d7fbb-143">Další informace o diffgrams naleznete v [tématu DiffGrams](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="d7fbb-143">For more information about DiffGrams, see [DiffGrams](diffgrams.md).</span></span>|  
|<span data-ttu-id="d7fbb-144">**Fragment**</span><span class="sxs-lookup"><span data-stu-id="d7fbb-144">**Fragment**</span></span>|<span data-ttu-id="d7fbb-145">Pokračuje ve čtení více fragmentů XML, dokud není dosaženo konce datového proudu.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-145">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="d7fbb-146">Fragmenty, které <xref:System.Data.DataSet> odpovídají schématu jsou připojeny k příslušné tabulky.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-146">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="d7fbb-147">Fragmenty, které neodpovídají schématu <xref:System.Data.DataSet> jsou zahozeny.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-147">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="d7fbb-148">Pokud předáte **XmlReader** **readxml,** který je umístěn část cesty do dokumentu XML, **ReadXml** bude číst do uzlu dalšího prvku a bude zacházet jako kořenový prvek, čtení až do konce uzlu elementu.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-148">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="d7fbb-149">To neplatí, pokud zadáte **XmlReadMode.Fragment**.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-149">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="d7fbb-150">DTD entity</span><span class="sxs-lookup"><span data-stu-id="d7fbb-150">DTD Entities</span></span>  
 <span data-ttu-id="d7fbb-151">Pokud váš jazyk XML obsahuje entity definované ve schématu definice typu dokumentu (DTD), bude vyvolána výjimka, pokud se pokusíte **XmlReader** načíst **ReadXml** <xref:System.Data.DataSet> soubor ud.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-151">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="d7fbb-152">Místo toho je nutné vytvořit **XmlValidatingReader**, s **EntityHandling** nastavena **na EntityHandling.ExpandEntities**a předat **XmlValidatingReader** **readxml**.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-152">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="d7fbb-153">**XmlValidatingReader** rozšíří entity před čtením <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-153">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="d7fbb-154">Následující příklady kódu ukazují, <xref:System.Data.DataSet> jak načíst datový proud XML.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-154">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="d7fbb-155">První příklad ukazuje název souboru předávaný metodě **ReadXml.**</span><span class="sxs-lookup"><span data-stu-id="d7fbb-155">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="d7fbb-156">Druhý příklad ukazuje řetězec, který obsahuje <xref:System.IO.StringReader>xml načtený pomocí .</span><span class="sxs-lookup"><span data-stu-id="d7fbb-156">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
> <span data-ttu-id="d7fbb-157">Pokud zavoláte **ReadXml** načíst velmi velký soubor, může dojít ke snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-157">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="d7fbb-158">Chcete-li zajistit nejlepší výkon pro **readxml** <xref:System.Data.DataTable.BeginLoadData%2A> , ve velkém <xref:System.Data.DataSet>souboru volejte metodu pro každou tabulku v oblasti aplikace a potom zavolejte **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-158">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="d7fbb-159">Nakonec volejte <xref:System.Data.DataTable.EndLoadData%2A> pro každou <xref:System.Data.DataSet>tabulku v , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-159">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
> <span data-ttu-id="d7fbb-160">Pokud schéma XSD pro vaše <xref:System.Data.DataSet> zahrnuje **targetNamespace**, data nemusí být číst a může dojít k výjimkám, při volání **ReadXml** načíst <xref:System.Data.DataSet> s XML, který obsahuje prvky bez opravňující obor názvů.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-160">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="d7fbb-161">Chcete-li číst neúplné prvky v tomto případě, nastavte **elementFormDefault** rovna "kvalifikované" ve schématu XSD.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-161">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="d7fbb-162">Například:</span><span class="sxs-lookup"><span data-stu-id="d7fbb-162">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="d7fbb-163">Sloučení dat z XML</span><span class="sxs-lookup"><span data-stu-id="d7fbb-163">Merging Data from XML</span></span>  
 <span data-ttu-id="d7fbb-164">Pokud <xref:System.Data.DataSet> již obsahuje data, nová data z XML se přidají <xref:System.Data.DataSet>k datům, která jsou již v rozhraní .</span><span class="sxs-lookup"><span data-stu-id="d7fbb-164">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="d7fbb-165">**ReadXml** se nesloučí <xref:System.Data.DataSet> z XML do žádné informace o řádku s odpovídající primární klíče.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-165">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="d7fbb-166">Chcete-li přepsat existující informace o řádcích novými informacemi z <xref:System.Data.DataSet.Merge%2A> XML, vytvořte pomocí **readxml** <xref:System.Data.DataSet>nového a potom nového <xref:System.Data.DataSet> do existujícího <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-166">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="d7fbb-167">Všimněte si, že načítání DiffGram pomocí **ReadXML** s **XmlReadMode** **DiffGram** sloučí řádky, které mají stejný jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="d7fbb-167">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7fbb-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7fbb-168">See also</span></span>

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d7fbb-169">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="d7fbb-169">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="d7fbb-170">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="d7fbb-170">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="d7fbb-171">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="d7fbb-171">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="d7fbb-172">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="d7fbb-172">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="d7fbb-173">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="d7fbb-173">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="d7fbb-174">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="d7fbb-174">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="d7fbb-175">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d7fbb-175">ADO.NET Overview</span></span>](../ado-net-overview.md)
