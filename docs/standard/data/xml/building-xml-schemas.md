---
title: Sestavování schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10b2471d13d410826cec3404725117649442297b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47402653"
---
# <a name="building-xml-schemas"></a><span data-ttu-id="471a1-102">Sestavování schémat XML</span><span class="sxs-lookup"><span data-stu-id="471a1-102">Building XML Schemas</span></span>
<span data-ttu-id="471a1-103">Třídy v <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů mapovat na struktury definované v doporučení schématu XML World Wide Web Consortium (W3C) a slouží k sestavení XML schémata v paměti.</span><span class="sxs-lookup"><span data-stu-id="471a1-103">The classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation and can be used to build XML schemas in-memory.</span></span>  
  
## <a name="building-an-xml-schema"></a><span data-ttu-id="471a1-104">Vytváření schématu XML</span><span class="sxs-lookup"><span data-stu-id="471a1-104">Building an XML Schema</span></span>  
 <span data-ttu-id="471a1-105">V příkladech kódu, které následují rozhraní API SOM slouží k vytváření zákazník XML schématu v paměti.</span><span class="sxs-lookup"><span data-stu-id="471a1-105">In the code examples that follow, the SOM API is used to build a customer XML schema in-memory.</span></span>  
  
### <a name="creating-element-and-attributes"></a><span data-ttu-id="471a1-106">Vytvoření elementu a atributy</span><span class="sxs-lookup"><span data-stu-id="471a1-106">Creating Element and Attributes</span></span>  
 <span data-ttu-id="471a1-107">Příklady kódu sestavte zákazník schématu zdola nahoru, podřízené prvky, atributy a jejich odpovídající typy nejprve vytvoříte a potom prvky nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="471a1-107">The code examples build the customer schema from the bottom up, creating the child elements, attributes, and their corresponding types first, and then the top-level elements.</span></span>  
  
 <span data-ttu-id="471a1-108">V následujícím příkladu kódu `FirstName` a `LastName` prvky, stejně jako `CustomerId` atribut schématu zákazníka se vytvoří s použitím <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute> třídy SOM.</span><span class="sxs-lookup"><span data-stu-id="471a1-108">In the following code example, the `FirstName` and `LastName` elements, as well as the `CustomerId` attribute of the customer schema are created using the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes of the SOM.</span></span> <span data-ttu-id="471a1-109">Kromě <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> vlastnosti <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute> třídy, které odpovídají atributu "name" `<xs:element />` a `<xs:attribute />` elementy ve schématu XML, všechny ostatní atributy tímhle schématem povolený (`defaultValue`, `fixedValue`, `form`, a tak dále) odpovídající vlastnosti <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="471a1-109">Apart from the <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> properties of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes, which correspond to the "name" attribute of the `<xs:element />` and `<xs:attribute />` elements in an XML schema, all other attributes allowed by the schema (`defaultValue`, `fixedValue`, `form`, and so on) have corresponding properties in the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a><span data-ttu-id="471a1-110">Vytváření typů schématu</span><span class="sxs-lookup"><span data-stu-id="471a1-110">Creating Schema Types</span></span>  
 <span data-ttu-id="471a1-111">Typy hodnot je definována obsah elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="471a1-111">The content of elements and attributes is defined by their types.</span></span> <span data-ttu-id="471a1-112">K vytváření elementů a atributů, jejichž typy jsou jedním z typů předdefinovaných schémat <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy se nastavují s odpovídající kvalifikovaný název předdefinovaný typ použití <xref:System.Xml.XmlQualifiedName> třídy.</span><span class="sxs-lookup"><span data-stu-id="471a1-112">To create elements and attributes whose types are one of the built-in schema types, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes are set with the corresponding qualified name of the built-in type using the <xref:System.Xml.XmlQualifiedName> class.</span></span> <span data-ttu-id="471a1-113">Vytvoření uživatelem definovaného typu pro elementy a atributy, je vytvořený pomocí nového typu jednoduché nebo složité <xref:System.Xml.Schema.XmlSchemaSimpleType> nebo <xref:System.Xml.Schema.XmlSchemaComplexType> třídy.</span><span class="sxs-lookup"><span data-stu-id="471a1-113">To create a user-defined type for elements and attributes, a new simple or complex type is created using the <xref:System.Xml.Schema.XmlSchemaSimpleType> or <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="471a1-114">K vytvoření nepojmenované jednoduchých nebo složitých typů, které jsou anonymní podřízené objekty daného elementu nebo atributu (pouze jednoduché typy lze použít pro atributy), nastavte <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy, které nepojmenované jednoduché nebo komplexní typ, místo <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="471a1-114">To create unnamed simple or complex types that are anonymous children of an element or attribute (only simple types apply for attributes), set the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes to the unnamed simple or complex type, instead of the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 <span data-ttu-id="471a1-115">Schémata XML povolit anonymní a pojmenované jednoduché typy mají být odvozené omezením z jiných jednoduché typy (integrované nebo uživatelem definovaný) nebo vytvořen jako seznam nebo sjednocení jiných typů jednoduché.</span><span class="sxs-lookup"><span data-stu-id="471a1-115">XML schemas allow both anonymous and named simple types to be derived by restriction from other simple types (built-in or user-defined) or constructed as a list or union of other simple types.</span></span> <span data-ttu-id="471a1-116"><xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> Třída se používá k vytvoření jednoduchého typu tak, že omezíte předdefinované `xs:string` typu.</span><span class="sxs-lookup"><span data-stu-id="471a1-116">The <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> class is used to create a simple type by restricting the built-in `xs:string` type.</span></span> <span data-ttu-id="471a1-117">Můžete také použít <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> nebo <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> tříd pro vytvoření seznamu nebo sjednocení typů.</span><span class="sxs-lookup"><span data-stu-id="471a1-117">You can also use the <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> or <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> classes to create list or union types.</span></span> <span data-ttu-id="471a1-118"><xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> Vlastnost označuje, zda je omezení jednoduchých typů, seznamu nebo sjednocení.</span><span class="sxs-lookup"><span data-stu-id="471a1-118">The <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> property denotes whether it is a simple type restriction, list, or union.</span></span>  
  
 <span data-ttu-id="471a1-119">V následujícím příkladu kódu `FirstName` předdefinovaný typ je typ prvku `xs:string`, `LastName` pojmenované jednoduchý typ, který představuje omezení typu předdefinovaný typ je typ prvku `xs:string`, s `MaxLength` hodnota omezující vlastnosti 20, a `CustomerId` typ atributu je předdefinovaný typ `xs:positiveInteger`.</span><span class="sxs-lookup"><span data-stu-id="471a1-119">In the following code example, the `FirstName` element's type is the built-in type `xs:string`, the `LastName` element's type is a named simple type that is a restriction of the built-in type `xs:string`, with a `MaxLength` facet value of 20, and the `CustomerId` attribute's type is the built-in type `xs:positiveInteger`.</span></span> <span data-ttu-id="471a1-120">`Customer` Element je anonymní komplexní typ, jehož částice je sekvenci z `FirstName` a `LastName` elementy a jejichž atributy obsahuje `CustomerId` atribut.</span><span class="sxs-lookup"><span data-stu-id="471a1-120">The `Customer` element is an anonymous complex type whose particle is the sequence of the `FirstName` and `LastName` elements and whose attributes contains the `CustomerId` attribute.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="471a1-121">Můžete také použít <xref:System.Xml.Schema.XmlSchemaChoice> nebo <xref:System.Xml.Schema.XmlSchemaAll> třídy jako částice složitý typ k replikaci `<xs:choice />` nebo `<xs:all />` sémantiku.</span><span class="sxs-lookup"><span data-stu-id="471a1-121">You can also use the <xref:System.Xml.Schema.XmlSchemaChoice> or <xref:System.Xml.Schema.XmlSchemaAll> classes as the particle of the complex type to replicate `<xs:choice />` or `<xs:all />` semantics.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a><span data-ttu-id="471a1-122">Vytváření a kompilování schémat</span><span class="sxs-lookup"><span data-stu-id="471a1-122">Creating and Compiling Schemas</span></span>  
 <span data-ttu-id="471a1-123">Na tento bod, podřízené prvky a atributy, jejich odpovídající typy a na nejvyšší úrovni `Customer` element byly vytvořeny pomocí rozhraní API SOM v paměti.</span><span class="sxs-lookup"><span data-stu-id="471a1-123">At this point, the child elements and attributes, their corresponding types, and the top-level `Customer` element have been created in-memory using the SOM API.</span></span> <span data-ttu-id="471a1-124">V následujícím příkladu kódu je vytvořený element schématu pomocí <xref:System.Xml.Schema.XmlSchema> třídy, prvky nejvyšší úrovně a typy jsou přidány pomocí <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> vlastností a dokončení schématu je zkompilován pomocí <xref:System.Xml.Schema.XmlSchemaSet> třídy a do něj zapisovat konzoly.</span><span class="sxs-lookup"><span data-stu-id="471a1-124">In the following code example, the schema element is created using the <xref:System.Xml.Schema.XmlSchema> class, the top-level elements and types are added to it using the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> property and the complete schema is compiled using the <xref:System.Xml.Schema.XmlSchemaSet> class and written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <span data-ttu-id="471a1-125"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> Metoda ověří zákazníka schématu s pomocí pravidel pro schématu XML a zpřístupní vlastnosti po schema kompilace.</span><span class="sxs-lookup"><span data-stu-id="471a1-125">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> method validates the customer schema against the rules for an XML schema and makes post-schema-compilation properties available.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="471a1-126">Všechny vlastnosti po schema kompilace v rozhraní API SOM se liší od po-schema-ověření – informační sadu.</span><span class="sxs-lookup"><span data-stu-id="471a1-126">All post-schema-compilation properties in the SOM API differ from the Post-Schema-Validation-Infoset.</span></span>  
  
 <span data-ttu-id="471a1-127"><xref:System.Xml.Schema.ValidationEventHandler> Přidán do <xref:System.Xml.Schema.XmlSchemaSet> je delegát, který volá metodu zpětného volání `ValidationCallback` schématu ověření upozornění a chyby.</span><span class="sxs-lookup"><span data-stu-id="471a1-127">The <xref:System.Xml.Schema.ValidationEventHandler> added to the <xref:System.Xml.Schema.XmlSchemaSet> is a delegate that calls the callback method `ValidationCallback` to handle schema validation warnings and errors.</span></span>  
  
 <span data-ttu-id="471a1-128">Tady je příklad úplného kódu a schéma zákazníka zapsána do konzoly.</span><span class="sxs-lookup"><span data-stu-id="471a1-128">The following is the complete code example, and the customer schema written to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="471a1-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="471a1-129">See also</span></span>

- [<span data-ttu-id="471a1-130">Přehled Modelu objektu schématu XML</span><span class="sxs-lookup"><span data-stu-id="471a1-130">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
- [<span data-ttu-id="471a1-131">Čtení ze schémat XML a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="471a1-131">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
- [<span data-ttu-id="471a1-132">Procházení schémat XML</span><span class="sxs-lookup"><span data-stu-id="471a1-132">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
- [<span data-ttu-id="471a1-133">Úpravy schémat XML</span><span class="sxs-lookup"><span data-stu-id="471a1-133">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
- [<span data-ttu-id="471a1-134">Zahrnutí nebo import schémat XML</span><span class="sxs-lookup"><span data-stu-id="471a1-134">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
- [<span data-ttu-id="471a1-135">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="471a1-135">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
- [<span data-ttu-id="471a1-136">Informační sada po kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="471a1-136">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
