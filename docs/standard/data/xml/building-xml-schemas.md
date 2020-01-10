---
title: Sestavování schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
ms.openlocfilehash: c921331b00fe137d4ad52d62951e8c161768dfae
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711139"
---
# <a name="building-xml-schemas"></a><span data-ttu-id="84bfc-102">Sestavování schémat XML</span><span class="sxs-lookup"><span data-stu-id="84bfc-102">Building XML Schemas</span></span>
<span data-ttu-id="84bfc-103">Třídy v oboru názvů <xref:System.Xml.Schema?displayProperty=nameWithType> namapují na struktury definované v doporučeních schématu XML konsorcium World Wide Web (W3C) a lze je použít k sestavení schémat XML v paměti.</span><span class="sxs-lookup"><span data-stu-id="84bfc-103">The classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation and can be used to build XML schemas in-memory.</span></span>  
  
## <a name="building-an-xml-schema"></a><span data-ttu-id="84bfc-104">Sestavení schématu XML</span><span class="sxs-lookup"><span data-stu-id="84bfc-104">Building an XML Schema</span></span>  
 <span data-ttu-id="84bfc-105">V příkladech kódu, které následují, se používá rozhraní API SOM k sestavení schématu XML pro zákazníky v paměti.</span><span class="sxs-lookup"><span data-stu-id="84bfc-105">In the code examples that follow, the SOM API is used to build a customer XML schema in-memory.</span></span>  
  
