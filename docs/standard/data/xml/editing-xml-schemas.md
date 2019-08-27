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
ms.openlocfilehash: bd40677b3b21a4ee1b237656ea2814badbbcd593
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040767"
---
# <a name="editing-xml-schemas"></a><span data-ttu-id="7d712-102">Úpravy schémat XML</span><span class="sxs-lookup"><span data-stu-id="7d712-102">Editing XML Schemas</span></span>

<span data-ttu-id="7d712-103">Úprava schématu XML je jednou z nejdůležitějších funkcí modelu SOM (Schema Object Model).</span><span class="sxs-lookup"><span data-stu-id="7d712-103">Editing an XML schema is one of the most important features of the Schema Object Model (SOM).</span></span> <span data-ttu-id="7d712-104">Ke změně stávajících hodnot ve schématu XML lze použít všechny vlastnosti rozhraní SOM před schématem-Schema-Compilation.</span><span class="sxs-lookup"><span data-stu-id="7d712-104">All of the pre-schema-compilation properties of the SOM can be used to change the existing values in an XML schema.</span></span> <span data-ttu-id="7d712-105">Schéma XML lze poté znovu zkompilovat, aby odráželo změny.</span><span class="sxs-lookup"><span data-stu-id="7d712-105">The XML schema can then be recompiled to reflect the changes.</span></span>

<span data-ttu-id="7d712-106">Prvním krokem při úpravách schématu načteného do modelu SOM je procházení schématu.</span><span class="sxs-lookup"><span data-stu-id="7d712-106">The first step in editing a schema loaded into the SOM is to traverse the schema.</span></span> <span data-ttu-id="7d712-107">Předtím, než se pokusíte upravit schéma, byste měli být obeznámeni s procházením schématu pomocí rozhraní API modelu SOM.</span><span class="sxs-lookup"><span data-stu-id="7d712-107">You should be familiar with traversing a schema using the SOM API before you attempt to edit a schema.</span></span> <span data-ttu-id="7d712-108">Měli byste být také obeznámeni s vlastnostmi předběžného a post-Schema-Compilation-PSCI (post-Schema-Compilation-informační sada).</span><span class="sxs-lookup"><span data-stu-id="7d712-108">You should also be familiar with the pre- and post-schema-compilation properties of the Post-Schema-Compilation-Infoset (PSCI).</span></span>

## <a name="editing-an-xml-schema"></a><span data-ttu-id="7d712-109">Úprava schématu XML</span><span class="sxs-lookup"><span data-stu-id="7d712-109">Editing an XML Schema</span></span>

<span data-ttu-id="7d712-110">V této části jsou k dispozici dva příklady kódu, jak upravit schéma zákazníka vytvořené v tématu [sestavení XML schémat](../../../../docs/standard/data/xml/building-xml-schemas.md) .</span><span class="sxs-lookup"><span data-stu-id="7d712-110">In this section, two code examples are provided, both of which edit the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span> <span data-ttu-id="7d712-111">První příklad kódu přidá `PhoneNumber` nový prvek `Customer` do prvku a druhý příklad kódu přidá nový `Title` atribut `FirstName` elementu.</span><span class="sxs-lookup"><span data-stu-id="7d712-111">The first code example adds a new `PhoneNumber` element to the `Customer` element and the second code example adds a new `Title` attribute to the `FirstName` element.</span></span> <span data-ttu-id="7d712-112">První vzorek také používá kolekci po kompilaci <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> po schématu jako způsob procházení schématu zákazníka, zatímco druhý příklad kódu používá kolekci předběžného schématu kompilace. <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7d712-112">The first sample also uses the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection as the means of traversing the customer schema while the second code example uses the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

### <a name="phonenumber-element-example"></a><span data-ttu-id="7d712-113">Příklad prvku PhoneNumber</span><span class="sxs-lookup"><span data-stu-id="7d712-113">PhoneNumber Element Example</span></span>

<span data-ttu-id="7d712-114">Tento první příklad kódu přidá nový `PhoneNumber` prvek `Customer` do prvku schématu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="7d712-114">This first code example adds a new `PhoneNumber` element to the `Customer` element of the customer schema.</span></span> <span data-ttu-id="7d712-115">Příklad kódu upravuje schéma zákazníka v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="7d712-115">The code example edits the customer schema in the following steps.</span></span>

