---
title: "Úpravy XML schémata"
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
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b9505f60b2000ef227463404dab051ecb7fa3cc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="editing-xml-schemas"></a>Úpravy XML schémata
Úpravy schématu XML je jedním z nejdůležitějších funkcích schématu objektu modelu (SOM). Všechny vlastnosti vedlejší schema kompilace SOM lze použít ke změně hodnot existující ve schématu XML. Schéma XML můžete pak překompilovat, aby se projevily změny.  
  
 Prvním krokem při úpravě schématu načtena do rozsahu SOM je procházení schématu. Měli byste se seznámit s procházení schématu pomocí rozhraní API SOM před dalším pokusem o upravit schéma. Také byste měli být obeznámeni s před a po schema kompilace vlastnosti po-schema-kompilace-informační sadu (PSCI).  
  
## <a name="editing-an-xml-schema"></a>Úpravy schématu XML  
 V této části jsou k dispozici dva příklady kódu, které obě upravit schéma zákazníka vytvořené v [schémat XML vytváření](../../../../docs/standard/data/xml/building-xml-schemas.md) tématu. V prvním příkladu kódu přidá nový `PhoneNumber` elementu, který chcete `Customer` elementu a v druhém příkladu kódu přidá nový `Title` atribut `FirstName` elementu. První ukázka používá také po-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekci jako způsob procházení schéma zákazníka při druhém příkladu kód používá vedlejší-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekce.  
  
### <a name="phonenumber-element-example"></a>Příklad Element telefonní číslo  
 Tento první příklad kódu přidá nový `PhoneNumber` elementu, který chcete `Customer` prvku schématu zákazníka. Příklad kódu upravuje schéma zákazníka v následujících krocích.  
  
1.  Přidá do nového schématu zákazníka <xref:System.Xml.Schema.XmlSchemaSet> objektu a pak zkompiluje ho. Žádné schéma ověřování upozornění a chyb zjištěných čtení nebo kompilace schématu jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegovat.  
  
2.  Načte zkompilovaný <xref:System.Xml.Schema.XmlSchema> objektu z <xref:System.Xml.Schema.XmlSchemaSet> podle iterování přes <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost. Protože je zadané schéma zkompilovat, jsou přístupné po-Schema-kompilace-informační sadu vlastností (PSCI).  
  
3.  Vytvoří `PhoneNumber` pomocí elementu <xref:System.Xml.Schema.XmlSchemaElement> třídy, `xs:string` pomocí jednoduchého typu omezení <xref:System.Xml.Schema.XmlSchemaSimpleType> a <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> třídy, přidá omezující vlastnost vzor k <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> vlastnost omezení a přidá omezení na <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> vlastnost jednoduchý typ a jednoduchý typ, který má <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> z `PhoneNumber` elementu.  
  
4.  Opakována na každé <xref:System.Xml.Schema.XmlSchemaElement> v <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekci po-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekce.  
  
5.  Pokud <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> elementu je `"Customer"`, získá komplexní typ `Customer` pomocí elementu <xref:System.Xml.Schema.XmlSchemaComplexType> třídy a částice pořadí použití komplexní typ <xref:System.Xml.Schema.XmlSchemaSequence> třídy.  
  
6.  Přidá novou `PhoneNumber` element obsahující existující pořadí `FirstName` a `LastName` elementů pomocí vedlejší-schema-kompilace <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> kolekce pořadí.  
  
