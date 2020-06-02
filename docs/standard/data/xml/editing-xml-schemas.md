---
title: Úpravy schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
ms.openlocfilehash: b309c390ede3afc38122188337fa0dc3336e3ad5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292056"
---
# <a name="editing-xml-schemas"></a>Úpravy schémat XML

Úprava schématu XML je jednou z nejdůležitějších funkcí modelu SOM (Schema Object Model). Ke změně stávajících hodnot ve schématu XML lze použít všechny vlastnosti rozhraní SOM před schématem-Schema-Compilation. Schéma XML lze poté znovu zkompilovat, aby odráželo změny.

Prvním krokem při úpravách schématu načteného do modelu SOM je procházení schématu. Předtím, než se pokusíte upravit schéma, byste měli být obeznámeni s procházením schématu pomocí rozhraní API modelu SOM. Měli byste být také obeznámeni s vlastnostmi předběžného a post-Schema-Compilation-PSCI (post-Schema-Compilation-informační sada).

## <a name="editing-an-xml-schema"></a>Úprava schématu XML

V této části jsou k dispozici dva příklady kódu, jak upravit schéma zákazníka vytvořené v tématu [sestavení XML schémat](building-xml-schemas.md) . První příklad kódu přidá nový `PhoneNumber` prvek do `Customer` prvku a druhý příklad kódu přidá nový `Title` atribut `FirstName` elementu. První vzorek také používá kolekci po kompilaci po schématu <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> jako způsob procházení schématu zákazníka, zatímco druhý příklad kódu používá kolekci předběžného schématu kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> .

### <a name="phonenumber-element-example"></a>Příklad prvku PhoneNumber

Tento první příklad kódu přidá nový `PhoneNumber` prvek do `Customer` prvku schématu zákazníka. Příklad kódu upravuje schéma zákazníka v následujících krocích.

1. Přidá schéma zákazníka do nového <xref:System.Xml.Schema.XmlSchemaSet> objektu a potom jej zkompiluje. Delegát zpracovává všechna upozornění ověřování schématu a chyby, ke kterým došlo při čtení nebo kompilování schématu <xref:System.Xml.Schema.ValidationEventHandler> .

2. Načte kompilovaný <xref:System.Xml.Schema.XmlSchema> objekt z rozhraní <xref:System.Xml.Schema.XmlSchemaSet> iterací přes <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost. Vzhledem k tomu, že schéma je kompilováno, jsou k dispozici vlastnosti po PSCI (post-Schema-Compilation-informační sada).

3. Vytvoří `PhoneNumber` element pomocí <xref:System.Xml.Schema.XmlSchemaElement> třídy, `xs:string` jednoduché omezení typu pomocí <xref:System.Xml.Schema.XmlSchemaSimpleType> <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> tříd a, přidá omezující vlastnost vzoru do <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> Vlastnosti omezení a přidá omezení do <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> vlastnosti jednoduchého typu a jednoduchý typ <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> `PhoneNumber` prvku.

4. Provede iteraci každého <xref:System.Xml.Schema.XmlSchemaElement> v <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekci kolekce post-Schema-Compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> .

5. Pokud <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> je element `"Customer"` , získá komplexní typ `Customer` elementu pomocí <xref:System.Xml.Schema.XmlSchemaComplexType> třídy a částice sekvence komplexního typu pomocí <xref:System.Xml.Schema.XmlSchemaSequence> třídy.

6. Přidá nový `PhoneNumber` prvek do sekvence obsahující existující `FirstName` prvky a pomocí kolekce předběžného `LastName` schématu kompilace <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> sekvence.

7. Nakonec znovu zpracuje a zkompiluje upravený <xref:System.Xml.Schema.XmlSchema> objekt pomocí <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metod a <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapíše jej do konzoly.

Následuje příklad kompletního příkladu kódu.

