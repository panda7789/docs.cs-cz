---
title: Literál XML elementu
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: d6a91de4e279816bafd29f46bb4f5422cbd934ff
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400186"
---
# <a name="xml-element-literal-visual-basic"></a>Literál XML elementu (Visual Basic)

Literál, který představuje <xref:System.Xml.Linq.XElement> objekt.

## <a name="syntax"></a>Syntaxe

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a>Součásti

- `<`

  Povinná hodnota. Otevře značku počátečního elementu.

- `name`

  Povinná hodnota. Název elementu. Formát je jeden z následujících:

  - Textový literál pro název prvku formuláře `[ePrefix:]eName` , kde:

    |Část|Description|
    |---|---|
    |`ePrefix`|Nepovinný parametr. Předpona oboru názvů XML pro element. Musí se jednat o globální obor názvů XML, který je definován pomocí `Imports` příkazu v souboru nebo na úrovni projektu, nebo místní obor názvů XML, který je definován v tomto elementu nebo v nadřazeném elementu.|
    |`eName`|Povinná hodnota. Název elementu. Formát je jeden z následujících:<br /><br /> -Literal text. Viz [Názvy deklarovaných elementů XML a atributů](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />– Vložený výraz formuláře `<%= eNameExp %>` . Typ `eNameExp` musí být `String` nebo typ, který je implicitně převoditelný na <xref:System.Xml.Linq.XName> .|

  - Vložený `<%= nameExp %>` výraz formuláře Typ `nameExp` musí být `String` nebo typ, který lze implicitně převést na <xref:System.Xml.Linq.XName> . Vložený výraz není povolený v uzavírací značce elementu.

- `attributeList`

  Nepovinný parametr. Seznam atributů deklarovaných v literálu

  `attribute [ attribute ... ]`

  Každá `attribute` z nich má jednu z následujících syntaxí:

  - Přiřazení atributu formuláře `[aPrefix:]aName=aValue` , kde:

    |Část|Description|
    |---|---|
    |`aPrefix`|Nepovinný parametr. Předpona oboru názvů XML pro atribut Musí se jednat o globální obor názvů XML, který je definován pomocí `Imports` příkazu, nebo místní obor názvů XML, který je definován v tomto elementu nebo v nadřazeném elementu.|
    |`aName`|Povinná hodnota. Název atributu Formát je jeden z následujících:<br /><br /> -Literal text. Viz [Názvy deklarovaných elementů XML a atributů](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />– Vložený výraz formuláře `<%= aNameExp %>` . Typ `aNameExp` musí být `String` nebo typ, který je implicitně převoditelný na <xref:System.Xml.Linq.XName> .|
    |`aValue`|Nepovinný parametr. Hodnota atributu Formát je jeden z následujících:<br /><br /> -Literal text uzavřený v uvozovkách.<br />– Vložený výraz formuláře `<%= aValueExp %>` . Je povolen libovolný typ.|

  - Vložený `<%= aExp %>` výraz formuláře

- `/>`

  Nepovinný parametr. Označuje, že element je prázdný prvek bez obsahu.

- `>`

  Povinná hodnota. Ukončí značku začátku nebo prázdného prvku.

- `elementContents`

  Nepovinný parametr. Obsah elementu

  `content [ content ... ]`

  Každá `content` z těchto možností může být jedna z následujících:

  - Textový literál Všechny prázdné znaky v `elementContents` je významné, pokud existuje nějaký literálový text.

  - Vložený `<%= contentExp %>` výraz formuláře

  - Literál elementu XML.

  - Literál komentáře XML Viz [literál komentáře XML](xml-comment-literal.md).

  - Literál instrukcí pro zpracování XML Viz [literál instrukcí pro zpracování XML](xml-processing-instruction-literal.md).

  - Literál XML CDATA. Viz [literál XML CDATA](xml-cdata-literal.md).

- `</[name]>`

  Nepovinný parametr. Představuje uzavírací značku elementu. Volitelný `name` parametr není povolen, pokud je výsledkem vloženého výrazu.

## <a name="return-value"></a>Návratová hodnota

Objekt <xref:System.Xml.Linq.XElement>.

## <a name="remarks"></a>Poznámky

Můžete použít syntaxi literálu elementu XML k vytvoření <xref:System.Xml.Linq.XElement> objektů ve vašem kódu.

> [!NOTE]
> Literál XML může zahrnovat více řádků bez použití znaků pro pokračování řádku. Tato funkce umožňuje kopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.

Vložené výrazy formuláře `<%= exp %>` umožňují přidat dynamické informace k literálu elementu XML. Další informace najdete v tématu [vložené výrazy v XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).

Kompilátor Visual Basic převádí literál elementu XML na volání <xref:System.Xml.Linq.XElement.%23ctor%2A> konstruktoru a, pokud je požadován, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> konstruktor.

## <a name="xml-namespaces"></a>XML – obory názvů

Předpony oboru názvů XML jsou užitečné v případě, že je nutné vytvořit literály XML s prvky ze stejného oboru názvů, kolikrát je kód. Můžete použít globální předpony oboru názvů XML, které definujete pomocí `Imports` příkazu, nebo místní předpony, které definujete pomocí `xmlns:xmlPrefix="xmlNamespace"` syntaxe atributu. Další informace naleznete v tématu [příkaz Imports (obor názvů XML)](../statements/imports-statement-xml-namespace.md).

V souladu s pravidly oboru názvů XML mají místní předpony přednost před globálními předponami. Pokud však literál XML definuje obor názvů XML, tento obor názvů není k dispozici pro výrazy, které se zobrazí ve vloženém výrazu. Vložený výraz má přístup pouze k globálnímu oboru názvů XML.

Kompilátor Visual Basic převádí všechny globální obory názvů XML, které jsou používány literály XML, do jedné definice místního oboru názvů v generovaném kódu. Globální obory názvů XML, které se nepoužívají, se ve vygenerovaném kódu nezobrazí.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit jednoduchý element XML, který má dva vnořené prázdné prvky.

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

V příkladu se zobrazí následující text. Všimněte si, že literál zachovává strukturu prázdných prvků.

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít vložené výrazy k pojmenování elementu a vytváření atributů.

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

Tento kód zobrazí následující text:

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a>Příklad

Následující příklad deklaruje `ns` jako předponu oboru názvů XML. Potom používá předponu oboru názvů k vytvoření literálu XML a zobrazí konečný formulář elementu.

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

Tento kód zobrazí následující text:

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

Všimněte si, že kompilátor převedl předponu globálního oboru názvů XML do definice předpony pro obor názvů XML. \<ns:middle>Element předefinuje předponu oboru názvů XML pro \<ns:inner1> element. \<ns:inner2>Element však používá obor názvů definovaný `Imports` příkazem.

## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XElement>
- [Názvy deklarovaných XML elementů a atributů](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [Literál komentáře XML](xml-comment-literal.md)
- [Literál XML CDATA](xml-cdata-literal.md)
- [Literály XML](index.md)
- [Vytvoření XML v jazyce Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Vložené výrazy v XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Imports – Příkaz (obor názvů XML)](../statements/imports-statement-xml-namespace.md)
