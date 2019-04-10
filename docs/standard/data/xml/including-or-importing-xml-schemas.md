---
title: Zahrnutí nebo import schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 45f6b402ae01b7f762f8ef10dcfb0bc46f949db6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343568"
---
# <a name="including-or-importing-xml-schemas"></a><span data-ttu-id="1718c-102">Zahrnutí nebo import schémat XML</span><span class="sxs-lookup"><span data-stu-id="1718c-102">Including or Importing XML Schemas</span></span>
<span data-ttu-id="1718c-103">Schéma XML může obsahovat `<xs:import />`, `<xs:include />`, a `<xs:redefine />` elementy.</span><span class="sxs-lookup"><span data-stu-id="1718c-103">An XML schema may contain `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements.</span></span> <span data-ttu-id="1718c-104">Tyto prvky schématu odkazují na jiná schémata XML, které lze použít k doplnění struktura schéma, které zahrnuje nebo importuje.</span><span class="sxs-lookup"><span data-stu-id="1718c-104">These schema elements refer to other XML schemas that can be used to supplement the structure of the schema that includes or imports them.</span></span> <span data-ttu-id="1718c-105"><xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> a <xref:System.Xml.Schema.XmlSchemaRedefine> třídy, mapování na tyto prvky v schématu objektu modelu (SOM) rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="1718c-105">The <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, map to these elements in the Schema Object Model (SOM) API.</span></span>  
  
## <a name="including-or-importing-an-xml-schema"></a><span data-ttu-id="1718c-106">Zahrnutí nebo import schématu XML</span><span class="sxs-lookup"><span data-stu-id="1718c-106">Including or Importing an XML Schema</span></span>  
 <span data-ttu-id="1718c-107">Následující příklad kódu doplňuje zákazníka schéma se vytvořilo v [sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) téma se schéma adres.</span><span class="sxs-lookup"><span data-stu-id="1718c-107">The following code example supplements the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic with the address schema.</span></span> <span data-ttu-id="1718c-108">Doplňující schéma zákazníka se schématem adresu zpřístupňuje typy adres ve schématu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="1718c-108">Supplementing the customer schema with the address schema makes address types available in the customer schema.</span></span>  
  
 <span data-ttu-id="1718c-109">Schéma adres být použity buď pomocí `<xs:include />` nebo `<xs:import />` prvků, které mají používat součástí schématu adresy jako-je, nebo pomocí `<xs:redefine />` element můžete upravit všechny součásti tak, aby vyhovoval potřebám zákazníků schématu.</span><span class="sxs-lookup"><span data-stu-id="1718c-109">The address schema can be incorporated using either `<xs:include />` or `<xs:import />` elements to use the components of the address schema as-is, or using an `<xs:redefine />` element to modify any of its components to suit the need of the customer schema.</span></span> <span data-ttu-id="1718c-110">Vzhledem k tomu, že schéma adres má `targetNamespace` , která se liší od schématu zákazníka `<xs:import />` elementu a proto se používá sémantiku import.</span><span class="sxs-lookup"><span data-stu-id="1718c-110">Because the address schema has a `targetNamespace` that is different from that of the customer schema, the `<xs:import />` element and therefore import semantics is used.</span></span>  
  
 <span data-ttu-id="1718c-111">Příklad kódu obsahuje schéma adresy v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="1718c-111">The code example includes the address schema in the following steps.</span></span>  
  
1. <span data-ttu-id="1718c-112">Přidá do nového schématu zákazníka a schéma adresy <xref:System.Xml.Schema.XmlSchemaSet> objektů a jejich kompiluje.</span><span class="sxs-lookup"><span data-stu-id="1718c-112">Adds the customer schema and the address schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles them.</span></span> <span data-ttu-id="1718c-113">Žádné schéma ověření upozornění a chyb zjištěných pro čtení nebo kompilování schémat jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegovat.</span><span class="sxs-lookup"><span data-stu-id="1718c-113">Any schema validation warnings and errors encountered reading or compiling the schemas are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="1718c-114">Načte zkompilovaný <xref:System.Xml.Schema.XmlSchema> objekty pro zákazníky i adresu schémata z <xref:System.Xml.Schema.XmlSchemaSet> pomocí provádí iterace <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1718c-114">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> objects for both the customer and address schemas from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="1718c-115">Vzhledem k tomu, že schémata jsou kompilovány, po-Schema-kompilace – informační sadu vlastností (PSCI) jsou přístupné.</span><span class="sxs-lookup"><span data-stu-id="1718c-115">Because the schemas are compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="1718c-116">Vytvoří <xref:System.Xml.Schema.XmlSchemaImport> objektu, nastaví <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> nastaví vlastnost importované do oboru názvů schématu adresy <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> vlastnost importovat <xref:System.Xml.Schema.XmlSchema> objekt schéma adresy a přidává import pro <xref:System.Xml.Schema.XmlSchema.Includes%2A> vlastnost schématu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="1718c-116">Creates an <xref:System.Xml.Schema.XmlSchemaImport> object, sets the <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> property of the import to the namespace of the address schema, sets the <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> property of the import to the <xref:System.Xml.Schema.XmlSchema> object of the address schema, and adds the import to the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span>  
  
4. <span data-ttu-id="1718c-117">Znovu zpracuje a zkompiluje upravené <xref:System.Xml.Schema.XmlSchema> objektu pomocí schématu zákazníků <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapíše jej do konzoly.</span><span class="sxs-lookup"><span data-stu-id="1718c-117">Reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object of the customer schema using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
5. <span data-ttu-id="1718c-118">Navíc rekurzivně zapíše všechna schémata importován schématu zákazníka pomocí konzoly <xref:System.Xml.Schema.XmlSchema.Includes%2A> vlastnost schématu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="1718c-118">Finally, recursively writes all of the schemas imported into the customer schema to the console using the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span> <span data-ttu-id="1718c-119"><xref:System.Xml.Schema.XmlSchema.Includes%2A> Vlastnost poskytuje přístup ke všem obsahuje, imports nebo předefinování přidá do schématu.</span><span class="sxs-lookup"><span data-stu-id="1718c-119">The <xref:System.Xml.Schema.XmlSchema.Includes%2A> property provides access to all the includes, imports, or redefines added to a schema.</span></span>  
  
 <span data-ttu-id="1718c-120">Tady je příklad úplného kódu a zákazníka a adresu schémata zapsána do konzoly.</span><span class="sxs-lookup"><span data-stu-id="1718c-120">The following is the complete code example and the customer and address schemas written to the console.</span></span>  
  
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
  
 <span data-ttu-id="1718c-121">Další informace o `<xs:import />`, `<xs:include />`, a `<xs:redefine />` elementy a <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> a <xref:System.Xml.Schema.XmlSchemaRedefine> třídy, najdete v článku [W3C XML schématu](https://www.w3.org/XML/Schema) a <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů tříd referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="1718c-121">For more information about the `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements and the <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, see the [W3C XML Schema](https://www.w3.org/XML/Schema) and the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace class reference documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1718c-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1718c-122">See also</span></span>

- [<span data-ttu-id="1718c-123">Přehled Modelu objektu schématu XML</span><span class="sxs-lookup"><span data-stu-id="1718c-123">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="1718c-124">Čtení ze schémat XML a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="1718c-124">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="1718c-125">Sestavování schémat XML</span><span class="sxs-lookup"><span data-stu-id="1718c-125">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="1718c-126">Procházení schémat XML</span><span class="sxs-lookup"><span data-stu-id="1718c-126">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="1718c-127">Úpravy schémat XML</span><span class="sxs-lookup"><span data-stu-id="1718c-127">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [<span data-ttu-id="1718c-128">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="1718c-128">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
