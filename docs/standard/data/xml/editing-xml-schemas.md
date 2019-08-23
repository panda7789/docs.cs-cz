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
ms.openlocfilehash: 3d0d67c82e753b044f759b4d1139c5f6b4837b31
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948485"
---
# <a name="editing-xml-schemas"></a>Úpravy schémat XML
Úprava schématu XML je jednou z nejdůležitějších funkcí modelu SOM (Schema Object Model). Ke změně stávajících hodnot ve schématu XML lze použít všechny vlastnosti rozhraní SOM před schématem-Schema-Compilation. Schéma XML lze poté znovu zkompilovat, aby odráželo změny.  
  
 Prvním krokem při úpravách schématu načteného do modelu SOM je procházení schématu. Předtím, než se pokusíte upravit schéma, byste měli být obeznámeni s procházením schématu pomocí rozhraní API modelu SOM. Měli byste být také obeznámeni s vlastnostmi předběžného a post-Schema-Compilation-PSCI (post-Schema-Compilation-informační sada).  
  
## <a name="editing-an-xml-schema"></a>Úprava schématu XML  
 V této části jsou k dispozici dva příklady kódu, jak upravit schéma zákazníka vytvořené v tématu [sestavení XML schémat](../../../../docs/standard/data/xml/building-xml-schemas.md) . První příklad kódu přidá `PhoneNumber` nový prvek `Customer` do prvku a druhý příklad kódu přidá nový `Title` atribut `FirstName` elementu. První vzorek také používá kolekci po kompilaci <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> po schématu jako způsob procházení schématu zákazníka, zatímco druhý příklad kódu používá kolekci předběžného schématu kompilace. <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType>  
  
### <a name="phonenumber-element-example"></a>Příklad prvku PhoneNumber  
 Tento první příklad kódu přidá nový `PhoneNumber` prvek `Customer` do prvku schématu zákazníka. Příklad kódu upravuje schéma zákazníka v následujících krocích.  
  
1. Přidá schéma zákazníka do nového <xref:System.Xml.Schema.XmlSchemaSet> objektu a potom jej zkompiluje. <xref:System.Xml.Schema.ValidationEventHandler> Delegát zpracovává všechna upozornění ověřování schématu a chyby, ke kterým došlo při čtení nebo kompilování schématu.  
  
2. Načte kompilovaný <xref:System.Xml.Schema.XmlSchema> objekt z rozhraní <xref:System.Xml.Schema.XmlSchemaSet> iterací přes <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost. Vzhledem k tomu, že schéma je kompilováno, jsou k dispozici vlastnosti po PSCI (post-Schema-Compilation-informační sada).  
  
3. `xs:string` <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> <xref:System.Xml.Schema.XmlSchemaSimpleType> Vytvoří element pomocí třídy, jednoduché omezení typu pomocí tříd a, přidá omezující <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> vlastnost vzoru do vlastnosti omezení a přidá <xref:System.Xml.Schema.XmlSchemaElement> `PhoneNumber` omezení na <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> vlastnost jednoduchého typu a jednoduchý typ <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> pro `PhoneNumber` element.  
  
4. Provede iteraci každého <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> v kolekci kolekce post-Schema-Compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> .  
  
5. <xref:System.Xml.Schema.XmlSchemaSequence> <xref:System.Xml.Schema.XmlSchemaComplexType> Pokud je `"Customer"`element, získá komplexní typ `Customer` elementu pomocí třídy a částice sekvence komplexního typu pomocí třídy. <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A>  
  
6. Přidá nový `PhoneNumber` prvek do sekvence obsahující existující `FirstName` prvky a `LastName` pomocí kolekce předběžného schématu kompilace <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> sekvence.  
  
7. Nakonec znovu zpracuje <xref:System.Xml.Schema.XmlSchema> a zkompiluje upravený objekt <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> pomocí metod <xref:System.Xml.Schema.XmlSchemaSet> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> třídy a zapíše jej do konzoly.  
  
 Následuje příklad kompletního příkladu kódu.  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 Toto je upravené schéma zákazníka vytvořené v tématu sestavování [schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) .  
  
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
  