[!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
[!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
[!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]

Toto je upravené schéma zákazníka vytvořené v tématu [sestavování schémat XML](building-xml-schemas.md) .

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
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />
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

Tento druhý příklad kódu přidá nový `Title` atribut do `FirstName` elementu schématu zákazníka. V prvním příkladu kódu `FirstName` je typ elementu `xs:string` . `FirstName`Aby element měl atribut spolu s obsahem řetězce, musí být jeho typ změněn na komplexní typ s jednoduchým obsahem obsahu rozšíření obsahu.

Příklad kódu upravuje schéma zákazníka v následujících krocích.

1. Přidá schéma zákazníka do nového <xref:System.Xml.Schema.XmlSchemaSet> objektu a potom jej zkompiluje. Delegát zpracovává všechna upozornění ověřování schématu a chyby, ke kterým došlo při čtení nebo kompilování schématu <xref:System.Xml.Schema.ValidationEventHandler> .

2. Načte kompilovaný <xref:System.Xml.Schema.XmlSchema> objekt z rozhraní <xref:System.Xml.Schema.XmlSchemaSet> iterací přes <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost. Vzhledem k tomu, že schéma je kompilováno, jsou k dispozici vlastnosti po PSCI (post-Schema-Compilation-informační sada).

3. Vytvoří nový komplexní typ pro `FirstName` element pomocí <xref:System.Xml.Schema.XmlSchemaComplexType> třídy.

4. Vytvoří nové jednoduché rozšíření obsahu se základním typem `xs:string` , pomocí <xref:System.Xml.Schema.XmlSchemaSimpleContent> <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> tříd a.

5. Vytvoří nový `Title` atribut pomocí <xref:System.Xml.Schema.XmlSchemaAttribute> třídy s <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> `xs:string` a a přidá do jednoduchého rozšíření obsahu atribut.

6. Nastaví model obsahu jednoduchého obsahu na jednoduché rozšíření obsahu a model obsahu komplexního typu na jednoduchý obsah.

7. Přidá nový komplexní typ do kolekce předběžného schématu kompilace <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> .

8. Iteruje u každého <xref:System.Xml.Schema.XmlSchemaObject> v kolekci kompilace před schématy <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> .

> [!NOTE]
> Vzhledem k tomu, že `FirstName` element není globálním prvkem ve schématu, není k dispozici v <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekcích ani. Příklad kódu vyhledá `FirstName` element tak, že nejprve najde `Customer` element.
>
> První příklad kódu procházel schéma pomocí kolekce post-Schema-Compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> . V této ukázce <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> se k procházení schématu používá kolekce předběžného schématu kompilace. Zatímco obě kolekce poskytují přístup k globálním prvkům ve schématu, iterace v <xref:System.Xml.Schema.XmlSchema.Items%2A> kolekci je více časově náročná, protože je nutné iterovat všechny globální prvky ve schématu a nemá žádné vlastnosti pSCI. Kolekce pSCI ( <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> ,, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType> <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType> a tak dále) poskytují přímý přístup ke svým globálním prvkům, atributům a typům a jejich PSCIm vlastnostem.

1. Pokud <xref:System.Xml.Schema.XmlSchemaObject> je element, jehož <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> `"Customer"` typ je, získá komplexní typ `Customer` elementu pomocí <xref:System.Xml.Schema.XmlSchemaComplexType> třídy a částice sekvence komplexního typu pomocí <xref:System.Xml.Schema.XmlSchemaSequence> třídy.

2. Iteruje u každého <xref:System.Xml.Schema.XmlSchemaParticle> v kolekci kompilace před schématy <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> .

3. Pokud <xref:System.Xml.Schema.XmlSchemaParticle> je prvek, který <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> je `"FirstName"` , je nastaveno na <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> `FirstName` nový `FirstName` komplexní typ elementu.

4. Nakonec znovu zpracuje a zkompiluje upravený <xref:System.Xml.Schema.XmlSchema> objekt pomocí <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metod a <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapíše jej do konzoly.

Následuje příklad kompletního příkladu kódu.

[!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
[!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
[!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]

Toto je upravené schéma zákazníka vytvořené v tématu [sestavování schémat XML](building-xml-schemas.md) .

```xml
<?xml version="1.0" encoding=" utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />
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
  <xs:complexType name="FirstNameComplexType">     <xs:simpleContent>       <xs:extension base="xs:string">         <xs:attribute name="Title" type="xs:string" />       </xs:extension>     </xs:simpleContent>   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a>Viz také

- [Přehled Modelu objektu schématu XML](xml-schema-object-model-overview.md)
- [Čtení ze schémat XML a zápis do nich](reading-and-writing-xml-schemas.md)
- [Sestavování schémat XML](building-xml-schemas.md)
- [Procházení schémat XML](traversing-xml-schemas.md)
- [Zahrnutí nebo import schémat XML](including-or-importing-xml-schemas.md)
- [XmlSchemaSet pro kompilaci schématu](xmlschemaset-for-schema-compilation.md)
- [Informační sada po kompilaci schématu](post-schema-compilation-infoset.md)
