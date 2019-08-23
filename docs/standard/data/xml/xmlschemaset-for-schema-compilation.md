---
title: XmlSchemaSet pro kompilaci schématu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0e05b09d5ce788b9a3da262d5890a0694b49375
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969034"
---
# <a name="xmlschemaset-for-schema-compilation"></a><span data-ttu-id="c8957-102">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="c8957-102">XmlSchemaSet for Schema Compilation</span></span>
<span data-ttu-id="c8957-103">Popisuje mezipaměť <xref:System.Xml.Schema.XmlSchemaSet>, kde lze uložit a ověřit schémata XML Schema Definition Language (XSD).</span><span class="sxs-lookup"><span data-stu-id="c8957-103">Describes the <xref:System.Xml.Schema.XmlSchemaSet>, a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
## <a name="the-xmlschemaset-class"></a><span data-ttu-id="c8957-104">Třída XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="c8957-104">The XmlSchemaSet Class</span></span>  
 <span data-ttu-id="c8957-105"><xref:System.Xml.Schema.XmlSchemaSet> Je mezipaměť, kde lze uložit a ověřit schémata XML Schema Definition Language (XSD).</span><span class="sxs-lookup"><span data-stu-id="c8957-105">The <xref:System.Xml.Schema.XmlSchemaSet> is a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
 <span data-ttu-id="c8957-106">Ve <xref:System.Xml?displayProperty=nameWithType> verzi 1,0 byly schémata XML načtena <xref:System.Xml.Schema.XmlSchemaCollection> do třídy jako knihovna schémat.</span><span class="sxs-lookup"><span data-stu-id="c8957-106">In <xref:System.Xml?displayProperty=nameWithType> version 1.0, XML schemas were loaded into an <xref:System.Xml.Schema.XmlSchemaCollection> class as a library of schemas.</span></span> <span data-ttu-id="c8957-107">Ve <xref:System.Xml?displayProperty=nameWithType> <xref:System.Xml.Schema.XmlSchemaCollection> verzi 2,0 <xref:System.Xml.XmlValidatingReader> třídy a jsou <xref:System.Xml.Schema.XmlSchemaSet> zastaralé a byly nahrazeny metodamiatřídouvuvedenémpořadí.<xref:System.Xml.XmlReader.Create%2A></span><span class="sxs-lookup"><span data-stu-id="c8957-107">In <xref:System.Xml?displayProperty=nameWithType> version 2.0, the <xref:System.Xml.XmlValidatingReader> and the <xref:System.Xml.Schema.XmlSchemaCollection> classes are obsolete, and have been replaced by the <xref:System.Xml.XmlReader.Create%2A> methods, and the <xref:System.Xml.Schema.XmlSchemaSet> class respectively.</span></span>  
  
 <span data-ttu-id="c8957-108"><xref:System.Xml.Schema.XmlSchemaSet> Byla představena Oprava počtu problémů, včetně kompatibility standardů, výkonu a zastaralých formátů schématu Microsoft XML-data redukovaná (XDR).</span><span class="sxs-lookup"><span data-stu-id="c8957-108">The <xref:System.Xml.Schema.XmlSchemaSet> has been introduced to fix a number of issues including standards compatibility, performance, and the obsolete Microsoft XML-Data Reduced (XDR) schema format.</span></span>  
  
 <span data-ttu-id="c8957-109">Následuje porovnání mezi <xref:System.Xml.Schema.XmlSchemaCollection> třídou <xref:System.Xml.Schema.XmlSchemaSet> a třídou.</span><span class="sxs-lookup"><span data-stu-id="c8957-109">The following is a comparison between the <xref:System.Xml.Schema.XmlSchemaCollection> class and the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span>  
  
