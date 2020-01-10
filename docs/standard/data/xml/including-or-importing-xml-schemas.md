---
title: Zahrnutí nebo import schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
ms.openlocfilehash: d9a18876d8a5ba3067aa35c617b1e20fce0411f5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710775"
---
# <a name="including-or-importing-xml-schemas"></a><span data-ttu-id="9f469-102">Zahrnutí nebo import schémat XML</span><span class="sxs-lookup"><span data-stu-id="9f469-102">Including or Importing XML Schemas</span></span>
<span data-ttu-id="9f469-103">Schéma XML může obsahovat prvky `<xs:import />`, `<xs:include />`a `<xs:redefine />`.</span><span class="sxs-lookup"><span data-stu-id="9f469-103">An XML schema may contain `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements.</span></span> <span data-ttu-id="9f469-104">Tyto prvky schématu odkazují na další schémata XML, která lze použít k doplnění struktury schématu, která obsahuje nebo importuje.</span><span class="sxs-lookup"><span data-stu-id="9f469-104">These schema elements refer to other XML schemas that can be used to supplement the structure of the schema that includes or imports them.</span></span> <span data-ttu-id="9f469-105">Třídy <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> a <xref:System.Xml.Schema.XmlSchemaRedefine> se mapují na tyto prvky v rozhraní API SOM (Schema Object Model).</span><span class="sxs-lookup"><span data-stu-id="9f469-105">The <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, map to these elements in the Schema Object Model (SOM) API.</span></span>  
  
## <a name="including-or-importing-an-xml-schema"></a><span data-ttu-id="9f469-106">Zahrnutí nebo import schématu XML</span><span class="sxs-lookup"><span data-stu-id="9f469-106">Including or Importing an XML Schema</span></span>  
 <span data-ttu-id="9f469-107">Následující příklad kódu doplňuje schéma zákazníka vytvořené v tématu [sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) pomocí schématu adresy.</span><span class="sxs-lookup"><span data-stu-id="9f469-107">The following code example supplements the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic with the address schema.</span></span> <span data-ttu-id="9f469-108">Doplnění schématu zákazníka pomocí schématu adresy zpřístupňuje typy adres ve schématu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="9f469-108">Supplementing the customer schema with the address schema makes address types available in the customer schema.</span></span>  
  
 <span data-ttu-id="9f469-109">Schéma adresy lze začlenit pomocí `<xs:include />` nebo `<xs:import />` prvky pro použití komponent schématu adresy, jak je, nebo pomocí elementu `<xs:redefine />` pro úpravu kterékoli jeho komponenty, aby vyhovovala potřebám schématu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="9f469-109">The address schema can be incorporated using either `<xs:include />` or `<xs:import />` elements to use the components of the address schema as-is, or using an `<xs:redefine />` element to modify any of its components to suit the need of the customer schema.</span></span> <span data-ttu-id="9f469-110">Vzhledem k tomu, že schéma adresy obsahuje `targetNamespace`, která se liší od schématu zákazníka, `<xs:import />` elementu, a proto je použita sémantika importu.</span><span class="sxs-lookup"><span data-stu-id="9f469-110">Because the address schema has a `targetNamespace` that is different from that of the customer schema, the `<xs:import />` element and therefore import semantics is used.</span></span>  
  
 <span data-ttu-id="9f469-111">Příklad kódu obsahuje schéma adresy v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="9f469-111">The code example includes the address schema in the following steps.</span></span>  
  
1. <span data-ttu-id="9f469-112">Přidá schéma zákazníka a schéma adresy do nového objektu <xref:System.Xml.Schema.XmlSchemaSet> a potom je zkompiluje.</span><span class="sxs-lookup"><span data-stu-id="9f469-112">Adds the customer schema and the address schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles them.</span></span> <span data-ttu-id="9f469-113">Všechna upozornění ověřování schématu a chyby, ke kterým došlo při čtení nebo kompilaci schémat, jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegátem.</span><span class="sxs-lookup"><span data-stu-id="9f469-113">Any schema validation warnings and errors encountered reading or compiling the schemas are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="9f469-114">Načte zkompilované objekty <xref:System.Xml.Schema.XmlSchema> pro schémata zákazníka i adresy z <xref:System.Xml.Schema.XmlSchemaSet> iterací přes vlastnost <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f469-114">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> objects for both the customer and address schemas from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="9f469-115">Vzhledem k tomu, že jsou schémata kompilována, jsou k dispozici vlastnosti post-Schema-Compilation-PSCI).</span><span class="sxs-lookup"><span data-stu-id="9f469-115">Because the schemas are compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="9f469-116">Vytvoří objekt <xref:System.Xml.Schema.XmlSchemaImport>, nastaví vlastnost <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> import do oboru názvů schématu adresy, nastaví vlastnost <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> importu do objektu <xref:System.Xml.Schema.XmlSchema> schématu adresy a přidá import do vlastnosti <xref:System.Xml.Schema.XmlSchema.Includes%2A> schématu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="9f469-116">Creates an <xref:System.Xml.Schema.XmlSchemaImport> object, sets the <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> property of the import to the namespace of the address schema, sets the <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> property of the import to the <xref:System.Xml.Schema.XmlSchema> object of the address schema, and adds the import to the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span>  
  
4. <span data-ttu-id="9f469-117">Znovu zpracuje a zkompiluje upravený <xref:System.Xml.Schema.XmlSchema> objekt schématu zákazníka pomocí metod <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> třídy <xref:System.Xml.Schema.XmlSchemaSet> a zapisuje je do konzoly.</span><span class="sxs-lookup"><span data-stu-id="9f469-117">Reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object of the customer schema using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
5. <span data-ttu-id="9f469-118">Nakonec rekurzivně zapíše všechna schémata importovaná do schématu zákazníka do konzoly pomocí vlastnosti <xref:System.Xml.Schema.XmlSchema.Includes%2A> schématu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="9f469-118">Finally, recursively writes all of the schemas imported into the customer schema to the console using the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span> <span data-ttu-id="9f469-119">Vlastnost <xref:System.Xml.Schema.XmlSchema.Includes%2A> poskytuje přístup ke všem příkazům zahrnutí, import nebo předefinování, které byly přidány do schématu.</span><span class="sxs-lookup"><span data-stu-id="9f469-119">The <xref:System.Xml.Schema.XmlSchema.Includes%2A> property provides access to all the includes, imports, or redefines added to a schema.</span></span>  
  
 <span data-ttu-id="9f469-120">Následuje kompletní příklad kódu a schémata zákazníka a adresy zapsané do konzoly.</span><span class="sxs-lookup"><span data-stu-id="9f469-120">The following is the complete code example and the customer and address schemas written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaImportExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaImportExample/CPP/XmlSchemaImportExample.cpp#1)]
 [!code-csharp[XmlSchemaImportExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaImportExample/CS/XmlSchemaImportExample.cs#1)]
 [!code-vb[XmlSchemaImportExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaImportExample/VB/XmlSchemaImportExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://www.example.com/IPO" />  
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
<schema targetNamespace="http://www.example.com/IPO" xmlns="http://www.w3.org/2001/XMLSchema" xmlns:ipo="http://www.example.com/IPO">  
  <annotation>  
    <documentation xml:lang="en">  
      Addresses for International Purchase order schema  
      Copyright 2000 Example.com. All rights reserved.  
    </documentation>  
  </annotation>  
  <complexType name="Address">  
    <sequence>  
      <element name="name"   type="string"/>  
      <element name="street" type="string"/>  
      <element name="city"   type="string"/>  
    </sequence>  
  </complexType>  
  <complexType name="USAddress">  
    <complexContent>  
      <extension base="ipo:Address">  
        <sequence>  
          <element name="state" type="ipo:USState"/>  
          <element name="zip"   type="positiveInteger"/>  
        </sequence>  
      </extension>  
    </complexContent>  
  </complexType>  
  <!-- other Address derivations for more countries or regions -->  
  <simpleType name="USState">  
    <restriction base="string">  
      <enumeration value="AK"/>  
      <enumeration value="AL"/>  
      <enumeration value="AR"/>  
      <!-- and so on ... -->  
    </restriction>  
  </simpleType>  
</schema>  
```  
  
 <span data-ttu-id="9f469-121">Další informace o `<xs:import />`, `<xs:include />`a `<xs:redefine />` prvcích a třídách <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> a <xref:System.Xml.Schema.XmlSchemaRedefine> naleznete v referenční dokumentaci ke [schématu XML W3C](https://www.w3.org/XML/Schema) a <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9f469-121">For more information about the `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements and the <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, see the [W3C XML Schema](https://www.w3.org/XML/Schema) and the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace class reference documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f469-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f469-122">See also</span></span>

- [<span data-ttu-id="9f469-123">Přehled Modelu objektu schématu XML</span><span class="sxs-lookup"><span data-stu-id="9f469-123">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="9f469-124">Čtení ze schémat XML a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="9f469-124">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="9f469-125">Sestavování schémat XML</span><span class="sxs-lookup"><span data-stu-id="9f469-125">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="9f469-126">Procházení schémat XML</span><span class="sxs-lookup"><span data-stu-id="9f469-126">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="9f469-127">Úpravy schémat XML</span><span class="sxs-lookup"><span data-stu-id="9f469-127">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [<span data-ttu-id="9f469-128">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="9f469-128">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
