---
title: Načtení informací o schématu datové sady z XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: d834f0c4517f4ff9fe8645257d5a947c03893881
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968400"
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="a1264-102">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="a1264-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="a1264-103">Schéma <xref:System.Data.DataSet> (jeho tabulky, sloupce, relace a omezení) lze definovat programově, vytvořené metodami **Fill** nebo **FillSchema** <xref:System.Data.Common.DataAdapter>nebo načteny z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a1264-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="a1264-104">Chcete-li načíst informace o schématu **datové sady** z dokumentu XML, lze použít metodu **ReadXmlSchema** nebo **InferXmlSchema** pro **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="a1264-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="a1264-105">**ReadXmlSchema** umožňuje načíst nebo odvodit informace o schématu **datové sady** z dokumentu, který obsahuje schéma XSD (XML Schema Definition Language), nebo dokumentu XML s vloženým schématem XML.</span><span class="sxs-lookup"><span data-stu-id="a1264-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="a1264-106">**InferXmlSchema** umožňuje odvodit schéma z dokumentu XML a ignorovat určité obory názvů XML, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="a1264-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1264-107">Řazení tabulky v **sadě dat** nemusí být zachováno, pokud použijete webové služby nebo serializaci XML k přenosu **datové sady** , která byla vytvořena v paměti, pomocí konstrukcí XSD (jako jsou vnořené relace).</span><span class="sxs-lookup"><span data-stu-id="a1264-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="a1264-108">Proto by příjemce **datové sady** neměl záviset na řazení tabulky v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="a1264-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="a1264-109">Řazení tabulky je však vždy zachované, pokud je schéma přenášené **datové sady** načteno ze souborů XSD namísto vytvoření v paměti.</span><span class="sxs-lookup"><span data-stu-id="a1264-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="a1264-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="a1264-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="a1264-111">Chcete-li načíst schéma **datové sady** z dokumentu XML bez načtení dat, můžete použít metodu **ReadXmlSchema** **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="a1264-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="a1264-112">**ReadXmlSchema** vytvoří schéma **datové sady** definované pomocí schématu XSD (XML Schema Definition Language).</span><span class="sxs-lookup"><span data-stu-id="a1264-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="a1264-113">Metoda **ReadXmlSchema** přijímá jeden argument názvu souboru, datový proud nebo objekt **XMLREADER** obsahující dokument XML, který má být načten.</span><span class="sxs-lookup"><span data-stu-id="a1264-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="a1264-114">Dokument XML může obsahovat pouze schéma nebo může obsahovat schéma vložené s prvky XML obsahující data.</span><span class="sxs-lookup"><span data-stu-id="a1264-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="a1264-115">Podrobnosti o zápisu vloženého schématu jako schématu XML naleznete v tématu [odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="a1264-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="a1264-116">Pokud dokument XML předaný do **ReadXmlSchema** neobsahuje žádné vložené informace o schématu, **ReadXmlSchema** bude odvodit schéma z prvků v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a1264-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="a1264-117">Pokud **datová sada** již obsahuje schéma, aktuální schéma bude rozšířeno přidáním nových tabulek, pokud ještě neexistují.</span><span class="sxs-lookup"><span data-stu-id="a1264-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="a1264-118">Do existujících tabulek nebudou přidány nové sloupce.</span><span class="sxs-lookup"><span data-stu-id="a1264-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="a1264-119">Pokud již přidávaný sloupec v **datové sadě** existuje, ale má nekompatibilní typ se sloupcem nalezeným v kódu XML, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="a1264-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="a1264-120">Podrobnosti o tom, jak **ReadXmlSchema** odvodí schéma z dokumentu XML, naleznete v tématu [odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a1264-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="a1264-121">I když **ReadXmlSchema** načítá nebo odvodí pouze schéma **datové sady**, metoda **ReadXml** **datové sady** načte nebo odvodí schéma i data obsažená v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a1264-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="a1264-122">Další informace naleznete v tématu [načtení datové sady z XML](loading-a-dataset-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a1264-122">For more information, see [Loading a DataSet from XML](loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="a1264-123">Následující příklady kódu ukazují, jak načíst schéma **datové sady** z dokumentu XML nebo datového proudu.</span><span class="sxs-lookup"><span data-stu-id="a1264-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="a1264-124">První příklad ukazuje název souboru schématu XML, který je předán metodě **ReadXmlSchema** .</span><span class="sxs-lookup"><span data-stu-id="a1264-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="a1264-125">Druhý příklad ukazuje **System. IO. StreamReader**.</span><span class="sxs-lookup"><span data-stu-id="a1264-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As New System.IO.StreamReader("schema.xsd")
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a><span data-ttu-id="a1264-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="a1264-126">InferXmlSchema</span></span>  
 <span data-ttu-id="a1264-127">Můžete také instruovat **datovou sadu** , aby odvodit schéma z dokumentu XML pomocí metody **InferXmlSchema** **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="a1264-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="a1264-128">**InferXmlSchema** funguje stejně jako **ReadXml** s **XmlReadModeem** **InferSchema** (načítá data a také odvodit schéma) a **ReadXmlSchema** , pokud dokument, který čte, neobsahuje žádné vložené schéma.</span><span class="sxs-lookup"><span data-stu-id="a1264-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="a1264-129">**InferXmlSchema** však poskytuje další funkce, které vám umožní určit konkrétní obory názvů XML, které se mají ignorovat při odvození schématu.</span><span class="sxs-lookup"><span data-stu-id="a1264-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="a1264-130">**InferXmlSchema** přebírá dva povinné argumenty: umístění dokumentu XML, určené názvem souboru, datovým proudem nebo **XmlReader**; a pole řetězců pro obory názvů XML, které bude operace ignorovat.</span><span class="sxs-lookup"><span data-stu-id="a1264-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="a1264-131">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="a1264-131">For example, consider the following XML:</span></span>  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>   
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>   
  <Description od:adotype="203">Soft drinks and teas</Description>   
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>   
  <ReorderLevel od:adotype="3">10</ReorderLevel>   
  <Discontinued od:adotype="11">0</Discontinued>   
</Products>  
</NewDataSet>  
```  
  
 <span data-ttu-id="a1264-132">Vzhledem k tomu, že atributy zadané pro prvky v předchozím dokumentu XML, by metoda **ReadXmlSchema** a metoda **ReadXml** s **XmlReadModeem** **InferSchema** vytvořily tabulky pro každý prvek v dokumentu: **Categories**, **KódKategorie**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**a **ukončeno**.</span><span class="sxs-lookup"><span data-stu-id="a1264-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="a1264-133">(Další informace najdete v tématu [odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md).) Vhodnější strukturou je však vytvořit pouze tabulky **Categories** a **Products** a následně vytvořit sloupce **KódKategorie**, **CategoryName**a **Description** v tabulce **Categories** a sloupce **ProductID**, **ReorderLevel**a **vyřazené** sloupce v tabulce **Products** .</span><span class="sxs-lookup"><span data-stu-id="a1264-133">(For more information, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="a1264-134">Aby bylo zajištěno, že odvozené schéma ignoruje atributy zadané v elementech XML, použijte metodu **InferXmlSchema** a určete obor názvů XML pro **officedata** , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a1264-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1264-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1264-135">See also</span></span>

- [<span data-ttu-id="a1264-136">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="a1264-136">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="a1264-137">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="a1264-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="a1264-138">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="a1264-138">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="a1264-139">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="a1264-139">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="a1264-140">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="a1264-140">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="a1264-141">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a1264-141">ADO.NET Overview</span></span>](../ado-net-overview.md)
