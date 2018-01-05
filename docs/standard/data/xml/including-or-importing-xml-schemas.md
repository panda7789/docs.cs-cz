---
title: "Včetně nebo import schémat XML"
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
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ce86969bb9dc4a8db4359afa333d1f003c767895
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="including-or-importing-xml-schemas"></a><span data-ttu-id="5d118-102">Včetně nebo import schémat XML</span><span class="sxs-lookup"><span data-stu-id="5d118-102">Including or Importing XML Schemas</span></span>
<span data-ttu-id="5d118-103">Schéma XML může obsahovat `<xs:import />`, `<xs:include />`, a `<xs:redefine />` elementy.</span><span class="sxs-lookup"><span data-stu-id="5d118-103">An XML schema may contain `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements.</span></span> <span data-ttu-id="5d118-104">Tyto prvky schématu naleznete v dalších schémat XML, které lze použít k doplnění strukturu schématu, která zahrnuje nebo importuje je.</span><span class="sxs-lookup"><span data-stu-id="5d118-104">These schema elements refer to other XML schemas that can be used to supplement the structure of the schema that includes or imports them.</span></span> <span data-ttu-id="5d118-105"><xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> a <xref:System.Xml.Schema.XmlSchemaRedefine> třídy, mapování na tyto prvky ve Model model (schématu objektu SOM) rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5d118-105">The <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, map to these elements in the Schema Object Model (SOM) API.</span></span>  
  
## <a name="including-or-importing-an-xml-schema"></a><span data-ttu-id="5d118-106">Včetně nebo import schématu XML</span><span class="sxs-lookup"><span data-stu-id="5d118-106">Including or Importing an XML Schema</span></span>  
 <span data-ttu-id="5d118-107">Následující příklad kódu doplňují schéma zákazníka vytvořené v [schémat XML vytváření](../../../../docs/standard/data/xml/building-xml-schemas.md) téma se schéma adres.</span><span class="sxs-lookup"><span data-stu-id="5d118-107">The following code example supplements the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic with the address schema.</span></span> <span data-ttu-id="5d118-108">Dodávání schématu zákazníků s schéma adres zpřístupní typů adresy ve schématu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="5d118-108">Supplementing the customer schema with the address schema makes address types available in the customer schema.</span></span>  
  
 <span data-ttu-id="5d118-109">Schéma adres lze začlenit buď pomocí `<xs:include />` nebo `<xs:import />` elementy komponent schéma adres jako-je nebo pomocí `<xs:redefine />` element můžete upravit všechny jeho komponenty tak, aby vyhovovala potřebám zákazníků schématu.</span><span class="sxs-lookup"><span data-stu-id="5d118-109">The address schema can be incorporated using either `<xs:include />` or `<xs:import />` elements to use the components of the address schema as-is, or using an `<xs:redefine />` element to modify any of its components to suit the need of the customer schema.</span></span> <span data-ttu-id="5d118-110">Protože má schéma adres `targetNamespace` která se liší od schématu zákazníka `<xs:import />` element, a proto je použít sémantiky importu.</span><span class="sxs-lookup"><span data-stu-id="5d118-110">Because the address schema has a `targetNamespace` that is different from that of the customer schema, the `<xs:import />` element and therefore import semantics is used.</span></span>  
  
 <span data-ttu-id="5d118-111">Příklad kódu obsahuje schéma adres v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="5d118-111">The code example includes the address schema in the following steps.</span></span>  
  
1.  <span data-ttu-id="5d118-112">Přidá do nového schématu zákazníků a schéma adres <xref:System.Xml.Schema.XmlSchemaSet> objektu a pak zkompiluje je.</span><span class="sxs-lookup"><span data-stu-id="5d118-112">Adds the customer schema and the address schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles them.</span></span> <span data-ttu-id="5d118-113">Žádné schéma ověřování upozornění a chyb zjištěných čtení nebo kompilování schémat jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegovat.</span><span class="sxs-lookup"><span data-stu-id="5d118-113">Any schema validation warnings and errors encountered reading or compiling the schemas are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2.  <span data-ttu-id="5d118-114">Načte zkompilovaný <xref:System.Xml.Schema.XmlSchema> objekty pro zákazníka i adresa schémata z <xref:System.Xml.Schema.XmlSchemaSet> podle iterování přes <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5d118-114">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> objects for both the customer and address schemas from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="5d118-115">Vzhledem k tomu, že se kompilují schémat, jsou dostupné po-Schema-kompilace-informační sadu vlastností (PSCI).</span><span class="sxs-lookup"><span data-stu-id="5d118-115">Because the schemas are compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3.  <span data-ttu-id="5d118-116">Vytvoří <xref:System.Xml.Schema.XmlSchemaImport> objektu, nastaví <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> nastaví vlastnost importu do oboru názvů schématu, adresu, <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> vlastnost importovat <xref:System.Xml.Schema.XmlSchema> objekt schéma adres a přidá importovat <xref:System.Xml.Schema.XmlSchema.Includes%2A> Vlastnost schéma zákazníka.</span><span class="sxs-lookup"><span data-stu-id="5d118-116">Creates an <xref:System.Xml.Schema.XmlSchemaImport> object, sets the <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> property of the import to the namespace of the address schema, sets the <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> property of the import to the <xref:System.Xml.Schema.XmlSchema> object of the address schema, and adds the import to the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span>  
  
4.  <span data-ttu-id="5d118-117">Znovu zpracuje a zkompiluje upravenou <xref:System.Xml.Schema.XmlSchema> objekt pomocí schématu zákazníka <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapíše ho do konzoly.</span><span class="sxs-lookup"><span data-stu-id="5d118-117">Reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object of the customer schema using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
5.  <span data-ttu-id="5d118-118">Nakonec rekurzivně zapíše všechny schémata importovat schéma zákazníka pomocí konzoly <xref:System.Xml.Schema.XmlSchema.Includes%2A> vlastnost schématu, zákazníka.</span><span class="sxs-lookup"><span data-stu-id="5d118-118">Finally, recursively writes all of the schemas imported into the customer schema to the console using the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span> <span data-ttu-id="5d118-119"><xref:System.Xml.Schema.XmlSchema.Includes%2A> Vlastnost poskytuje přístup ke všem obsahuje, importy nebo předefinování přidán do schématu.</span><span class="sxs-lookup"><span data-stu-id="5d118-119">The <xref:System.Xml.Schema.XmlSchema.Includes%2A> property provides access to all the includes, imports, or redefines added to a schema.</span></span>  
  
 <span data-ttu-id="5d118-120">Níže je úplný příklad kódu a zákazníka a adresu schémat, které jsou zapsána do konzoly.</span><span class="sxs-lookup"><span data-stu-id="5d118-120">The following is the complete code example and the customer and address schemas written to the console.</span></span>  
  
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
  
 <span data-ttu-id="5d118-121">Další informace o `<xs:import />`, `<xs:include />`, a `<xs:redefine />` elementy a <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> a <xref:System.Xml.Schema.XmlSchemaRedefine> třídách naleznete v tématu [schématu XML W3C](http://go.microsoft.com/fwlink/?LinkId=45242) a <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů třída referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="5d118-121">For more information about the `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements and the <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, see the [W3C XML Schema](http://go.microsoft.com/fwlink/?LinkId=45242) and the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace class reference documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d118-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d118-122">See Also</span></span>  
 [<span data-ttu-id="5d118-123">Přehled Modelu objektu schématu XML</span><span class="sxs-lookup"><span data-stu-id="5d118-123">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [<span data-ttu-id="5d118-124">Čtení ze schémat XML a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="5d118-124">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [<span data-ttu-id="5d118-125">Sestavování schémat XML</span><span class="sxs-lookup"><span data-stu-id="5d118-125">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [<span data-ttu-id="5d118-126">Procházení schémat XML</span><span class="sxs-lookup"><span data-stu-id="5d118-126">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [<span data-ttu-id="5d118-127">Úpravy schémat XML</span><span class="sxs-lookup"><span data-stu-id="5d118-127">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [<span data-ttu-id="5d118-128">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="5d118-128">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
