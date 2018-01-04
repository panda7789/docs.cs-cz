---
title: "Vytváření XML schémata"
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
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 72e3d707caf9c5e64c9860a8e79b5e151ce68852
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="building-xml-schemas"></a><span data-ttu-id="e1de9-102">Vytváření XML schémata</span><span class="sxs-lookup"><span data-stu-id="e1de9-102">Building XML Schemas</span></span>
<span data-ttu-id="e1de9-103">Třídy v <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů namapovat struktury definované v doporučení schématu XML World Wide Web Consortium (W3C) a slouží k vytvoření XML schémata v paměti.</span><span class="sxs-lookup"><span data-stu-id="e1de9-103">The classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation and can be used to build XML schemas in-memory.</span></span>  
  
## <a name="building-an-xml-schema"></a><span data-ttu-id="e1de9-104">Vytváření schématu XML</span><span class="sxs-lookup"><span data-stu-id="e1de9-104">Building an XML Schema</span></span>  
 <span data-ttu-id="e1de9-105">Příklady kódu, které následují rozhraní API SOM slouží k vytvoření zákazníka XML schématu v paměti.</span><span class="sxs-lookup"><span data-stu-id="e1de9-105">In the code examples that follow, the SOM API is used to build a customer XML schema in-memory.</span></span>  
  
