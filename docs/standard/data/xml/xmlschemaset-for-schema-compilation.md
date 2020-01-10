---
title: XmlSchemaSet pro kompilaci schématu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
ms.openlocfilehash: 55347de81c65b7390584415dd29044f4ca4ba02a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709813"
---
# <a name="xmlschemaset-for-schema-compilation"></a><span data-ttu-id="ebea5-102">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="ebea5-102">XmlSchemaSet for Schema Compilation</span></span>
<span data-ttu-id="ebea5-103">Popisuje <xref:System.Xml.Schema.XmlSchemaSet>mezipaměť, kde lze uložit a ověřit schémata XML Schema Definition Language (XSD).</span><span class="sxs-lookup"><span data-stu-id="ebea5-103">Describes the <xref:System.Xml.Schema.XmlSchemaSet>, a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
## <a name="the-xmlschemaset-class"></a><span data-ttu-id="ebea5-104">Třída XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="ebea5-104">The XmlSchemaSet Class</span></span>  
 <span data-ttu-id="ebea5-105"><xref:System.Xml.Schema.XmlSchemaSet> je mezipaměť, kde lze uložit a ověřit schémata XML Schema Definition Language (XSD).</span><span class="sxs-lookup"><span data-stu-id="ebea5-105">The <xref:System.Xml.Schema.XmlSchemaSet> is a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
 <span data-ttu-id="ebea5-106">V <xref:System.Xml?displayProperty=nameWithType> verze 1,0 byla schémata XML načtena do <xref:System.Xml.Schema.XmlSchemaCollection> třídy jako knihovna schémat.</span><span class="sxs-lookup"><span data-stu-id="ebea5-106">In <xref:System.Xml?displayProperty=nameWithType> version 1.0, XML schemas were loaded into an <xref:System.Xml.Schema.XmlSchemaCollection> class as a library of schemas.</span></span> <span data-ttu-id="ebea5-107">V <xref:System.Xml?displayProperty=nameWithType> verze 2,0 jsou <xref:System.Xml.XmlValidatingReader> a <xref:System.Xml.Schema.XmlSchemaCollection> třídy zastaralé a byly nahrazeny <xref:System.Xml.XmlReader.Create%2A> metodami a <xref:System.Xml.Schema.XmlSchemaSet>ou třídou v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ebea5-107">In <xref:System.Xml?displayProperty=nameWithType> version 2.0, the <xref:System.Xml.XmlValidatingReader> and the <xref:System.Xml.Schema.XmlSchemaCollection> classes are obsolete, and have been replaced by the <xref:System.Xml.XmlReader.Create%2A> methods, and the <xref:System.Xml.Schema.XmlSchemaSet> class respectively.</span></span>  
  
 <span data-ttu-id="ebea5-108"><xref:System.Xml.Schema.XmlSchemaSet> byla zavedena za účelem opravy řady problémů, včetně kompatibility standardů, výkonu a zastaralých formátů schématu Microsoft XML-data redukovaná (XDR).</span><span class="sxs-lookup"><span data-stu-id="ebea5-108">The <xref:System.Xml.Schema.XmlSchemaSet> has been introduced to fix a number of issues including standards compatibility, performance, and the obsolete Microsoft XML-Data Reduced (XDR) schema format.</span></span>  
  
 <span data-ttu-id="ebea5-109">Následuje porovnání mezi <xref:System.Xml.Schema.XmlSchemaCollection> třídou a <xref:System.Xml.Schema.XmlSchemaSet>ou třídou.</span><span class="sxs-lookup"><span data-stu-id="ebea5-109">The following is a comparison between the <xref:System.Xml.Schema.XmlSchemaCollection> class and the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span>  
  