|<span data-ttu-id="c8957-110">XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="c8957-110">XmlSchemaCollection</span></span>|<span data-ttu-id="c8957-111">XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="c8957-111">XmlSchemaSet</span></span>|  
|-------------------------|------------------|  
|<span data-ttu-id="c8957-112">Podporuje schémata Microsoft XDR a W3C XML.</span><span class="sxs-lookup"><span data-stu-id="c8957-112">Supports Microsoft XDR and W3C XML schemas.</span></span>|<span data-ttu-id="c8957-113">Podporuje pouze schémata W3C XML.</span><span class="sxs-lookup"><span data-stu-id="c8957-113">Only supports W3C XML schemas.</span></span>|  
|<span data-ttu-id="c8957-114">Schémata jsou kompilována při <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> volání metody.</span><span class="sxs-lookup"><span data-stu-id="c8957-114">Schemas are compiled when the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method is called.</span></span>|<span data-ttu-id="c8957-115">Schémata nejsou kompilována při <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> volání metody.</span><span class="sxs-lookup"><span data-stu-id="c8957-115">Schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span> <span data-ttu-id="c8957-116">Tím je zajištěno zlepšení výkonu při vytváření knihovny schémat.</span><span class="sxs-lookup"><span data-stu-id="c8957-116">This provides a performance improvement during creation of the schema library.</span></span>|  
|<span data-ttu-id="c8957-117">Každé schéma generuje jednotlivé kompilované verze, které mohou mít za následek "ostrovy schemas".</span><span class="sxs-lookup"><span data-stu-id="c8957-117">Each schema generates an individual compiled version that can result in "schema islands."</span></span> <span data-ttu-id="c8957-118">V důsledku toho jsou všechny zahrnutí a importy vymezeny pouze v rámci tohoto schématu.</span><span class="sxs-lookup"><span data-stu-id="c8957-118">As a result, all includes and imports are scoped only within that schema.</span></span>|<span data-ttu-id="c8957-119">Kompilovaná schémata generují jedno logické schéma, "sadu" schémat.</span><span class="sxs-lookup"><span data-stu-id="c8957-119">Compiled schemas generate a single logical schema, a "set" of schemas.</span></span> <span data-ttu-id="c8957-120">Všechna importovaná schémata v rámci schématu, která jsou přidána do sady, jsou přímo přidána do samotné sady.</span><span class="sxs-lookup"><span data-stu-id="c8957-120">Any imported schemas within a schema that are added to the set are directly added to the set themselves.</span></span> <span data-ttu-id="c8957-121">To znamená, že všechny typy jsou k dispozici pro všechna schémata.</span><span class="sxs-lookup"><span data-stu-id="c8957-121">This means that all types are available to all schemas.</span></span>|  
|<span data-ttu-id="c8957-122">V kolekci může existovat pouze jedno schéma pro určitý cílový obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c8957-122">Only one schema for a particular target namespace can exist in the collection.</span></span>|<span data-ttu-id="c8957-123">Více schémat stejného cílového oboru názvů lze přidat, pokud neexistují žádné konflikty typů.</span><span class="sxs-lookup"><span data-stu-id="c8957-123">Multiple schemas for the same target namespace can be added as long as there are no type conflicts.</span></span>|  
  
## <a name="migrating-to-the-xmlschemaset"></a><span data-ttu-id="c8957-124">Migrace do sady XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="c8957-124">Migrating to the XmlSchemaSet</span></span>  
 <span data-ttu-id="c8957-125">Následující příklad kódu poskytuje průvodce pro migraci na novou <xref:System.Xml.Schema.XmlSchemaSet> třídu z zastaralé <xref:System.Xml.Schema.XmlSchemaCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="c8957-125">The following code example provides a guide to migrating to the new <xref:System.Xml.Schema.XmlSchemaSet> class from the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class.</span></span> <span data-ttu-id="c8957-126">Příklad kódu ukazuje následující hlavní rozdíly mezi dvěma třídami.</span><span class="sxs-lookup"><span data-stu-id="c8957-126">The code example illustrates the following major differences between the two classes.</span></span>  
  
- <span data-ttu-id="c8957-127">Na rozdíl od <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaCollection> třídy nejsou schémata kompilována při <xref:System.Xml.Schema.XmlSchemaSet>volání <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c8957-127">Unlike the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when calling the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="c8957-128"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Metoda<xref:System.Xml.Schema.XmlSchemaSet> je explicitně volána v příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="c8957-128">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is explicitly called in the example code.</span></span>  
  
- <span data-ttu-id="c8957-129">Chcete-li iterovat <xref:System.Xml.Schema.XmlSchemaSet>přes, je nutné <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> použít vlastnost <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="c8957-129">To iterate over an <xref:System.Xml.Schema.XmlSchemaSet>, you must use the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="c8957-130">Následuje příklad zastaralého <xref:System.Xml.Schema.XmlSchemaCollection> kódu.</span><span class="sxs-lookup"><span data-stu-id="c8957-130">The following is the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> code example.</span></span>  
  
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
  
 <span data-ttu-id="c8957-131">V následujícím příkladu je podobný <xref:System.Xml.Schema.XmlSchemaSet> příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="c8957-131">The following is the equivalent <xref:System.Xml.Schema.XmlSchemaSet> code example.</span></span>  
  
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
  
