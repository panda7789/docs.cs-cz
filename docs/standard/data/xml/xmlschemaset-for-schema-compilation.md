---
title: "XmlSchemaSet pro kompilaci schématu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 193a9980bba423292921beff6c4c3172ce02fd92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xmlschemaset-for-schema-compilation"></a><span data-ttu-id="5a918-102">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="5a918-102">XmlSchemaSet for Schema Compilation</span></span>
<span data-ttu-id="5a918-103">Popisuje <xref:System.Xml.Schema.XmlSchemaSet>, mezipaměti, kde můžete ukládat a ověření schématu XML definition language (XSD) schémata.</span><span class="sxs-lookup"><span data-stu-id="5a918-103">Describes the <xref:System.Xml.Schema.XmlSchemaSet>, a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
## <a name="the-xmlschemaset-class"></a><span data-ttu-id="5a918-104">XmlSchemaSet – třída</span><span class="sxs-lookup"><span data-stu-id="5a918-104">The XmlSchemaSet Class</span></span>  
 <span data-ttu-id="5a918-105"><xref:System.Xml.Schema.XmlSchemaSet> Je mezipaměti, kde můžete ukládat a ověření schématu XML definition language (XSD) schémata.</span><span class="sxs-lookup"><span data-stu-id="5a918-105">The <xref:System.Xml.Schema.XmlSchemaSet> is a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
 <span data-ttu-id="5a918-106">V <xref:System.Xml?displayProperty=nameWithType> verze 1.0, schémat XML byly načteny do <xref:System.Xml.Schema.XmlSchemaCollection> třída jako Knihovna schémat.</span><span class="sxs-lookup"><span data-stu-id="5a918-106">In <xref:System.Xml?displayProperty=nameWithType> version 1.0, XML schemas were loaded into an <xref:System.Xml.Schema.XmlSchemaCollection> class as a library of schemas.</span></span> <span data-ttu-id="5a918-107">V <xref:System.Xml?displayProperty=nameWithType> verze 2.0, <xref:System.Xml.XmlValidatingReader> a <xref:System.Xml.Schema.XmlSchemaCollection> třídy jsou zastaralé a byly nahrazeny <xref:System.Xml.XmlReader.Create%2A> metody a <xref:System.Xml.Schema.XmlSchemaSet> třídy v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="5a918-107">In <xref:System.Xml?displayProperty=nameWithType> version 2.0, the <xref:System.Xml.XmlValidatingReader> and the <xref:System.Xml.Schema.XmlSchemaCollection> classes are obsolete, and have been replaced by the <xref:System.Xml.XmlReader.Create%2A> methods, and the <xref:System.Xml.Schema.XmlSchemaSet> class respectively.</span></span>  
  
 <span data-ttu-id="5a918-108"><xref:System.Xml.Schema.XmlSchemaSet> Je zavedený vyřešit řadu problémů, včetně kompatibility standardů, výkonu a zastaralé schéma formátu Microsoft XML-Data Reduced (XDR).</span><span class="sxs-lookup"><span data-stu-id="5a918-108">The <xref:System.Xml.Schema.XmlSchemaSet> has been introduced to fix a number of issues including standards compatibility, performance, and the obsolete Microsoft XML-Data Reduced (XDR) schema format.</span></span>  
  
 <span data-ttu-id="5a918-109">Následuje porovnání mezi <xref:System.Xml.Schema.XmlSchemaCollection> třídy a <xref:System.Xml.Schema.XmlSchemaSet> třídy.</span><span class="sxs-lookup"><span data-stu-id="5a918-109">The following is a comparison between the <xref:System.Xml.Schema.XmlSchemaCollection> class and the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span>  
  
