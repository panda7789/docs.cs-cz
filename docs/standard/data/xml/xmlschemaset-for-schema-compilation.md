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
ms.openlocfilehash: 742f031961a24475d67718c595431e36bfca8c22
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615377"
---
# <a name="xmlschemaset-for-schema-compilation"></a><span data-ttu-id="aed4b-102">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="aed4b-102">XmlSchemaSet for Schema Compilation</span></span>
<span data-ttu-id="aed4b-103">Popisuje <xref:System.Xml.Schema.XmlSchemaSet>, mezipaměti, kde můžete ukládat a ověření schématu XML definice jazyk (XSD) schémata.</span><span class="sxs-lookup"><span data-stu-id="aed4b-103">Describes the <xref:System.Xml.Schema.XmlSchemaSet>, a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
## <a name="the-xmlschemaset-class"></a><span data-ttu-id="aed4b-104">Třída XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="aed4b-104">The XmlSchemaSet Class</span></span>  
 <span data-ttu-id="aed4b-105"><xref:System.Xml.Schema.XmlSchemaSet> Je do mezipaměti, kde můžete ukládat a ověření schématu XML definice jazyk (XSD) schémata.</span><span class="sxs-lookup"><span data-stu-id="aed4b-105">The <xref:System.Xml.Schema.XmlSchemaSet> is a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
 <span data-ttu-id="aed4b-106">V <xref:System.Xml?displayProperty=nameWithType> verze 1.0, schémat XML byly načteny do <xref:System.Xml.Schema.XmlSchemaCollection> třídu jako knihovny schémat.</span><span class="sxs-lookup"><span data-stu-id="aed4b-106">In <xref:System.Xml?displayProperty=nameWithType> version 1.0, XML schemas were loaded into an <xref:System.Xml.Schema.XmlSchemaCollection> class as a library of schemas.</span></span> <span data-ttu-id="aed4b-107">V <xref:System.Xml?displayProperty=nameWithType> verze 2.0, <xref:System.Xml.XmlValidatingReader> a <xref:System.Xml.Schema.XmlSchemaCollection> třídy jsou zastaralé a byly nahrazeny <xref:System.Xml.XmlReader.Create%2A> metody a <xref:System.Xml.Schema.XmlSchemaSet> třídy v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="aed4b-107">In <xref:System.Xml?displayProperty=nameWithType> version 2.0, the <xref:System.Xml.XmlValidatingReader> and the <xref:System.Xml.Schema.XmlSchemaCollection> classes are obsolete, and have been replaced by the <xref:System.Xml.XmlReader.Create%2A> methods, and the <xref:System.Xml.Schema.XmlSchemaSet> class respectively.</span></span>  
  
 <span data-ttu-id="aed4b-108"><xref:System.Xml.Schema.XmlSchemaSet> Zavedl vyřešit řadu problémů, včetně kompatibility standardy, výkonu a zastaralý formát schématu Microsoft XML-Data Reduced (XDR).</span><span class="sxs-lookup"><span data-stu-id="aed4b-108">The <xref:System.Xml.Schema.XmlSchemaSet> has been introduced to fix a number of issues including standards compatibility, performance, and the obsolete Microsoft XML-Data Reduced (XDR) schema format.</span></span>  
  
 <span data-ttu-id="aed4b-109">Tady je porovnání mezi službou <xref:System.Xml.Schema.XmlSchemaCollection> třídy a <xref:System.Xml.Schema.XmlSchemaSet> třídy.</span><span class="sxs-lookup"><span data-stu-id="aed4b-109">The following is a comparison between the <xref:System.Xml.Schema.XmlSchemaCollection> class and the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span>  
  
