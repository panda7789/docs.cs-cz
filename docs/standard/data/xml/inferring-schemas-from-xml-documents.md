---
title: "Odvození schémata z dokumentů XML"
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
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8085ecb86018460f14a2532b55907472988b67b2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="inferring-schemas-from-xml-documents"></a><span data-ttu-id="0e272-102">Odvození schémata z dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="0e272-102">Inferring Schemas from XML Documents</span></span>
<span data-ttu-id="0e272-103">Toto téma popisuje postup použití <xref:System.Xml.Schema.XmlSchemaInference> třídy pro odvození schématu XML definition language (XSD) schématu ze struktury dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0e272-103">This topic describes how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XML Schema definition language (XSD) schema from the structure of an XML document.</span></span>  
  
## <a name="the-schema-inference-process"></a><span data-ttu-id="0e272-104">Proces odvození schématu</span><span class="sxs-lookup"><span data-stu-id="0e272-104">The Schema Inference Process</span></span>  
 <span data-ttu-id="0e272-105"><xref:System.Xml.Schema.XmlSchemaInference> Třídu <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů se používá ke generování jednoho nebo více schématu XML definition language (XSD) schémat ze struktury dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0e272-105">The <xref:System.Xml.Schema.XmlSchemaInference> class of the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace is used to generate one or more XML Schema definition language (XSD) schemas from the structure of an XML document.</span></span> <span data-ttu-id="0e272-106">Vygenerovaný schémata může sloužit k ověření původního dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0e272-106">The generated schemas may be used to validate the original XML document.</span></span>  
  
 <span data-ttu-id="0e272-107">Jako XML dokumentu zpracovává <xref:System.Xml.Schema.XmlSchemaInference> třídy, <xref:System.Xml.Schema.XmlSchemaInference> třída provádí předpoklady o komponenty schématu, které popisují elementů a atributů v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0e272-107">As an XML document is processed by the <xref:System.Xml.Schema.XmlSchemaInference> class, the <xref:System.Xml.Schema.XmlSchemaInference> class makes assumptions about the schema components that describe the elements and attributes in the XML document.</span></span> <span data-ttu-id="0e272-108"><xref:System.Xml.Schema.XmlSchemaInference> Třída také odvodí komponenty schématu omezené způsobem podle odvození nejvíc omezující typ pro konkrétní elementu nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="0e272-108">The <xref:System.Xml.Schema.XmlSchemaInference> class also infers schema components in a constrained way by inferring the most restrictive type for a particular element or attribute.</span></span> <span data-ttu-id="0e272-109">Jako další informace o dokumentu XML jsou shromažďovány, jsou tyto omezení snížit podle odvození méně omezující typy.</span><span class="sxs-lookup"><span data-stu-id="0e272-109">As more information about the XML document is gathered, these constraints are loosened by inferring less restrictive types.</span></span> <span data-ttu-id="0e272-110">Je nejméně omezující typ, který lze odvodit `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="0e272-110">The least restrictive type that can be inferred is `xs:string`.</span></span>  
  
 <span data-ttu-id="0e272-111">Využít, například následující část dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0e272-111">Take, for example, the following piece of an XML document.</span></span>  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A">  
