---
title: Sestavování schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
ms.openlocfilehash: adc1a10bb9acb14ee88589c13e28c49773e42100
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291588"
---
# <a name="building-xml-schemas"></a><span data-ttu-id="4ce53-102">Sestavování schémat XML</span><span class="sxs-lookup"><span data-stu-id="4ce53-102">Building XML Schemas</span></span>
<span data-ttu-id="4ce53-103">Třídy v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů se mapují na struktury definované v doporučení schématu xml konsorcium World Wide Web (W3C) a lze je použít k sestavení schémat XML v paměti.</span><span class="sxs-lookup"><span data-stu-id="4ce53-103">The classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation and can be used to build XML schemas in-memory.</span></span>  
  
## <a name="building-an-xml-schema"></a><span data-ttu-id="4ce53-104">Sestavení schématu XML</span><span class="sxs-lookup"><span data-stu-id="4ce53-104">Building an XML Schema</span></span>  
 <span data-ttu-id="4ce53-105">V příkladech kódu, které následují, se používá rozhraní API SOM k sestavení schématu XML pro zákazníky v paměti.</span><span class="sxs-lookup"><span data-stu-id="4ce53-105">In the code examples that follow, the SOM API is used to build a customer XML schema in-memory.</span></span>  
  
### <a name="creating-element-and-attributes"></a><span data-ttu-id="4ce53-106">Vytváření elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="4ce53-106">Creating Element and Attributes</span></span>  
 <span data-ttu-id="4ce53-107">Příklady kódu sestavují schéma zákazníka z dolní části nahoru, vytváření podřízených prvků, atributů a jejich odpovídajících typů a pak prvků na nejvyšší úrovni.</span><span class="sxs-lookup"><span data-stu-id="4ce53-107">The code examples build the customer schema from the bottom up, creating the child elements, attributes, and their corresponding types first, and then the top-level elements.</span></span>  
  
 <span data-ttu-id="4ce53-108">V následujícím příkladu kódu `FirstName` jsou prvky a a `LastName` také `CustomerId` atribut schématu zákazníka vytvořeny pomocí <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> tříd a třídy SOM.</span><span class="sxs-lookup"><span data-stu-id="4ce53-108">In the following code example, the `FirstName` and `LastName` elements, as well as the `CustomerId` attribute of the customer schema are created using the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes of the SOM.</span></span> <span data-ttu-id="4ce53-109">Kromě <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> vlastností <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> tříd a, které odpovídají atributu "Name" `<xs:element />` `<xs:attribute />` elementů a ve schématu XML, všechny ostatní atributy povolené schématem (,, atd `defaultValue` `fixedValue` `form` .) mají odpovídající vlastnosti v <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> třídách a.</span><span class="sxs-lookup"><span data-stu-id="4ce53-109">Apart from the <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> properties of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes, which correspond to the "name" attribute of the `<xs:element />` and `<xs:attribute />` elements in an XML schema, all other attributes allowed by the schema (`defaultValue`, `fixedValue`, `form`, and so on) have corresponding properties in the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a><span data-ttu-id="4ce53-110">Vytváření typů schémat</span><span class="sxs-lookup"><span data-stu-id="4ce53-110">Creating Schema Types</span></span>  
 <span data-ttu-id="4ce53-111">Obsah elementů a atributů je definován jejich typy.</span><span class="sxs-lookup"><span data-stu-id="4ce53-111">The content of elements and attributes is defined by their types.</span></span> <span data-ttu-id="4ce53-112">Chcete-li vytvořit prvky a atributy, jejichž typy jsou jedním z vestavěných typů schémat, <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy jsou nastaveny s odpovídajícím kvalifikovaným názvem předdefinovaného typu pomocí <xref:System.Xml.XmlQualifiedName> třídy.</span><span class="sxs-lookup"><span data-stu-id="4ce53-112">To create elements and attributes whose types are one of the built-in schema types, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes are set with the corresponding qualified name of the built-in type using the <xref:System.Xml.XmlQualifiedName> class.</span></span> <span data-ttu-id="4ce53-113">Chcete-li vytvořit uživatelsky definovaný typ pro prvky a atributy, je vytvořen nový jednoduchý nebo komplexní typ pomocí <xref:System.Xml.Schema.XmlSchemaSimpleType> třídy or <xref:System.Xml.Schema.XmlSchemaComplexType> .</span><span class="sxs-lookup"><span data-stu-id="4ce53-113">To create a user-defined type for elements and attributes, a new simple or complex type is created using the <xref:System.Xml.Schema.XmlSchemaSimpleType> or <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ce53-114">Chcete-li vytvořit nepojmenované jednoduché nebo komplexní typy, které jsou anonymními podřízenými prvky elementu nebo atributu (pro atributy platí pouze jednoduché typy), nastavte <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> třídy nebo na nepojmenované jednoduché nebo komplexní typ namísto <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> vlastnosti <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> třídy nebo.</span><span class="sxs-lookup"><span data-stu-id="4ce53-114">To create unnamed simple or complex types that are anonymous children of an element or attribute (only simple types apply for attributes), set the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes to the unnamed simple or complex type, instead of the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 <span data-ttu-id="4ce53-115">Schémata XML umožňují odvození anonymních i pojmenovaných jednoduchých typů omezením z jiných jednoduchých typů (předdefinované nebo definované uživatelem) nebo konstruované jako seznam nebo sjednocení jiných jednoduchých typů.</span><span class="sxs-lookup"><span data-stu-id="4ce53-115">XML schemas allow both anonymous and named simple types to be derived by restriction from other simple types (built-in or user-defined) or constructed as a list or union of other simple types.</span></span> <span data-ttu-id="4ce53-116"><xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction>Třída se používá k vytvoření jednoduchého typu omezením vestavěného `xs:string` typu.</span><span class="sxs-lookup"><span data-stu-id="4ce53-116">The <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> class is used to create a simple type by restricting the built-in `xs:string` type.</span></span> <span data-ttu-id="4ce53-117">Můžete také použít <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> třídy nebo k vytvoření typu seznamu nebo sjednocení.</span><span class="sxs-lookup"><span data-stu-id="4ce53-117">You can also use the <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> or <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> classes to create list or union types.</span></span> <span data-ttu-id="4ce53-118"><xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType>Vlastnost označuje, zda se jedná o jednoduché omezení typu, seznam nebo sjednocení.</span><span class="sxs-lookup"><span data-stu-id="4ce53-118">The <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> property denotes whether it is a simple type restriction, list, or union.</span></span>  
  
 <span data-ttu-id="4ce53-119">V následujícím příkladu kódu `FirstName` je typ prvku vestavěný typ `xs:string` , `LastName` typ prvku je pojmenovaný jednoduchý typ, který je omezením vestavěného typu `xs:string` s `MaxLength` hodnotou omezující vlastnosti 20 a `CustomerId` typem atributu je předdefinovaný typ typu `xs:positiveInteger` .</span><span class="sxs-lookup"><span data-stu-id="4ce53-119">In the following code example, the `FirstName` element's type is the built-in type `xs:string`, the `LastName` element's type is a named simple type that is a restriction of the built-in type `xs:string`, with a `MaxLength` facet value of 20, and the `CustomerId` attribute's type is the built-in type `xs:positiveInteger`.</span></span> <span data-ttu-id="4ce53-120">`Customer`Element je anonymní komplexní typ, jehož částice je sekvence `FirstName` `LastName` prvků a a jejichž atributy obsahují `CustomerId` atribut.</span><span class="sxs-lookup"><span data-stu-id="4ce53-120">The `Customer` element is an anonymous complex type whose particle is the sequence of the `FirstName` and `LastName` elements and whose attributes contains the `CustomerId` attribute.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ce53-121">Můžete také použít <xref:System.Xml.Schema.XmlSchemaChoice> <xref:System.Xml.Schema.XmlSchemaAll> třídy nebo jako části složeného typu pro replikaci `<xs:choice />` nebo `<xs:all />` sémantiku.</span><span class="sxs-lookup"><span data-stu-id="4ce53-121">You can also use the <xref:System.Xml.Schema.XmlSchemaChoice> or <xref:System.Xml.Schema.XmlSchemaAll> classes as the particle of the complex type to replicate `<xs:choice />` or `<xs:all />` semantics.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a><span data-ttu-id="4ce53-122">Vytváření a kompilování schémat</span><span class="sxs-lookup"><span data-stu-id="4ce53-122">Creating and Compiling Schemas</span></span>  
 <span data-ttu-id="4ce53-123">V tomto okamžiku se podřízené prvky a atributy, jejich odpovídající typy a element nejvyšší úrovně `Customer` vytvořily v paměti pomocí rozhraní API modelu SOM.</span><span class="sxs-lookup"><span data-stu-id="4ce53-123">At this point, the child elements and attributes, their corresponding types, and the top-level `Customer` element have been created in-memory using the SOM API.</span></span> <span data-ttu-id="4ce53-124">V následujícím příkladu kódu je prvek schématu vytvořen pomocí <xref:System.Xml.Schema.XmlSchema> třídy, prvky nejvyšší úrovně a typy jsou do něj přidány pomocí <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> vlastnosti a kompletní schéma je kompilováno pomocí <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapsána do konzoly.</span><span class="sxs-lookup"><span data-stu-id="4ce53-124">In the following code example, the schema element is created using the <xref:System.Xml.Schema.XmlSchema> class, the top-level elements and types are added to it using the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> property and the complete schema is compiled using the <xref:System.Xml.Schema.XmlSchemaSet> class and written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <span data-ttu-id="4ce53-125"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType>Metoda ověřuje schéma zákazníka proti pravidlům pro schéma XML a zpřístupňuje vlastnosti kompilace po schématu.</span><span class="sxs-lookup"><span data-stu-id="4ce53-125">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> method validates the customer schema against the rules for an XML schema and makes post-schema-compilation properties available.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ce53-126">Všechny vlastnosti kompilace post-Schema-compilation v rozhraní API SOM se liší od post-Schema-Validation-informační sady.</span><span class="sxs-lookup"><span data-stu-id="4ce53-126">All post-schema-compilation properties in the SOM API differ from the Post-Schema-Validation-Infoset.</span></span>  
  
 <span data-ttu-id="4ce53-127"><xref:System.Xml.Schema.ValidationEventHandler>Přidaný do <xref:System.Xml.Schema.XmlSchemaSet> je delegát, který volá metodu zpětného volání `ValidationCallback` pro zpracování upozornění a chyb ověřování schématu.</span><span class="sxs-lookup"><span data-stu-id="4ce53-127">The <xref:System.Xml.Schema.ValidationEventHandler> added to the <xref:System.Xml.Schema.XmlSchemaSet> is a delegate that calls the callback method `ValidationCallback` to handle schema validation warnings and errors.</span></span>  
  
 <span data-ttu-id="4ce53-128">Následuje příklad kompletního příkladu kódu a schéma zákazníka zapsané do konzoly.</span><span class="sxs-lookup"><span data-stu-id="4ce53-128">The following is the complete code example, and the customer schema written to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ce53-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ce53-129">See also</span></span>

- [<span data-ttu-id="4ce53-130">Přehled Modelu objektu schématu XML</span><span class="sxs-lookup"><span data-stu-id="4ce53-130">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="4ce53-131">Čtení ze schémat XML a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="4ce53-131">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="4ce53-132">Procházení schémat XML</span><span class="sxs-lookup"><span data-stu-id="4ce53-132">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="4ce53-133">Úpravy schémat XML</span><span class="sxs-lookup"><span data-stu-id="4ce53-133">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="4ce53-134">Zahrnutí nebo import schémat XML</span><span class="sxs-lookup"><span data-stu-id="4ce53-134">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="4ce53-135">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="4ce53-135">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="4ce53-136">Informační sada po kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="4ce53-136">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