### <a name="creating-element-and-attributes"></a><span data-ttu-id="84bfc-106">Vytváření elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="84bfc-106">Creating Element and Attributes</span></span>  
 <span data-ttu-id="84bfc-107">Příklady kódu sestavují schéma zákazníka z dolní části nahoru, vytváření podřízených prvků, atributů a jejich odpovídajících typů a pak prvků na nejvyšší úrovni.</span><span class="sxs-lookup"><span data-stu-id="84bfc-107">The code examples build the customer schema from the bottom up, creating the child elements, attributes, and their corresponding types first, and then the top-level elements.</span></span>  
  
 <span data-ttu-id="84bfc-108">V následujícím příkladu kódu `FirstName` a `LastName` prvky a také atribut `CustomerId` schématu zákazníka jsou vytvořeny pomocí <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute> tříd modelu SOM.</span><span class="sxs-lookup"><span data-stu-id="84bfc-108">In the following code example, the `FirstName` and `LastName` elements, as well as the `CustomerId` attribute of the customer schema are created using the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes of the SOM.</span></span> <span data-ttu-id="84bfc-109">Kromě <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> vlastností tříd <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute>, které odpovídají atributu "Name" `<xs:element />` a `<xs:attribute />` prvků ve schématu XML, všechny ostatní atributy povolené schématem (`defaultValue`, `fixedValue`, `form`atd.) mají odpovídající vlastnosti v <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute>ch třídách.</span><span class="sxs-lookup"><span data-stu-id="84bfc-109">Apart from the <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> properties of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes, which correspond to the "name" attribute of the `<xs:element />` and `<xs:attribute />` elements in an XML schema, all other attributes allowed by the schema (`defaultValue`, `fixedValue`, `form`, and so on) have corresponding properties in the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a><span data-ttu-id="84bfc-110">Vytváření typů schémat</span><span class="sxs-lookup"><span data-stu-id="84bfc-110">Creating Schema Types</span></span>  
 <span data-ttu-id="84bfc-111">Obsah elementů a atributů je definován jejich typy.</span><span class="sxs-lookup"><span data-stu-id="84bfc-111">The content of elements and attributes is defined by their types.</span></span> <span data-ttu-id="84bfc-112">Chcete-li vytvořit prvky a atributy, jejichž typy jsou jedním z vestavěných typů schémat, vlastnost <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> třídy <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> jsou nastaveny s odpovídajícím kvalifikovaným názvem předdefinovaného typu pomocí třídy <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="84bfc-112">To create elements and attributes whose types are one of the built-in schema types, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes are set with the corresponding qualified name of the built-in type using the <xref:System.Xml.XmlQualifiedName> class.</span></span> <span data-ttu-id="84bfc-113">Chcete-li vytvořit uživatelsky definovaný typ pro prvky a atributy, je vytvořen nový jednoduchý nebo komplexní typ pomocí třídy <xref:System.Xml.Schema.XmlSchemaSimpleType> nebo <xref:System.Xml.Schema.XmlSchemaComplexType>.</span><span class="sxs-lookup"><span data-stu-id="84bfc-113">To create a user-defined type for elements and attributes, a new simple or complex type is created using the <xref:System.Xml.Schema.XmlSchemaSimpleType> or <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84bfc-114">Chcete-li vytvořit nepojmenované jednoduché nebo komplexní typy, které jsou anonymními podřízenými prvky elementu nebo atributu (pro atributy platí pouze jednoduché typy), nastavte vlastnost <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy na nepojmenované jednoduché nebo komplexní typ místo vlastnosti <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> třídy <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute>.</span><span class="sxs-lookup"><span data-stu-id="84bfc-114">To create unnamed simple or complex types that are anonymous children of an element or attribute (only simple types apply for attributes), set the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes to the unnamed simple or complex type, instead of the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 <span data-ttu-id="84bfc-115">Schémata XML umožňují odvození anonymních i pojmenovaných jednoduchých typů omezením z jiných jednoduchých typů (předdefinované nebo definované uživatelem) nebo konstruované jako seznam nebo sjednocení jiných jednoduchých typů.</span><span class="sxs-lookup"><span data-stu-id="84bfc-115">XML schemas allow both anonymous and named simple types to be derived by restriction from other simple types (built-in or user-defined) or constructed as a list or union of other simple types.</span></span> <span data-ttu-id="84bfc-116">Třída <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> slouží k vytvoření jednoduchého typu omezením vestavěné `xs:string` typu.</span><span class="sxs-lookup"><span data-stu-id="84bfc-116">The <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> class is used to create a simple type by restricting the built-in `xs:string` type.</span></span> <span data-ttu-id="84bfc-117">Můžete také použít třídy <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> nebo <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> k vytvoření typu seznamu nebo sjednocení.</span><span class="sxs-lookup"><span data-stu-id="84bfc-117">You can also use the <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> or <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> classes to create list or union types.</span></span> <span data-ttu-id="84bfc-118">Vlastnost <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> označuje, zda se jedná o jednoduché omezení typu, seznam nebo sjednocení.</span><span class="sxs-lookup"><span data-stu-id="84bfc-118">The <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> property denotes whether it is a simple type restriction, list, or union.</span></span>  
  
 <span data-ttu-id="84bfc-119">V následujícím příkladu kódu je typ prvku `FirstName` předdefinovaný typ `xs:string`, typ `LastName` elementu je pojmenovaný jednoduchý typ, který je omezením předdefinovaného `xs:string`typu s hodnotou `MaxLength` omezující vlastnost 20 a typem atributu `CustomerId` je vestavěný typ `xs:positiveInteger`.</span><span class="sxs-lookup"><span data-stu-id="84bfc-119">In the following code example, the `FirstName` element's type is the built-in type `xs:string`, the `LastName` element's type is a named simple type that is a restriction of the built-in type `xs:string`, with a `MaxLength` facet value of 20, and the `CustomerId` attribute's type is the built-in type `xs:positiveInteger`.</span></span> <span data-ttu-id="84bfc-120">Element `Customer` je anonymní složitý typ, jehož částice je sekvence `FirstName` a `LastName` prvků a jejichž atributy obsahují atribut `CustomerId`.</span><span class="sxs-lookup"><span data-stu-id="84bfc-120">The `Customer` element is an anonymous complex type whose particle is the sequence of the `FirstName` and `LastName` elements and whose attributes contains the `CustomerId` attribute.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84bfc-121">Můžete také použít <xref:System.Xml.Schema.XmlSchemaChoice> nebo <xref:System.Xml.Schema.XmlSchemaAll> třídy jako části složeného typu pro replikaci `<xs:choice />` nebo `<xs:all />` sémantiky.</span><span class="sxs-lookup"><span data-stu-id="84bfc-121">You can also use the <xref:System.Xml.Schema.XmlSchemaChoice> or <xref:System.Xml.Schema.XmlSchemaAll> classes as the particle of the complex type to replicate `<xs:choice />` or `<xs:all />` semantics.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a><span data-ttu-id="84bfc-122">Vytváření a kompilování schémat</span><span class="sxs-lookup"><span data-stu-id="84bfc-122">Creating and Compiling Schemas</span></span>  
 <span data-ttu-id="84bfc-123">V tomto okamžiku byly podřízené prvky a atributy, jejich odpovídající typy a `Customer` element nejvyšší úrovně vytvořeny v paměti pomocí rozhraní API modelu SOM.</span><span class="sxs-lookup"><span data-stu-id="84bfc-123">At this point, the child elements and attributes, their corresponding types, and the top-level `Customer` element have been created in-memory using the SOM API.</span></span> <span data-ttu-id="84bfc-124">V následujícím příkladu kódu je prvek schématu vytvořen pomocí třídy <xref:System.Xml.Schema.XmlSchema>, prvky nejvyšší úrovně a typy jsou do něj přidány pomocí vlastnosti <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> a kompletní schéma je zkompilováno pomocí třídy <xref:System.Xml.Schema.XmlSchemaSet> a zapsána do konzoly.</span><span class="sxs-lookup"><span data-stu-id="84bfc-124">In the following code example, the schema element is created using the <xref:System.Xml.Schema.XmlSchema> class, the top-level elements and types are added to it using the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> property and the complete schema is compiled using the <xref:System.Xml.Schema.XmlSchemaSet> class and written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <span data-ttu-id="84bfc-125">Metoda <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> ověřuje schéma zákazníka proti pravidlům schématu XML a zpřístupňuje vlastnosti kompilace po schématu.</span><span class="sxs-lookup"><span data-stu-id="84bfc-125">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> method validates the customer schema against the rules for an XML schema and makes post-schema-compilation properties available.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84bfc-126">Všechny vlastnosti kompilace post-Schema-compilation v rozhraní API SOM se liší od post-Schema-Validation-informační sady.</span><span class="sxs-lookup"><span data-stu-id="84bfc-126">All post-schema-compilation properties in the SOM API differ from the Post-Schema-Validation-Infoset.</span></span>  
  
 <span data-ttu-id="84bfc-127"><xref:System.Xml.Schema.ValidationEventHandler> přidaný do <xref:System.Xml.Schema.XmlSchemaSet> je delegát, který volá metodu zpětného volání `ValidationCallback` pro zpracování upozornění a chyb ověřování schématu.</span><span class="sxs-lookup"><span data-stu-id="84bfc-127">The <xref:System.Xml.Schema.ValidationEventHandler> added to the <xref:System.Xml.Schema.XmlSchemaSet> is a delegate that calls the callback method `ValidationCallback` to handle schema validation warnings and errors.</span></span>  
  
 <span data-ttu-id="84bfc-128">Následuje příklad kompletního příkladu kódu a schéma zákazníka zapsané do konzoly.</span><span class="sxs-lookup"><span data-stu-id="84bfc-128">The following is the complete code example, and the customer schema written to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84bfc-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84bfc-129">See also</span></span>

- [<span data-ttu-id="84bfc-130">Přehled Modelu objektu schématu XML</span><span class="sxs-lookup"><span data-stu-id="84bfc-130">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="84bfc-131">Čtení ze schémat XML a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="84bfc-131">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="84bfc-132">Procházení schémat XML</span><span class="sxs-lookup"><span data-stu-id="84bfc-132">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="84bfc-133">Úpravy schémat XML</span><span class="sxs-lookup"><span data-stu-id="84bfc-133">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [<span data-ttu-id="84bfc-134">Zahrnutí nebo import schémat XML</span><span class="sxs-lookup"><span data-stu-id="84bfc-134">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [<span data-ttu-id="84bfc-135">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="84bfc-135">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="84bfc-136">Informační sada po kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="84bfc-136">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