|<span data-ttu-id="ebea5-110">XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="ebea5-110">XmlSchemaCollection</span></span>|<span data-ttu-id="ebea5-111">XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="ebea5-111">XmlSchemaSet</span></span>|  
|-------------------------|------------------|  
|<span data-ttu-id="ebea5-112">Podporuje schémata Microsoft XDR a W3C XML.</span><span class="sxs-lookup"><span data-stu-id="ebea5-112">Supports Microsoft XDR and W3C XML schemas.</span></span>|<span data-ttu-id="ebea5-113">Podporuje pouze schémata W3C XML.</span><span class="sxs-lookup"><span data-stu-id="ebea5-113">Only supports W3C XML schemas.</span></span>|  
|<span data-ttu-id="ebea5-114">Schémata jsou kompilována při volání metody <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-114">Schemas are compiled when the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method is called.</span></span>|<span data-ttu-id="ebea5-115">Schémata nejsou kompilována při volání metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-115">Schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span> <span data-ttu-id="ebea5-116">Tím je zajištěno zlepšení výkonu při vytváření knihovny schémat.</span><span class="sxs-lookup"><span data-stu-id="ebea5-116">This provides a performance improvement during creation of the schema library.</span></span>|  
|<span data-ttu-id="ebea5-117">Každé schéma generuje jednotlivé kompilované verze, které mohou mít za následek "ostrovy schemas".</span><span class="sxs-lookup"><span data-stu-id="ebea5-117">Each schema generates an individual compiled version that can result in "schema islands."</span></span> <span data-ttu-id="ebea5-118">V důsledku toho jsou všechny zahrnutí a importy vymezeny pouze v rámci tohoto schématu.</span><span class="sxs-lookup"><span data-stu-id="ebea5-118">As a result, all includes and imports are scoped only within that schema.</span></span>|<span data-ttu-id="ebea5-119">Kompilovaná schémata generují jedno logické schéma, "sadu" schémat.</span><span class="sxs-lookup"><span data-stu-id="ebea5-119">Compiled schemas generate a single logical schema, a "set" of schemas.</span></span> <span data-ttu-id="ebea5-120">Všechna importovaná schémata v rámci schématu, která jsou přidána do sady, jsou přímo přidána do samotné sady.</span><span class="sxs-lookup"><span data-stu-id="ebea5-120">Any imported schemas within a schema that are added to the set are directly added to the set themselves.</span></span> <span data-ttu-id="ebea5-121">To znamená, že všechny typy jsou k dispozici pro všechna schémata.</span><span class="sxs-lookup"><span data-stu-id="ebea5-121">This means that all types are available to all schemas.</span></span>|  
|<span data-ttu-id="ebea5-122">V kolekci může existovat pouze jedno schéma pro určitý cílový obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ebea5-122">Only one schema for a particular target namespace can exist in the collection.</span></span>|<span data-ttu-id="ebea5-123">Více schémat stejného cílového oboru názvů lze přidat, pokud neexistují žádné konflikty typů.</span><span class="sxs-lookup"><span data-stu-id="ebea5-123">Multiple schemas for the same target namespace can be added as long as there are no type conflicts.</span></span>|  
  
## <a name="migrating-to-the-xmlschemaset"></a><span data-ttu-id="ebea5-124">Migrace do sady XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="ebea5-124">Migrating to the XmlSchemaSet</span></span>  
 <span data-ttu-id="ebea5-125">Následující příklad kódu poskytuje průvodce pro migraci na novou <xref:System.Xml.Schema.XmlSchemaSet> třídu z zastaralé <xref:System.Xml.Schema.XmlSchemaCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="ebea5-125">The following code example provides a guide to migrating to the new <xref:System.Xml.Schema.XmlSchemaSet> class from the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class.</span></span> <span data-ttu-id="ebea5-126">Příklad kódu ukazuje následující hlavní rozdíly mezi dvěma třídami.</span><span class="sxs-lookup"><span data-stu-id="ebea5-126">The code example illustrates the following major differences between the two classes.</span></span>  
  
- <span data-ttu-id="ebea5-127">Na rozdíl od metody <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> třídy <xref:System.Xml.Schema.XmlSchemaCollection> nejsou schémata kompilována při volání metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-127">Unlike the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when calling the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="ebea5-128">Metoda <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> je explicitně volána v příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="ebea5-128">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is explicitly called in the example code.</span></span>  
  