|<span data-ttu-id="aed4b-110">XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="aed4b-110">XmlSchemaCollection</span></span>|<span data-ttu-id="aed4b-111">XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="aed4b-111">XmlSchemaSet</span></span>|  
|-------------------------|------------------|  
|<span data-ttu-id="aed4b-112">Podporuje schémata Microsoft XDR a W3C XML.</span><span class="sxs-lookup"><span data-stu-id="aed4b-112">Supports Microsoft XDR and W3C XML schemas.</span></span>|<span data-ttu-id="aed4b-113">Podporuje se jenom schémata W3C XML.</span><span class="sxs-lookup"><span data-stu-id="aed4b-113">Only supports W3C XML schemas.</span></span>|  
|<span data-ttu-id="aed4b-114">Schémata jsou zkompilovány při <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="aed4b-114">Schemas are compiled when the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method is called.</span></span>|<span data-ttu-id="aed4b-115">Schémata nejsou při kompilaci <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="aed4b-115">Schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span> <span data-ttu-id="aed4b-116">To poskytuje vylepšení výkonu při vytváření knihovny schémat.</span><span class="sxs-lookup"><span data-stu-id="aed4b-116">This provides a performance improvement during creation of the schema library.</span></span>|  
|<span data-ttu-id="aed4b-117">Každý schématu generuje jednotlivých Kompilovaná verze, který může mít za následek "schéma ostrovy."</span><span class="sxs-lookup"><span data-stu-id="aed4b-117">Each schema generates an individual compiled version that can result in "schema islands."</span></span> <span data-ttu-id="aed4b-118">V důsledku toho zahrnuje všechny a pouze v rámci tohoto schématu jsou omezená importy.</span><span class="sxs-lookup"><span data-stu-id="aed4b-118">As a result, all includes and imports are scoped only within that schema.</span></span>|<span data-ttu-id="aed4b-119">Zkompilovaných schémat generování jednoho logického schématu, "set" schémat.</span><span class="sxs-lookup"><span data-stu-id="aed4b-119">Compiled schemas generate a single logical schema, a "set" of schemas.</span></span> <span data-ttu-id="aed4b-120">Žádné importované schémata v rámci schématu, které jsou přidány do sady jsou přímo přidat do sady samotné.</span><span class="sxs-lookup"><span data-stu-id="aed4b-120">Any imported schemas within a schema that are added to the set are directly added to the set themselves.</span></span> <span data-ttu-id="aed4b-121">To znamená, že všechny typy jsou k dispozici ke všem schématům.</span><span class="sxs-lookup"><span data-stu-id="aed4b-121">This means that all types are available to all schemas.</span></span>|  
|<span data-ttu-id="aed4b-122">V kolekci může existovat pouze jedno schéma pro konkrétní cílový obor názvů.</span><span class="sxs-lookup"><span data-stu-id="aed4b-122">Only one schema for a particular target namespace can exist in the collection.</span></span>|<span data-ttu-id="aed4b-123">Více schémat pro stejný cílový obor názvů je možné přidat, dokud nebyly zjištěny žádné konflikty typu.</span><span class="sxs-lookup"><span data-stu-id="aed4b-123">Multiple schemas for the same target namespace can be added as long as there are no type conflicts.</span></span>|  
  
## <a name="migrating-to-the-xmlschemaset"></a><span data-ttu-id="aed4b-124">Migrace na sadě XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="aed4b-124">Migrating to the XmlSchemaSet</span></span>  
 <span data-ttu-id="aed4b-125">Následující příklad kódu poskytuje návod pro migraci do nového <xref:System.Xml.Schema.XmlSchemaSet> třídy z zastaralý <xref:System.Xml.Schema.XmlSchemaCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="aed4b-125">The following code example provides a guide to migrating to the new <xref:System.Xml.Schema.XmlSchemaSet> class from the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class.</span></span> <span data-ttu-id="aed4b-126">Příklad kódu znázorňuje následující hlavní rozdíly mezi dvěma třídami.</span><span class="sxs-lookup"><span data-stu-id="aed4b-126">The code example illustrates the following major differences between the two classes.</span></span>  
  
- <span data-ttu-id="aed4b-127">Na rozdíl od <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaCollection> třídy, schémata nejsou zkompilovány při volání <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="aed4b-127">Unlike the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when calling the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="aed4b-128"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Metodu <xref:System.Xml.Schema.XmlSchemaSet> je explicitně volána v příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="aed4b-128">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is explicitly called in the example code.</span></span>  
  
