---
title: Vlastnost osy nástupce XML (Visual Basic)
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
ms.openlocfilehash: bc1dff6dc3b580079087f370212b7d3acd30e4fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938668"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>Vlastnost osy nástupce XML (Visual Basic)

Poskytuje přístup k následníky z následujících akcí: <xref:System.Xml.Linq.XElement> objektu, <xref:System.Xml.Linq.XDocument> object, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.

## <a name="syntax"></a>Syntaxe

```
object...<descendant>
```

## <a name="parts"></a>Součásti

`object` Povinné. <xref:System.Xml.Linq.XElement> Objekt, <xref:System.Xml.Linq.XDocument> object, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.

`...<` Povinné. Označuje začátek vlastnost Následnické osy.

`descendant` Povinné. Název podřízených uzlů pro přístup k ve tvaru [`prefix:]name`.

|Část|Popis|
|----------|-----------------|
|`prefix`|Volitelné. Předpona oboru názvů XML pro uzel potomka. Musí být globální obor názvů XML, který je definován s použitím `Imports` příkazu.|
|`name`|Povinný parametr. Místní název uzel potomka. Zobrazit [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|

`>` Povinné. Označuje konec vlastnost Následnické osy.

## <a name="return-value"></a>Návratová hodnota

Kolekce <xref:System.Xml.Linq.XElement> objekty.

## <a name="remarks"></a>Poznámky

Můžete použít vlastnost osy nástupce XML pro přístup k následnickým uzlů podle názvu ze <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objektu, nebo z kolekce <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekty. Použít XML `Value` pro přístup k hodnotě první uzel potomka v kolekci vrácené vlastností. Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).

Kompilátor jazyka Visual Basic převede vlastnosti osy nástupce na volání <xref:System.Xml.Linq.XContainer.Descendants%2A> metody.

## <a name="xml-namespaces"></a>Obory názvů XML

Název v vlastnost Následnické osy můžete použít pouze obory názvů XML globálně deklarované s `Imports` příkazu. Místně deklarované v rámci elementu literály XML obory názvů XML nemůže používat. Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak přistupovat k hodnotě prvního následníky uzel s názvem `name` a hodnoty všech podřízených uzlů s názvem `phone` z `contacts` objektu.

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

Tento kód zobrazí následující text:

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a>Příklad

Následující příklad deklaruje `ns` jako předponu oboru názvů XML. Poté použije předponu oboru názvů k vytvoření literálu XML a přistupovat k hodnotě první podřízený uzel s kvalifikovaným názvem `ns:name`.

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

Tento kód zobrazí následující text:

`Name: Patrick Hines`

## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement>
- [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