- <span data-ttu-id="ebea5-129">Chcete-li iterovat přes <xref:System.Xml.Schema.XmlSchemaSet>, je nutné použít vlastnost <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-129">To iterate over an <xref:System.Xml.Schema.XmlSchemaSet>, you must use the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="ebea5-130">Následuje příklad zastaralého příkladu kódu <xref:System.Xml.Schema.XmlSchemaCollection>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-130">The following is the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> code example.</span></span>  
  
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
  
 <span data-ttu-id="ebea5-131">Níže je podobný příklad kódu <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-131">The following is the equivalent <xref:System.Xml.Schema.XmlSchemaSet> code example.</span></span>  
  
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
  
## <a name="adding-and-retrieving-schemas"></a><span data-ttu-id="ebea5-132">Přidání a načtení schémat</span><span class="sxs-lookup"><span data-stu-id="ebea5-132">Adding and Retrieving Schemas</span></span>  
 <span data-ttu-id="ebea5-133">Schémata jsou přidána do <xref:System.Xml.Schema.XmlSchemaSet> pomocí metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-133">Schemas are added to an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="ebea5-134">Když je schéma přidáno do <xref:System.Xml.Schema.XmlSchemaSet>, je přidruženo k identifikátoru URI cílového oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ebea5-134">When a schema is added to an <xref:System.Xml.Schema.XmlSchemaSet>, it is associated with a target namespace URI.</span></span> <span data-ttu-id="ebea5-135">Identifikátor URI cílového oboru názvů může být buď zadán jako parametr metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>, nebo pokud není zadán žádný cílový obor názvů, <xref:System.Xml.Schema.XmlSchemaSet> používá cílový obor názvů definovaný ve schématu.</span><span class="sxs-lookup"><span data-stu-id="ebea5-135">The target namespace URI can either be specified as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method or if no target namespace is specified, the <xref:System.Xml.Schema.XmlSchemaSet> uses the target namespace defined in the schema.</span></span>  
  
 <span data-ttu-id="ebea5-136">Schémata se načítají z <xref:System.Xml.Schema.XmlSchemaSet> pomocí vlastnosti <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-136">Schemas are retrieved from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="ebea5-137">Vlastnost <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet> umožňuje iterovat objekty <xref:System.Xml.Schema.XmlSchema> obsažené v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-137">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> allows you to iterate over the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="ebea5-138">Vlastnost <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> buď vrátí všechny objekty <xref:System.Xml.Schema.XmlSchema> obsažené v <xref:System.Xml.Schema.XmlSchemaSet>, nebo s předaným parametrem cílového oboru názvů vrátí všechny objekty <xref:System.Xml.Schema.XmlSchema>, které patří do cílového oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ebea5-138">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property either returns all the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>, or, given a target namespace parameter, returns all the <xref:System.Xml.Schema.XmlSchema> objects that belong to the target namespace.</span></span> <span data-ttu-id="ebea5-139">Pokud je jako parametr cílového oboru názvů zadán parametr `null`, vrátí vlastnost <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> všechna schémata bez oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ebea5-139">If `null` is specified as the target namespace parameter, the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property returns all schemas without a namespace.</span></span>  
  
 <span data-ttu-id="ebea5-140">Následující příklad přidá schéma `books.xsd` v oboru názvů `http://www.contoso.com/books` do <xref:System.Xml.Schema.XmlSchemaSet>, načte všechna schémata, která patří do oboru názvů `http://www.contoso.com/books` z <xref:System.Xml.Schema.XmlSchemaSet>, a pak tato schémata zapíše do <xref:System.Console>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-140">The following example adds the `books.xsd` schema in the `http://www.contoso.com/books` namespace to an <xref:System.Xml.Schema.XmlSchemaSet>, retrieves all schemas that belong to the `http://www.contoso.com/books` namespace from the <xref:System.Xml.Schema.XmlSchemaSet>, and then writes those schemas to the <xref:System.Console>.</span></span>  
  
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
  
 <span data-ttu-id="ebea5-141">Další informace o přidání a načtení schémat z <xref:System.Xml.Schema.XmlSchemaSet> objektu naleznete v tématu metoda <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> a referenční dokumentace k vlastnosti <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-141">For more information about adding and retrieving schemas from an <xref:System.Xml.Schema.XmlSchemaSet> object, see the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method and the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property reference documentation.</span></span>  
  
