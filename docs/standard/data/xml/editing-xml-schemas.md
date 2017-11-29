---
title: "Úpravy XML schémata"
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
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b9505f60b2000ef227463404dab051ecb7fa3cc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="editing-xml-schemas"></a><span data-ttu-id="0212f-102">Úpravy XML schémata</span><span class="sxs-lookup"><span data-stu-id="0212f-102">Editing XML Schemas</span></span>
<span data-ttu-id="0212f-103">Úpravy schématu XML je jedním z nejdůležitějších funkcích schématu objektu modelu (SOM).</span><span class="sxs-lookup"><span data-stu-id="0212f-103">Editing an XML schema is one of the most important features of the Schema Object Model (SOM).</span></span> <span data-ttu-id="0212f-104">Všechny vlastnosti vedlejší schema kompilace SOM lze použít ke změně hodnot existující ve schématu XML.</span><span class="sxs-lookup"><span data-stu-id="0212f-104">All of the pre-schema-compilation properties of the SOM can be used to change the existing values in an XML schema.</span></span> <span data-ttu-id="0212f-105">Schéma XML můžete pak překompilovat, aby se projevily změny.</span><span class="sxs-lookup"><span data-stu-id="0212f-105">The XML schema can then be recompiled to reflect the changes.</span></span>  
  
 <span data-ttu-id="0212f-106">Prvním krokem při úpravě schématu načtena do rozsahu SOM je procházení schématu.</span><span class="sxs-lookup"><span data-stu-id="0212f-106">The first step in editing a schema loaded into the SOM is to traverse the schema.</span></span> <span data-ttu-id="0212f-107">Měli byste se seznámit s procházení schématu pomocí rozhraní API SOM před dalším pokusem o upravit schéma.</span><span class="sxs-lookup"><span data-stu-id="0212f-107">You should be familiar with traversing a schema using the SOM API before you attempt to edit a schema.</span></span> <span data-ttu-id="0212f-108">Také byste měli být obeznámeni s před a po schema kompilace vlastnosti po-schema-kompilace-informační sadu (PSCI).</span><span class="sxs-lookup"><span data-stu-id="0212f-108">You should also be familiar with the pre- and post-schema-compilation properties of the Post-Schema-Compilation-Infoset (PSCI).</span></span>  
  
