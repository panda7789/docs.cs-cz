---
title: Načtení datové sady z XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 4c8b26651a1f4050145b6d43e03f9d4cc3d68202
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785278"
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="7234a-102">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="7234a-102">Loading a DataSet from XML</span></span>
<span data-ttu-id="7234a-103">Obsah ADO.NET <xref:System.Data.DataSet> lze vytvořit z datového proudu XML nebo dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7234a-103">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="7234a-104">Kromě toho s .NET Framework máte skvělou flexibilitu nad tím, které informace jsou načteny z XML a jak se vytváří schéma nebo relační struktura <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="7234a-104">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="7234a-105">Chcete-li <xref:System.Data.DataSet> vyplnit data z XML, použijte metodu <xref:System.Data.DataSet> ReadXml objektu.</span><span class="sxs-lookup"><span data-stu-id="7234a-105">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="7234a-106">Metoda **ReadXml** čte ze souboru, datového proudu nebo objektu **XmlReader**a přijímá jako argumenty zdroj XML a volitelný argument **XmlReadMode** .</span><span class="sxs-lookup"><span data-stu-id="7234a-106">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="7234a-107">Další informace o objektu **XmlReader**najdete v tématu věnovaném [čtení dat XML pomocí třídy XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7234a-107">For more information about the **XmlReader**, see [Reading XML Data with XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span></span> <span data-ttu-id="7234a-108">Metoda **ReadXml** čte obsah datového proudu XML nebo dokumentu a načítá <xref:System.Data.DataSet> data.</span><span class="sxs-lookup"><span data-stu-id="7234a-108">The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="7234a-109">Vytvoří také relační schéma <xref:System.Data.DataSet> v závislosti na zadané **XmlReadMode** a nezávisle na tom, zda relační schéma již existuje.</span><span class="sxs-lookup"><span data-stu-id="7234a-109">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="7234a-110">Následující tabulka popisuje možnosti pro argument **XmlReadMode** .</span><span class="sxs-lookup"><span data-stu-id="7234a-110">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="7234a-111">Možnost</span><span class="sxs-lookup"><span data-stu-id="7234a-111">Option</span></span>|<span data-ttu-id="7234a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7234a-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7234a-113">**Auto**</span><span class="sxs-lookup"><span data-stu-id="7234a-113">**Auto**</span></span>|<span data-ttu-id="7234a-114">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="7234a-114">This is the default.</span></span> <span data-ttu-id="7234a-115">Ověří XML a zvolí nejvhodnější možnost v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="7234a-115">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="7234a-116">– Pokud je kód XML formátu DiffGram, použije se formát **DiffGram** .</span><span class="sxs-lookup"><span data-stu-id="7234a-116">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="7234a-117">– Pokud <xref:System.Data.DataSet> obsahuje schéma nebo XML obsahuje vložené schéma, použije se **ReadSchema** .</span><span class="sxs-lookup"><span data-stu-id="7234a-117">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="7234a-118">– Pokud <xref:System.Data.DataSet> neobsahuje schéma a XML neobsahuje vložené schéma, použije se **InferSchema** .</span><span class="sxs-lookup"><span data-stu-id="7234a-118">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="7234a-119">Pokud znáte formát XML, který je právě čten, doporučujeme pro nejlepší výkon nastavit explicitní **XmlReadMode**místo toho, abyste přijali **Automatické** výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7234a-119">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="7234a-120">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="7234a-120">**ReadSchema**</span></span>|<span data-ttu-id="7234a-121">Přečte jakékoli vložené schéma a načte data a schéma.</span><span class="sxs-lookup"><span data-stu-id="7234a-121">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="7234a-122">Pokud již schéma obsahuje, přidají se nové tabulky z vloženého schématu do stávajícího schématu <xref:System.Data.DataSet>v. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="7234a-122">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7234a-123">Pokud některé tabulky ve vloženém schématu již existují v <xref:System.Data.DataSet>, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="7234a-123">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="7234a-124">Schéma existující tabulky nebudete moct změnit pomocí **XmlReadMode. ReadSchema**.</span><span class="sxs-lookup"><span data-stu-id="7234a-124">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="7234a-125"><xref:System.Data.DataSet> Pokud neobsahuje schéma a není k dispozici žádné vložené schéma, nebudou čtena žádná data.</span><span class="sxs-lookup"><span data-stu-id="7234a-125">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="7234a-126">Vložené schéma lze definovat pomocí schématu XML Schema Definition Language (XSD).</span><span class="sxs-lookup"><span data-stu-id="7234a-126">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="7234a-127">Podrobnosti o zápisu vloženého schématu jako schématu XML naleznete v tématu [odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="7234a-127">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="7234a-128">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="7234a-128">**IgnoreSchema**</span></span>|<span data-ttu-id="7234a-129">Ignoruje všechna vložená schémata a načte data do stávajícího <xref:System.Data.DataSet> schématu.</span><span class="sxs-lookup"><span data-stu-id="7234a-129">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="7234a-130">Všechna data, která neodpovídají existujícímu schématu, budou zahozena.</span><span class="sxs-lookup"><span data-stu-id="7234a-130">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="7234a-131">Pokud v <xref:System.Data.DataSet>nástroji neexistuje žádné schéma, nejsou načtena žádná data.</span><span class="sxs-lookup"><span data-stu-id="7234a-131">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="7234a-132">Pokud jsou data formátem DiffGram, **ignoreschema** má stejné funkce jako formát **DiffGram** *.*</span><span class="sxs-lookup"><span data-stu-id="7234a-132">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="7234a-133">**InferSchema**</span><span class="sxs-lookup"><span data-stu-id="7234a-133">**InferSchema**</span></span>|<span data-ttu-id="7234a-134">Ignoruje všechna vložená schématu a odvodí schéma podle struktury dat XML a potom načte data.</span><span class="sxs-lookup"><span data-stu-id="7234a-134">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="7234a-135"><xref:System.Data.DataSet> Pokud již schéma obsahuje, aktuální schéma je rozšířeno přidáním sloupců do existujících tabulek.</span><span class="sxs-lookup"><span data-stu-id="7234a-135">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="7234a-136">Pokud nejsou k dispozici žádné tabulky, nebudou přidány další tabulky.</span><span class="sxs-lookup"><span data-stu-id="7234a-136">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="7234a-137">Výjimka je vyvolána, pokud již existuje odvozená tabulka s jiným oborem názvů, nebo pokud jsou všechny odvozené sloupce v konfliktu se stávajícími sloupci.</span><span class="sxs-lookup"><span data-stu-id="7234a-137">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="7234a-138">Podrobnosti o tom, jak **ReadXmlSchema** odvodí schéma z dokumentu XML, naleznete v tématu [odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7234a-138">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="7234a-139">**Formát**</span><span class="sxs-lookup"><span data-stu-id="7234a-139">**DiffGram**</span></span>|<span data-ttu-id="7234a-140">Přečte formát DiffGram a přidá data do aktuálního schématu.</span><span class="sxs-lookup"><span data-stu-id="7234a-140">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="7234a-141">Formát **DiffGram** sloučí nové řádky se stávajícími řádky, kde se shodují hodnoty jedinečného identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="7234a-141">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="7234a-142">Viz téma "sloučení dat z XML" na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="7234a-142">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="7234a-143">Další informace o formátech DiffGram naleznete v tématu [DiffGram](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="7234a-143">For more information about DiffGrams, see [DiffGrams](diffgrams.md).</span></span>|  
|<span data-ttu-id="7234a-144">**Zpomalen**</span><span class="sxs-lookup"><span data-stu-id="7234a-144">**Fragment**</span></span>|<span data-ttu-id="7234a-145">Pokračuje v čtení více fragmentů XML, dokud není dosaženo konce datového proudu.</span><span class="sxs-lookup"><span data-stu-id="7234a-145">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="7234a-146">Fragmenty, které <xref:System.Data.DataSet> odpovídají schématu, jsou připojeny k příslušným tabulkám.</span><span class="sxs-lookup"><span data-stu-id="7234a-146">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="7234a-147">Fragmenty, které neodpovídají <xref:System.Data.DataSet> schématu, jsou zahozeny.</span><span class="sxs-lookup"><span data-stu-id="7234a-147">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="7234a-148">Pokud předáte **třídu XmlReader** k **ReadXml** , která je umístěna do dokumentu XML, **ReadXml** se přečte do dalšího uzlu elementu a bude se považovat za kořenový prvek, který se bude načítat až do konce uzlu elementu.</span><span class="sxs-lookup"><span data-stu-id="7234a-148">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="7234a-149">To se nevztahuje, pokud zadáte **XmlReadMode. fragment**.</span><span class="sxs-lookup"><span data-stu-id="7234a-149">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="7234a-150">Entity DTD</span><span class="sxs-lookup"><span data-stu-id="7234a-150">DTD Entities</span></span>  
 <span data-ttu-id="7234a-151">Pokud váš kód XML obsahuje entity definované v rámci schématu definice typu dokumentu (DTD), bude vyvolána výjimka, pokud se pokusíte načíst objekt <xref:System.Data.DataSet> předáním názvu souboru, datového proudu nebo neověření objektu **XmlReader** do **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="7234a-151">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="7234a-152">Místo toho musíte vytvořit **XmlValidatingReader**s **EntityHandling** nastavenou na **EntityHandling. ExpandEntities**a předat **XmlValidatingReader** **ReadXml.**</span><span class="sxs-lookup"><span data-stu-id="7234a-152">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="7234a-153">**XmlValidatingReader** rozšíří entity před jejich čtením <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="7234a-153">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="7234a-154">Následující příklady kódu ukazují, jak načíst <xref:System.Data.DataSet> z datového proudu XML.</span><span class="sxs-lookup"><span data-stu-id="7234a-154">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="7234a-155">První příklad ukazuje název souboru předávaný do metody **ReadXml** .</span><span class="sxs-lookup"><span data-stu-id="7234a-155">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="7234a-156">Druhý příklad ukazuje řetězec, který obsahuje kód XML, který je načítán <xref:System.IO.StringReader>pomocí.</span><span class="sxs-lookup"><span data-stu-id="7234a-156">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
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
> <span data-ttu-id="7234a-157">Pokud zavoláte **ReadXml** , abyste načetli velmi velký soubor, může dojít ke zpomalení výkonu.</span><span class="sxs-lookup"><span data-stu-id="7234a-157">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="7234a-158">Pro zajištění nejlepšího výkonu pro **ReadXml**, ve velkém souboru volejte <xref:System.Data.DataTable.BeginLoadData%2A> metodu pro <xref:System.Data.DataSet>každou tabulku v a pak zavolejte **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="7234a-158">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="7234a-159">Nakonec zavolejte <xref:System.Data.DataTable.EndLoadData%2A> pro každou tabulku <xref:System.Data.DataSet>v, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7234a-159">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="7234a-160">Pokud schéma <xref:System.Data.DataSet> XSD pro váš obsahuje **obor názvů targetNamespace**, data pravděpodobně nebudou načtena a při volání **ReadXml** pro načtení <xref:System.Data.DataSet> kódu XML, který obsahuje prvky bez kvalifikovaného oboru názvů, může dojít k výjimkám.</span><span class="sxs-lookup"><span data-stu-id="7234a-160">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="7234a-161">Chcete-li v tomto případě číst nekvalifikované prvky, nastavte **elementFormDefault** ve schématu XSD na hodnotu kvalifikováno.</span><span class="sxs-lookup"><span data-stu-id="7234a-161">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="7234a-162">Příklad:</span><span class="sxs-lookup"><span data-stu-id="7234a-162">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="7234a-163">Slučování dat z XML</span><span class="sxs-lookup"><span data-stu-id="7234a-163">Merging Data from XML</span></span>  
 <span data-ttu-id="7234a-164">Pokud již data obsahují, jsou nová data z XML přidána do dat, která jsou již přítomna <xref:System.Data.DataSet>v nástroji. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="7234a-164">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7234a-165">**ReadXml** se nesloučí z kódu XML do <xref:System.Data.DataSet> žádné informace o řádku s vyhovujícími primárními klíči.</span><span class="sxs-lookup"><span data-stu-id="7234a-165">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="7234a-166">Chcete-li přepsat stávající informace o řádcích novými informacemi z XML, vytvořte pomocí **ReadXml** nové <xref:System.Data.DataSet>a pak <xref:System.Data.DataSet.Merge%2A> nový <xref:System.Data.DataSet> do existující <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="7234a-166">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7234a-167">Všimněte si, že načtení formátu DiffGram pomocí **ReadXml** s **XmlReadModeem** formátu **DiffGram** sloučí řádky, které mají stejný jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="7234a-167">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7234a-168">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7234a-168">See also</span></span>

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7234a-169">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="7234a-169">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="7234a-170">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="7234a-170">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="7234a-171">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="7234a-171">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="7234a-172">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="7234a-172">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="7234a-173">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="7234a-173">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="7234a-174">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="7234a-174">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="7234a-175">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7234a-175">ADO.NET Overview</span></span>](../ado-net-overview.md)