## <a name="adding-and-retrieving-schemas"></a><span data-ttu-id="c8957-132">Přidání a načtení schémat</span><span class="sxs-lookup"><span data-stu-id="c8957-132">Adding and Retrieving Schemas</span></span>  
 <span data-ttu-id="c8957-133">Schémata jsou přidána do objektu <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> pomocí metody <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="c8957-133">Schemas are added to an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="c8957-134">Když je schéma přidáno do <xref:System.Xml.Schema.XmlSchemaSet>, je přidruženo k identifikátoru URI cílového oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c8957-134">When a schema is added to an <xref:System.Xml.Schema.XmlSchemaSet>, it is associated with a target namespace URI.</span></span> <span data-ttu-id="c8957-135">Identifikátor URI cílového oboru názvů je možné zadat buď jako parametr <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> , nebo pokud není zadaný žádný cílový obor názvů, použije cílový obor názvů definovaný ve schématu.</span><span class="sxs-lookup"><span data-stu-id="c8957-135">The target namespace URI can either be specified as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method or if no target namespace is specified, the <xref:System.Xml.Schema.XmlSchemaSet> uses the target namespace defined in the schema.</span></span>  
  
 <span data-ttu-id="c8957-136">Schémata jsou načítána z <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> pomocí vlastnosti <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="c8957-136">Schemas are retrieved from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="c8957-137">Vlastnost umožňuje iterovat <xref:System.Xml.Schema.XmlSchemaSet>objekty, které jsou obsaženy v. <xref:System.Xml.Schema.XmlSchema> <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A></span><span class="sxs-lookup"><span data-stu-id="c8957-137">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> allows you to iterate over the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="c8957-138">Vlastnost buď vrátí <xref:System.Xml.Schema.XmlSchema> všechny objekty obsažené v <xref:System.Xml.Schema.XmlSchemaSet>, nebo s daným parametrem cílového oboru názvů, vrátí všechny <xref:System.Xml.Schema.XmlSchema> objekty, které patří do cílového oboru názvů. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A></span><span class="sxs-lookup"><span data-stu-id="c8957-138">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property either returns all the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>, or, given a target namespace parameter, returns all the <xref:System.Xml.Schema.XmlSchema> objects that belong to the target namespace.</span></span> <span data-ttu-id="c8957-139">Pokud `null` je zadána jako parametr cílového oboru názvů <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> , vrátí vlastnost všechna schémata bez oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c8957-139">If `null` is specified as the target namespace parameter, the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property returns all schemas without a namespace.</span></span>  
  
 <span data-ttu-id="c8957-140">`books.xsd` Následující příklad přidá schéma `http://www.contoso.com/books` v oboru názvů do <xref:System.Xml.Schema.XmlSchemaSet> `http://www.contoso.com/books` , načte všechna <xref:System.Xml.Schema.XmlSchemaSet>schémata, která patří do <xref:System.Console>oboru názvů z a následně zapíše tato schémata do.</span><span class="sxs-lookup"><span data-stu-id="c8957-140">The following example adds the `books.xsd` schema in the `http://www.contoso.com/books` namespace to an <xref:System.Xml.Schema.XmlSchemaSet>, retrieves all schemas that belong to the `http://www.contoso.com/books` namespace from the <xref:System.Xml.Schema.XmlSchemaSet>, and then writes those schemas to the <xref:System.Console>.</span></span>  
  
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
  
 <span data-ttu-id="c8957-141">Další informace o přidání a načtení schémat z <xref:System.Xml.Schema.XmlSchemaSet> objektu <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> naleznete v tématu metoda a <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Referenční dokumentace k vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="c8957-141">For more information about adding and retrieving schemas from an <xref:System.Xml.Schema.XmlSchemaSet> object, see the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method and the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property reference documentation.</span></span>  
  