|<span data-ttu-id="5a918-110">Kolekci XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="5a918-110">XmlSchemaCollection</span></span>|<span data-ttu-id="5a918-111">XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="5a918-111">XmlSchemaSet</span></span>|  
|-------------------------|------------------|  
|<span data-ttu-id="5a918-112">Podporuje Microsoft XDR a W3C schémat XML.</span><span class="sxs-lookup"><span data-stu-id="5a918-112">Supports Microsoft XDR and W3C XML schemas.</span></span>|<span data-ttu-id="5a918-113">Podporuje jenom schémata W3C XML.</span><span class="sxs-lookup"><span data-stu-id="5a918-113">Only supports W3C XML schemas.</span></span>|  
|<span data-ttu-id="5a918-114">Kompilované schémata při <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="5a918-114">Schemas are compiled when the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method is called.</span></span>|<span data-ttu-id="5a918-115">Schémata nejsou kompilovat, kdy <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="5a918-115">Schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span> <span data-ttu-id="5a918-116">To poskytuje zlepšení výkonu během vytváření knihovny schématu.</span><span class="sxs-lookup"><span data-stu-id="5a918-116">This provides a performance improvement during creation of the schema library.</span></span>|  
|<span data-ttu-id="5a918-117">Každý schématu generuje jednotlivých kompilované verze, která může mít za následek "schématu ostrovy."</span><span class="sxs-lookup"><span data-stu-id="5a918-117">Each schema generates an individual compiled version that can result in "schema islands."</span></span> <span data-ttu-id="5a918-118">V důsledku toho všechny zahrnuje a importy jsou vymezeny pouze v rámci tohoto schématu.</span><span class="sxs-lookup"><span data-stu-id="5a918-118">As a result, all includes and imports are scoped only within that schema.</span></span>|<span data-ttu-id="5a918-119">Kompilované schémata generovat jediné logické schéma, "set" schémat.</span><span class="sxs-lookup"><span data-stu-id="5a918-119">Compiled schemas generate a single logical schema, a "set" of schemas.</span></span> <span data-ttu-id="5a918-120">Importovaná schémata v rámci schématu, které jsou přidány do sady jsou přímo přidat do sady sami.</span><span class="sxs-lookup"><span data-stu-id="5a918-120">Any imported schemas within a schema that are added to the set are directly added to the set themselves.</span></span> <span data-ttu-id="5a918-121">To znamená, že všechny typy jsou k dispozici pro všechny schémat.</span><span class="sxs-lookup"><span data-stu-id="5a918-121">This means that all types are available to all schemas.</span></span>|  
|<span data-ttu-id="5a918-122">V kolekci může existovat pouze jedno schéma pro konkrétní cílový obor názvů.</span><span class="sxs-lookup"><span data-stu-id="5a918-122">Only one schema for a particular target namespace can exist in the collection.</span></span>|<span data-ttu-id="5a918-123">Více schématy pro stejný cílový obor názvů lze přidat, dokud nejsou konflikty typu.</span><span class="sxs-lookup"><span data-stu-id="5a918-123">Multiple schemas for the same target namespace can be added as long as there are no type conflicts.</span></span>|  
  
## <a name="migrating-to-the-xmlschemaset"></a><span data-ttu-id="5a918-124">Migrace na sadě XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="5a918-124">Migrating to the XmlSchemaSet</span></span>  
 <span data-ttu-id="5a918-125">Následující příklad kódu poskytuje návod k migraci na nové <xref:System.Xml.Schema.XmlSchemaSet> třídy z zastaralé <xref:System.Xml.Schema.XmlSchemaCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="5a918-125">The following code example provides a guide to migrating to the new <xref:System.Xml.Schema.XmlSchemaSet> class from the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class.</span></span> <span data-ttu-id="5a918-126">Příklad kódu ukazuje následující hlavní rozdíly mezi dvěma třídami.</span><span class="sxs-lookup"><span data-stu-id="5a918-126">The code example illustrates the following major differences between the two classes.</span></span>  
  
-   <span data-ttu-id="5a918-127">Na rozdíl od <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaCollection> třída, schémata nejsou kompilovány při volání metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="5a918-127">Unlike the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when calling the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="5a918-128"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Metodu <xref:System.Xml.Schema.XmlSchemaSet> je explicitně volána v ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="5a918-128">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is explicitly called in the example code.</span></span>  
  
-   <span data-ttu-id="5a918-129">Iterace nad <xref:System.Xml.Schema.XmlSchemaSet>, je nutné použít <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="5a918-129">To iterate over an <xref:System.Xml.Schema.XmlSchemaSet>, you must use the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="5a918-130">Toto je zastaralé <xref:System.Xml.Schema.XmlSchemaCollection> příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="5a918-130">The following is the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> code example.</span></span>  
  