### <a name="title-attribute-example"></a>Příklad atributu title  
 Tento druhý příklad kódu přidá nový `Title` atribut `FirstName` do elementu schématu zákazníka. V prvním příkladu kódu je `FirstName` `xs:string`typ elementu. `FirstName` Aby element měl atribut spolu s obsahem řetězce, musí být jeho typ změněn na komplexní typ s jednoduchým obsahem obsahu rozšíření obsahu.  
  
 Příklad kódu upravuje schéma zákazníka v následujících krocích.  
  
1. Přidá schéma zákazníka do nového <xref:System.Xml.Schema.XmlSchemaSet> objektu a potom jej zkompiluje. <xref:System.Xml.Schema.ValidationEventHandler> Delegát zpracovává všechna upozornění ověřování schématu a chyby, ke kterým došlo při čtení nebo kompilování schématu.  
  
2. Načte kompilovaný <xref:System.Xml.Schema.XmlSchema> objekt z rozhraní <xref:System.Xml.Schema.XmlSchemaSet> iterací přes <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost. Vzhledem k tomu, že schéma je kompilováno, jsou k dispozici vlastnosti po PSCI (post-Schema-Compilation-informační sada).  
  
3. Vytvoří nový komplexní typ pro `FirstName` element <xref:System.Xml.Schema.XmlSchemaComplexType> pomocí třídy.  
  
4. Vytvoří nové jednoduché rozšíření obsahu se základním typem `xs:string`, <xref:System.Xml.Schema.XmlSchemaSimpleContent> pomocí tříd a <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> .  
  
5. Vytvoří nový `Title` atribut <xref:System.Xml.Schema.XmlSchemaAttribute> <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> pomocí`xs:string` třídy s a a přidá do jednoduchého rozšíření obsahu atribut.  
  
6. Nastaví model obsahu jednoduchého obsahu na jednoduché rozšíření obsahu a model obsahu komplexního typu na jednoduchý obsah.  
  
7. Přidá nový komplexní typ do kolekce předběžného schématu kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> .  
  
8. Iteruje u každého <xref:System.Xml.Schema.XmlSchemaObject> v kolekci kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> před schématy.  
  
> [!NOTE]
> Vzhledem k tomu, že <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> elementneníglobálnímprvkemveschématu,neníkdispoziciv`FirstName` kolekcích ani. Příklad kódu vyhledá `FirstName` element tak, že nejprve `Customer` najde element.  
>   
>  První příklad kódu procházel schéma pomocí kolekce post-Schema-Compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> . V této ukázce se k procházení schématu používá kolekce předběžného schématu kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> . Zatímco obě kolekce poskytují přístup k globálním prvkům ve schématu, iterace <xref:System.Xml.Schema.XmlSchema.Items%2A> v kolekci je více časově náročná, protože je nutné iterovat všechny globální prvky ve schématu a nemá žádné vlastnosti pSCI. Kolekce pSCI (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>,, a tak dále) poskytují přímý přístup ke svým globálním prvkům, atributům a typům a jejich PSCIm vlastnostem. <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>  
  
1. `Customer` `"Customer"` <xref:System.Xml.Schema.XmlSchemaComplexType> <xref:System.Xml.Schema.XmlSchemaSequence> Pokud je element, jehož <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> typ je, získá komplexní typ elementu pomocí třídy a částice sekvence komplexního typu pomocí třídy. <xref:System.Xml.Schema.XmlSchemaObject>  
  
2. Iteruje u každého <xref:System.Xml.Schema.XmlSchemaParticle> v kolekci kompilace <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> před schématy.  
  
3. <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> `"FirstName"` `FirstName` Pokud je prvek, <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> který je, je nastaveno na nový `FirstName` komplexní typ elementu. <xref:System.Xml.Schema.XmlSchemaParticle>  
  
4. Nakonec znovu zpracuje <xref:System.Xml.Schema.XmlSchema> a zkompiluje upravený objekt <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> pomocí metod <xref:System.Xml.Schema.XmlSchemaSet> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> třídy a zapíše jej do konzoly.  
  
 Následuje příklad kompletního příkladu kódu.  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 Toto je upravené schéma zákazníka vytvořené v tématu sestavování [schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) .  
  
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
