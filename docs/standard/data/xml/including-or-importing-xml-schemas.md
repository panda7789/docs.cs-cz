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
# <a name="including-or-importing-xml-schemas"></a>Zahrnutí nebo import schémat XML
Schéma XML může obsahovat `<xs:import />`, `<xs:include />`, a `<xs:redefine />` elementy. Tyto prvky schématu odkazují na jiná schémata XML, které lze použít k doplnění struktura schéma, které zahrnuje nebo importuje. <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> a <xref:System.Xml.Schema.XmlSchemaRedefine> třídy, mapování na tyto prvky v schématu objektu modelu (SOM) rozhraní API.  
  
## <a name="including-or-importing-an-xml-schema"></a>Zahrnutí nebo import schématu XML  
 Následující příklad kódu doplňuje zákazníka schéma se vytvořilo v [sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) téma se schéma adres. Doplňující schéma zákazníka se schématem adresu zpřístupňuje typy adres ve schématu zákazníka.  
  
 Schéma adres být použity buď pomocí `<xs:include />` nebo `<xs:import />` prvků, které mají používat součástí schématu adresy jako-je, nebo pomocí `<xs:redefine />` element můžete upravit všechny součásti tak, aby vyhovoval potřebám zákazníků schématu. Vzhledem k tomu, že schéma adres má `targetNamespace` , která se liší od schématu zákazníka `<xs:import />` elementu a proto se používá sémantiku import.  
  
 Příklad kódu obsahuje schéma adresy v následujících krocích.  
  
1. Přidá do nového schématu zákazníka a schéma adresy <xref:System.Xml.Schema.XmlSchemaSet> objektů a jejich kompiluje. Žádné schéma ověření upozornění a chyb zjištěných pro čtení nebo kompilování schémat jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegovat.  
  
2. Načte zkompilovaný <xref:System.Xml.Schema.XmlSchema> objekty pro zákazníky i adresu schémata z <xref:System.Xml.Schema.XmlSchemaSet> pomocí provádí iterace <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost. Vzhledem k tomu, že schémata jsou kompilovány, po-Schema-kompilace – informační sadu vlastností (PSCI) jsou přístupné.  
  
3. Vytvoří <xref:System.Xml.Schema.XmlSchemaImport> objektu, nastaví <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> nastaví vlastnost importované do oboru názvů schématu adresy <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> vlastnost importovat <xref:System.Xml.Schema.XmlSchema> objekt schéma adresy a přidává import pro <xref:System.Xml.Schema.XmlSchema.Includes%2A> vlastnost schématu zákazníka.  
  
4. Znovu zpracuje a zkompiluje upravené <xref:System.Xml.Schema.XmlSchema> objektu pomocí schématu zákazníků <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapíše jej do konzoly.  
  
5. Navíc rekurzivně zapíše všechna schémata importován schématu zákazníka pomocí konzoly <xref:System.Xml.Schema.XmlSchema.Includes%2A> vlastnost schématu zákazníka. <xref:System.Xml.Schema.XmlSchema.Includes%2A> Vlastnost poskytuje přístup ke všem obsahuje, imports nebo předefinování přidá do schématu.  
  
 Tady je příklad úplného kódu a zákazníka a adresu schémata zapsána do konzoly.  
  
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
  
 Další informace o `<xs:import />`, `<xs:include />`, a `<xs:redefine />` elementy a <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> a <xref:System.Xml.Schema.XmlSchemaRedefine> třídy, najdete v článku [W3C XML schématu](https://www.w3.org/XML/Schema) a <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů tříd referenční dokumentaci.  
  
## <a name="see-also"></a>Viz také:

- [Přehled Modelu objektu schématu XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [Čtení ze schémat XML a zápis do nich](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [Sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [Procházení schémat XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [Úpravy schémat XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