## <a name="compiling-schemas"></a><span data-ttu-id="ebea5-142">Kompilace schémat</span><span class="sxs-lookup"><span data-stu-id="ebea5-142">Compiling Schemas</span></span>  
 <span data-ttu-id="ebea5-143">Schémata ve <xref:System.Xml.Schema.XmlSchemaSet> jsou kompilována do jednoho logického schématu <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodou <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-143">Schemas in an <xref:System.Xml.Schema.XmlSchemaSet> are compiled into one logical schema by the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ebea5-144">Na rozdíl od zastaralých <xref:System.Xml.Schema.XmlSchemaCollection> třídy nejsou schémata kompilována při volání metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-144">Unlike the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span>  
  
 <span data-ttu-id="ebea5-145">Pokud se metoda <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> úspěšně spustí, vlastnost <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="ebea5-145">If the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method executes successfully, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ebea5-146">Vlastnost <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> není ovlivněna, pokud jsou schémata upravována v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-146">The <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is not affected if schemas are edited while in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="ebea5-147">Aktualizace jednotlivých schémat v <xref:System.Xml.Schema.XmlSchemaSet> nejsou sledovány.</span><span class="sxs-lookup"><span data-stu-id="ebea5-147">Updates of the individual schemas in the <xref:System.Xml.Schema.XmlSchemaSet> are not tracked.</span></span> <span data-ttu-id="ebea5-148">V důsledku toho může být vlastnost <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> `true`, i když jedno ze schémat obsažených v <xref:System.Xml.Schema.XmlSchemaSet> bylo změněno, pokud do <xref:System.Xml.Schema.XmlSchemaSet>nebyla přidána ani odebrána žádná schémata.</span><span class="sxs-lookup"><span data-stu-id="ebea5-148">As a result, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property can be `true` even though one of the schemas contained in the <xref:System.Xml.Schema.XmlSchemaSet> has been altered, as long as no schemas were added or removed from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="ebea5-149">Následující příklad přidá soubor `books.xsd` do <xref:System.Xml.Schema.XmlSchemaSet> a pak zavolá metodu <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-149">The following example adds the `books.xsd` file to the <xref:System.Xml.Schema.XmlSchemaSet> and then calls the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="ebea5-150">Další informace o kompilaci schémat v <xref:System.Xml.Schema.XmlSchemaSet>naleznete v referenční dokumentaci k metodě <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-150">For more information about compiling schemas in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method reference documentation.</span></span>  
  
## <a name="reprocessing-schemas"></a><span data-ttu-id="ebea5-151">Zpracování schémat</span><span class="sxs-lookup"><span data-stu-id="ebea5-151">Reprocessing Schemas</span></span>  
 <span data-ttu-id="ebea5-152">Rezpracování schématu ve <xref:System.Xml.Schema.XmlSchemaSet> provádí všechny kroky předzpracování provedené ve schématu při volání metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-152">Reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet> performs all the preprocessing steps performed on a schema when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span> <span data-ttu-id="ebea5-153">Pokud je volání metody <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> úspěšné, vlastnost <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> je nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="ebea5-153">If the call to the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method is successful, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `false`.</span></span>  
  
 <span data-ttu-id="ebea5-154">Metoda <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> by měla být použita, pokud je schéma v <xref:System.Xml.Schema.XmlSchemaSet> změněno poté, co byla provedena kompilace <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-154">The <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method should be used when a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified after the <xref:System.Xml.Schema.XmlSchemaSet> has performed compilation.</span></span>  
  
 <span data-ttu-id="ebea5-155">Následující příklad ukazuje, jak znovu zpracovat schéma přidané do <xref:System.Xml.Schema.XmlSchemaSet> pomocí metody <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-155">The following example illustrates reprocessing a schema added to the <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method.</span></span> <span data-ttu-id="ebea5-156">Po kompilaci <xref:System.Xml.Schema.XmlSchemaSet> pomocí metody <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> a změně schématu přidaného do <xref:System.Xml.Schema.XmlSchemaSet> je vlastnost <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> nastavena na `true`, i když bylo upraveno schéma v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-156">After the <xref:System.Xml.Schema.XmlSchemaSet> is compiled using the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method, and the schema added to the <xref:System.Xml.Schema.XmlSchemaSet> is modified, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is set to `true` even though a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified.</span></span> <span data-ttu-id="ebea5-157">Volání metody <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> provede všechny předzpracování prováděné metodou <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> a nastaví vlastnost <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> na `false`.</span><span class="sxs-lookup"><span data-stu-id="ebea5-157">Calling the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method performs all the preprocessing performed by the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method, and sets the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property to `false`.</span></span>  
  
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
  
 <span data-ttu-id="ebea5-158">Další informace o přepracování schématu v <xref:System.Xml.Schema.XmlSchemaSet>naleznete v referenční dokumentaci k metodě <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-158">For more information about reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method reference documentation.</span></span>  
  
