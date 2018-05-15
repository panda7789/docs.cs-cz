---
title: Načítání informací o schématu sady dat z XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 4b212a7233e6eec93cdce3e521b58e08745e35e0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="871a6-102">Načítání informací o schématu sady dat z XML</span><span class="sxs-lookup"><span data-stu-id="871a6-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="871a6-103">Schéma <xref:System.Data.DataSet> (jeho tabulek, sloupců, vztahů a omezení) je možné definovat prostřednictvím kódu programu, vytvořené **vyplnění** nebo **FillSchema** metody <xref:System.Data.Common.DataAdapter>, nebo načíst z Dokument XML.</span><span class="sxs-lookup"><span data-stu-id="871a6-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="871a6-104">Načíst **datovou sadu** informace o schématu z dokumentu XML, můžete použít buď **ReadXmlSchema** nebo **InferXmlSchema** metodu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="871a6-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="871a6-105">**ReadXmlSchema** umožňuje načíst nebo odvození **datovou sadu** informace o schématu z dokumentu obsahující schématu XML definition language (XSD) schématu nebo dokumentu XML se vloženého schématu XML.</span><span class="sxs-lookup"><span data-stu-id="871a6-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="871a6-106">**InferXmlSchema** umožňuje odvození schématu z dokumentu XML při ignoruje určité obory názvů XML, který určíte.</span><span class="sxs-lookup"><span data-stu-id="871a6-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="871a6-107">Řazení v tabulce **datovou sadu** nemusí být zachová, i když používáte webové služby nebo serializace XML pro přenos **datovou sadu** v paměti, byla vytvořena pomocí XSD konstruktory (jako jsou vnořené relace).</span><span class="sxs-lookup"><span data-stu-id="871a6-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="871a6-108">Proto příjemce **datovou sadu** by neměl závisí na tabulky v tomto případě řazení.</span><span class="sxs-lookup"><span data-stu-id="871a6-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="871a6-109">Ale tabulky pořadí je vždy zachováno Pokud schéma **datovou sadu** přenášení byl načten z XSD souborů, namísto vytváří v paměti.</span><span class="sxs-lookup"><span data-stu-id="871a6-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="871a6-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="871a6-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="871a6-111">Načíst schéma **datovou sadu** z dokumentu XML bez načítání žádná data, můžete použít **ReadXmlSchema** metodu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="871a6-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="871a6-112">**ReadXmlSchema** vytvoří **datovou sadu** schéma definované pomocí schématu XML definition language (XSD) schématu.</span><span class="sxs-lookup"><span data-stu-id="871a6-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="871a6-113">**ReadXmlSchema** metoda přebírá jediný argument název souboru, datového proudu, nebo **XmlReader** obsahující dokument XML, který má být načten.</span><span class="sxs-lookup"><span data-stu-id="871a6-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="871a6-114">V dokumentu XML může obsahovat pouze schématu, nebo může obsahovat vložené schéma s elementů XML obsahující data.</span><span class="sxs-lookup"><span data-stu-id="871a6-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="871a6-115">Podrobnosti o zápis vloženého schématu jako schématu XML najdete v tématu [odvozování relační strukturu datové sady z schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="871a6-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="871a6-116">Pokud v dokumentu XML předaný **ReadXmlSchema** obsahuje žádné informace o schématu vložené **ReadXmlSchema** schéma z elementů v dokumentu XML odvodí.</span><span class="sxs-lookup"><span data-stu-id="871a6-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="871a6-117">Pokud **datovou sadu** již obsahuje schéma, bude aktuální schéma rozšířeno přidáním nové tabulky, pokud dosud neexistují.</span><span class="sxs-lookup"><span data-stu-id="871a6-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="871a6-118">Nové sloupce nebudou přidány do přidat do existující tabulky.</span><span class="sxs-lookup"><span data-stu-id="871a6-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="871a6-119">Pokud sloupec se přidat, již existuje v **datovou sadu** , ale má nekompatibilní typ se sloupcem nalezen v souboru XML, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="871a6-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="871a6-120">Podrobnosti o **ReadXmlSchema** odvodí schématu z dokumentu XML, najdete na stránce [odvození datovou sadu relační struktura z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="871a6-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="871a6-121">I když **ReadXmlSchema** načte nebo odvodí pouze schéma **datovou sadu**, **ReadXml** metodu **datovou sadu** načte nebo odvodí, že oba schéma a data obsažená v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="871a6-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="871a6-122">Další informace najdete v tématu [načítání datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="871a6-122">For more information, see [Loading a DataSet from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="871a6-123">Následující příklady kódu ukazují, jak načíst **datovou sadu** schématu z dokumentu XML nebo datový proud.</span><span class="sxs-lookup"><span data-stu-id="871a6-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="871a6-124">V prvním příkladu zobrazuje název souboru schématu XML je předán **ReadXmlSchema** metoda.</span><span class="sxs-lookup"><span data-stu-id="871a6-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="871a6-125">Druhý příklad ukazuje **System.IO.StreamReader**.</span><span class="sxs-lookup"><span data-stu-id="871a6-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As System.IO.StreamReader = New System.IO.StreamReader ("schema.xsd");  
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
  
## <a name="inferxmlschema"></a><span data-ttu-id="871a6-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="871a6-126">InferXmlSchema</span></span>  
 <span data-ttu-id="871a6-127">Můžete také určit, aby **datovou sadu** odvodit jeho schématu z dokumentu XML pomocí **InferXmlSchema** metodu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="871a6-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="871a6-128">**InferXmlSchema** funguje stejně jako proveďte obojí **ReadXml** s **XmlReadMode** z **InferSchema** (načte data a také odvodí, že schéma) a **ReadXmlSchema** Pokud žádné vložené schéma obsahuje dokument, který je čten.</span><span class="sxs-lookup"><span data-stu-id="871a6-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="871a6-129">Ale **InferXmlSchema** poskytuje další možnost umožňuje zadat konkrétní obory názvů XML, který se má ignorovat při je odvodit schématu.</span><span class="sxs-lookup"><span data-stu-id="871a6-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="871a6-130">**InferXmlSchema** má dva vyžaduje argumenty: umístění v dokumentu XML určeného názvu souboru datového proudu, nebo **XmlReader**; a obory názvů XML, který se má ignorovat operací pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="871a6-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="871a6-131">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="871a6-131">For example, consider the following XML:</span></span>  
  
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
  
 <span data-ttu-id="871a6-132">Z důvodu atributy určené pro prvky v předchozí dokument XML jak **ReadXmlSchema** metoda a **ReadXml** metoda s **XmlReadMode** z **InferSchema** by vytváření tabulek pro každý element v dokumentu: **kategorie**, **CategoryID**, **CategoryName**, **Popis**, **produkty**, **ProductID**, **MinimálníÚroveň**, a **zastaví**.</span><span class="sxs-lookup"><span data-stu-id="871a6-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="871a6-133">(Další informace najdete v tématu [odvození datovou sadu relační struktura z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) Však může být vhodnější struktura vytvořit jenom **kategorie** a **produkty** tabulky a pak vytvořit **CategoryID**, **CategoryName** , a **popis** sloupců v **kategorie** tabulky, a **ProductID**, **MinimálníÚroveň**, a **Nákup ukončen** sloupců v **produkty** tabulky.</span><span class="sxs-lookup"><span data-stu-id="871a6-133">(For more information, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="871a6-134">K zajištění, že schéma odvozené ignoruje atributy určené v elementy XML, použijte **InferXmlSchema** metoda a zadejte obor názvů XML pro **officedata** budou ignorovány, jak je znázorněno Následující příklad.</span><span class="sxs-lookup"><span data-stu-id="871a6-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="871a6-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="871a6-135">See Also</span></span>  
 [<span data-ttu-id="871a6-136">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="871a6-136">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="871a6-137">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="871a6-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="871a6-138">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="871a6-138">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="871a6-139">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="871a6-139">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="871a6-140">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="871a6-140">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="871a6-141">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="871a6-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