### <a name="creating-element-and-attributes"></a><span data-ttu-id="e1de9-106">Vytváření elementu a atributy</span><span class="sxs-lookup"><span data-stu-id="e1de9-106">Creating Element and Attributes</span></span>  
 <span data-ttu-id="e1de9-107">Příklady kódu sestavení zákazník schématu zdola nahoru, vytváření podřízené prvky, atributy a jejich odpovídající typy první a pak nejvyšší úrovně elementy.</span><span class="sxs-lookup"><span data-stu-id="e1de9-107">The code examples build the customer schema from the bottom up, creating the child elements, attributes, and their corresponding types first, and then the top-level elements.</span></span>  
  
 <span data-ttu-id="e1de9-108">V následujícím příkladu kódu `FirstName` a `LastName` prvky, a taky `CustomerId` atribut zákazníka schématu, které jsou vytvořené pomocí <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute> třídy SOM.</span><span class="sxs-lookup"><span data-stu-id="e1de9-108">In the following code example, the `FirstName` and `LastName` elements, as well as the `CustomerId` attribute of the customer schema are created using the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes of the SOM.</span></span> <span data-ttu-id="e1de9-109">Kromě <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> vlastnosti <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute> třídy, které odpovídají podle atributu "name" `<xs:element />` a `<xs:attribute />` elementy ve schématu XML, všechny atributy povolena schématem (`defaultValue`, `fixedValue`, `form`a tak dále) mít odpovídající vlastnosti <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="e1de9-109">Apart from the <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> properties of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes, which correspond to the "name" attribute of the `<xs:element />` and `<xs:attribute />` elements in an XML schema, all other attributes allowed by the schema (`defaultValue`, `fixedValue`, `form`, and so on) have corresponding properties in the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a><span data-ttu-id="e1de9-110">Vytváření typy schémat</span><span class="sxs-lookup"><span data-stu-id="e1de9-110">Creating Schema Types</span></span>  
 <span data-ttu-id="e1de9-111">Obsah elementů a atributů je definována jejich typy.</span><span class="sxs-lookup"><span data-stu-id="e1de9-111">The content of elements and attributes is defined by their types.</span></span> <span data-ttu-id="e1de9-112">K vytvoření elementů a atributů, jejichž typy jsou jeden z předdefinovaných schémat typů <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy se nastavují s odpovídající úplný název předdefinovaný typ pomocí <xref:System.Xml.XmlQualifiedName> – třída.</span><span class="sxs-lookup"><span data-stu-id="e1de9-112">To create elements and attributes whose types are one of the built-in schema types, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes are set with the corresponding qualified name of the built-in type using the <xref:System.Xml.XmlQualifiedName> class.</span></span> <span data-ttu-id="e1de9-113">Vytvoření typu uživatelem definované pro elementy a atributy, je vytvořený nový jednoduché nebo komplexní typ, pomocí <xref:System.Xml.Schema.XmlSchemaSimpleType> nebo <xref:System.Xml.Schema.XmlSchemaComplexType> třídy.</span><span class="sxs-lookup"><span data-stu-id="e1de9-113">To create a user-defined type for elements and attributes, a new simple or complex type is created using the <xref:System.Xml.Schema.XmlSchemaSimpleType> or <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1de9-114">Chcete-li vytvořit nepojmenované jednoduché nebo komplexní typy, které jsou anonymní podřízené položky elementu nebo atributu (pouze jednoduché typy použít pro atributy), nastavit <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy nepojmenované jednoduché nebo komplexní typ, místo <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="e1de9-114">To create unnamed simple or complex types that are anonymous children of an element or attribute (only simple types apply for attributes), set the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes to the unnamed simple or complex type, instead of the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 <span data-ttu-id="e1de9-115">Schémata XML povolit také oba anonymní a pojmenované jednoduché typy pocházet omezením z dalších jednoduchý typů (předdefinovaných nebo uživatelsky definovaných) nebo sestavený jako seznam nebo sjednocení dalších jednoduchý typů.</span><span class="sxs-lookup"><span data-stu-id="e1de9-115">XML schemas allow both anonymous and named simple types to be derived by restriction from other simple types (built-in or user-defined) or constructed as a list or union of other simple types.</span></span> <span data-ttu-id="e1de9-116"><xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> Třída se používá k vytvoření jednoduchého typu omezením integrované `xs:string` typu.</span><span class="sxs-lookup"><span data-stu-id="e1de9-116">The <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> class is used to create a simple type by restricting the built-in `xs:string` type.</span></span> <span data-ttu-id="e1de9-117">Můžete také <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> nebo <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> třídy pro vytvoření seznamu nebo sjednocení typů.</span><span class="sxs-lookup"><span data-stu-id="e1de9-117">You can also use the <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> or <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> classes to create list or union types.</span></span> <span data-ttu-id="e1de9-118"><xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> Vlastnost označuje, zda se jedná o jednoduchý typ omezení, seznamu nebo union.</span><span class="sxs-lookup"><span data-stu-id="e1de9-118">The <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> property denotes whether it is a simple type restriction, list, or union.</span></span>  
  
 <span data-ttu-id="e1de9-119">V následujícím příkladu kódu `FirstName` předdefinovaný typ je typ elementu `xs:string`, `LastName` pojmenované jednoduchý typ, který je omezení předdefinovaný typ je typ elementu `xs:string`, s `MaxLength` hodnota omezující vlastnosti 20, a `CustomerId` typ atributu je předdefinovaný typ `xs:positiveInteger`.</span><span class="sxs-lookup"><span data-stu-id="e1de9-119">In the following code example, the `FirstName` element's type is the built-in type `xs:string`, the `LastName` element's type is a named simple type that is a restriction of the built-in type `xs:string`, with a `MaxLength` facet value of 20, and the `CustomerId` attribute's type is the built-in type `xs:positiveInteger`.</span></span> <span data-ttu-id="e1de9-120">`Customer` Element je anonymní komplexní typ, jejichž částice je sekvenci z `FirstName` a `LastName` elementy a atributy, jejichž obsahuje `CustomerId` atribut.</span><span class="sxs-lookup"><span data-stu-id="e1de9-120">The `Customer` element is an anonymous complex type whose particle is the sequence of the `FirstName` and `LastName` elements and whose attributes contains the `CustomerId` attribute.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1de9-121">Můžete také <xref:System.Xml.Schema.XmlSchemaChoice> nebo <xref:System.Xml.Schema.XmlSchemaAll> třídy jako částice komplexního typu k replikaci `<xs:choice />` nebo `<xs:all />` sémantiku.</span><span class="sxs-lookup"><span data-stu-id="e1de9-121">You can also use the <xref:System.Xml.Schema.XmlSchemaChoice> or <xref:System.Xml.Schema.XmlSchemaAll> classes as the particle of the complex type to replicate `<xs:choice />` or `<xs:all />` semantics.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a><span data-ttu-id="e1de9-122">Vytváření a kompilování schémat.</span><span class="sxs-lookup"><span data-stu-id="e1de9-122">Creating and Compiling Schemas</span></span>  
 <span data-ttu-id="e1de9-123">V tomto bodu, podřízené elementy a atributy, jejich odpovídající typy a nejvyšší úrovně `Customer` element byla vytvořena pomocí rozhraní API SOM v paměti.</span><span class="sxs-lookup"><span data-stu-id="e1de9-123">At this point, the child elements and attributes, their corresponding types, and the top-level `Customer` element have been created in-memory using the SOM API.</span></span> <span data-ttu-id="e1de9-124">V následujícím příkladu kódu je vytvořený pomocí elementu schema <xref:System.Xml.Schema.XmlSchema> třídy, nejvyšší úrovně prvky a typy jsou přidány do pomocí <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> vlastností a dokončení schématu je kompilovat, pomocí <xref:System.Xml.Schema.XmlSchemaSet> – třída a zapisují do Konzola.</span><span class="sxs-lookup"><span data-stu-id="e1de9-124">In the following code example, the schema element is created using the <xref:System.Xml.Schema.XmlSchema> class, the top-level elements and types are added to it using the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> property and the complete schema is compiled using the <xref:System.Xml.Schema.XmlSchemaSet> class and written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <span data-ttu-id="e1de9-125"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> Metoda ověří schéma zákazníka proti pravidla pro schéma XML a zpřístupní po schema kompilace vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e1de9-125">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> method validates the customer schema against the rules for an XML schema and makes post-schema-compilation properties available.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1de9-126">Všechny vlastnosti po schema kompilace v rozhraní API SOM se liší od po-schema-ověření-informační sadu.</span><span class="sxs-lookup"><span data-stu-id="e1de9-126">All post-schema-compilation properties in the SOM API differ from the Post-Schema-Validation-Infoset.</span></span>  
  
 <span data-ttu-id="e1de9-127"><xref:System.Xml.Schema.ValidationEventHandler> Přidán do <xref:System.Xml.Schema.XmlSchemaSet> je delegáta, který volá metodu zpětného volání `ValidationCallback` pro zpracování chyby a varování ověřování schématu.</span><span class="sxs-lookup"><span data-stu-id="e1de9-127">The <xref:System.Xml.Schema.ValidationEventHandler> added to the <xref:System.Xml.Schema.XmlSchemaSet> is a delegate that calls the callback method `ValidationCallback` to handle schema validation warnings and errors.</span></span>  
  
 <span data-ttu-id="e1de9-128">Níže je úplný příklad kódu a schéma zákazníka zapsána do konzoly.</span><span class="sxs-lookup"><span data-stu-id="e1de9-128">The following is the complete code example, and the customer schema written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#1)]
 [!code-csharp[XmlSchemaCreateExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#1)]
 [!code-vb[XmlSchemaCreateExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="Customer">  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="FirstName" type="xs:string" />  
            <xs:element name="LastName" type="tns:LastNameType" />  
         </xs:sequence>  
         <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />  
      </xs:complexType>  
   </xs:element>  
   <xs:simpleType name="LastNameType">  
      <xs:restriction base="xs:string">  
         <xs:maxLength value="20" />  
      </xs:restriction>  
   </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1de9-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1de9-129">See Also</span></span>  
 [<span data-ttu-id="e1de9-130">Přehled Modelu objektu schématu XML</span><span class="sxs-lookup"><span data-stu-id="e1de9-130">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [<span data-ttu-id="e1de9-131">Čtení ze schémat XML a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="e1de9-131">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [<span data-ttu-id="e1de9-132">Procházení schémat XML</span><span class="sxs-lookup"><span data-stu-id="e1de9-132">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [<span data-ttu-id="e1de9-133">Úpravy schémat XML</span><span class="sxs-lookup"><span data-stu-id="e1de9-133">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [<span data-ttu-id="e1de9-134">Zahrnutí nebo import schémat XML</span><span class="sxs-lookup"><span data-stu-id="e1de9-134">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [<span data-ttu-id="e1de9-135">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="e1de9-135">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="e1de9-136">Informační sada po kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="e1de9-136">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