## <a name="checking-for-a-schema"></a><span data-ttu-id="ebea5-159">Kontroluje se schéma.</span><span class="sxs-lookup"><span data-stu-id="ebea5-159">Checking for a Schema</span></span>  
 <span data-ttu-id="ebea5-160">Pomocí metody <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> <xref:System.Xml.Schema.XmlSchemaSet> můžete zjistit, zda je schéma obsaženo v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-160">You can use the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> to check if a schema is contained within an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="ebea5-161">Metoda <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> přebírá buď cílový obor názvů, nebo objekt <xref:System.Xml.Schema.XmlSchema>, který se má ověřit.</span><span class="sxs-lookup"><span data-stu-id="ebea5-161">The <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method takes either a target namespace or an <xref:System.Xml.Schema.XmlSchema> object to check for.</span></span> <span data-ttu-id="ebea5-162">V obou případech metoda <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> vrátí `true`, pokud je schéma obsaženo v <xref:System.Xml.Schema.XmlSchemaSet>; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="ebea5-162">In either case, the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method returns `true` if the schema is contained within the <xref:System.Xml.Schema.XmlSchemaSet>; otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="ebea5-163">Další informace o kontrole schématu naleznete v referenční dokumentaci k metodě <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-163">For more information about checking for a schema, see the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method reference documentation.</span></span>  
  
## <a name="removing-schemas"></a><span data-ttu-id="ebea5-164">Odebírání schémat</span><span class="sxs-lookup"><span data-stu-id="ebea5-164">Removing Schemas</span></span>  
 <span data-ttu-id="ebea5-165">Schémata jsou odebrána z <xref:System.Xml.Schema.XmlSchemaSet> pomocí metod <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> a <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-165">Schemas are removed from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="ebea5-166">Metoda <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> Odstraní zadané schéma z <xref:System.Xml.Schema.XmlSchemaSet>, zatímco metoda <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> Odstraní zadané schéma a všechna schémata, která importuje z <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-166">The <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> method removes the specified schema from the <xref:System.Xml.Schema.XmlSchemaSet>, while the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method removes the specified schema and all the schemas it imports from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="ebea5-167">Následující příklad znázorňuje přidání více schémat do <xref:System.Xml.Schema.XmlSchemaSet>a následné použití metody <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> k odebrání jednoho ze schémat a všech schémat, která importuje.</span><span class="sxs-lookup"><span data-stu-id="ebea5-167">The following example illustrates adding multiple schemas to an <xref:System.Xml.Schema.XmlSchemaSet>, then using the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method to remove one of the schemas and all the schemas it imports.</span></span>  
  
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
  
 <span data-ttu-id="ebea5-168">Další informace o odebírání schémat z <xref:System.Xml.Schema.XmlSchemaSet>naleznete v referenční dokumentaci k metodám <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> a <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-168">For more information about removing schemas from an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods reference documentation.</span></span>  
  
