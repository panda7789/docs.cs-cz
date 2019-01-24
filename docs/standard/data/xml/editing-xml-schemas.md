---
title: Úpravy schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e2cf9e1b4349d83a378f6b17e8740c95546bbe4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573960"
---
# <a name="editing-xml-schemas"></a>Úpravy schémat XML
Úprava schématu XML je jednou z vašich nejdůležitějších funkcí z modelu objektu schématu (SOM). Všechny vlastnosti vedlejší schema kompilace SOM lze použít ke změně existujícího hodnot ve schématu XML. Schéma XML můžete pak překompilovány tak, aby odrážely změny.  
  
 Prvním krokem při úpravách schématu načtená SOM je procházení schématu. Měli byste se seznámit s procházení schématu pomocí rozhraní API SOM, než se pokusíte upravit schéma. Také byste měli být obeznámeni s vlastností před instrumentací a po schema kompilace po-schema-kompilace – informační sada (PSCI).  
  
## <a name="editing-an-xml-schema"></a>Úpravy schématu XML  
 V této části jsou k dispozici dva příklady kódu, které upravit schéma zákazníka vytvoří v [sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tématu. První příklad kódu přidá nový `PhoneNumber` elementu `Customer` prvku a druhý příklad kódu přidá nový `Title` atribut `FirstName` elementu. První příklad používá také po-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekce jako způsob procházení schématu zákazníků při druhý příklad kódu používá předprodukční-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekce.  
  
### <a name="phonenumber-element-example"></a>Příklad prvek PhoneNumber  
 Tento první příklad kódu přidá nový `PhoneNumber` elementu `Customer` prvek schématu zákazníka. Příklad kódu upraví schéma zákazníka v následujících krocích.  
  
1.  Přidá schématu zákazníků na novou <xref:System.Xml.Schema.XmlSchemaSet> objekt a potom jej zkompiluje. Žádné schéma ověření upozornění a chyb zjištěných čtení nebo kompilaci schématu jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegovat.  
  
2.  Načte zkompilovaný <xref:System.Xml.Schema.XmlSchema> objektu z <xref:System.Xml.Schema.XmlSchemaSet> pomocí provádí iterace <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost. Protože kompilaci schématu, po-Schema-kompilace – informační sadu vlastností (PSCI) jsou přístupné.  
  
3.  Vytvoří `PhoneNumber` pomocí elementu <xref:System.Xml.Schema.XmlSchemaElement> třídy, `xs:string` jednoduchého typu pomocí omezení <xref:System.Xml.Schema.XmlSchemaSimpleType> a <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> třídy, přidá vlastnost pattern k <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> vlastnost omezení a přidá omezení <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> vlastnost jednoduchý typ a jednoduchý typ, který má <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> z `PhoneNumber` elementu.  
  
4.  Iteruje přes každý <xref:System.Xml.Schema.XmlSchemaElement> v <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekce po-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekce.  
  
5.  Pokud <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> elementu, který je `"Customer"`, získá komplexní typ `Customer` pomocí elementu <xref:System.Xml.Schema.XmlSchemaComplexType> třídy a částice sequence komplexní typ použití <xref:System.Xml.Schema.XmlSchemaSequence> třídy.  
  
6.  Přidá novou `PhoneNumber` element obsahující existující pořadí `FirstName` a `LastName` prvky pomocí předprodukční-schema-kompilace <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> kolekce pořadí.  
  
7.  Nakonec znovu zpracuje a zkompiluje upravené <xref:System.Xml.Schema.XmlSchema> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapíše jej do konzoly.  
  
 Tady je příklad úplného kódu.  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 Tady je upravený zákazníka schéma se vytvořilo v [sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tématu.  
  
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
  
### <a name="title-attribute-example"></a>Příklad název atributu  
 Tento druhý příklad kódu přidá nový `Title` atribut `FirstName` prvek schématu zákazníka. V prvním příkladu kódu, typ `FirstName` element je `xs:string`. Pro `FirstName` element má atribut spolu s řetězec obsahu, jeho typ musí být změněn na složitý typ s jednoduchým rozšířením obsahu obsahu modelu.  
  
 Příklad kódu upraví schéma zákazníka v následujících krocích.  
  
1.  Přidá schématu zákazníků na novou <xref:System.Xml.Schema.XmlSchemaSet> objekt a potom jej zkompiluje. Žádné schéma ověření upozornění a chyb zjištěných čtení nebo kompilaci schématu jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegovat.  
  
2.  Načte zkompilovaný <xref:System.Xml.Schema.XmlSchema> objektu z <xref:System.Xml.Schema.XmlSchemaSet> pomocí provádí iterace <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost. Protože kompilaci schématu, po-Schema-kompilace – informační sadu vlastností (PSCI) jsou přístupné.  
  
3.  Vytvoří nový komplexní typ pro `FirstName` pomocí elementu <xref:System.Xml.Schema.XmlSchemaComplexType> třídy.  
  
4.  Vytvoří nový jednoduchým rozšířením obsahu, se jako základní typ `xs:string`, použije <xref:System.Xml.Schema.XmlSchemaSimpleContent> a <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> třídy.  
  
5.  Vytvoří nový `Title` atribut, pomocí <xref:System.Xml.Schema.XmlSchemaAttribute> třídy, se <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> z `xs:string` a přidá atribut k jednoduchým rozšířením obsahu.  
  
6.  Nastaví model obsahu jednoduchý obsah k jednoduchým rozšířením obsahu a obsahu modelu komplexní typ, který má jednoduchý obsah.  
  
7.  Přidá nový komplexní typ do předprodukční-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekce.  
  
8.  Iteruje přes každý <xref:System.Xml.Schema.XmlSchemaObject> v předprodukčním-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekce.  
  
> [!NOTE]
>  Vzhledem k tomu, `FirstName` element není globální element ve schématu, není k dispozici v <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> nebo <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekce. Příklad kódu vyhledá `FirstName` elementu první vyhledáním `Customer` elementu.  
>   
>  První příklad kódu provázán schématu pomocí po-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekce. V této ukázce předprodukční-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekce se používá k procházení schématu. Obě kolekce nabízejí přístup ke globální prvky ve schématu, iterace <xref:System.Xml.Schema.XmlSchema.Items%2A> kolekce je časově náročnější, protože nutné iterovat všechny globální elementy ve schématu a nemá žádné vlastnosti PSCI. Kolekce PSCI (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, a tak dále) poskytuje přímý přístup k jejich globální prvky, atributy a typy a jejich vlastnosti PSCI.  
  
1.  Pokud <xref:System.Xml.Schema.XmlSchemaObject> je prvek, jehož <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> je `"Customer"`, získá komplexní typ `Customer` pomocí elementu <xref:System.Xml.Schema.XmlSchemaComplexType> třídy a částice sequence komplexní typ použití <xref:System.Xml.Schema.XmlSchemaSequence> třídy.  
  
2.  Iteruje přes každý <xref:System.Xml.Schema.XmlSchemaParticle> v předprodukčním-schema-kompilace <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> kolekce.  
  
3.  Pokud <xref:System.Xml.Schema.XmlSchemaParticle> je prvek, který vaší <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> je `"FirstName"`, nastaví <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> z `FirstName` elementu do nového `FirstName` komplexního typu.  
  
4.  Nakonec znovu zpracuje a zkompiluje upravené <xref:System.Xml.Schema.XmlSchema> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapíše jej do konzoly.  
  
 Tady je příklad úplného kódu.  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 Tady je upravený zákazníka schéma se vytvořilo v [sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tématu.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Přehled Modelu objektu schématu XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [Čtení ze schémat XML a zápis do nich](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [Sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [Procházení schémat XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [Zahrnutí nebo import schémat XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Informační sada po kompilaci schématu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