1. <span data-ttu-id="7d712-116">Přidá schéma zákazníka do nového <xref:System.Xml.Schema.XmlSchemaSet> objektu a potom jej zkompiluje.</span><span class="sxs-lookup"><span data-stu-id="7d712-116">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="7d712-117"><xref:System.Xml.Schema.ValidationEventHandler> Delegát zpracovává všechna upozornění ověřování schématu a chyby, ke kterým došlo při čtení nebo kompilování schématu.</span><span class="sxs-lookup"><span data-stu-id="7d712-117">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="7d712-118">Načte kompilovaný <xref:System.Xml.Schema.XmlSchema> objekt z rozhraní <xref:System.Xml.Schema.XmlSchemaSet> iterací přes <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7d712-118">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="7d712-119">Vzhledem k tomu, že schéma je kompilováno, jsou k dispozici vlastnosti po PSCI (post-Schema-Compilation-informační sada).</span><span class="sxs-lookup"><span data-stu-id="7d712-119">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="7d712-120">`xs:string` <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> <xref:System.Xml.Schema.XmlSchemaSimpleType> Vytvoří element pomocí třídy, jednoduché omezení typu pomocí tříd a, přidá omezující <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> vlastnost vzoru do vlastnosti omezení a přidá <xref:System.Xml.Schema.XmlSchemaElement> `PhoneNumber` omezení na <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> vlastnost jednoduchého typu a jednoduchý typ <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> pro `PhoneNumber` element.</span><span class="sxs-lookup"><span data-stu-id="7d712-120">Creates the `PhoneNumber` element using the <xref:System.Xml.Schema.XmlSchemaElement> class, the `xs:string` simple type restriction using the <xref:System.Xml.Schema.XmlSchemaSimpleType> and <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classes, adds a pattern facet to the <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> property of the restriction, and adds the restriction to the <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> property of the simple type and the simple type to the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> of the `PhoneNumber` element.</span></span>

4. <span data-ttu-id="7d712-121">Provede iteraci každého <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> v kolekci kolekce post-Schema-Compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7d712-121">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span>

5. <span data-ttu-id="7d712-122"><xref:System.Xml.Schema.XmlSchemaSequence> <xref:System.Xml.Schema.XmlSchemaComplexType> Pokud je `"Customer"`element, získá komplexní typ `Customer` elementu pomocí třídy a částice sekvence komplexního typu pomocí třídy. <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A></span><span class="sxs-lookup"><span data-stu-id="7d712-122">If the <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> of the element is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

6. <span data-ttu-id="7d712-123">Přidá nový `PhoneNumber` prvek do sekvence obsahující existující `FirstName` prvky a `LastName` pomocí kolekce předběžného schématu kompilace <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> sekvence.</span><span class="sxs-lookup"><span data-stu-id="7d712-123">Adds the new `PhoneNumber` element to the sequence containing the existing `FirstName` and `LastName` elements using the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> collection of the sequence.</span></span>

7. <span data-ttu-id="7d712-124">Nakonec znovu zpracuje <xref:System.Xml.Schema.XmlSchema> a zkompiluje upravený objekt <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> pomocí metod <xref:System.Xml.Schema.XmlSchemaSet> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> třídy a zapíše jej do konzoly.</span><span class="sxs-lookup"><span data-stu-id="7d712-124">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>

