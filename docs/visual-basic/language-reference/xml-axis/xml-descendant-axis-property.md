---
title: Vlastnost osy nástupce XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 52544619171dbc7034baeb5feb61395d81096387
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400250"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>Vlastnost osy nástupce XML (Visual Basic)

Poskytuje přístup k následníkům následujících objektů: <xref:System.Xml.Linq.XElement> objekt, <xref:System.Xml.Linq.XDocument> objekt, kolekce <xref:System.Xml.Linq.XElement> objektů nebo kolekce <xref:System.Xml.Linq.XDocument> objektů.

## <a name="syntax"></a>Syntaxe

```vb
object...<descendant>
```

## <a name="parts"></a>Součásti

`object`Požadovanou. <xref:System.Xml.Linq.XElement>Objekt, <xref:System.Xml.Linq.XDocument> objekt, kolekce <xref:System.Xml.Linq.XElement> objektů nebo kolekce <xref:System.Xml.Linq.XDocument> objektů.

`...<`Požadovanou. Označuje začátek vlastnosti následníka.

`descendant`Požadovanou. Název potomkních uzlů, které mají být přístupné, z formuláře [ `prefix:]name` .

|Část|Description|
|----------|-----------------|
|`prefix`|Nepovinný parametr. Předpona oboru názvů XML pro podřízený uzel Musí se jednat o globální obor názvů XML, který je definován pomocí `Imports` příkazu.|
|`name`|Povinná hodnota. Místní název odvozeného uzlu. Viz [Názvy deklarovaných elementů XML a atributů](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|

`>`Požadovanou. Označuje konec vlastnosti odvozené osy.

## <a name="return-value"></a>Návratová hodnota

Kolekce objektů <xref:System.Xml.Linq.XElement>.

## <a name="remarks"></a>Poznámky

Vlastnost osy následníka XML můžete použít pro přístup k potomkovým uzlům podle názvu <xref:System.Xml.Linq.XElement> z <xref:System.Xml.Linq.XDocument> objektu nebo nebo z kolekce <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objektů nebo. Použijte vlastnost XML `Value` pro přístup k hodnotě prvního podřízeného uzlu ve vrácené kolekci. Další informace najdete v tématu [vlastnost hodnoty XML](xml-value-property.md).

Kompilátor Visual Basic převádí vlastnosti následníka na volání <xref:System.Xml.Linq.XContainer.Descendants%2A> metody.

## <a name="xml-namespaces"></a>XML – obory názvů

Název v Vlastnosti osy následníka může použít pouze obory názvů XML deklarované globálně s `Imports` příkazem. Nemůže používat obory názvů XML deklarované místně v rámci literálů elementů XML. Další informace naleznete v tématu [příkaz Imports (obor názvů XML)](../statements/imports-statement-xml-namespace.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak přistupovat k hodnotě prvního odvozeného uzlu s názvem `name` a hodnoty všech potomkních uzlů s názvem `phone` z `contacts` objektu.

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

Tento kód zobrazí následující text:

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a>Příklad

Následující příklad deklaruje `ns` jako předponu oboru názvů XML. Poté pomocí předpony oboru názvů vytvoří literál XML a přistupuje k hodnotě prvního podřízeného uzlu s kvalifikovaným názvem `ns:name` .

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

Tento kód zobrazí následující text:

`Name: Patrick Hines`

## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XElement>
- [Vlastnosti osy XML](index.md)
- [Literály XML](../xml-literals/index.md)
- [Vytvoření XML v jazyce Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Názvy deklarovaných XML elementů a atributů](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
