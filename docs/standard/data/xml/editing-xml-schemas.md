---
title: Úpravy schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 119c4c13c90aeca8c14d2725d927c38be32212a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934456"
---
# <a name="editing-xml-schemas"></a><span data-ttu-id="b9f07-102">Úpravy schémat XML</span><span class="sxs-lookup"><span data-stu-id="b9f07-102">Editing XML Schemas</span></span>
<span data-ttu-id="b9f07-103">Úprava schématu XML je jednou z vašich nejdůležitějších funkcí z modelu objektu schématu (SOM).</span><span class="sxs-lookup"><span data-stu-id="b9f07-103">Editing an XML schema is one of the most important features of the Schema Object Model (SOM).</span></span> <span data-ttu-id="b9f07-104">Všechny vlastnosti vedlejší schema kompilace SOM lze použít ke změně existujícího hodnot ve schématu XML.</span><span class="sxs-lookup"><span data-stu-id="b9f07-104">All of the pre-schema-compilation properties of the SOM can be used to change the existing values in an XML schema.</span></span> <span data-ttu-id="b9f07-105">Schéma XML můžete pak překompilovány tak, aby odrážely změny.</span><span class="sxs-lookup"><span data-stu-id="b9f07-105">The XML schema can then be recompiled to reflect the changes.</span></span>  
  
 <span data-ttu-id="b9f07-106">Prvním krokem při úpravách schématu načtená SOM je procházení schématu.</span><span class="sxs-lookup"><span data-stu-id="b9f07-106">The first step in editing a schema loaded into the SOM is to traverse the schema.</span></span> <span data-ttu-id="b9f07-107">Měli byste se seznámit s procházení schématu pomocí rozhraní API SOM, než se pokusíte upravit schéma.</span><span class="sxs-lookup"><span data-stu-id="b9f07-107">You should be familiar with traversing a schema using the SOM API before you attempt to edit a schema.</span></span> <span data-ttu-id="b9f07-108">Také byste měli být obeznámeni s vlastností před instrumentací a po schema kompilace po-schema-kompilace – informační sada (PSCI).</span><span class="sxs-lookup"><span data-stu-id="b9f07-108">You should also be familiar with the pre- and post-schema-compilation properties of the Post-Schema-Compilation-Infoset (PSCI).</span></span>  
  