- <span data-ttu-id="aed4b-129">K iteraci přes <xref:System.Xml.Schema.XmlSchemaSet>, je nutné použít <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="aed4b-129">To iterate over an <xref:System.Xml.Schema.XmlSchemaSet>, you must use the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="aed4b-130">Tady je zastaralý <xref:System.Xml.Schema.XmlSchemaCollection> příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="aed4b-130">The following is the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> code example.</span></span>  
  
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
  
 <span data-ttu-id="aed4b-131">Tady je ekvivalentem <xref:System.Xml.Schema.XmlSchemaSet> příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="aed4b-131">The following is the equivalent <xref:System.Xml.Schema.XmlSchemaSet> code example.</span></span>  
  
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
  
## <a name="adding-and-retrieving-schemas"></a><span data-ttu-id="aed4b-132">Přidávání a načítání schémat</span><span class="sxs-lookup"><span data-stu-id="aed4b-132">Adding and Retrieving Schemas</span></span>  
 <span data-ttu-id="aed4b-133">Schémata jsou přidány do <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="aed4b-133">Schemas are added to an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="aed4b-134">Při přidání schéma <xref:System.Xml.Schema.XmlSchemaSet>, je přidružen k cílový obor názvů identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="aed4b-134">When a schema is added to an <xref:System.Xml.Schema.XmlSchemaSet>, it is associated with a target namespace URI.</span></span> <span data-ttu-id="aed4b-135">Cílový obor názvů identifikátoru URI může být buď určena jako parametr <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody nebo pokud není zadán žádný cílový obor názvů, <xref:System.Xml.Schema.XmlSchemaSet> používá cílový obor názvů definovaný ve schématu.</span><span class="sxs-lookup"><span data-stu-id="aed4b-135">The target namespace URI can either be specified as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method or if no target namespace is specified, the <xref:System.Xml.Schema.XmlSchemaSet> uses the target namespace defined in the schema.</span></span>  
  
 <span data-ttu-id="aed4b-136">Schémata jsou načteny z <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="aed4b-136">Schemas are retrieved from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="aed4b-137"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Vlastnost <xref:System.Xml.Schema.XmlSchemaSet> umožňuje iterovat <xref:System.Xml.Schema.XmlSchema> objekty obsažené v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="aed4b-137">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> allows you to iterate over the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="aed4b-138"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Vlastnost vrací buď všechny <xref:System.Xml.Schema.XmlSchema> objekty obsažené v <xref:System.Xml.Schema.XmlSchemaSet>, nebo zadaný cílový obor názvů parametrů, vrátí všechny <xref:System.Xml.Schema.XmlSchema> objektů, které patří cílový obor názvů.</span><span class="sxs-lookup"><span data-stu-id="aed4b-138">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property either returns all the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>, or, given a target namespace parameter, returns all the <xref:System.Xml.Schema.XmlSchema> objects that belong to the target namespace.</span></span> <span data-ttu-id="aed4b-139">Pokud `null` je zadána jako parametr cílový obor názvů <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost vrací všechna schémata bez oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="aed4b-139">If `null` is specified as the target namespace parameter, the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property returns all schemas without a namespace.</span></span>  
  
 <span data-ttu-id="aed4b-140">Následující příklad přidá `books.xsd` schéma v `http://www.contoso.com/books` obor názvů, abyste <xref:System.Xml.Schema.XmlSchemaSet>, načte všechna schémata, které patří do `http://www.contoso.com/books` obor názvů z <xref:System.Xml.Schema.XmlSchemaSet>a pak zapíše tato schémata <xref:System.Console>.</span><span class="sxs-lookup"><span data-stu-id="aed4b-140">The following example adds the `books.xsd` schema in the `http://www.contoso.com/books` namespace to an <xref:System.Xml.Schema.XmlSchemaSet>, retrieves all schemas that belong to the `http://www.contoso.com/books` namespace from the <xref:System.Xml.Schema.XmlSchemaSet>, and then writes those schemas to the <xref:System.Console>.</span></span>  
  
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
  
 <span data-ttu-id="aed4b-141">Další informace o přidávání a načítání schémat ze <xref:System.Xml.Schema.XmlSchemaSet> objektu, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda a <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="aed4b-141">For more information about adding and retrieving schemas from an <xref:System.Xml.Schema.XmlSchemaSet> object, see the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method and the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property reference documentation.</span></span>  
  