## <a name="editing-an-xml-schema"></a><span data-ttu-id="0212f-109">Úpravy schématu XML</span><span class="sxs-lookup"><span data-stu-id="0212f-109">Editing an XML Schema</span></span>  
 <span data-ttu-id="0212f-110">V této části jsou k dispozici dva příklady kódu, které obě upravit schéma zákazníka vytvořené v [schémat XML vytváření](../../../../docs/standard/data/xml/building-xml-schemas.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="0212f-110">In this section, two code examples are provided, both of which edit the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span> <span data-ttu-id="0212f-111">V prvním příkladu kódu přidá nový `PhoneNumber` elementu, který chcete `Customer` elementu a v druhém příkladu kódu přidá nový `Title` atribut `FirstName` elementu.</span><span class="sxs-lookup"><span data-stu-id="0212f-111">The first code example adds a new `PhoneNumber` element to the `Customer` element and the second code example adds a new `Title` attribute to the `FirstName` element.</span></span> <span data-ttu-id="0212f-112">První ukázka používá také po-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekci jako způsob procházení schéma zákazníka při druhém příkladu kód používá vedlejší-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="0212f-112">The first sample also uses the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection as the means of traversing the customer schema while the second code example uses the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
### <a name="phonenumber-element-example"></a><span data-ttu-id="0212f-113">Příklad Element telefonní číslo</span><span class="sxs-lookup"><span data-stu-id="0212f-113">PhoneNumber Element Example</span></span>  
 <span data-ttu-id="0212f-114">Tento první příklad kódu přidá nový `PhoneNumber` elementu, který chcete `Customer` prvku schématu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="0212f-114">This first code example adds a new `PhoneNumber` element to the `Customer` element of the customer schema.</span></span> <span data-ttu-id="0212f-115">Příklad kódu upravuje schéma zákazníka v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="0212f-115">The code example edits the customer schema in the following steps.</span></span>  
  
1.  <span data-ttu-id="0212f-116">Přidá do nového schématu zákazníka <xref:System.Xml.Schema.XmlSchemaSet> objektu a pak zkompiluje ho.</span><span class="sxs-lookup"><span data-stu-id="0212f-116">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="0212f-117">Žádné schéma ověřování upozornění a chyb zjištěných čtení nebo kompilace schématu jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegovat.</span><span class="sxs-lookup"><span data-stu-id="0212f-117">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2.  <span data-ttu-id="0212f-118">Načte zkompilovaný <xref:System.Xml.Schema.XmlSchema> objektu z <xref:System.Xml.Schema.XmlSchemaSet> podle iterování přes <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0212f-118">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="0212f-119">Protože je zadané schéma zkompilovat, jsou přístupné po-Schema-kompilace-informační sadu vlastností (PSCI).</span><span class="sxs-lookup"><span data-stu-id="0212f-119">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3.  <span data-ttu-id="0212f-120">Vytvoří `PhoneNumber` pomocí elementu <xref:System.Xml.Schema.XmlSchemaElement> třídy, `xs:string` pomocí jednoduchého typu omezení <xref:System.Xml.Schema.XmlSchemaSimpleType> a <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> třídy, přidá omezující vlastnost vzor k <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> vlastnost omezení a přidá omezení na <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> vlastnost jednoduchý typ a jednoduchý typ, který má <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> z `PhoneNumber` elementu.</span><span class="sxs-lookup"><span data-stu-id="0212f-120">Creates the `PhoneNumber` element using the <xref:System.Xml.Schema.XmlSchemaElement> class, the `xs:string` simple type restriction using the <xref:System.Xml.Schema.XmlSchemaSimpleType> and <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classes, adds a pattern facet to the <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> property of the restriction, and adds the restriction to the <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> property of the simple type and the simple type to the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> of the `PhoneNumber` element.</span></span>  
  
4.  <span data-ttu-id="0212f-121">Opakována na každé <xref:System.Xml.Schema.XmlSchemaElement> v <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekci po-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="0212f-121">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span>  
  
5.  <span data-ttu-id="0212f-122">Pokud <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> elementu je `"Customer"`, získá komplexní typ `Customer` pomocí elementu <xref:System.Xml.Schema.XmlSchemaComplexType> třídy a částice pořadí použití komplexní typ <xref:System.Xml.Schema.XmlSchemaSequence> třídy.</span><span class="sxs-lookup"><span data-stu-id="0212f-122">If the <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> of the element is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
6.  <span data-ttu-id="0212f-123">Přidá novou `PhoneNumber` element obsahující existující pořadí `FirstName` a `LastName` elementů pomocí vedlejší-schema-kompilace <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> kolekce pořadí.</span><span class="sxs-lookup"><span data-stu-id="0212f-123">Adds the new `PhoneNumber` element to the sequence containing the existing `FirstName` and `LastName` elements using the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> collection of the sequence.</span></span>  
  
7.  <span data-ttu-id="0212f-124">Nakonec znovu zpracuje a zkompiluje upravenou <xref:System.Xml.Schema.XmlSchema> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapíše ho do konzoly.</span><span class="sxs-lookup"><span data-stu-id="0212f-124">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="0212f-125">Níže je úplný příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="0212f-125">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 <span data-ttu-id="0212f-126">Toto je schéma upravené zákazníka vytvořené v [schémat XML vytváření](../../../../docs/standard/data/xml/building-xml-schemas.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="0212f-126">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
        <xs:element name="PhoneNumber">           <xs:simpleType>             <xs:restriction base="xs:string">               <xs:pattern value="\d{3}-\d{3}-\d(4)" />             </xs:restriction>           </xs:simpleType>         </xs:element>  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /  
>  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
### <a name="title-attribute-example"></a><span data-ttu-id="0212f-127">Příklad názvu atributu</span><span class="sxs-lookup"><span data-stu-id="0212f-127">Title Attribute Example</span></span>  
 <span data-ttu-id="0212f-128">Tento druhý příklad kódu přidá nový `Title` atribut `FirstName` prvku schématu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="0212f-128">This second code example, adds a new `Title` attribute to the `FirstName` element of the customer schema.</span></span> <span data-ttu-id="0212f-129">V prvním příkladu kódu, typ `FirstName` element je `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="0212f-129">In the first code example, the type of the `FirstName` element is `xs:string`.</span></span> <span data-ttu-id="0212f-130">Pro `FirstName` element tak, aby měl atribut společně s řetězec obsah, její typ musí být změněn na složitý typ s modelu obsahu jednoduché obsahu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="0212f-130">For the `FirstName` element to have an attribute along with string content, its type must be changed to a complex type with a simple content extension content model.</span></span>  
  
 <span data-ttu-id="0212f-131">Příklad kódu upravuje schéma zákazníka v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="0212f-131">The code example edits the customer schema in the following steps.</span></span>  
  
1.  <span data-ttu-id="0212f-132">Přidá do nového schématu zákazníka <xref:System.Xml.Schema.XmlSchemaSet> objektu a pak zkompiluje ho.</span><span class="sxs-lookup"><span data-stu-id="0212f-132">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="0212f-133">Žádné schéma ověřování upozornění a chyb zjištěných čtení nebo kompilace schématu jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegovat.</span><span class="sxs-lookup"><span data-stu-id="0212f-133">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2.  <span data-ttu-id="0212f-134">Načte zkompilovaný <xref:System.Xml.Schema.XmlSchema> objektu z <xref:System.Xml.Schema.XmlSchemaSet> podle iterování přes <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0212f-134">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="0212f-135">Protože je zadané schéma zkompilovat, jsou přístupné po-Schema-kompilace-informační sadu vlastností (PSCI).</span><span class="sxs-lookup"><span data-stu-id="0212f-135">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3.  <span data-ttu-id="0212f-136">Vytvoří nový komplexní typ pro `FirstName` element pomocí <xref:System.Xml.Schema.XmlSchemaComplexType> třídy.</span><span class="sxs-lookup"><span data-stu-id="0212f-136">Creates a new complex type for the `FirstName` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
4.  <span data-ttu-id="0212f-137">Vytvoří nový jednoduchý rozšíření obsahu, se základní typ `xs:string`pomocí <xref:System.Xml.Schema.XmlSchemaSimpleContent> a <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="0212f-137">Creates a new simple content extension, with a base type of `xs:string`, using the <xref:System.Xml.Schema.XmlSchemaSimpleContent> and <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> classes.</span></span>  
  
5.  <span data-ttu-id="0212f-138">Vytvoří nový `Title` atribut, pomocí <xref:System.Xml.Schema.XmlSchemaAttribute> třída, s <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> z `xs:string` a přidá atribut jednoduché obsahu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="0212f-138">Creates the new `Title` attribute using the <xref:System.Xml.Schema.XmlSchemaAttribute> class, with a <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> of `xs:string` and adds the attribute to the simple content extension.</span></span>  
  
6.  <span data-ttu-id="0212f-139">Nastaví model obsahu jednoduchým obsahem jednoduchého rozšíření obsahu a obsahu model komplexní typ a jednoduchý obsah.</span><span class="sxs-lookup"><span data-stu-id="0212f-139">Sets the content model of the simple content to the simple content extension and the content model of the complex type to the simple content.</span></span>  
  
7.  <span data-ttu-id="0212f-140">Přidá nový komplexní typ vedlejší-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="0212f-140">Adds the new complex type to the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
8.  <span data-ttu-id="0212f-141">Opakována na každé <xref:System.Xml.Schema.XmlSchemaObject> v vedlejší-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="0212f-141">Iterates over each <xref:System.Xml.Schema.XmlSchemaObject> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0212f-142">Protože `FirstName` element není globální element ve schématu, není k dispozici v <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> nebo <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="0212f-142">Because the `FirstName` element is not a global element in the schema, it is not available in the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> or <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="0212f-143">Vyhledá příkladu kódu `FirstName` element tím, že se první `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="0212f-143">The code example locates the `FirstName` element by first locating the `Customer` element.</span></span>  
>   
>  <span data-ttu-id="0212f-144">V prvním příkladu kódu provázán schématu pomocí po-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="0212f-144">The first code example traversed the schema using the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="0212f-145">V této ukázce vedlejší-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekce se používá k procházení schématu.</span><span class="sxs-lookup"><span data-stu-id="0212f-145">In this sample, the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection is used to traverse the schema.</span></span> <span data-ttu-id="0212f-146">Zatímco obě kolekce poskytují přístup k globální elementy ve schématu, iterace v rámci <xref:System.Xml.Schema.XmlSchema.Items%2A> kolekce je více časově náročné, protože všechny globální elementy ve schématu musí iterovat a nemá žádné vlastnosti PSCI.</span><span class="sxs-lookup"><span data-stu-id="0212f-146">While both collections provide access to the global elements in the schema, iterating through the <xref:System.Xml.Schema.XmlSchema.Items%2A> collection is more time consuming because you must iterate over all global elements in the schema and it does not have any PSCI properties.</span></span> <span data-ttu-id="0212f-147">Kolekce PSCI (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>a tak dále) poskytuje přímý přístup k jejich globální prvky, atributy a typy a jejich vlastnosti PSCI.</span><span class="sxs-lookup"><span data-stu-id="0212f-147">The PSCI collections (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, and so on) provide direct access to their global elements, attributes, and types and their PSCI properties.</span></span>  
  
1.  <span data-ttu-id="0212f-148">Pokud <xref:System.Xml.Schema.XmlSchemaObject> je element, jehož <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> je `"Customer"`, získá komplexní typ `Customer` pomocí elementu <xref:System.Xml.Schema.XmlSchemaComplexType> třídy a částice pořadí použití komplexní typ <xref:System.Xml.Schema.XmlSchemaSequence> – třída.</span><span class="sxs-lookup"><span data-stu-id="0212f-148">If the <xref:System.Xml.Schema.XmlSchemaObject> is an element, whose <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
2.  <span data-ttu-id="0212f-149">Opakována na každé <xref:System.Xml.Schema.XmlSchemaParticle> v vedlejší-schema-kompilace <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="0212f-149">Iterates over each <xref:System.Xml.Schema.XmlSchemaParticle> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
3.  <span data-ttu-id="0212f-150">Pokud <xref:System.Xml.Schema.XmlSchemaParticle> je element, který na <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> je `"FirstName"`, nastaví <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> z `FirstName` element do nového `FirstName` komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="0212f-150">If the <xref:System.Xml.Schema.XmlSchemaParticle> is an element, who's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"FirstName"`, sets the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> of the `FirstName` element to the new `FirstName` complex type.</span></span>  
  
4.  <span data-ttu-id="0212f-151">Nakonec znovu zpracuje a zkompiluje upravenou <xref:System.Xml.Schema.XmlSchema> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapíše ho do konzoly.</span><span class="sxs-lookup"><span data-stu-id="0212f-151">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="0212f-152">Níže je úplný příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="0212f-152">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 <span data-ttu-id="0212f-153">Toto je schéma upravené zákazníka vytvořené v [schémat XML vytváření](../../../../docs/standard/data/xml/building-xml-schemas.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="0212f-153">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
```xml  
<?xml version="1.0" encoding=" utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /  
>  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:complexType name="FirstNameComplexType">     <xs:simpleContent>       <xs:extension base="xs:string">         <xs:attribute name="Title" type="xs:string" />       </xs:extension>     </xs:simpleContent>   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0212f-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="0212f-154">See Also</span></span>  
 [<span data-ttu-id="0212f-155">Přehled modelu objektů schématu XML</span><span class="sxs-lookup"><span data-stu-id="0212f-155">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [<span data-ttu-id="0212f-156">Čtení a zápis XML schémata</span><span class="sxs-lookup"><span data-stu-id="0212f-156">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [<span data-ttu-id="0212f-157">Vytváření XML schémata</span><span class="sxs-lookup"><span data-stu-id="0212f-157">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [<span data-ttu-id="0212f-158">Procházení schémat XML</span><span class="sxs-lookup"><span data-stu-id="0212f-158">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [<span data-ttu-id="0212f-159">Včetně nebo import schémat XML</span><span class="sxs-lookup"><span data-stu-id="0212f-159">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [<span data-ttu-id="0212f-160">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="0212f-160">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="0212f-161">Informační sadu po schématu kompilace</span><span class="sxs-lookup"><span data-stu-id="0212f-161">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