```vb  
Dim schemaCollection As XmlSchemaCollection = New XmlSchemaCollection()  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema in schemaCollection  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaCollection schemaCollection = new XmlSchemaCollection();  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
  
foreach(XmlSchema schema in schemaCollection)  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
 <span data-ttu-id="5a918-131">Toto je ekvivalentem <xref:System.Xml.Schema.XmlSchemaSet> příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="5a918-131">The following is the equivalent <xref:System.Xml.Schema.XmlSchemaSet> code example.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim schema As XmlSchema  
  
For Each schema in schemaSet.Schemas()  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
foreach(XmlSchema schema in schemaSet.Schemas())  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
## <a name="adding-and-retrieving-schemas"></a><span data-ttu-id="5a918-132">Přidávání a načítání schémat.</span><span class="sxs-lookup"><span data-stu-id="5a918-132">Adding and Retrieving Schemas</span></span>  
 <span data-ttu-id="5a918-133">Schémata jsou přidány do <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="5a918-133">Schemas are added to an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="5a918-134">Po přidání schématu do <xref:System.Xml.Schema.XmlSchemaSet>, je přidružen cílový obor názvů identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="5a918-134">When a schema is added to an <xref:System.Xml.Schema.XmlSchemaSet>, it is associated with a target namespace URI.</span></span> <span data-ttu-id="5a918-135">Identifikátor URI, můžete buď zadat jako parametr pro cílový obor názvů <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda nebo pokud není zadán žádný cílový obor názvů, <xref:System.Xml.Schema.XmlSchemaSet> používá cílový obor názvů definováno ve schématu.</span><span class="sxs-lookup"><span data-stu-id="5a918-135">The target namespace URI can either be specified as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method or if no target namespace is specified, the <xref:System.Xml.Schema.XmlSchemaSet> uses the target namespace defined in the schema.</span></span>  
  
 <span data-ttu-id="5a918-136">Schémata jsou načteny z <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="5a918-136">Schemas are retrieved from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="5a918-137"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Vlastnost <xref:System.Xml.Schema.XmlSchemaSet> umožňuje iterace <xref:System.Xml.Schema.XmlSchema> objekty obsažené v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="5a918-137">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> allows you to iterate over the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="5a918-138"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Vlastnost vrací buď všechny <xref:System.Xml.Schema.XmlSchema> objekty obsažené v <xref:System.Xml.Schema.XmlSchemaSet>, nebo zadaný cílový obor názvů parametrů, vrátí všechny <xref:System.Xml.Schema.XmlSchema> objekty, které patří do cílový obor názvů.</span><span class="sxs-lookup"><span data-stu-id="5a918-138">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property either returns all the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>, or, given a target namespace parameter, returns all the <xref:System.Xml.Schema.XmlSchema> objects that belong to the target namespace.</span></span> <span data-ttu-id="5a918-139">Pokud `null` je zadána jako parametr cílový obor názvů <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost vrací všechny schémata bez oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5a918-139">If `null` is specified as the target namespace parameter, the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property returns all schemas without a namespace.</span></span>  
  
 <span data-ttu-id="5a918-140">Následující příklad přidá `books.xsd` schéma v `http://www.contoso.com/books` názvů <xref:System.Xml.Schema.XmlSchemaSet>, načte všechny schémat, které patří do `http://www.contoso.com/books` oboru názvů z <xref:System.Xml.Schema.XmlSchemaSet>a pak zapíše těchto schémat na <xref:System.Console>.</span><span class="sxs-lookup"><span data-stu-id="5a918-140">The following example adds the `books.xsd` schema in the `http://www.contoso.com/books` namespace to an <xref:System.Xml.Schema.XmlSchemaSet>, retrieves all schemas that belong to the `http://www.contoso.com/books` namespace from the <xref:System.Xml.Schema.XmlSchemaSet>, and then writes those schemas to the <xref:System.Console>.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas("http://www.contoso.com/books")  
  
   schema.Write(Console.Out)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas("http://www.contoso.com/books"))  
{  
   schema.Write(Console.Out);  
}  
```  
  
 <span data-ttu-id="5a918-141">Další informace o přidávání a načítání schémat ze <xref:System.Xml.Schema.XmlSchemaSet> objektu, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda a <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="5a918-141">For more information about adding and retrieving schemas from an <xref:System.Xml.Schema.XmlSchemaSet> object, see the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method and the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property reference documentation.</span></span>  
  
## <a name="compiling-schemas"></a><span data-ttu-id="5a918-142">Kompilování schémat.</span><span class="sxs-lookup"><span data-stu-id="5a918-142">Compiling Schemas</span></span>  
 <span data-ttu-id="5a918-143">Schémata v <xref:System.Xml.Schema.XmlSchemaSet> kompilovány do jednoho logického schématu pomocí <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="5a918-143">Schemas in an <xref:System.Xml.Schema.XmlSchemaSet> are compiled into one logical schema by the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a918-144">Na rozdíl od zastaralé <xref:System.Xml.Schema.XmlSchemaCollection> třídy, schémata nejsou kompilovat, kdy <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="5a918-144">Unlike the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span>  
  
 <span data-ttu-id="5a918-145">Pokud <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda provede úspěšně, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet> je nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="5a918-145">If the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method executes successfully, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a918-146"><xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> Vlastnost nemá vliv, pokud jsou upravit schémata během činnosti v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="5a918-146">The <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is not affected if schemas are edited while in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="5a918-147">Aktualizace v jednotlivých schémat <xref:System.Xml.Schema.XmlSchemaSet> nejsou sledovat.</span><span class="sxs-lookup"><span data-stu-id="5a918-147">Updates of the individual schemas in the <xref:System.Xml.Schema.XmlSchemaSet> are not tracked.</span></span> <span data-ttu-id="5a918-148">V důsledku toho <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> lze vlastnost `true` to i v případě, že jeden z schémat obsažené v <xref:System.Xml.Schema.XmlSchemaSet> byla změněna, tak dlouho, dokud se žádná schémata přidat nebo odebrat z <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="5a918-148">As a result, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property can be `true` even though one of the schemas contained in the <xref:System.Xml.Schema.XmlSchemaSet> has been altered, as long as no schemas were added or removed from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="5a918-149">Následující příklad přidá `books.xsd` do souboru <xref:System.Xml.Schema.XmlSchemaSet> a potom zavolá <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="5a918-149">The following example adds the `books.xsd` file to the <xref:System.Xml.Schema.XmlSchemaSet> and then calls the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
schemaSet.Compile()  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
schemaSet.Compile();  
```  
  
 <span data-ttu-id="5a918-150">Další informace o kompilování schémat v <xref:System.Xml.Schema.XmlSchemaSet>, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="5a918-150">For more information about compiling schemas in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method reference documentation.</span></span>  
  