<span data-ttu-id="7d712-125">Následuje příklad kompletního příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="7d712-125">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
[!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
[!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]

<span data-ttu-id="7d712-126">Toto je upravené schéma zákazníka vytvořené v tématu sestavování [schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) .</span><span class="sxs-lookup"><span data-stu-id="7d712-126">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>

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

### <a name="title-attribute-example"></a><span data-ttu-id="7d712-127">Příklad atributu title</span><span class="sxs-lookup"><span data-stu-id="7d712-127">Title Attribute Example</span></span>

<span data-ttu-id="7d712-128">Tento druhý příklad kódu přidá nový `Title` atribut `FirstName` do elementu schématu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="7d712-128">This second code example, adds a new `Title` attribute to the `FirstName` element of the customer schema.</span></span> <span data-ttu-id="7d712-129">V prvním příkladu kódu je `FirstName` `xs:string`typ elementu.</span><span class="sxs-lookup"><span data-stu-id="7d712-129">In the first code example, the type of the `FirstName` element is `xs:string`.</span></span> <span data-ttu-id="7d712-130">`FirstName` Aby element měl atribut spolu s obsahem řetězce, musí být jeho typ změněn na komplexní typ s jednoduchým obsahem obsahu rozšíření obsahu.</span><span class="sxs-lookup"><span data-stu-id="7d712-130">For the `FirstName` element to have an attribute along with string content, its type must be changed to a complex type with a simple content extension content model.</span></span>

<span data-ttu-id="7d712-131">Příklad kódu upravuje schéma zákazníka v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="7d712-131">The code example edits the customer schema in the following steps.</span></span>

1. <span data-ttu-id="7d712-132">Přidá schéma zákazníka do nového <xref:System.Xml.Schema.XmlSchemaSet> objektu a potom jej zkompiluje.</span><span class="sxs-lookup"><span data-stu-id="7d712-132">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="7d712-133"><xref:System.Xml.Schema.ValidationEventHandler> Delegát zpracovává všechna upozornění ověřování schématu a chyby, ke kterým došlo při čtení nebo kompilování schématu.</span><span class="sxs-lookup"><span data-stu-id="7d712-133">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="7d712-134">Načte kompilovaný <xref:System.Xml.Schema.XmlSchema> objekt z rozhraní <xref:System.Xml.Schema.XmlSchemaSet> iterací přes <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7d712-134">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="7d712-135">Vzhledem k tomu, že schéma je kompilováno, jsou k dispozici vlastnosti po PSCI (post-Schema-Compilation-informační sada).</span><span class="sxs-lookup"><span data-stu-id="7d712-135">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="7d712-136">Vytvoří nový komplexní typ pro `FirstName` element <xref:System.Xml.Schema.XmlSchemaComplexType> pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="7d712-136">Creates a new complex type for the `FirstName` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>

4. <span data-ttu-id="7d712-137">Vytvoří nové jednoduché rozšíření obsahu se základním typem `xs:string`, <xref:System.Xml.Schema.XmlSchemaSimpleContent> pomocí tříd a <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> .</span><span class="sxs-lookup"><span data-stu-id="7d712-137">Creates a new simple content extension, with a base type of `xs:string`, using the <xref:System.Xml.Schema.XmlSchemaSimpleContent> and <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> classes.</span></span>

5. <span data-ttu-id="7d712-138">Vytvoří nový `Title` atribut <xref:System.Xml.Schema.XmlSchemaAttribute> <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> pomocí`xs:string` třídy s a a přidá do jednoduchého rozšíření obsahu atribut.</span><span class="sxs-lookup"><span data-stu-id="7d712-138">Creates the new `Title` attribute using the <xref:System.Xml.Schema.XmlSchemaAttribute> class, with a <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> of `xs:string` and adds the attribute to the simple content extension.</span></span>

6. <span data-ttu-id="7d712-139">Nastaví model obsahu jednoduchého obsahu na jednoduché rozšíření obsahu a model obsahu komplexního typu na jednoduchý obsah.</span><span class="sxs-lookup"><span data-stu-id="7d712-139">Sets the content model of the simple content to the simple content extension and the content model of the complex type to the simple content.</span></span>

7. <span data-ttu-id="7d712-140">Přidá nový komplexní typ do kolekce předběžného schématu kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7d712-140">Adds the new complex type to the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

8. <span data-ttu-id="7d712-141">Iteruje u každého <xref:System.Xml.Schema.XmlSchemaObject> v kolekci kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> před schématy.</span><span class="sxs-lookup"><span data-stu-id="7d712-141">Iterates over each <xref:System.Xml.Schema.XmlSchemaObject> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

> [!NOTE]
> <span data-ttu-id="7d712-142">Vzhledem k tomu, že <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> elementneníglobálnímprvkemveschématu,neníkdispoziciv`FirstName` kolekcích ani.</span><span class="sxs-lookup"><span data-stu-id="7d712-142">Because the `FirstName` element is not a global element in the schema, it is not available in the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> or <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="7d712-143">Příklad kódu vyhledá `FirstName` element tak, že nejprve `Customer` najde element.</span><span class="sxs-lookup"><span data-stu-id="7d712-143">The code example locates the `FirstName` element by first locating the `Customer` element.</span></span>
>
> <span data-ttu-id="7d712-144">První příklad kódu procházel schéma pomocí kolekce post-Schema-Compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7d712-144">The first code example traversed the schema using the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="7d712-145">V této ukázce se k procházení schématu používá kolekce předběžného schématu kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7d712-145">In this sample, the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection is used to traverse the schema.</span></span> <span data-ttu-id="7d712-146">Zatímco obě kolekce poskytují přístup k globálním prvkům ve schématu, iterace <xref:System.Xml.Schema.XmlSchema.Items%2A> v kolekci je více časově náročná, protože je nutné iterovat všechny globální prvky ve schématu a nemá žádné vlastnosti pSCI.</span><span class="sxs-lookup"><span data-stu-id="7d712-146">While both collections provide access to the global elements in the schema, iterating through the <xref:System.Xml.Schema.XmlSchema.Items%2A> collection is more time consuming because you must iterate over all global elements in the schema and it does not have any PSCI properties.</span></span> <span data-ttu-id="7d712-147">Kolekce pSCI (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>,, a tak dále) poskytují přímý přístup ke svým globálním prvkům, atributům a typům a jejich PSCIm vlastnostem. <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7d712-147">The PSCI collections (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, and so on) provide direct access to their global elements, attributes, and types and their PSCI properties.</span></span>

1. <span data-ttu-id="7d712-148">`Customer` `"Customer"` <xref:System.Xml.Schema.XmlSchemaComplexType> <xref:System.Xml.Schema.XmlSchemaSequence> Pokud je element, jehož <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> typ je, získá komplexní typ elementu pomocí třídy a částice sekvence komplexního typu pomocí třídy. <xref:System.Xml.Schema.XmlSchemaObject></span><span class="sxs-lookup"><span data-stu-id="7d712-148">If the <xref:System.Xml.Schema.XmlSchemaObject> is an element, whose <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

2. <span data-ttu-id="7d712-149">Iteruje u každého <xref:System.Xml.Schema.XmlSchemaParticle> v kolekci kompilace <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> před schématy.</span><span class="sxs-lookup"><span data-stu-id="7d712-149">Iterates over each <xref:System.Xml.Schema.XmlSchemaParticle> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="7d712-150"><xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> `"FirstName"` `FirstName` Pokud je prvek, <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> který je, je nastaveno na nový `FirstName` komplexní typ elementu. <xref:System.Xml.Schema.XmlSchemaParticle></span><span class="sxs-lookup"><span data-stu-id="7d712-150">If the <xref:System.Xml.Schema.XmlSchemaParticle> is an element, who's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"FirstName"`, sets the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> of the `FirstName` element to the new `FirstName` complex type.</span></span>

4. <span data-ttu-id="7d712-151">Nakonec znovu zpracuje <xref:System.Xml.Schema.XmlSchema> a zkompiluje upravený objekt <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> pomocí metod <xref:System.Xml.Schema.XmlSchemaSet> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> třídy a zapíše jej do konzoly.</span><span class="sxs-lookup"><span data-stu-id="7d712-151">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>

<span data-ttu-id="7d712-152">Následuje příklad kompletního příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="7d712-152">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
[!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
[!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]

<span data-ttu-id="7d712-153">Toto je upravené schéma zákazníka vytvořené v tématu sestavování [schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) .</span><span class="sxs-lookup"><span data-stu-id="7d712-153">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7d712-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d712-154">See also</span></span>

- [<span data-ttu-id="7d712-155">Přehled Modelu objektu schématu XML</span><span class="sxs-lookup"><span data-stu-id="7d712-155">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="7d712-156">Čtení ze schémat XML a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="7d712-156">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="7d712-157">Sestavování schémat XML</span><span class="sxs-lookup"><span data-stu-id="7d712-157">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="7d712-158">Procházení schémat XML</span><span class="sxs-lookup"><span data-stu-id="7d712-158">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="7d712-159">Zahrnutí nebo import schémat XML</span><span class="sxs-lookup"><span data-stu-id="7d712-159">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [<span data-ttu-id="7d712-160">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="7d712-160">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="7d712-161">Informační sada po kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="7d712-161">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
