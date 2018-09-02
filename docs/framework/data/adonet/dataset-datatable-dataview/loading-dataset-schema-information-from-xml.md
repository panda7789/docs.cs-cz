---
title: Načítání informací o schématu datové sady z XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: a076dcbbe79a7ec0dfbd727e0d0c752bd4675eef
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398603"
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="30b91-102">Načítání informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="30b91-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="30b91-103">Schéma <xref:System.Data.DataSet> (jeho tabulky, sloupce, relace a omezení) lze definovat prostřednictvím kódu programu, vytvořené **vyplnit** nebo **FillSchema** metody <xref:System.Data.Common.DataAdapter>, nebo načtena z Dokument XML.</span><span class="sxs-lookup"><span data-stu-id="30b91-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="30b91-104">Načíst **datovou sadu** informace o schématu z dokumentu XML, můžete použít buď **ReadXmlSchema** nebo **InferXmlSchema** metodu **datovésady**.</span><span class="sxs-lookup"><span data-stu-id="30b91-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="30b91-105">**ReadXmlSchema** umožňuje načíst nebo odvodit **datovou sadu** informace o schématu z dokumentu obsahující jazyk (XSD) schématu definice schématu XML nebo dokument XML s vloženého schématu XML.</span><span class="sxs-lookup"><span data-stu-id="30b91-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="30b91-106">**InferXmlSchema** umožňuje odvození schématu z dokumentu XML při ignoruje některé obory názvů XML, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="30b91-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30b91-107">Pořadí v tabulce **datovou sadu** nemusí být zachová, i když používáte webové služby nebo serializace XML pro přenos **datovou sadu** v paměti, který byl vytvořen pomocí konstrukce XSD (například vnořené relace).</span><span class="sxs-lookup"><span data-stu-id="30b91-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="30b91-108">Proto příjemce **datovou sadu** neměli spoléhat na tabulky v tomto případě řazení.</span><span class="sxs-lookup"><span data-stu-id="30b91-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="30b91-109">Ale tabulka pořadí je vždy zachováno Pokud schéma **datovou sadu** přenášených byl načten z soubory XSD, namísto vytváření v paměti.</span><span class="sxs-lookup"><span data-stu-id="30b91-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="30b91-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="30b91-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="30b91-111">Načíst schéma **datovou sadu** z dokumentu XML bez načtení všech dat, můžete použít **ReadXmlSchema** metodu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="30b91-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="30b91-112">**ReadXmlSchema** vytvoří **datovou sadu** schéma, které jsou definovány pomocí jazyk (XSD) schématu definice schématu XML.</span><span class="sxs-lookup"><span data-stu-id="30b91-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="30b91-113">**ReadXmlSchema** metoda přijímá jeden argument názvu souboru datového proudu, nebo **XmlReader** obsahující dokumentu XML, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="30b91-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="30b91-114">Dokument XML může obsahovat pouze schéma, nebo může obsahovat vložené schéma elementů XML obsahující data.</span><span class="sxs-lookup"><span data-stu-id="30b91-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="30b91-115">Podrobnosti o vytváření vložené schéma jako schématu XML, naleznete v tématu [odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="30b91-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="30b91-116">Pokud dokument XML předán **ReadXmlSchema** neobsahuje žádné informace o schématu vložené **ReadXmlSchema** odvodí schéma z prvků v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="30b91-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="30b91-117">Pokud **datovou sadu** již obsahuje schéma s aktuální schéma rozšíříme přidáním nové tabulky, pokud ještě neexistují.</span><span class="sxs-lookup"><span data-stu-id="30b91-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="30b91-118">Nové sloupce nebude přidán do přidat do existující tabulky.</span><span class="sxs-lookup"><span data-stu-id="30b91-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="30b91-119">Pokud již přidán sloupec existuje v **datovou sadu** , ale má nekompatibilní typ se sloupcem nalezen v souboru XML, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="30b91-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="30b91-120">Podrobné informace o tom **ReadXmlSchema** odvodí schéma z dokumentu XML, naleznete v tématu [odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="30b91-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="30b91-121">I když **ReadXmlSchema** načte nebo odvodí schéma z **datovou sadu**, **ReadXml** metodu **datovou sadu** načte nebo odvodí obojí schéma a data obsažená v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="30b91-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="30b91-122">Další informace najdete v tématu [načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="30b91-122">For more information, see [Loading a DataSet from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="30b91-123">Následující příklady kódu ukazují, jak načíst **datovou sadu** schématu z dokumentu XML nebo datového proudu.</span><span class="sxs-lookup"><span data-stu-id="30b91-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="30b91-124">První příklad ukazuje název souboru schématu XML předána **ReadXmlSchema** metody.</span><span class="sxs-lookup"><span data-stu-id="30b91-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="30b91-125">Druhý příklad ukazuje **System.IO.StreamReader**.</span><span class="sxs-lookup"><span data-stu-id="30b91-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
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
  
## <a name="inferxmlschema"></a><span data-ttu-id="30b91-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="30b91-126">InferXmlSchema</span></span>  
 <span data-ttu-id="30b91-127">Můžete taky nastavit **datovou sadu** odvodit jeho schématu z dokumentu XML pomocí **InferXmlSchema** metodu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="30b91-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="30b91-128">**InferXmlSchema** funguje stejně jako obojí **ReadXml** s **XmlReadMode** z **InferSchema** (načte data stejně jako odvodí schéma) a **ReadXmlSchema** Pokud dokument čtená neobsahuje žádné vložené schéma.</span><span class="sxs-lookup"><span data-stu-id="30b91-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="30b91-129">Ale **InferXmlSchema** poskytuje další možnost umožňuje zadat konkrétní obory názvů XML ignorován odvodit schéma.</span><span class="sxs-lookup"><span data-stu-id="30b91-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="30b91-130">**InferXmlSchema** přebírá dva argumenty požadované: umístění dokumentu XML, které jsou určeny názvem souboru, datový proud nebo **XmlReader**; a pole řetězců oborů názvů XML pro operaci ignorovat.</span><span class="sxs-lookup"><span data-stu-id="30b91-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="30b91-131">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="30b91-131">For example, consider the following XML:</span></span>  
  
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
  
 <span data-ttu-id="30b91-132">Z důvodu atributy určené pro prvky v předchozí dokument XML jak **ReadXmlSchema** metoda a **ReadXml** metodu s **XmlReadMode** z **InferSchema** by vytvoření tabulek pro každý prvek v dokumentu: **kategorie**, **CategoryID**, **CategoryName**, **Popis**, **produkty**, **ProductID**, **MinimálníÚroveň**, a **ukončena**.</span><span class="sxs-lookup"><span data-stu-id="30b91-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="30b91-133">(Další informace najdete v tématu [odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) Však může být vhodnější struktura vytvořit pouze **kategorie** a **produkty** tabulky a pak vytvořte **CategoryID**, **CategoryName** , a **popis** sloupců **kategorie** tabulky, a **ProductID**, **MinimálníÚroveň**, a **Vyřazeno** sloupců **produkty** tabulky.</span><span class="sxs-lookup"><span data-stu-id="30b91-133">(For more information, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="30b91-134">K zajištění, že odvozené schématu ignoruje atributy určené v elementů XML, použijte **InferXmlSchema** – metoda a určete obor názvů XML pro **officedata** ignorovány, jak je znázorněno Následující příklad.</span><span class="sxs-lookup"><span data-stu-id="30b91-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="30b91-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="30b91-135">See Also</span></span>  
 [<span data-ttu-id="30b91-136">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="30b91-136">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="30b91-137">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="30b91-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="30b91-138">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="30b91-138">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="30b91-139">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="30b91-139">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="30b91-140">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="30b91-140">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="30b91-141">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="30b91-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