## <a name="compiling-schemas"></a><span data-ttu-id="aed4b-142">Kompilování schémat</span><span class="sxs-lookup"><span data-stu-id="aed4b-142">Compiling Schemas</span></span>  
 <span data-ttu-id="aed4b-143">Schémata v <xref:System.Xml.Schema.XmlSchemaSet> jsou kompilovány do jedné logické schématu <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="aed4b-143">Schemas in an <xref:System.Xml.Schema.XmlSchemaSet> are compiled into one logical schema by the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aed4b-144">Na rozdíl od zastaralý <xref:System.Xml.Schema.XmlSchemaCollection> třídy, schémata nejsou při kompilaci <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="aed4b-144">Unlike the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span>  
  
 <span data-ttu-id="aed4b-145">Pokud <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda provedena úspěšně, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="aed4b-145">If the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method executes successfully, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aed4b-146"><xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> Vlastnost nemá vliv, pokud jsou upravovat schémata během činnosti v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="aed4b-146">The <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is not affected if schemas are edited while in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="aed4b-147">Aktualizace v jednotlivých schémat <xref:System.Xml.Schema.XmlSchemaSet> nebudou pro účely.</span><span class="sxs-lookup"><span data-stu-id="aed4b-147">Updates of the individual schemas in the <xref:System.Xml.Schema.XmlSchemaSet> are not tracked.</span></span> <span data-ttu-id="aed4b-148">V důsledku toho <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost může být `true` i v případě, že jeden schémat součástí <xref:System.Xml.Schema.XmlSchemaSet> byla změněna, tak dlouho, dokud se přidaly nebo odebraly z žádná schémata <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="aed4b-148">As a result, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property can be `true` even though one of the schemas contained in the <xref:System.Xml.Schema.XmlSchemaSet> has been altered, as long as no schemas were added or removed from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="aed4b-149">Následující příklad přidá `books.xsd` do souboru <xref:System.Xml.Schema.XmlSchemaSet> a pak zavolá <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="aed4b-149">The following example adds the `books.xsd` file to the <xref:System.Xml.Schema.XmlSchemaSet> and then calls the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="aed4b-150">Další informace o kompilaci schémata v <xref:System.Xml.Schema.XmlSchemaSet>, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="aed4b-150">For more information about compiling schemas in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method reference documentation.</span></span>  
  
## <a name="reprocessing-schemas"></a><span data-ttu-id="aed4b-151">Schémata se znovu zpracovávají</span><span class="sxs-lookup"><span data-stu-id="aed4b-151">Reprocessing Schemas</span></span>  
 <span data-ttu-id="aed4b-152">Přepracování schéma v <xref:System.Xml.Schema.XmlSchemaSet> provede všechny kroky předběžného zpracování provést ve schématu při <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet> je volána.</span><span class="sxs-lookup"><span data-stu-id="aed4b-152">Reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet> performs all the preprocessing steps performed on a schema when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span> <span data-ttu-id="aed4b-153">Pokud volání <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda je úspěšná, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet> je nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="aed4b-153">If the call to the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method is successful, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `false`.</span></span>  
  
 <span data-ttu-id="aed4b-154"><xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Metoda má být použit při schéma v <xref:System.Xml.Schema.XmlSchemaSet> byl změněn po <xref:System.Xml.Schema.XmlSchemaSet> provedl kompilace.</span><span class="sxs-lookup"><span data-stu-id="aed4b-154">The <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method should be used when a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified after the <xref:System.Xml.Schema.XmlSchemaSet> has performed compilation.</span></span>  
  
 <span data-ttu-id="aed4b-155">Následující příklad ukazuje přepracování schématu přidat do <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="aed4b-155">The following example illustrates reprocessing a schema added to the <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method.</span></span> <span data-ttu-id="aed4b-156">Po <xref:System.Xml.Schema.XmlSchemaSet> je zkompilován pomocí <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda a přidá do schématu <xref:System.Xml.Schema.XmlSchemaSet> se změní, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> je nastavena na `true` i když schéma v <xref:System.Xml.Schema.XmlSchemaSet> byla změněna.</span><span class="sxs-lookup"><span data-stu-id="aed4b-156">After the <xref:System.Xml.Schema.XmlSchemaSet> is compiled using the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method, and the schema added to the <xref:System.Xml.Schema.XmlSchemaSet> is modified, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is set to `true` even though a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified.</span></span> <span data-ttu-id="aed4b-157">Volání <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda provádí všechny předzpracování prováděné <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda a nastaví <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="aed4b-157">Calling the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method performs all the preprocessing performed by the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method, and sets the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property to `false`.</span></span>  
  
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
  
 <span data-ttu-id="aed4b-158">Další informace o opětovném zpracování schéma v <xref:System.Xml.Schema.XmlSchemaSet>, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="aed4b-158">For more information about reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method reference documentation.</span></span>  
  