## <a name="compiling-schemas"></a><span data-ttu-id="c8957-142">Kompilace schémat</span><span class="sxs-lookup"><span data-stu-id="c8957-142">Compiling Schemas</span></span>  
 <span data-ttu-id="c8957-143">Schémata v <xref:System.Xml.Schema.XmlSchemaSet> jsou zkompilována do jednoho logického schématu <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodou <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="c8957-143">Schemas in an <xref:System.Xml.Schema.XmlSchemaSet> are compiled into one logical schema by the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8957-144">Na rozdíl od zastaralé <xref:System.Xml.Schema.XmlSchemaCollection> třídy nejsou schémata kompilována <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> při volání metody.</span><span class="sxs-lookup"><span data-stu-id="c8957-144">Unlike the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span>  
  
 <span data-ttu-id="c8957-145">Pokud se <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda úspěšně spustí <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> , vlastnost <xref:System.Xml.Schema.XmlSchemaSet> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="c8957-145">If the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method executes successfully, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8957-146">Tato <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost není ovlivněna, pokud jsou schémata upravována <xref:System.Xml.Schema.XmlSchemaSet>v.</span><span class="sxs-lookup"><span data-stu-id="c8957-146">The <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is not affected if schemas are edited while in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="c8957-147">Aktualizace jednotlivých schémat v <xref:System.Xml.Schema.XmlSchemaSet> nástroji nejsou sledovány.</span><span class="sxs-lookup"><span data-stu-id="c8957-147">Updates of the individual schemas in the <xref:System.Xml.Schema.XmlSchemaSet> are not tracked.</span></span> <span data-ttu-id="c8957-148">V důsledku toho může být <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> `true` vlastnost i v případě, že jedno ze schémat obsažených v <xref:System.Xml.Schema.XmlSchemaSet> nástroji bylo upraveno, pokud nebyla přidána ani odebrána <xref:System.Xml.Schema.XmlSchemaSet>žádná schémata z.</span><span class="sxs-lookup"><span data-stu-id="c8957-148">As a result, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property can be `true` even though one of the schemas contained in the <xref:System.Xml.Schema.XmlSchemaSet> has been altered, as long as no schemas were added or removed from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="c8957-149">Následující příklad přidá `books.xsd` soubor <xref:System.Xml.Schema.XmlSchemaSet> do a pak zavolá <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="c8957-149">The following example adds the `books.xsd` file to the <xref:System.Xml.Schema.XmlSchemaSet> and then calls the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="c8957-150">Další informace o kompilaci schémat v <xref:System.Xml.Schema.XmlSchemaSet>nástroji <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> naleznete v referenční dokumentaci k metodě.</span><span class="sxs-lookup"><span data-stu-id="c8957-150">For more information about compiling schemas in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method reference documentation.</span></span>  
  
## <a name="reprocessing-schemas"></a><span data-ttu-id="c8957-151">Zpracování schémat</span><span class="sxs-lookup"><span data-stu-id="c8957-151">Reprocessing Schemas</span></span>  
 <span data-ttu-id="c8957-152">Rezpracování schématu v <xref:System.Xml.Schema.XmlSchemaSet> provádí všechny kroky předzpracování provedené ve schématu <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> při volání metody <xref:System.Xml.Schema.XmlSchemaSet> .</span><span class="sxs-lookup"><span data-stu-id="c8957-152">Reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet> performs all the preprocessing steps performed on a schema when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span> <span data-ttu-id="c8957-153">Pokud je volání <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metody úspěšné <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> , vlastnost <xref:System.Xml.Schema.XmlSchemaSet> je nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="c8957-153">If the call to the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method is successful, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `false`.</span></span>  
  
 <span data-ttu-id="c8957-154">Metoda <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> by měla být použita, pokud bylo po <xref:System.Xml.Schema.XmlSchemaSet> provedení <xref:System.Xml.Schema.XmlSchemaSet> kompilace změněno schéma v.</span><span class="sxs-lookup"><span data-stu-id="c8957-154">The <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method should be used when a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified after the <xref:System.Xml.Schema.XmlSchemaSet> has performed compilation.</span></span>  
  
 <span data-ttu-id="c8957-155">Následující příklad ukazuje, jak znovu zpracovat schéma přidané do <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metody pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="c8957-155">The following example illustrates reprocessing a schema added to the <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method.</span></span> <span data-ttu-id="c8957-156"><xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> `true` <xref:System.Xml.Schema.XmlSchemaSet> Po kompilaci <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> pomocí metody a změně schématu přidaného do je vlastnost nastavena na i v případě, že schéma v nástroji bylo upraveno. <xref:System.Xml.Schema.XmlSchemaSet></span><span class="sxs-lookup"><span data-stu-id="c8957-156">After the <xref:System.Xml.Schema.XmlSchemaSet> is compiled using the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method, and the schema added to the <xref:System.Xml.Schema.XmlSchemaSet> is modified, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is set to `true` even though a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified.</span></span> <span data-ttu-id="c8957-157">Volání metody provede všechny předzpracování prováděné <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> metodou a nastaví vlastnost na `false`hodnotu. <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A></span><span class="sxs-lookup"><span data-stu-id="c8957-157">Calling the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method performs all the preprocessing performed by the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method, and sets the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property to `false`.</span></span>  
  
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
  
 <span data-ttu-id="c8957-158">Další informace o přepracování schématu v <xref:System.Xml.Schema.XmlSchemaSet>nástroji <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> naleznete v referenční dokumentaci k metodě.</span><span class="sxs-lookup"><span data-stu-id="c8957-158">For more information about reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method reference documentation.</span></span>  
  