## <a name="reprocessing-schemas"></a><span data-ttu-id="5a918-151">Opětovné zpracování schémat.</span><span class="sxs-lookup"><span data-stu-id="5a918-151">Reprocessing Schemas</span></span>  
 <span data-ttu-id="5a918-152">Opětovné zpracování schéma v <xref:System.Xml.Schema.XmlSchemaSet> provede všechny předběžného zpracování kroků prováděných na schématu při <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet> je volána.</span><span class="sxs-lookup"><span data-stu-id="5a918-152">Reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet> performs all the preprocessing steps performed on a schema when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span> <span data-ttu-id="5a918-153">Pokud volání <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda proběhne úspěšně, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet> je nastaven na `false`.</span><span class="sxs-lookup"><span data-stu-id="5a918-153">If the call to the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method is successful, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `false`.</span></span>  
  
 <span data-ttu-id="5a918-154"><xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Metoda by měl být použit při schéma v <xref:System.Xml.Schema.XmlSchemaSet> bylo změněno po <xref:System.Xml.Schema.XmlSchemaSet> byla provedena kompilace.</span><span class="sxs-lookup"><span data-stu-id="5a918-154">The <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method should be used when a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified after the <xref:System.Xml.Schema.XmlSchemaSet> has performed compilation.</span></span>  
  
 <span data-ttu-id="5a918-155">Následující příklad ilustruje, opětovné zpracování schéma přidán do <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="5a918-155">The following example illustrates reprocessing a schema added to the <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method.</span></span> <span data-ttu-id="5a918-156">Po <xref:System.Xml.Schema.XmlSchemaSet> kompiluje pomocí <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda a schéma přidán do <xref:System.Xml.Schema.XmlSchemaSet> je změněn, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> je nastavena na `true` to i v případě schéma v <xref:System.Xml.Schema.XmlSchemaSet> byla změněna.</span><span class="sxs-lookup"><span data-stu-id="5a918-156">After the <xref:System.Xml.Schema.XmlSchemaSet> is compiled using the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method, and the schema added to the <xref:System.Xml.Schema.XmlSchemaSet> is modified, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is set to `true` even though a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified.</span></span> <span data-ttu-id="5a918-157">Volání <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda provádí všechny předběžném zpracování provádí <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda a nastaví <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="5a918-157">Calling the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method performs all the preprocessing performed by the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method, and sets the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property to `false`.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
