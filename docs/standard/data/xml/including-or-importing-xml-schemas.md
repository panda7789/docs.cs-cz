---
title: Zahrnutí nebo import schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
ms.openlocfilehash: f6c2829d45db147c81592c00710f04168b40679e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287698"
---
# <a name="including-or-importing-xml-schemas"></a>Zahrnutí nebo import schémat XML
Schéma XML může obsahovat `<xs:import />` elementy, `<xs:include />` a `<xs:redefine />` . Tyto prvky schématu odkazují na další schémata XML, která lze použít k doplnění struktury schématu, která obsahuje nebo importuje. <xref:System.Xml.Schema.XmlSchemaImport> <xref:System.Xml.Schema.XmlSchemaInclude> Třídy a se <xref:System.Xml.Schema.XmlSchemaRedefine> mapují na tyto prvky v rozhraní API modelu SOM (Schema Object Model).  
  
## <a name="including-or-importing-an-xml-schema"></a>Zahrnutí nebo import schématu XML  
 Následující příklad kódu doplňuje schéma zákazníka vytvořené v tématu [sestavování schémat XML](building-xml-schemas.md) pomocí schématu adresy. Doplnění schématu zákazníka pomocí schématu adresy zpřístupňuje typy adres ve schématu zákazníka.  
  
 Schéma adresy lze pomocí `<xs:include />` `<xs:import />` elementů nebo použít k použití součástí schématu adresy, jak je, nebo pomocí `<xs:redefine />` elementu pro úpravu kterékoli jeho komponenty, aby vyhovovala potřebám schématu zákazníka. Vzhledem k tomu, že schéma adres má `targetNamespace` , které se liší od schématu zákazníka, `<xs:import />` je použit prvek, a proto je použita sémantika importu.  
  
 Příklad kódu obsahuje schéma adresy v následujících krocích.  
  
1. Přidá schéma zákazníka a schéma adresy do nového <xref:System.Xml.Schema.XmlSchemaSet> objektu a potom je zkompiluje. Delegát zpracovává všechna upozornění ověřování schématu a chyby, ke kterým došlo při čtení nebo kompilování schémat <xref:System.Xml.Schema.ValidationEventHandler> .  
  
2. Načte zkompilované <xref:System.Xml.Schema.XmlSchema> objekty pro schémata zákazníka i adresy z rozhraní <xref:System.Xml.Schema.XmlSchemaSet> iterací přes <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost. Vzhledem k tomu, že jsou schémata kompilována, jsou k dispozici vlastnosti post-Schema-Compilation-PSCI).  
  
3. Vytvoří <xref:System.Xml.Schema.XmlSchemaImport> objekt, nastaví <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> vlastnost import na obor názvů schématu adresy, nastaví <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> vlastnost import na <xref:System.Xml.Schema.XmlSchema> objekt schématu adresy a přidá import do <xref:System.Xml.Schema.XmlSchema.Includes%2A> vlastnosti schématu zákazníka...  
  
4. Znovu zpracuje a zkompiluje upravený <xref:System.Xml.Schema.XmlSchema> objekt schématu zákazníka pomocí <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metod a <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapíše jej do konzoly.  
  
5. Nakonec rekurzivně zapíše všechna schémata importovaná do schématu zákazníka do konzoly pomocí <xref:System.Xml.Schema.XmlSchema.Includes%2A> vlastnosti schématu zákazníka. <xref:System.Xml.Schema.XmlSchema.Includes%2A>Vlastnost poskytuje přístup ke všem příkazům zahrnutí, import nebo předefinování, které byly přidány do schématu.  
  
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
  
 Další informace o `<xs:import />` prvcích, a `<xs:include />` `<xs:redefine />` a <xref:System.Xml.Schema.XmlSchemaImport> třídách, a naleznete <xref:System.Xml.Schema.XmlSchemaInclude> v <xref:System.Xml.Schema.XmlSchemaRedefine> dokumentaci [schématu W3C XML](https://www.w3.org/XML/Schema) a v <xref:System.Xml.Schema?displayProperty=nameWithType> referenční dokumentaci třídy oboru názvů.  
  
## <a name="see-also"></a>Viz také

- [Přehled Modelu objektu schématu XML](xml-schema-object-model-overview.md)
- [Čtení ze schémat XML a zápis do nich](reading-and-writing-xml-schemas.md)
- [Sestavování schémat XML](building-xml-schemas.md)
- [Procházení schémat XML](traversing-xml-schemas.md)
- [Úpravy schémat XML](editing-xml-schemas.md)
- [XmlSchemaSet pro kompilaci schématu](xmlschemaset-for-schema-compilation.md)