## <a name="checking-for-a-schema"></a><span data-ttu-id="aed4b-159">Kontrolují se schéma</span><span class="sxs-lookup"><span data-stu-id="aed4b-159">Checking for a Schema</span></span>  
 <span data-ttu-id="aed4b-160">Můžete použít <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet> ke kontrole, pokud je součástí schématu <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="aed4b-160">You can use the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> to check if a schema is contained within an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="aed4b-161"><xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> Metoda přebírá buď cílový obor názvů nebo <xref:System.Xml.Schema.XmlSchema> objektu, který chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="aed4b-161">The <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method takes either a target namespace or an <xref:System.Xml.Schema.XmlSchema> object to check for.</span></span> <span data-ttu-id="aed4b-162">V obou případech <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> vrátí metoda `true` Pokud schéma je obsažena v <xref:System.Xml.Schema.XmlSchemaSet>; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="aed4b-162">In either case, the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method returns `true` if the schema is contained within the <xref:System.Xml.Schema.XmlSchemaSet>; otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="aed4b-163">Další informace o kontrole pro schéma, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metoda referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="aed4b-163">For more information about checking for a schema, see the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method reference documentation.</span></span>  
  
## <a name="removing-schemas"></a><span data-ttu-id="aed4b-164">Odebrání schémata</span><span class="sxs-lookup"><span data-stu-id="aed4b-164">Removing Schemas</span></span>  
 <span data-ttu-id="aed4b-165">Schémata jsou odebrány z <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> a <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="aed4b-165">Schemas are removed from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="aed4b-166"><xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> Metoda odstraní zadané schéma z <xref:System.Xml.Schema.XmlSchemaSet>, zatímco <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metoda odstraní zadané schéma a všechna schémata importy z <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="aed4b-166">The <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> method removes the specified schema from the <xref:System.Xml.Schema.XmlSchemaSet>, while the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method removes the specified schema and all the schemas it imports from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="aed4b-167">Následující příklad ukazuje přidání více schémat, chcete-li <xref:System.Xml.Schema.XmlSchemaSet>, pak pomocí <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metoda odebrání jednoho ze schémat a všechna schémata importuje.</span><span class="sxs-lookup"><span data-stu-id="aed4b-167">The following example illustrates adding multiple schemas to an <xref:System.Xml.Schema.XmlSchemaSet>, then using the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method to remove one of the schemas and all the schemas it imports.</span></span>  
  
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
  
 <span data-ttu-id="aed4b-168">Další informace o odebrání schémata z <xref:System.Xml.Schema.XmlSchemaSet>, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> a <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metody referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="aed4b-168">For more information about removing schemas from an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods reference documentation.</span></span>  
  
