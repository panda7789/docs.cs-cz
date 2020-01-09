---
title: Úpravy schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
ms.openlocfilehash: d7d9f8e0d4ec2f343b50e68e942bf94e93576f25
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710944"
---
# <a name="editing-xml-schemas"></a>Úpravy schémat XML

Úprava schématu XML je jednou z nejdůležitějších funkcí modelu SOM (Schema Object Model). Ke změně stávajících hodnot ve schématu XML lze použít všechny vlastnosti rozhraní SOM před schématem-Schema-Compilation. Schéma XML lze poté znovu zkompilovat, aby odráželo změny.

Prvním krokem při úpravách schématu načteného do modelu SOM je procházení schématu. Předtím, než se pokusíte upravit schéma, byste měli být obeznámeni s procházením schématu pomocí rozhraní API modelu SOM. Měli byste být také obeznámeni s vlastnostmi předběžného a post-Schema-Compilation-PSCI (post-Schema-Compilation-informační sada).

## <a name="editing-an-xml-schema"></a>Úprava schématu XML

V této části jsou k dispozici dva příklady kódu, jak upravit schéma zákazníka vytvořené v tématu [sestavení XML schémat](../../../../docs/standard/data/xml/building-xml-schemas.md) . První příklad kódu přidá nový prvek `PhoneNumber` do elementu `Customer` a druhý příklad kódu přidá nový `Title` atribut elementu `FirstName`. První vzorek také používá kolekci post-Schema-Compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> jako způsob procházení schématu zákazníka, zatímco druhý příklad kódu používá shromažďování <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> předběžného schématu a kompilace.

### <a name="phonenumber-element-example"></a>Příklad prvku PhoneNumber

Tento první příklad kódu přidá nový prvek `PhoneNumber` do prvku `Customer` schématu zákazníka. Příklad kódu upravuje schéma zákazníka v následujících krocích.

1. Přidá schéma zákazníka do nového objektu <xref:System.Xml.Schema.XmlSchemaSet> a potom jej zkompiluje. Všechna upozornění ověřování schématu a chyby, ke kterým došlo při čtení nebo kompilaci schématu, jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegátem.

2. Načte kompilovaný <xref:System.Xml.Schema.XmlSchema> objekt z <xref:System.Xml.Schema.XmlSchemaSet> iterací přes vlastnost <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>. Vzhledem k tomu, že schéma je kompilováno, jsou k dispozici vlastnosti po PSCI (post-Schema-Compilation-informační sada).

3. Vytvoří `PhoneNumber` element pomocí <xref:System.Xml.Schema.XmlSchemaElement> třídy, `xs:string` jednoduchý typ omezení pomocí tříd <xref:System.Xml.Schema.XmlSchemaSimpleType> a <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction>, přidá omezující vlastnost vzoru do vlastnosti <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> omezení a přidá omezení do vlastnosti <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> jednoduchého typu a jednoduchý typ pro <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> `PhoneNumber` elementu.

4. Provede iteraci každého <xref:System.Xml.Schema.XmlSchemaElement> v kolekci <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekce post-Schema-Compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>.

5. Pokud je <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> prvku `"Customer"`, získá komplexní typ `Customer` elementu pomocí třídy <xref:System.Xml.Schema.XmlSchemaComplexType> a částice sekvence komplexního typu pomocí třídy <xref:System.Xml.Schema.XmlSchemaSequence>.

6. Přidá nový prvek `PhoneNumber` do sekvence, která obsahuje existující `FirstName` a `LastName` prvky pomocí kolekce <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> před schématy kompilace sekvence.

7. Nakonec znovu zpracuje a zkompiluje upravený <xref:System.Xml.Schema.XmlSchema> objekt pomocí metod <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> třídy <xref:System.Xml.Schema.XmlSchemaSet> a zapíše jej do konzoly.

Následuje příklad kompletního příkladu kódu.