```  
  
 <span data-ttu-id="0e272-112">V příkladu výše, kdy `attribute1` zjistil se atributu s hodnotou `6` podle <xref:System.Xml.Schema.XmlSchemaInference> procesu, se předpokládá, bude typu `xs:unsignedByte`.</span><span class="sxs-lookup"><span data-stu-id="0e272-112">In the example above, when the `attribute1` attribute is encountered with a value of `6` by the <xref:System.Xml.Schema.XmlSchemaInference> process, it is assumed to be of type `xs:unsignedByte`.</span></span> <span data-ttu-id="0e272-113">Při druhý `parent` je element kterými <xref:System.Xml.Schema.XmlSchemaInference> procesů, omezení je snížit změnou typ, který má `xs:string` protože hodnota `attribute1` je atribut `A`.</span><span class="sxs-lookup"><span data-stu-id="0e272-113">When the second `parent` element is encountered by the <xref:System.Xml.Schema.XmlSchemaInference> process, the constraint is loosened by modifying the type to `xs:string` because the value of the `attribute1` attribute is now `A`.</span></span> <span data-ttu-id="0e272-114">Podobně `minOccurs` atribut pro všechny `child` elementy odvodit ve schématu se snížit na `minOccurs="0"` protože druhý nadřazeného elementu nemá žádné podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="0e272-114">Similarly, the `minOccurs` attribute for all the `child` elements inferred in the schema are loosened to `minOccurs="0"` because the second parent element has no child elements.</span></span>  
  
## <a name="inferring-schemas-from-xml-documents"></a><span data-ttu-id="0e272-115">Odvození schémata z dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="0e272-115">Inferring Schemas from XML Documents</span></span>  
 <span data-ttu-id="0e272-116"><xref:System.Xml.Schema.XmlSchemaInference> Třída používá dva přetížený <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metody pro odvození schématu z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0e272-116">The <xref:System.Xml.Schema.XmlSchemaInference> class uses two overloaded <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> methods to infer a schema from an XML document.</span></span>  
  
 <span data-ttu-id="0e272-117">První <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda se používá k vytvoření schéma založené na dokument XML.</span><span class="sxs-lookup"><span data-stu-id="0e272-117">The first <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method is used to create a schema based on an XML document.</span></span> <span data-ttu-id="0e272-118">Druhý <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda se používá k odvození schéma, které popisuje více dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="0e272-118">The second <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method is used to infer a schema that describes multiple XML documents.</span></span> <span data-ttu-id="0e272-119">Například může zadat více dokumentů XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda, jeden v době vytvoření schéma, které popisuje celou sadu dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="0e272-119">For example, you can feed multiple XML documents to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method one at a time to produce a schema that describes the entire set of XML documents.</span></span>  
  
 <span data-ttu-id="0e272-120">První <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda odvodí schématu z dokumentu XML, který je součástí <xref:System.Xml.XmlReader> objekt a vrátí <xref:System.Xml.Schema.XmlSchemaSet> objekt obsahující odvozené schématu.</span><span class="sxs-lookup"><span data-stu-id="0e272-120">The first <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method infers a schema from an XML document contained in an <xref:System.Xml.XmlReader> object, and returns an <xref:System.Xml.Schema.XmlSchemaSet> object containing the inferred schema.</span></span> <span data-ttu-id="0e272-121">Druhý <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda hledání <xref:System.Xml.Schema.XmlSchemaSet> objekt pro schématu s stejný cílový obor názvů jako dokument XML obsažených v <xref:System.Xml.XmlReader> zpřesnění schéma existující objekt a vrátí <xref:System.Xml.Schema.XmlSchemaSet> objekt obsahující odvozené schéma.</span><span class="sxs-lookup"><span data-stu-id="0e272-121">The second <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method searches an <xref:System.Xml.Schema.XmlSchemaSet> object for a schema with the same target namespace as the XML document contained in the <xref:System.Xml.XmlReader> object, refines the existing schema, and returns an <xref:System.Xml.Schema.XmlSchemaSet> object containing the inferred schema.</span></span>  
  
 <span data-ttu-id="0e272-122">Změny provedené v přesnějších schématu jsou založené na nové struktura nalezen v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0e272-122">The changes made to the refined schema are based on new structure found in the XML document.</span></span> <span data-ttu-id="0e272-123">Například jako dokument XML vyčerpán, předpoklady jsou vytvářeny o datových typech, najít a schéma se vytvoří na základě těchto předpokladů.</span><span class="sxs-lookup"><span data-stu-id="0e272-123">For example, as an XML document is traversed, assumptions are made about the data types found, and the schema is created based on those assumptions.</span></span> <span data-ttu-id="0e272-124">Schéma je přesnějších však v případě dat při druhý odvození průchodu odlišnou od původního předpokladů.</span><span class="sxs-lookup"><span data-stu-id="0e272-124">However, if data is encountered on a second inference pass that differs from the original assumption, the schema is refined.</span></span> <span data-ttu-id="0e272-125">Následující příklad znázorňuje proces vylepšení.</span><span class="sxs-lookup"><span data-stu-id="0e272-125">The following example illustrates the refinement process.</span></span>  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 <span data-ttu-id="0e272-126">V příkladu přijímá následující soubor, `item1.xml`, jako první vstup.</span><span class="sxs-lookup"><span data-stu-id="0e272-126">The example takes the following file, `item1.xml`, as its first input.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 <span data-ttu-id="0e272-127">V příkladu pak dojde `item2.xml` souboru jako druhý vstup:</span><span class="sxs-lookup"><span data-stu-id="0e272-127">The example then takes the `item2.xml` file as its second input:</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 <span data-ttu-id="0e272-128">Když `productID` atribut se vyskytuje v první dokument XML, hodnota `123456789` předpokládá se, že `xs:unsignedInt` typu.</span><span class="sxs-lookup"><span data-stu-id="0e272-128">When the `productID` attribute is encountered in the first XML document, the value of `123456789` is assumed to be an `xs:unsignedInt` type.</span></span> <span data-ttu-id="0e272-129">Ale pokud je druhého dokumentu XML pro čtení a hodnota `A53-246` nenajde, `xs:unsignedInt` už předpokládá typ.</span><span class="sxs-lookup"><span data-stu-id="0e272-129">However, when the second XML document is read and the value of `A53-246` is found, the `xs:unsignedInt` type can no longer be assumed.</span></span> <span data-ttu-id="0e272-130">Schéma je přesnějších a typ `productID` se změní na `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="0e272-130">The schema is refined and the type of `productID` is changed to `xs:string`.</span></span> <span data-ttu-id="0e272-131">Kromě toho `minOccurs` atribut pro `supplierID` element je nastaven na hodnotu `0`, protože druhého dokumentu XML obsahuje Ne `supplierID` elementu.</span><span class="sxs-lookup"><span data-stu-id="0e272-131">In addition, the `minOccurs` attribute for the `supplierID` element is set to `0`, because the second XML document contains no `supplierID` element.</span></span>  
  
 <span data-ttu-id="0e272-132">Toto je schéma odvodit z první dokument XML.</span><span class="sxs-lookup"><span data-stu-id="0e272-132">The following is the schema inferred from the first XML document.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 <span data-ttu-id="0e272-133">Toto je schéma odvodit z první dokument XML, vylepšení podle druhého dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0e272-133">The following is the schema inferred from the first XML document, refined by the second XML document.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a><span data-ttu-id="0e272-134">Vložené schémata</span><span class="sxs-lookup"><span data-stu-id="0e272-134">Inline Schemas</span></span>  
 <span data-ttu-id="0e272-135">Pokud je vložené schéma schématu XML definition language (XSD) došlo během <xref:System.Xml.Schema.XmlSchemaInference> procesu <xref:System.Xml.Schema.XmlSchemaInferenceException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="0e272-135">If an inline XML Schema definition language (XSD) schema is encountered during the <xref:System.Xml.Schema.XmlSchemaInference> process, an <xref:System.Xml.Schema.XmlSchemaInferenceException> is thrown.</span></span> <span data-ttu-id="0e272-136">Například následující vložené schéma vyvolá <xref:System.Xml.Schema.XmlSchemaInferenceException>.</span><span class="sxs-lookup"><span data-stu-id="0e272-136">For example, the following inline schema throws an <xref:System.Xml.Schema.XmlSchemaInferenceException>.</span></span>  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a><span data-ttu-id="0e272-137">Schémata, které nelze Refined</span><span class="sxs-lookup"><span data-stu-id="0e272-137">Schemas that Cannot be Refined</span></span>  
 <span data-ttu-id="0e272-138">Koncepty schémat XML W3C, která jsou schéma schématu XML definition language (XSD) <xref:System.Xml.Schema.XmlSchemaInference> proces nemůže zpracovat, pokud daný typ Upřesnit a způsobit, že vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="0e272-138">There are W3C XML Schema constructs that the XML Schema definition language (XSD) schema <xref:System.Xml.Schema.XmlSchemaInference> process cannot handle if given a type to refine and cause an exception to be thrown.</span></span> <span data-ttu-id="0e272-139">Například pro komplexní typ jejichž složku nejvyšší úrovně je jakoukoli jinou hodnotu než sekvenci.</span><span class="sxs-lookup"><span data-stu-id="0e272-139">Such as a complex type whose top-level compositor is anything other than a sequence.</span></span> <span data-ttu-id="0e272-140">Ve schématu objektu modelu (model SOM), odpovídá <xref:System.Xml.Schema.XmlSchemaComplexType> jejichž <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> vlastnost není instance <xref:System.Xml.Schema.XmlSchemaSequence>.</span><span class="sxs-lookup"><span data-stu-id="0e272-140">In the Schema Object Model (SOM), this corresponds to an <xref:System.Xml.Schema.XmlSchemaComplexType> whose <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> property is not an instance of <xref:System.Xml.Schema.XmlSchemaSequence>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e272-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e272-141">See Also</span></span>  
 <xref:System.Xml.Schema.XmlSchemaInference>  
 [<span data-ttu-id="0e272-142">Model objektu schématu (SOM) XML</span><span class="sxs-lookup"><span data-stu-id="0e272-142">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 [<span data-ttu-id="0e272-143">Odvození schématu XML</span><span class="sxs-lookup"><span data-stu-id="0e272-143">Inferring an XML Schema</span></span>](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 [<span data-ttu-id="0e272-144">Pravidla pro odvození typů a struktury uzlů schémat</span><span class="sxs-lookup"><span data-stu-id="0e272-144">Rules for Inferring Schema Node Types and Structure</span></span>](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)  
 [<span data-ttu-id="0e272-145">Pravidla pro odvození jednoduchých typů</span><span class="sxs-lookup"><span data-stu-id="0e272-145">Rules for Inferring Simple Types</span></span>](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