## <a name="editing-an-xml-schema"></a><span data-ttu-id="b9f07-109">Úpravy schématu XML</span><span class="sxs-lookup"><span data-stu-id="b9f07-109">Editing an XML Schema</span></span>  
 <span data-ttu-id="b9f07-110">V této části jsou k dispozici dva příklady kódu, které upravit schéma zákazníka vytvoří v [sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="b9f07-110">In this section, two code examples are provided, both of which edit the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span> <span data-ttu-id="b9f07-111">První příklad kódu přidá nový `PhoneNumber` elementu `Customer` prvku a druhý příklad kódu přidá nový `Title` atribut `FirstName` elementu.</span><span class="sxs-lookup"><span data-stu-id="b9f07-111">The first code example adds a new `PhoneNumber` element to the `Customer` element and the second code example adds a new `Title` attribute to the `FirstName` element.</span></span> <span data-ttu-id="b9f07-112">První příklad používá také po-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekce jako způsob procházení schématu zákazníků při druhý příklad kódu používá předprodukční-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="b9f07-112">The first sample also uses the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection as the means of traversing the customer schema while the second code example uses the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
### <a name="phonenumber-element-example"></a><span data-ttu-id="b9f07-113">Příklad prvek PhoneNumber</span><span class="sxs-lookup"><span data-stu-id="b9f07-113">PhoneNumber Element Example</span></span>  
 <span data-ttu-id="b9f07-114">Tento první příklad kódu přidá nový `PhoneNumber` elementu `Customer` prvek schématu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="b9f07-114">This first code example adds a new `PhoneNumber` element to the `Customer` element of the customer schema.</span></span> <span data-ttu-id="b9f07-115">Příklad kódu upraví schéma zákazníka v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="b9f07-115">The code example edits the customer schema in the following steps.</span></span>  
  
1. <span data-ttu-id="b9f07-116">Přidá schématu zákazníků na novou <xref:System.Xml.Schema.XmlSchemaSet> objekt a potom jej zkompiluje.</span><span class="sxs-lookup"><span data-stu-id="b9f07-116">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="b9f07-117">Žádné schéma ověření upozornění a chyb zjištěných čtení nebo kompilaci schématu jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegovat.</span><span class="sxs-lookup"><span data-stu-id="b9f07-117">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="b9f07-118">Načte zkompilovaný <xref:System.Xml.Schema.XmlSchema> objektu z <xref:System.Xml.Schema.XmlSchemaSet> pomocí provádí iterace <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b9f07-118">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="b9f07-119">Protože kompilaci schématu, po-Schema-kompilace – informační sadu vlastností (PSCI) jsou přístupné.</span><span class="sxs-lookup"><span data-stu-id="b9f07-119">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="b9f07-120">Vytvoří `PhoneNumber` pomocí elementu <xref:System.Xml.Schema.XmlSchemaElement> třídy, `xs:string` jednoduchého typu pomocí omezení <xref:System.Xml.Schema.XmlSchemaSimpleType> a <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> třídy, přidá vlastnost pattern k <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> vlastnost omezení a přidá omezení <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> vlastnost jednoduchý typ a jednoduchý typ, který má <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> z `PhoneNumber` elementu.</span><span class="sxs-lookup"><span data-stu-id="b9f07-120">Creates the `PhoneNumber` element using the <xref:System.Xml.Schema.XmlSchemaElement> class, the `xs:string` simple type restriction using the <xref:System.Xml.Schema.XmlSchemaSimpleType> and <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classes, adds a pattern facet to the <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> property of the restriction, and adds the restriction to the <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> property of the simple type and the simple type to the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> of the `PhoneNumber` element.</span></span>  
  
4. <span data-ttu-id="b9f07-121">Iteruje přes každý <xref:System.Xml.Schema.XmlSchemaElement> v <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekce po-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="b9f07-121">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span>  
  
5. <span data-ttu-id="b9f07-122">Pokud <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> elementu, který je `"Customer"`, získá komplexní typ `Customer` pomocí elementu <xref:System.Xml.Schema.XmlSchemaComplexType> třídy a částice sequence komplexní typ použití <xref:System.Xml.Schema.XmlSchemaSequence> třídy.</span><span class="sxs-lookup"><span data-stu-id="b9f07-122">If the <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> of the element is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
6. <span data-ttu-id="b9f07-123">Přidá novou `PhoneNumber` element obsahující existující pořadí `FirstName` a `LastName` prvky pomocí předprodukční-schema-kompilace <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> kolekce pořadí.</span><span class="sxs-lookup"><span data-stu-id="b9f07-123">Adds the new `PhoneNumber` element to the sequence containing the existing `FirstName` and `LastName` elements using the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> collection of the sequence.</span></span>  
  
7. <span data-ttu-id="b9f07-124">Nakonec znovu zpracuje a zkompiluje upravené <xref:System.Xml.Schema.XmlSchema> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapíše jej do konzoly.</span><span class="sxs-lookup"><span data-stu-id="b9f07-124">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="b9f07-125">Tady je příklad úplného kódu.</span><span class="sxs-lookup"><span data-stu-id="b9f07-125">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 <span data-ttu-id="b9f07-126">Tady je upravený zákazníka schéma se vytvořilo v [sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="b9f07-126">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
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
  
### <a name="title-attribute-example"></a><span data-ttu-id="b9f07-127">Příklad název atributu</span><span class="sxs-lookup"><span data-stu-id="b9f07-127">Title Attribute Example</span></span>  
 <span data-ttu-id="b9f07-128">Tento druhý příklad kódu přidá nový `Title` atribut `FirstName` prvek schématu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="b9f07-128">This second code example, adds a new `Title` attribute to the `FirstName` element of the customer schema.</span></span> <span data-ttu-id="b9f07-129">V prvním příkladu kódu, typ `FirstName` element je `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="b9f07-129">In the first code example, the type of the `FirstName` element is `xs:string`.</span></span> <span data-ttu-id="b9f07-130">Pro `FirstName` element má atribut spolu s řetězec obsahu, jeho typ musí být změněn na složitý typ s jednoduchým rozšířením obsahu obsahu modelu.</span><span class="sxs-lookup"><span data-stu-id="b9f07-130">For the `FirstName` element to have an attribute along with string content, its type must be changed to a complex type with a simple content extension content model.</span></span>  
  
 <span data-ttu-id="b9f07-131">Příklad kódu upraví schéma zákazníka v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="b9f07-131">The code example edits the customer schema in the following steps.</span></span>  
  
1. <span data-ttu-id="b9f07-132">Přidá schématu zákazníků na novou <xref:System.Xml.Schema.XmlSchemaSet> objekt a potom jej zkompiluje.</span><span class="sxs-lookup"><span data-stu-id="b9f07-132">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="b9f07-133">Žádné schéma ověření upozornění a chyb zjištěných čtení nebo kompilaci schématu jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegovat.</span><span class="sxs-lookup"><span data-stu-id="b9f07-133">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="b9f07-134">Načte zkompilovaný <xref:System.Xml.Schema.XmlSchema> objektu z <xref:System.Xml.Schema.XmlSchemaSet> pomocí provádí iterace <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b9f07-134">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="b9f07-135">Protože kompilaci schématu, po-Schema-kompilace – informační sadu vlastností (PSCI) jsou přístupné.</span><span class="sxs-lookup"><span data-stu-id="b9f07-135">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="b9f07-136">Vytvoří nový komplexní typ pro `FirstName` pomocí elementu <xref:System.Xml.Schema.XmlSchemaComplexType> třídy.</span><span class="sxs-lookup"><span data-stu-id="b9f07-136">Creates a new complex type for the `FirstName` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
4. <span data-ttu-id="b9f07-137">Vytvoří nový jednoduchým rozšířením obsahu, se jako základní typ `xs:string`, použije <xref:System.Xml.Schema.XmlSchemaSimpleContent> a <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="b9f07-137">Creates a new simple content extension, with a base type of `xs:string`, using the <xref:System.Xml.Schema.XmlSchemaSimpleContent> and <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> classes.</span></span>  
  
5. <span data-ttu-id="b9f07-138">Vytvoří nový `Title` atribut, pomocí <xref:System.Xml.Schema.XmlSchemaAttribute> třídy, se <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> z `xs:string` a přidá atribut k jednoduchým rozšířením obsahu.</span><span class="sxs-lookup"><span data-stu-id="b9f07-138">Creates the new `Title` attribute using the <xref:System.Xml.Schema.XmlSchemaAttribute> class, with a <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> of `xs:string` and adds the attribute to the simple content extension.</span></span>  
  
6. <span data-ttu-id="b9f07-139">Nastaví model obsahu jednoduchý obsah k jednoduchým rozšířením obsahu a obsahu modelu komplexní typ, který má jednoduchý obsah.</span><span class="sxs-lookup"><span data-stu-id="b9f07-139">Sets the content model of the simple content to the simple content extension and the content model of the complex type to the simple content.</span></span>  
  
7. <span data-ttu-id="b9f07-140">Přidá nový komplexní typ do předprodukční-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="b9f07-140">Adds the new complex type to the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
8. <span data-ttu-id="b9f07-141">Iteruje přes každý <xref:System.Xml.Schema.XmlSchemaObject> v předprodukčním-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="b9f07-141">Iterates over each <xref:System.Xml.Schema.XmlSchemaObject> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9f07-142">Vzhledem k tomu, `FirstName` element není globální element ve schématu, není k dispozici v <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> nebo <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="b9f07-142">Because the `FirstName` element is not a global element in the schema, it is not available in the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> or <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="b9f07-143">Příklad kódu vyhledá `FirstName` elementu první vyhledáním `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="b9f07-143">The code example locates the `FirstName` element by first locating the `Customer` element.</span></span>  
>   
>  <span data-ttu-id="b9f07-144">První příklad kódu provázán schématu pomocí po-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="b9f07-144">The first code example traversed the schema using the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="b9f07-145">V této ukázce předprodukční-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekce se používá k procházení schématu.</span><span class="sxs-lookup"><span data-stu-id="b9f07-145">In this sample, the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection is used to traverse the schema.</span></span> <span data-ttu-id="b9f07-146">Obě kolekce nabízejí přístup ke globální prvky ve schématu, iterace <xref:System.Xml.Schema.XmlSchema.Items%2A> kolekce je časově náročnější, protože nutné iterovat všechny globální elementy ve schématu a nemá žádné vlastnosti PSCI.</span><span class="sxs-lookup"><span data-stu-id="b9f07-146">While both collections provide access to the global elements in the schema, iterating through the <xref:System.Xml.Schema.XmlSchema.Items%2A> collection is more time consuming because you must iterate over all global elements in the schema and it does not have any PSCI properties.</span></span> <span data-ttu-id="b9f07-147">Kolekce PSCI (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, a tak dále) poskytuje přímý přístup k jejich globální prvky, atributy a typy a jejich vlastnosti PSCI.</span><span class="sxs-lookup"><span data-stu-id="b9f07-147">The PSCI collections (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, and so on) provide direct access to their global elements, attributes, and types and their PSCI properties.</span></span>  
  
1. <span data-ttu-id="b9f07-148">Pokud <xref:System.Xml.Schema.XmlSchemaObject> je prvek, jehož <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> je `"Customer"`, získá komplexní typ `Customer` pomocí elementu <xref:System.Xml.Schema.XmlSchemaComplexType> třídy a částice sequence komplexní typ použití <xref:System.Xml.Schema.XmlSchemaSequence> třídy.</span><span class="sxs-lookup"><span data-stu-id="b9f07-148">If the <xref:System.Xml.Schema.XmlSchemaObject> is an element, whose <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
2. <span data-ttu-id="b9f07-149">Iteruje přes každý <xref:System.Xml.Schema.XmlSchemaParticle> v předprodukčním-schema-kompilace <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="b9f07-149">Iterates over each <xref:System.Xml.Schema.XmlSchemaParticle> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
3. <span data-ttu-id="b9f07-150">Pokud <xref:System.Xml.Schema.XmlSchemaParticle> je prvek, který vaší <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> je `"FirstName"`, nastaví <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> z `FirstName` elementu do nového `FirstName` komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="b9f07-150">If the <xref:System.Xml.Schema.XmlSchemaParticle> is an element, who's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"FirstName"`, sets the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> of the `FirstName` element to the new `FirstName` complex type.</span></span>  
  
4. <span data-ttu-id="b9f07-151">Nakonec znovu zpracuje a zkompiluje upravené <xref:System.Xml.Schema.XmlSchema> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapíše jej do konzoly.</span><span class="sxs-lookup"><span data-stu-id="b9f07-151">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="b9f07-152">Tady je příklad úplného kódu.</span><span class="sxs-lookup"><span data-stu-id="b9f07-152">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 <span data-ttu-id="b9f07-153">Tady je upravený zákazníka schéma se vytvořilo v [sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="b9f07-153">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b9f07-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9f07-154">See also</span></span>

- [<span data-ttu-id="b9f07-155">Přehled Modelu objektu schématu XML</span><span class="sxs-lookup"><span data-stu-id="b9f07-155">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="b9f07-156">Čtení ze schémat XML a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="b9f07-156">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="b9f07-157">Sestavování schémat XML</span><span class="sxs-lookup"><span data-stu-id="b9f07-157">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="b9f07-158">Procházení schémat XML</span><span class="sxs-lookup"><span data-stu-id="b9f07-158">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="b9f07-159">Zahrnutí nebo import schémat XML</span><span class="sxs-lookup"><span data-stu-id="b9f07-159">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [<span data-ttu-id="b9f07-160">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="b9f07-160">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="b9f07-161">Informační sada po kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="b9f07-161">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