[!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
[!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
[!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]

Toto je upravené schéma zákazníka vytvořené v tématu [sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) .

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

Tento druhý příklad kódu přidá nový atribut `Title` do prvku `FirstName` schématu zákazníka. V prvním příkladu kódu je typ prvku `FirstName` `xs:string`. Aby element `FirstName` měl atribut spolu s obsahem řetězce, musí být jeho typ změněn na komplexní typ s jednoduchým obsahem obsahu rozšíření obsahu.

Příklad kódu upravuje schéma zákazníka v následujících krocích.

1. Přidá schéma zákazníka do nového objektu <xref:System.Xml.Schema.XmlSchemaSet> a potom jej zkompiluje. Všechna upozornění ověřování schématu a chyby, ke kterým došlo při čtení nebo kompilaci schématu, jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegátem.

2. Načte kompilovaný <xref:System.Xml.Schema.XmlSchema> objekt z <xref:System.Xml.Schema.XmlSchemaSet> iterací přes vlastnost <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>. Vzhledem k tomu, že schéma je kompilováno, jsou k dispozici vlastnosti po PSCI (post-Schema-Compilation-informační sada).

3. Vytvoří nový komplexní typ prvku `FirstName` pomocí <xref:System.Xml.Schema.XmlSchemaComplexType> třídy.

4. Vytvoří nové jednoduché rozšíření obsahu se základním typem `xs:string`pomocí tříd <xref:System.Xml.Schema.XmlSchemaSimpleContent> a <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension>.

5. Vytvoří nový atribut `Title` pomocí <xref:System.Xml.Schema.XmlSchemaAttribute> třídy s <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> `xs:string` a přidá atribut do jednoduchého rozšíření obsahu.

6. Nastaví model obsahu jednoduchého obsahu na jednoduché rozšíření obsahu a model obsahu komplexního typu na jednoduchý obsah.

7. Přidá nový komplexní typ do kolekce <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> před schématem kompilace.

8. Iteruje každý <xref:System.Xml.Schema.XmlSchemaObject> v kolekci pre-Schema-Compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType>.

> [!NOTE]
> Vzhledem k tomu, že prvek `FirstName` není globálním prvkem ve schématu, není k dispozici v kolekcích <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> nebo <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>. Příklad kódu vyhledá prvek `FirstName` tím, že nejprve najde `Customer` prvek.
>
> První příklad kódu procházel schéma pomocí kolekce <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> po schématu kompilace. V této ukázce se k procházení schématu používá kolekce pre-Schema-Compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType>. Zatímco obě kolekce poskytují přístup k globálním prvkům ve schématu, iterace v kolekci <xref:System.Xml.Schema.XmlSchema.Items%2A> je více časově náročná, protože je nutné iterovat všechny globální prvky ve schématu a nemá žádné vlastnosti PSCI. Kolekce PSCI (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>a tak dále) poskytují přímý přístup ke svým globálním prvkům, atributům a typům a jejich PSCIm vlastnostem.

1. Je-li <xref:System.Xml.Schema.XmlSchemaObject> element, jehož <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> je `"Customer"`, získá komplexní typ `Customer` prvku pomocí třídy <xref:System.Xml.Schema.XmlSchemaComplexType> a částice sekvence komplexního typu pomocí třídy <xref:System.Xml.Schema.XmlSchemaSequence>.

2. Iteruje každý <xref:System.Xml.Schema.XmlSchemaParticle> v kolekci pre-Schema-Compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType>.

3. Pokud <xref:System.Xml.Schema.XmlSchemaParticle> je prvek, který je <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> `"FirstName"`, nastaví <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> prvku `FirstName` na nový `FirstName` komplexní typ.

4. Nakonec znovu zpracuje a zkompiluje upravený <xref:System.Xml.Schema.XmlSchema> objekt pomocí metod <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> a <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> třídy <xref:System.Xml.Schema.XmlSchemaSet> a zapíše jej do konzoly.

Následuje příklad kompletního příkladu kódu.

[!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
[!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
[!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]

Toto je upravené schéma zákazníka vytvořené v tématu [sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) .

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
