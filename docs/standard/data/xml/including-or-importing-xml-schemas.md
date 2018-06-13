---
title: Včetně nebo import schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2f83128f47a687e75a7db9bb36c487fa1f5bb6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573060"
---
# <a name="including-or-importing-xml-schemas"></a>Včetně nebo import schémat XML
Schéma XML může obsahovat `<xs:import />`, `<xs:include />`, a `<xs:redefine />` elementy. Tyto prvky schématu naleznete v dalších schémat XML, které lze použít k doplnění strukturu schématu, která zahrnuje nebo importuje je. <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> a <xref:System.Xml.Schema.XmlSchemaRedefine> třídy, mapování na tyto prvky ve Model model (schématu objektu SOM) rozhraní API.  
  
## <a name="including-or-importing-an-xml-schema"></a>Včetně nebo import schématu XML  
 Následující příklad kódu doplňují schéma zákazníka vytvořené v [schémat XML vytváření](../../../../docs/standard/data/xml/building-xml-schemas.md) téma se schéma adres. Dodávání schématu zákazníků s schéma adres zpřístupní typů adresy ve schématu zákazníka.  
  
 Schéma adres lze začlenit buď pomocí `<xs:include />` nebo `<xs:import />` elementy komponent schéma adres jako-je nebo pomocí `<xs:redefine />` element můžete upravit všechny jeho komponenty tak, aby vyhovovala potřebám zákazníků schématu. Protože má schéma adres `targetNamespace` která se liší od schématu zákazníka `<xs:import />` element, a proto je použít sémantiky importu.  
  
 Příklad kódu obsahuje schéma adres v následujících krocích.  
  
1.  Přidá do nového schématu zákazníků a schéma adres <xref:System.Xml.Schema.XmlSchemaSet> objektu a pak zkompiluje je. Žádné schéma ověřování upozornění a chyb zjištěných čtení nebo kompilování schémat jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegovat.  
  
2.  Načte zkompilovaný <xref:System.Xml.Schema.XmlSchema> objekty pro zákazníka i adresa schémata z <xref:System.Xml.Schema.XmlSchemaSet> podle iterování přes <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost. Vzhledem k tomu, že se kompilují schémat, jsou dostupné po-Schema-kompilace-informační sadu vlastností (PSCI).  
  
3.  Vytvoří <xref:System.Xml.Schema.XmlSchemaImport> objektu, nastaví <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> nastaví vlastnost importu do oboru názvů schématu, adresu, <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> vlastnost importovat <xref:System.Xml.Schema.XmlSchema> objekt schéma adres a přidá importovat <xref:System.Xml.Schema.XmlSchema.Includes%2A> Vlastnost schéma zákazníka.  
  
4.  Znovu zpracuje a zkompiluje upravenou <xref:System.Xml.Schema.XmlSchema> objekt pomocí schématu zákazníka <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapíše ho do konzoly.  
  
5.  Nakonec rekurzivně zapíše všechny schémata importovat schéma zákazníka pomocí konzoly <xref:System.Xml.Schema.XmlSchema.Includes%2A> vlastnost schématu, zákazníka. <xref:System.Xml.Schema.XmlSchema.Includes%2A> Vlastnost poskytuje přístup ke všem obsahuje, importy nebo předefinování přidán do schématu.  
  
 Níže je úplný příklad kódu a zákazníka a adresu schémat, které jsou zapsána do konzoly.  
  
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
  
 Další informace o `<xs:import />`, `<xs:include />`, a `<xs:redefine />` elementy a <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> a <xref:System.Xml.Schema.XmlSchemaRedefine> třídách naleznete v tématu [schématu XML W3C](https://www.w3.org/XML/Schema) a <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů třída referenční dokumentaci.  
  
## <a name="see-also"></a>Viz také  
 [Přehled Modelu objektu schématu XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [Čtení ze schémat XML a zápis do nich](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [Sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [Procházení schémat XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [Úpravy schémat XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