Dim schema As XmlSchema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim element As XmlSchemaElement = New XmlSchemaElement()  
schema.Items.Add(element)  
element.Name = "book"  
element.SchemaTypeName = New XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema")  
  
schemaSet.Reprocess(schema)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
XmlSchema schema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
XmlSchemaElement element = new XmlSchemaElement();  
schema.Items.Add(element);  
element.Name = "book";  
element.SchemaTypeName = new XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema");  
  
schemaSet.Reprocess(schema);  
```  
  
 <span data-ttu-id="5a918-158">Další informace o opětovné zpracování schéma v <xref:System.Xml.Schema.XmlSchemaSet>, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="5a918-158">For more information about reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method reference documentation.</span></span>  
  
## <a name="checking-for-a-schema"></a><span data-ttu-id="5a918-159">Kontrola schéma.</span><span class="sxs-lookup"><span data-stu-id="5a918-159">Checking for a Schema</span></span>  
 <span data-ttu-id="5a918-160">Můžete použít <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet> ke kontrole, pokud je schéma obsažené v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="5a918-160">You can use the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> to check if a schema is contained within an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="5a918-161"><xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> Metoda přebírá buď cílový obor názvů nebo <xref:System.Xml.Schema.XmlSchema> objekt, který chcete vyhledávat.</span><span class="sxs-lookup"><span data-stu-id="5a918-161">The <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method takes either a target namespace or an <xref:System.Xml.Schema.XmlSchema> object to check for.</span></span> <span data-ttu-id="5a918-162">V obou případech <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metoda vrátí `true` Pokud schéma je obsažena v <xref:System.Xml.Schema.XmlSchemaSet>, jinak vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="5a918-162">In either case, the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method returns `true` if the schema is contained within the <xref:System.Xml.Schema.XmlSchemaSet>; otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="5a918-163">Další informace o kontrole pro schéma, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metoda referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="5a918-163">For more information about checking for a schema, see the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method reference documentation.</span></span>  
  
## <a name="removing-schemas"></a><span data-ttu-id="5a918-164">Odebrání schémat.</span><span class="sxs-lookup"><span data-stu-id="5a918-164">Removing Schemas</span></span>  
 <span data-ttu-id="5a918-165">Schémata jsou odebrány z <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> a <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="5a918-165">Schemas are removed from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="5a918-166"><xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> Metoda odebere zadaný schématu z <xref:System.Xml.Schema.XmlSchemaSet>, při <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metoda odebere určené schéma a všechny schémata ho importovat z <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="5a918-166">The <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> method removes the specified schema from the <xref:System.Xml.Schema.XmlSchemaSet>, while the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method removes the specified schema and all the schemas it imports from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="5a918-167">Následující příklad ilustruje, přidání více schématy k <xref:System.Xml.Schema.XmlSchemaSet>, pak pomocí <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metoda odebrat jedno z schémat a všechny schémat se importuje.</span><span class="sxs-lookup"><span data-stu-id="5a918-167">The following example illustrates adding multiple schemas to an <xref:System.Xml.Schema.XmlSchemaSet>, then using the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method to remove one of the schemas and all the schemas it imports.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas()  
  
   If schema.TargetNamespace = "http://www.contoso.com/music" Then  
      schemaSet.RemoveRecursive(schema)  
   End If  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas())  
{  
   if (schema.TargetNamespace == "http://www.contoso.com/music")  
   {  
      schemaSet.RemoveRecursive(schema);  
   }  
}  
```  
  
 <span data-ttu-id="5a918-168">Další informace o odebrání schémat ze <xref:System.Xml.Schema.XmlSchemaSet>, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> a <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metody referenční dokumentace.</span><span class="sxs-lookup"><span data-stu-id="5a918-168">For more information about removing schemas from an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods reference documentation.</span></span>  
  