## <a name="checking-for-a-schema"></a><span data-ttu-id="c8957-159">Kontroluje se schéma.</span><span class="sxs-lookup"><span data-stu-id="c8957-159">Checking for a Schema</span></span>  
 <span data-ttu-id="c8957-160">Můžete použít <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet> pro kontrolu, zda je <xref:System.Xml.Schema.XmlSchemaSet>schéma obsaženo v.</span><span class="sxs-lookup"><span data-stu-id="c8957-160">You can use the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> to check if a schema is contained within an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="c8957-161">Metoda přijímá buď cílový obor názvů <xref:System.Xml.Schema.XmlSchema> , nebo objekt, který má být zkontrolován. <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A></span><span class="sxs-lookup"><span data-stu-id="c8957-161">The <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method takes either a target namespace or an <xref:System.Xml.Schema.XmlSchema> object to check for.</span></span> <span data-ttu-id="c8957-162">V obou případech <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metoda vrátí `true` , pokud je <xref:System.Xml.Schema.XmlSchemaSet>schéma obsaženo v; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="c8957-162">In either case, the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method returns `true` if the schema is contained within the <xref:System.Xml.Schema.XmlSchemaSet>; otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="c8957-163">Další informace o kontrole schématu naleznete <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> v referenční dokumentaci k metodě.</span><span class="sxs-lookup"><span data-stu-id="c8957-163">For more information about checking for a schema, see the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method reference documentation.</span></span>  
  
## <a name="removing-schemas"></a><span data-ttu-id="c8957-164">Odebírání schémat</span><span class="sxs-lookup"><span data-stu-id="c8957-164">Removing Schemas</span></span>  
 <span data-ttu-id="c8957-165"><xref:System.Xml.Schema.XmlSchemaSet> Schémata jsou odebrána z <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> pomocí metody <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> <xref:System.Xml.Schema.XmlSchemaSet>a.</span><span class="sxs-lookup"><span data-stu-id="c8957-165">Schemas are removed from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="c8957-166">Metoda odebere zadané schéma z rozhraní <xref:System.Xml.Schema.XmlSchemaSet>, zatímco <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metoda odebere zadané schéma <xref:System.Xml.Schema.XmlSchemaSet>a všechna schémata, která importuje z. <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A></span><span class="sxs-lookup"><span data-stu-id="c8957-166">The <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> method removes the specified schema from the <xref:System.Xml.Schema.XmlSchemaSet>, while the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method removes the specified schema and all the schemas it imports from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="c8957-167">Následující příklad znázorňuje přidání více schémat do objektu <xref:System.Xml.Schema.XmlSchemaSet>a následné <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> použití metody pro odebrání jednoho ze schémat a všech schémat, která importuje.</span><span class="sxs-lookup"><span data-stu-id="c8957-167">The following example illustrates adding multiple schemas to an <xref:System.Xml.Schema.XmlSchemaSet>, then using the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method to remove one of the schemas and all the schemas it imports.</span></span>  
  
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
  
 <span data-ttu-id="c8957-168">Další informace o odebrání schémat z <xref:System.Xml.Schema.XmlSchemaSet>naleznete <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> v referenční dokumentaci metod a <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> .</span><span class="sxs-lookup"><span data-stu-id="c8957-168">For more information about removing schemas from an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods reference documentation.</span></span>  
  
