---
title: "Přehled modelu objektů schématu XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6a06de3f8fb6351d340e1c8f1bfe8f4105967e25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xml-schema-object-model-overview"></a><span data-ttu-id="e6580-102">Přehled modelu objektů schématu XML</span><span class="sxs-lookup"><span data-stu-id="e6580-102">XML Schema Object Model Overview</span></span>
<span data-ttu-id="e6580-103">Model objektu schématu (SOM) v rozhraní Microsoft .NET Framework je bohatá rozhraní API, která umožňuje vytvářet, upravovat a ověřit schémata prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="e6580-103">The Schema Object Model (SOM) in the Microsoft .NET Framework is a rich API that allows you to create, edit, and validate schemas programmatically.</span></span> <span data-ttu-id="e6580-104">SOM funguje na dokumentech schémat XML podobně jako na způsob, jakým modelu objektu dokumentu (DOM) funguje na dokumenty XML.</span><span class="sxs-lookup"><span data-stu-id="e6580-104">The SOM operates on XML schema documents similarly to the way the Document Object Model (DOM) operates on XML documents.</span></span> <span data-ttu-id="e6580-105">Dokumentech schémat XML. jsou platné soubory XML, které jednou načtena do SOM, nesou význam o struktuře a platnosti jiných dokumentů XML, která vyhovují schématu.</span><span class="sxs-lookup"><span data-stu-id="e6580-105">XML schema documents are valid XML files that, once loaded into the SOM, convey meaning about the structure and validity of other XML documents which conform to the schema.</span></span>  
  
 <span data-ttu-id="e6580-106">Schéma je dokument XML, který definuje třídu dokumentů XML zadáním struktura nebo model dokumentů XML pro konkrétní schématu.</span><span class="sxs-lookup"><span data-stu-id="e6580-106">A schema is an XML document that defines a class of XML documents by specifying the structure or model of XML documents for a particular schema.</span></span> <span data-ttu-id="e6580-107">Schéma identifikuje omezení u obsah dokumentů XML a popisuje termínů (pravidla nebo gramatika), aby se považovala za schématu platný s dané schéma musí následovat kompatibilní dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="e6580-107">A schema identifies the constraints on the content of the XML documents, and describes the vocabulary (rules or grammar) that compliant XML documents must follow in order to be considered schema-valid with that particular schema.</span></span> <span data-ttu-id="e6580-108">Ověření dokumentu XML je proces, který zajistí, že dokument odpovídá gramatika určeného schématu.</span><span class="sxs-lookup"><span data-stu-id="e6580-108">Validation of an XML document is the process that ensures that the document conforms to the grammar specified by the schema.</span></span>  
  
 <span data-ttu-id="e6580-109">Následují způsoby rozhraní API SOM v rozhraní .NET Framework umožňuje vytvářet, upravovat a ověřit schémata.</span><span class="sxs-lookup"><span data-stu-id="e6580-109">The following are ways the SOM API in the .NET Framework enables you to create, edit, and validate schemas.</span></span>  
  
-   <span data-ttu-id="e6580-110">Načtení a uložte platná schémata do a z soubory.</span><span class="sxs-lookup"><span data-stu-id="e6580-110">Load and save valid schemas to and from files.</span></span>  
  
-   <span data-ttu-id="e6580-111">Vytvořte v paměti schémata pomocí třídy silného typu.</span><span class="sxs-lookup"><span data-stu-id="e6580-111">Create in-memory schemas using strongly typed classes.</span></span>  
  
-   <span data-ttu-id="e6580-112">Komunikovat s <xref:System.Xml.Schema.XmlSchemaSet> třída ukládat do mezipaměti, kompilace a načíst schémat.</span><span class="sxs-lookup"><span data-stu-id="e6580-112">Interact with the <xref:System.Xml.Schema.XmlSchemaSet> class to cache, compile, and retrieve schemas.</span></span>  
  
-   <span data-ttu-id="e6580-113">Komunikovat s <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> třída k ověření instance dokumentů XML pomocí schémat.</span><span class="sxs-lookup"><span data-stu-id="e6580-113">Interact with the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to validate XML instance documents against schemas.</span></span>  
  