## <a name="schema-resolution-and-xsimport"></a><span data-ttu-id="ebea5-169">Rozlišení schématu a xs: Import</span><span class="sxs-lookup"><span data-stu-id="ebea5-169">Schema Resolution and xs:import</span></span>  
 <span data-ttu-id="ebea5-170">Následující příklady popisují chování <xref:System.Xml.Schema.XmlSchemaSet> pro import schémat, pokud v <xref:System.Xml.Schema.XmlSchemaSet>existuje více schémat pro daný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ebea5-170">The following examples describe the <xref:System.Xml.Schema.XmlSchemaSet> behavior for importing schemas when multiple schemas for a given namespace exist in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="ebea5-171">Zvažte například <xref:System.Xml.Schema.XmlSchemaSet>, který obsahuje více schémat pro `http://www.contoso.com` obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ebea5-171">For example, consider an <xref:System.Xml.Schema.XmlSchemaSet> that contains multiple schemas for the `http://www.contoso.com` namespace.</span></span> <span data-ttu-id="ebea5-172">Do <xref:System.Xml.Schema.XmlSchemaSet>se přidá schéma s následující direktivou `xs:import`.</span><span class="sxs-lookup"><span data-stu-id="ebea5-172">A schema with the following `xs:import` directive is added to the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <span data-ttu-id="ebea5-173"><xref:System.Xml.Schema.XmlSchemaSet> se pokusí importovat schéma pro `http://www.contoso.com` oboru názvů načtením z adresy URL `http://www.contoso.com/schema.xsd`.</span><span class="sxs-lookup"><span data-stu-id="ebea5-173">The <xref:System.Xml.Schema.XmlSchemaSet> attempts to import a schema for the `http://www.contoso.com` namespace by loading it from the `http://www.contoso.com/schema.xsd` URL.</span></span> <span data-ttu-id="ebea5-174">Pouze deklarace schématu a typy deklarované v dokumentu schématu jsou k dispozici v rámci importu schématu, i když existují další dokumenty schématu pro obor názvů `http://www.contoso.com` v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-174">Only the schema declaration and types declared in the schema document are available in the importing schema, even though there are other schema documents for the `http://www.contoso.com` namespace in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="ebea5-175">Pokud `schema.xsd` soubor nejde najít na `http://www.contoso.com/schema.xsd` adrese URL, neimportuje se do importovaného schématu žádné schéma pro `http://www.contoso.com` obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ebea5-175">If the `schema.xsd` file cannot be located at the `http://www.contoso.com/schema.xsd` URL, no schema for the `http://www.contoso.com` namespace is imported into the importing schema.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="ebea5-176">Ověřování dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="ebea5-176">Validating XML Documents</span></span>  
 <span data-ttu-id="ebea5-177">Dokumenty XML lze ověřit proti schématům v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-177">XML documents can be validated against schemas in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="ebea5-178">Můžete ověřit dokument XML přidáním schématu do vlastnosti <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> objektu <xref:System.Xml.XmlReaderSettings> nebo přidáním <xref:System.Xml.Schema.XmlSchemaSet> do vlastnosti <xref:System.Xml.XmlReaderSettings.Schemas%2A> objektu <xref:System.Xml.XmlReaderSettings>.</span><span class="sxs-lookup"><span data-stu-id="ebea5-178">You validate an XML document by adding a schema to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object, or by adding an <xref:System.Xml.Schema.XmlSchemaSet> to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="ebea5-179">Objekt <xref:System.Xml.XmlReaderSettings> je poté použit metodou <xref:System.Xml.XmlReader.Create%2A> třídy <xref:System.Xml.XmlReader> k vytvoření objektu <xref:System.Xml.XmlReader> a ověření dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ebea5-179">The <xref:System.Xml.XmlReaderSettings> object is then used by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to create an <xref:System.Xml.XmlReader> object and validate the XML document.</span></span>  
  
 <span data-ttu-id="ebea5-180">Další informace o ověřování dokumentů XML pomocí <xref:System.Xml.Schema.XmlSchemaSet>naleznete v tématu [ověřování schématu XML (XSD) pomocí sady XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span><span class="sxs-lookup"><span data-stu-id="ebea5-180">For more information about validating XML documents using an <xref:System.Xml.Schema.XmlSchemaSet>, see [XML Schema (XSD) Validation with XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebea5-181">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebea5-181">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [<span data-ttu-id="ebea5-182">Třída XmlSchemaSet jako mezipaměť schématu</span><span class="sxs-lookup"><span data-stu-id="ebea5-182">XmlSchemaSet as a Schema Cache</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="ebea5-183">Ověření schématu XML (XSD) s třídou XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="ebea5-183">XML Schema (XSD) Validation with XmlSchemaSet</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