7.  Nakonec znovu zpracuje a zkompiluje upravenou <xref:System.Xml.Schema.XmlSchema> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapíše ho do konzoly.  
  
 Níže je úplný příklad kódu.  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 Toto je schéma upravené zákazníka vytvořené v [schémat XML vytváření](../../../../docs/standard/data/xml/building-xml-schemas.md) tématu.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
        <xs:element name="PhoneNumber">           <xs:simpleType>             <xs:restriction base="xs:string">               <xs:pattern value="\d{3}-\d{3}-\d(4)" />             </xs:restriction>           </xs:simpleType>         </xs:element>  
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
```  
  
### <a name="title-attribute-example"></a>Příklad názvu atributu  
 Tento druhý příklad kódu přidá nový `Title` atribut `FirstName` prvku schématu zákazníka. V prvním příkladu kódu, typ `FirstName` element je `xs:string`. Pro `FirstName` element tak, aby měl atribut společně s řetězec obsah, její typ musí být změněn na složitý typ s modelu obsahu jednoduché obsahu rozšíření.  
  
 Příklad kódu upravuje schéma zákazníka v následujících krocích.  
  
1.  Přidá do nového schématu zákazníka <xref:System.Xml.Schema.XmlSchemaSet> objektu a pak zkompiluje ho. Žádné schéma ověřování upozornění a chyb zjištěných čtení nebo kompilace schématu jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegovat.  
  
2.  Načte zkompilovaný <xref:System.Xml.Schema.XmlSchema> objektu z <xref:System.Xml.Schema.XmlSchemaSet> podle iterování přes <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost. Protože je zadané schéma zkompilovat, jsou přístupné po-Schema-kompilace-informační sadu vlastností (PSCI).  
  
3.  Vytvoří nový komplexní typ pro `FirstName` element pomocí <xref:System.Xml.Schema.XmlSchemaComplexType> třídy.  
  
4.  Vytvoří nový jednoduchý rozšíření obsahu, se základní typ `xs:string`pomocí <xref:System.Xml.Schema.XmlSchemaSimpleContent> a <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> třídy.  
  
5.  Vytvoří nový `Title` atribut, pomocí <xref:System.Xml.Schema.XmlSchemaAttribute> třída, s <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> z `xs:string` a přidá atribut jednoduché obsahu rozšíření.  
  
6.  Nastaví model obsahu jednoduchým obsahem jednoduchého rozšíření obsahu a obsahu model komplexní typ a jednoduchý obsah.  
  
7.  Přidá nový komplexní typ vedlejší-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekce.  
  
8.  Opakována na každé <xref:System.Xml.Schema.XmlSchemaObject> v vedlejší-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekce.  
  
> [!NOTE]
>  Protože `FirstName` element není globální element ve schématu, není k dispozici v <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> nebo <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekce. Vyhledá příkladu kódu `FirstName` element tím, že se první `Customer` elementu.  
>   
>  V prvním příkladu kódu provázán schématu pomocí po-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekce. V této ukázce vedlejší-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekce se používá k procházení schématu. Zatímco obě kolekce poskytují přístup k globální elementy ve schématu, iterace v rámci <xref:System.Xml.Schema.XmlSchema.Items%2A> kolekce je více časově náročné, protože všechny globální elementy ve schématu musí iterovat a nemá žádné vlastnosti PSCI. Kolekce PSCI (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>a tak dále) poskytuje přímý přístup k jejich globální prvky, atributy a typy a jejich vlastnosti PSCI.  
  
1.  Pokud <xref:System.Xml.Schema.XmlSchemaObject> je element, jehož <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> je `"Customer"`, získá komplexní typ `Customer` pomocí elementu <xref:System.Xml.Schema.XmlSchemaComplexType> třídy a částice pořadí použití komplexní typ <xref:System.Xml.Schema.XmlSchemaSequence> – třída.  
  
2.  Opakována na každé <xref:System.Xml.Schema.XmlSchemaParticle> v vedlejší-schema-kompilace <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> kolekce.  
  
3.  Pokud <xref:System.Xml.Schema.XmlSchemaParticle> je element, který na <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> je `"FirstName"`, nastaví <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> z `FirstName` element do nového `FirstName` komplexního typu.  
  
4.  Nakonec znovu zpracuje a zkompiluje upravenou <xref:System.Xml.Schema.XmlSchema> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapíše ho do konzoly.  
  
 Níže je úplný příklad kódu.  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 Toto je schéma upravené zákazníka vytvořené v [schémat XML vytváření](../../../../docs/standard/data/xml/building-xml-schemas.md) tématu.  
  
```xml  
<?xml version="1.0" encoding=" utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />  
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
  <xs:complexType name="FirstNameComplexType">     <xs:simpleContent>       <xs:extension base="xs:string">         <xs:attribute name="Title" type="xs:string" />       </xs:extension>     </xs:simpleContent>   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Viz také  
 [Přehled modelu objektů schématu XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [Čtení a zápis XML schémata](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [Vytváření XML schémata](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [Procházení schémat XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [Včetně nebo import schémat XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Informační sadu po schématu kompilace](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
