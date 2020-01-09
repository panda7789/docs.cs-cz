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
# <a name="including-or-importing-xml-schemas"></a>Zahrnutí nebo import schémat XML
Schéma XML může obsahovat prvky `<xs:import />`, `<xs:include />`a `<xs:redefine />`. Tyto prvky schématu odkazují na další schémata XML, která lze použít k doplnění struktury schématu, která obsahuje nebo importuje. Třídy <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> a <xref:System.Xml.Schema.XmlSchemaRedefine> se mapují na tyto prvky v rozhraní API SOM (Schema Object Model).  
  
## <a name="including-or-importing-an-xml-schema"></a>Zahrnutí nebo import schématu XML  
 Následující příklad kódu doplňuje schéma zákazníka vytvořené v tématu [sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) pomocí schématu adresy. Doplnění schématu zákazníka pomocí schématu adresy zpřístupňuje typy adres ve schématu zákazníka.  
  
 Schéma adresy lze začlenit pomocí `<xs:include />` nebo `<xs:import />` prvky pro použití komponent schématu adresy, jak je, nebo pomocí elementu `<xs:redefine />` pro úpravu kterékoli jeho komponenty, aby vyhovovala potřebám schématu zákazníka. Vzhledem k tomu, že schéma adresy obsahuje `targetNamespace`, která se liší od schématu zákazníka, `<xs:import />` elementu, a proto je použita sémantika importu.  
  
 Příklad kódu obsahuje schéma adresy v následujících krocích.  
  
1. Přidá schéma zákazníka a schéma adresy do nového objektu <xref:System.Xml.Schema.XmlSchemaSet> a potom je zkompiluje. Všechna upozornění ověřování schématu a chyby, ke kterým došlo při čtení nebo kompilaci schémat, jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegátem.  
  
2. Načte zkompilované objekty <xref:System.Xml.Schema.XmlSchema> pro schémata zákazníka i adresy z <xref:System.Xml.Schema.XmlSchemaSet> iterací přes vlastnost <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>. Vzhledem k tomu, že jsou schémata kompilována, jsou k dispozici vlastnosti post-Schema-Compilation-PSCI).  
  
3. Vytvoří objekt <xref:System.Xml.Schema.XmlSchemaImport>, nastaví vlastnost <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> import do oboru názvů schématu adresy, nastaví vlastnost <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> importu do objektu <xref:System.Xml.Schema.XmlSchema> schématu adresy a přidá import do vlastnosti <xref:System.Xml.Schema.XmlSchema.Includes%2A> schématu zákazníka.  
  
4. Znovu zpracuje a zkompiluje upravený <xref:System.Xml.Schema.XmlSchema> objekt schématu zákazníka pomocí metod <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> třídy <xref:System.Xml.Schema.XmlSchemaSet> a zapisuje je do konzoly.  
  
5. Nakonec rekurzivně zapíše všechna schémata importovaná do schématu zákazníka do konzoly pomocí vlastnosti <xref:System.Xml.Schema.XmlSchema.Includes%2A> schématu zákazníka. Vlastnost <xref:System.Xml.Schema.XmlSchema.Includes%2A> poskytuje přístup ke všem příkazům zahrnutí, import nebo předefinování, které byly přidány do schématu.  
  
 Následuje kompletní příklad kódu a schémata zákazníka a adresy zapsané do konzoly.  
  
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
  
 Další informace o `<xs:import />`, `<xs:include />`a `<xs:redefine />` prvcích a třídách <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> a <xref:System.Xml.Schema.XmlSchemaRedefine> naleznete v referenční dokumentaci ke [schématu XML W3C](https://www.w3.org/XML/Schema) a <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů.  
  
## <a name="see-also"></a>Viz také:

- [Přehled Modelu objektu schématu XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [Čtení ze schémat XML a zápis do nich](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [Sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [Procházení schémat XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [Úpravy schémat XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
