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
ms.openlocfilehash: b2bf524214fa8ecca215d50c198b23d127e3b400
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349450"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>Vlastnost osy nástupce XML (Visual Basic)

Poskytuje přístup k následníkům následujících: objekt <xref:System.Xml.Linq.XElement>, objekt <xref:System.Xml.Linq.XDocument>, kolekci objektů <xref:System.Xml.Linq.XElement> nebo kolekci objektů <xref:System.Xml.Linq.XDocument>.

## <a name="syntax"></a>Syntaxe

```vb
object...<descendant>
```

## <a name="parts"></a>Součásti

`object` nutné. Objekt <xref:System.Xml.Linq.XElement>, objekt <xref:System.Xml.Linq.XDocument>, kolekce objektů <xref:System.Xml.Linq.XElement> nebo kolekce objektů <xref:System.Xml.Linq.XDocument>.

`...<` nutné. Označuje začátek vlastnosti následníka.

`descendant` nutné. Název potomkních uzlů, na které má být přístup, z formuláře [`prefix:]name`.

|Částí|Popis|
|----------|-----------------|
|`prefix`|Volitelná. Předpona oboru názvů XML pro podřízený uzel Musí se jednat o globální obor názvů XML, který je definován pomocí příkazu `Imports`.|
|`name`|Požadováno. Místní název odvozeného uzlu. Viz [Názvy deklarovaných elementů XML a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|

`>` nutné. Označuje konec vlastnosti odvozené osy.

## <a name="return-value"></a>Návratová hodnota

Kolekce objektů <xref:System.Xml.Linq.XElement>.

## <a name="remarks"></a>Poznámky

Vlastnost osy následníka XML můžete použít pro přístup k potomkovým uzlům podle názvu z <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objektu nebo z kolekce objektů <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>. Pro přístup k hodnotě prvního podřízeného uzlu ve vrácené kolekci použijte vlastnost `Value` XML. Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).

Kompilátor Visual Basic převádí vlastnosti následníka na volání metody <xref:System.Xml.Linq.XContainer.Descendants%2A>.

## <a name="xml-namespaces"></a>XML – obory názvů

Název v Vlastnosti osy následníka může používat pouze obory názvů XML deklarované globálně pomocí příkazu `Imports`. Nemůže používat obory názvů XML deklarované místně v rámci literálů elementů XML. Další informace naleznete v tématu [příkaz Imports (obor názvů XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak přistupovat k hodnotě prvního odvozeného uzlu s názvem `name` a hodnot všech potomkových uzlů s názvem `phone` z objektu `contacts`.

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

Tento kód zobrazí následující text:

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a>Příklad

Následující příklad deklaruje `ns` jako předponu oboru názvů XML. Poté pomocí předpony oboru názvů vytvoří literál XML a přistupuje k hodnotě prvního podřízeného uzlu s kvalifikovaným názvem `ns:name`.

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

Tento kód zobrazí následující text:

`Name: Patrick Hines`

## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement>
- [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytváření XML v Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
