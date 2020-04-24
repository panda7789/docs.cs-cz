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
Schéma XML může obsahovat `<xs:import />`elementy, `<xs:include />`a. `<xs:redefine />` Tyto prvky schématu odkazují na další schémata XML, která lze použít k doplnění struktury schématu, která obsahuje nebo importuje. <xref:System.Xml.Schema.XmlSchemaImport>Třídy <xref:System.Xml.Schema.XmlSchemaInclude> a <xref:System.Xml.Schema.XmlSchemaRedefine> se mapují na tyto prvky v rozhraní API modelu SOM (Schema Object Model).  
  
## <a name="including-or-importing-an-xml-schema"></a>Zahrnutí nebo import schématu XML  
 Následující příklad kódu doplňuje schéma zákazníka vytvořené v tématu [sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) pomocí schématu adresy. Doplnění schématu zákazníka pomocí schématu adresy zpřístupňuje typy adres ve schématu zákazníka.  
  
 Schéma adresy lze pomocí elementů `<xs:include />` nebo `<xs:import />` použít k použití součástí schématu adresy, jak je, nebo pomocí `<xs:redefine />` elementu pro úpravu kterékoli jeho komponenty, aby vyhovovala potřebám schématu zákazníka. Vzhledem k tomu, že schéma `targetNamespace` adres má, které se liší od schématu zákazníka, je `<xs:import />` použit prvek, a proto je použita sémantika importu.  
  
 Příklad kódu obsahuje schéma adresy v následujících krocích.  
  
1. Přidá schéma zákazníka a schéma adresy do nového <xref:System.Xml.Schema.XmlSchemaSet> objektu a potom je zkompiluje. <xref:System.Xml.Schema.ValidationEventHandler> Delegát zpracovává všechna upozornění ověřování schématu a chyby, ke kterým došlo při čtení nebo kompilování schémat.  
  
2. Načte zkompilované <xref:System.Xml.Schema.XmlSchema> objekty pro schémata zákazníka i adresy z rozhraní <xref:System.Xml.Schema.XmlSchemaSet> iterací přes <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost. Vzhledem k tomu, že jsou schémata kompilována, jsou k dispozici vlastnosti post-Schema-Compilation-PSCI).  
  
3. <xref:System.Xml.Schema.XmlSchemaImport> Vytvoří objekt <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> , nastaví vlastnost import na obor názvů schématu adresy, nastaví <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> vlastnost import na <xref:System.Xml.Schema.XmlSchema> objekt schématu adresy a přidá import do <xref:System.Xml.Schema.XmlSchema.Includes%2A> vlastnosti schématu zákazníka...  
  
4. <xref:System.Xml.Schema.XmlSchema> Znovu zpracuje a zkompiluje upravený objekt schématu zákazníka pomocí metod <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapíše jej do konzoly.  
  
5. Nakonec rekurzivně zapíše všechna schémata importovaná do schématu zákazníka do konzoly pomocí <xref:System.Xml.Schema.XmlSchema.Includes%2A> vlastnosti schématu zákazníka. <xref:System.Xml.Schema.XmlSchema.Includes%2A> Vlastnost poskytuje přístup ke všem příkazům zahrnutí, import nebo předefinování, které byly přidány do schématu.  
  
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
  
 Další informace `<xs:import />`o `<xs:include />` `<xs:redefine />` prvcích, a a <xref:System.Xml.Schema.XmlSchemaImport>třídách, <xref:System.Xml.Schema.XmlSchemaInclude> a <xref:System.Xml.Schema.XmlSchemaRedefine> naleznete v dokumentaci [schématu W3C XML](https://www.w3.org/XML/Schema) a v <xref:System.Xml.Schema?displayProperty=nameWithType> referenční dokumentaci třídy oboru názvů.  
  
## <a name="see-also"></a>Viz také

- [Přehled Modelu objektu schématu XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [Čtení ze schémat XML a zápis do nich](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [Sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [Procházení schémat XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [Úpravy schémat XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