## <a name="schema-resolution-and-xsimport"></a><span data-ttu-id="c8957-169">Rozlišení schématu a xs: Import</span><span class="sxs-lookup"><span data-stu-id="c8957-169">Schema Resolution and xs:import</span></span>  
 <span data-ttu-id="c8957-170">Následující příklady popisují <xref:System.Xml.Schema.XmlSchemaSet> chování při importu schémat, pokud <xref:System.Xml.Schema.XmlSchemaSet>v nástroji existuje více schémat pro daný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c8957-170">The following examples describe the <xref:System.Xml.Schema.XmlSchemaSet> behavior for importing schemas when multiple schemas for a given namespace exist in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="c8957-171">Zvažte <xref:System.Xml.Schema.XmlSchemaSet> například, že obsahuje více schémat `http://www.contoso.com` pro obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c8957-171">For example, consider an <xref:System.Xml.Schema.XmlSchemaSet> that contains multiple schemas for the `http://www.contoso.com` namespace.</span></span> <span data-ttu-id="c8957-172">Do nástroje se přidá schéma `xs:import` s následující direktivou. <xref:System.Xml.Schema.XmlSchemaSet></span><span class="sxs-lookup"><span data-stu-id="c8957-172">A schema with the following `xs:import` directive is added to the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <span data-ttu-id="c8957-173">Pokusí se importovat schéma `http://www.contoso.com` pro obor názvů načtením z `http://www.contoso.com/schema.xsd` adresy URL. <xref:System.Xml.Schema.XmlSchemaSet></span><span class="sxs-lookup"><span data-stu-id="c8957-173">The <xref:System.Xml.Schema.XmlSchemaSet> attempts to import a schema for the `http://www.contoso.com` namespace by loading it from the `http://www.contoso.com/schema.xsd` URL.</span></span> <span data-ttu-id="c8957-174">Pouze deklarace schématu a typy deklarované v dokumentu schématu jsou k dispozici v rámci importu schématu, i když existují další dokumenty schématu pro `http://www.contoso.com` obor názvů <xref:System.Xml.Schema.XmlSchemaSet>v.</span><span class="sxs-lookup"><span data-stu-id="c8957-174">Only the schema declaration and types declared in the schema document are available in the importing schema, even though there are other schema documents for the `http://www.contoso.com` namespace in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="c8957-175">Pokud soubor nejde najít `http://www.contoso.com/schema.xsd` na adrese URL `http://www.contoso.com` , do importovaného schématu se neimportuje žádné schéma pro obor názvů. `schema.xsd`</span><span class="sxs-lookup"><span data-stu-id="c8957-175">If the `schema.xsd` file cannot be located at the `http://www.contoso.com/schema.xsd` URL, no schema for the `http://www.contoso.com` namespace is imported into the importing schema.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="c8957-176">Ověřování dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="c8957-176">Validating XML Documents</span></span>  
 <span data-ttu-id="c8957-177">Dokumenty XML lze ověřit proti schématům v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="c8957-177">XML documents can be validated against schemas in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="c8957-178">Můžete ověřit dokument XML přidáním <xref:System.Xml.Schema.XmlSchemaSet> schématu do <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnosti <xref:System.Xml.XmlReaderSettings> <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings> objektu nebo přidáním prvku do vlastnostiobjektu.<xref:System.Xml.XmlReaderSettings.Schemas%2A></span><span class="sxs-lookup"><span data-stu-id="c8957-178">You validate an XML document by adding a schema to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object, or by adding an <xref:System.Xml.Schema.XmlSchemaSet> to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="c8957-179">Objekt je pak použit <xref:System.Xml.XmlReader.Create%2A> metodou <xref:System.Xml.XmlReader> třídy pro vytvoření <xref:System.Xml.XmlReader> objektu a ověření dokumentu XML. <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="c8957-179">The <xref:System.Xml.XmlReaderSettings> object is then used by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to create an <xref:System.Xml.XmlReader> object and validate the XML document.</span></span>  
  
 <span data-ttu-id="c8957-180">Další informace o ověřování dokumentů XML pomocí naleznete v <xref:System.Xml.Schema.XmlSchemaSet>tématu [ověření schématu XML (XSD) pomocí sady XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span><span class="sxs-lookup"><span data-stu-id="c8957-180">For more information about validating XML documents using an <xref:System.Xml.Schema.XmlSchemaSet>, see [XML Schema (XSD) Validation with XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8957-181">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8957-181">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [<span data-ttu-id="c8957-182">Třída XmlSchemaSet jako mezipaměť schématu</span><span class="sxs-lookup"><span data-stu-id="c8957-182">XmlSchemaSet as a Schema Cache</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="c8957-183">Ověření schématu XML (XSD) s třídou XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="c8957-183">XML Schema (XSD) Validation with XmlSchemaSet</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