## <a name="schema-resolution-and-xsimport"></a><span data-ttu-id="5a918-169">Schéma řešení a xs:import</span><span class="sxs-lookup"><span data-stu-id="5a918-169">Schema Resolution and xs:import</span></span>  
 <span data-ttu-id="5a918-170">Následující příklady popisují <xref:System.Xml.Schema.XmlSchemaSet> chování pro import schémat, pokud existují více schématy pro daný obor názvů v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="5a918-170">The following examples describe the <xref:System.Xml.Schema.XmlSchemaSet> behavior for importing schemas when multiple schemas for a given namespace exist in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="5a918-171">Představte si třeba <xref:System.Xml.Schema.XmlSchemaSet> obsahující více schématy pro `http://www.contoso.com` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5a918-171">For example, consider an <xref:System.Xml.Schema.XmlSchemaSet> that contains multiple schemas for the `http://www.contoso.com` namespace.</span></span> <span data-ttu-id="5a918-172">Schéma s následující `xs:import` – direktiva je přidán do <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="5a918-172">A schema with the following `xs:import` directive is added to the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <span data-ttu-id="5a918-173"><xref:System.Xml.Schema.XmlSchemaSet> Pokusu o import schématu pro `http://www.contoso.com` obor názvů načtením z `http://www.contoso.com/schema.xsd` adresy URL.</span><span class="sxs-lookup"><span data-stu-id="5a918-173">The <xref:System.Xml.Schema.XmlSchemaSet> attempts to import a schema for the `http://www.contoso.com` namespace by loading it from the `http://www.contoso.com/schema.xsd` URL.</span></span> <span data-ttu-id="5a918-174">Schématu deklarace a typy, které jsou deklarované v dokument schématu jsou k dispozici v import schématu, i když se jiné schéma dokumenty pro pouze `http://www.contoso.com` oboru názvů v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="5a918-174">Only the schema declaration and types declared in the schema document are available in the importing schema, even though there are other schema documents for the `http://www.contoso.com` namespace in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="5a918-175">Pokud `schema.xsd` soubor nemůže být v umístění `http://www.contoso.com/schema.xsd` adresu URL, žádné schéma pro `http://www.contoso.com` obor názvů je importovat do import schématu.</span><span class="sxs-lookup"><span data-stu-id="5a918-175">If the `schema.xsd` file cannot be located at the `http://www.contoso.com/schema.xsd` URL, no schema for the `http://www.contoso.com` namespace is imported into the importing schema.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="5a918-176">Ověření XML – dokumenty</span><span class="sxs-lookup"><span data-stu-id="5a918-176">Validating XML Documents</span></span>  
 <span data-ttu-id="5a918-177">Dokumenty XML může být ověřen pomocí schémat v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="5a918-177">XML documents can be validated against schemas in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="5a918-178">Ověřit dokument XML přidáním schéma, aby <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost <xref:System.Xml.XmlReaderSettings> objektu, nebo pomocí přidání <xref:System.Xml.Schema.XmlSchemaSet> k <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost <xref:System.Xml.XmlReaderSettings> objektu.</span><span class="sxs-lookup"><span data-stu-id="5a918-178">You validate an XML document by adding a schema to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object, or by adding an <xref:System.Xml.Schema.XmlSchemaSet> to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="5a918-179"><xref:System.Xml.XmlReaderSettings> Objektu je následně používán <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> třídy za účelem vytvoření <xref:System.Xml.XmlReader> objektu a ověření v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="5a918-179">The <xref:System.Xml.XmlReaderSettings> object is then used by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to create an <xref:System.Xml.XmlReader> object and validate the XML document.</span></span>  
  
 <span data-ttu-id="5a918-180">Další informace o ověření XML dokumenty pomocí <xref:System.Xml.Schema.XmlSchemaSet>, najdete v části [ověřování schématu XML (XSD) pomocí XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span><span class="sxs-lookup"><span data-stu-id="5a918-180">For more information about validating XML documents using an <xref:System.Xml.Schema.XmlSchemaSet>, see [XML Schema (XSD) Validation with XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a918-181">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a918-181">See Also</span></span>  
 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>  
 [<span data-ttu-id="5a918-182">XmlSchemaSet jako mezipaměti schématu</span><span class="sxs-lookup"><span data-stu-id="5a918-182">XmlSchemaSet as a Schema Cache</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="5a918-183">Ověření schématu (XSD) XML s XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="5a918-183">XML Schema (XSD) Validation with XmlSchemaSet</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