## <a name="schema-resolution-and-xsimport"></a><span data-ttu-id="aed4b-169">Schéma překlad IP adres a xs:import</span><span class="sxs-lookup"><span data-stu-id="aed4b-169">Schema Resolution and xs:import</span></span>  
 <span data-ttu-id="aed4b-170">Následující příklady popisují <xref:System.Xml.Schema.XmlSchemaSet> chování pro import schémat, pokud existuje více schémat pro daný obor názvů v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="aed4b-170">The following examples describe the <xref:System.Xml.Schema.XmlSchemaSet> behavior for importing schemas when multiple schemas for a given namespace exist in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="aed4b-171">Představte si třeba <xref:System.Xml.Schema.XmlSchemaSet> , který obsahuje více schémat pro `http://www.contoso.com` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="aed4b-171">For example, consider an <xref:System.Xml.Schema.XmlSchemaSet> that contains multiple schemas for the `http://www.contoso.com` namespace.</span></span> <span data-ttu-id="aed4b-172">Schéma s následující `xs:import` – direktiva se přidá do <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="aed4b-172">A schema with the following `xs:import` directive is added to the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <span data-ttu-id="aed4b-173"><xref:System.Xml.Schema.XmlSchemaSet> Pokusu o import schématu pro `http://www.contoso.com` oboru názvů z načtením `http://www.contoso.com/schema.xsd` adresy URL.</span><span class="sxs-lookup"><span data-stu-id="aed4b-173">The <xref:System.Xml.Schema.XmlSchemaSet> attempts to import a schema for the `http://www.contoso.com` namespace by loading it from the `http://www.contoso.com/schema.xsd` URL.</span></span> <span data-ttu-id="aed4b-174">Pouze schéma deklarace a typy deklarované v dokumentu schématu jsou k dispozici v importu schématu, i když existují jiných schématu dokumentů pro `http://www.contoso.com` obor názvů v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="aed4b-174">Only the schema declaration and types declared in the schema document are available in the importing schema, even though there are other schema documents for the `http://www.contoso.com` namespace in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="aed4b-175">Pokud `schema.xsd` soubor nemůže být umístěn v `http://www.contoso.com/schema.xsd` žádné schéma pro adresu URL `http://www.contoso.com` obor názvů se importuje do import schématu.</span><span class="sxs-lookup"><span data-stu-id="aed4b-175">If the `schema.xsd` file cannot be located at the `http://www.contoso.com/schema.xsd` URL, no schema for the `http://www.contoso.com` namespace is imported into the importing schema.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="aed4b-176">Ověření XML dokumenty</span><span class="sxs-lookup"><span data-stu-id="aed4b-176">Validating XML Documents</span></span>  
 <span data-ttu-id="aed4b-177">XML dokumenty můžou ověřovat na schémata v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="aed4b-177">XML documents can be validated against schemas in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="aed4b-178">Ověření dokumentu XML tak, že přidáte schématu a <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost <xref:System.Xml.XmlReaderSettings> objektu nebo přidáním <xref:System.Xml.Schema.XmlSchemaSet> k <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost <xref:System.Xml.XmlReaderSettings> objektu.</span><span class="sxs-lookup"><span data-stu-id="aed4b-178">You validate an XML document by adding a schema to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object, or by adding an <xref:System.Xml.Schema.XmlSchemaSet> to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="aed4b-179"><xref:System.Xml.XmlReaderSettings> Objektu se potom využijí <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> třídy za účelem vytvoření <xref:System.Xml.XmlReader> objektu a ověření dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="aed4b-179">The <xref:System.Xml.XmlReaderSettings> object is then used by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to create an <xref:System.Xml.XmlReader> object and validate the XML document.</span></span>  
  
 <span data-ttu-id="aed4b-180">Další informace o ověření XML dokumenty pomocí <xref:System.Xml.Schema.XmlSchemaSet>, naleznete v tématu [ověření schématu XML (XSD) s třídou XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span><span class="sxs-lookup"><span data-stu-id="aed4b-180">For more information about validating XML documents using an <xref:System.Xml.Schema.XmlSchemaSet>, see [XML Schema (XSD) Validation with XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aed4b-181">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aed4b-181">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [<span data-ttu-id="aed4b-182">Třída XmlSchemaSet jako mezipaměť schémat</span><span class="sxs-lookup"><span data-stu-id="aed4b-182">XmlSchemaSet as a Schema Cache</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="aed4b-183">Ověření schématu XML (XSD) s třídou XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="aed4b-183">XML Schema (XSD) Validation with XmlSchemaSet</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