-   <span data-ttu-id="e6580-114">Sestavení editory pro vytváření a Správa schémat.</span><span class="sxs-lookup"><span data-stu-id="e6580-114">Build editors for creating and maintaining schemas.</span></span>  
  
-   <span data-ttu-id="e6580-115">Dynamicky upravte schéma, které mohou být v souladu a uložit pro použití při ověřování dokumentů XML instance.</span><span class="sxs-lookup"><span data-stu-id="e6580-115">Dynamically edit a schema that can be complied and saved for use in the validation of XML instance documents.</span></span>  
  
## <a name="the-schema-object-model"></a><span data-ttu-id="e6580-116">Objektový Model schématu</span><span class="sxs-lookup"><span data-stu-id="e6580-116">The Schema Object Model</span></span>  
 <span data-ttu-id="e6580-117">Se skládá z rozsáhlou sadu tříd ve model SOM <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů odpovídající elementům ve schématu XML.</span><span class="sxs-lookup"><span data-stu-id="e6580-117">The SOM consists of an extensive set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace corresponding to the elements in an XML schema.</span></span> <span data-ttu-id="e6580-118">Například `<xsd:schema>...</xsd:schema>` se mapuje na element <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> třídy a veškeré informace, které může být obsažený v rámci `<xsd:schema/>` element může být reprezentován pomocí <xref:System.Xml.Schema.XmlSchema> třídy.</span><span class="sxs-lookup"><span data-stu-id="e6580-118">For example, the `<xsd:schema>...</xsd:schema>` element maps to the <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> class, and all the information that can be contained within an `<xsd:schema/>` element can be represented using the <xref:System.Xml.Schema.XmlSchema> class.</span></span> <span data-ttu-id="e6580-119">Podobně `<xsd:element>...</xsd:element>` a `<xsd:attribute>...</xsd:attribute>` elementy mapovat <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> a <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> třídy v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e6580-119">Similarly, the `<xsd:element>...</xsd:element>` and `<xsd:attribute>...</xsd:attribute>` elements map to the <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> and <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> classes respectively.</span></span> <span data-ttu-id="e6580-120">Toto mapování pokračuje pro všechny elementy schématu XML vytváření objektový model schématu XML v <xref:System.Xml.Schema> obor názvů znázorněné na obrázku, který následuje dále.</span><span class="sxs-lookup"><span data-stu-id="e6580-120">This mapping continues for all the elements of an XML schema creating an XML schema object model in the <xref:System.Xml.Schema> namespace illustrated in the diagram that follows.</span></span>  
  
 <span data-ttu-id="e6580-121">![Objektový Model System.Xml.Schema](../../../../docs/standard/data/xml/media/xmlschemaobjmodeloverview.gif "XMLSchemaObjModelOverview")</span><span class="sxs-lookup"><span data-stu-id="e6580-121">![System.Xml.Schema Object Model](../../../../docs/standard/data/xml/media/xmlschemaobjmodeloverview.gif "XMLSchemaObjModelOverview")</span></span>  
  
 <span data-ttu-id="e6580-122">Další informace o každé třídě <xref:System.Xml.Schema> obor názvů, najdete v článku <xref:System.Xml.Schema> obor názvů referenční dokumentaci v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e6580-122">For more information about each class in the <xref:System.Xml.Schema> namespace, see the <xref:System.Xml.Schema> namespace reference documentation in the .NET Framework class library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6580-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6580-123">See Also</span></span>  
 [<span data-ttu-id="e6580-124">Čtení a zápis XML schémata</span><span class="sxs-lookup"><span data-stu-id="e6580-124">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [<span data-ttu-id="e6580-125">Vytváření XML schémata</span><span class="sxs-lookup"><span data-stu-id="e6580-125">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [<span data-ttu-id="e6580-126">Procházení schémat XML</span><span class="sxs-lookup"><span data-stu-id="e6580-126">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [<span data-ttu-id="e6580-127">Úpravy XML schémata</span><span class="sxs-lookup"><span data-stu-id="e6580-127">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [<span data-ttu-id="e6580-128">Včetně nebo import schémat XML</span><span class="sxs-lookup"><span data-stu-id="e6580-128">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [<span data-ttu-id="e6580-129">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="e6580-129">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="e6580-130">Informační sadu po schématu kompilace</span><span class="sxs-lookup"><span data-stu-id="e6580-130">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
