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
ms.openlocfilehash: d6d900ca6868cfffe6b0e5b349321a79c5716c46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347031"
---
# <a name="xml-element-literal-visual-basic"></a>Literál XML elementu (Visual Basic)

Literál, který představuje objekt <xref:System.Xml.Linq.XElement>.

## <a name="syntax"></a>Syntaxe

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a>Součásti

- `<`

  Požadováno. Otevře značku počátečního elementu.

- `name`

  Požadováno. Název elementu. Formát je jeden z následujících:

  - Textový literál pro název prvku `[ePrefix:]eName`formuláře, kde:

    |Částí|Popis|
    |---|---|
    |`ePrefix`|Volitelná. Předpona oboru názvů XML pro element. Musí být globální obor názvů XML, který je definován pomocí příkazu `Imports` v souboru nebo na úrovni projektu, nebo místní obor názvů XML, který je definován v tomto elementu nebo v nadřazeném elementu.|
    |`eName`|Požadováno. Název elementu. Formát je jeden z následujících:<br /><br /> -Literal text. Viz [Názvy deklarovaných elementů XML a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />– Vložený výraz formuláře `<%= eNameExp %>`. Typ `eNameExp` musí být `String` nebo typ, který lze implicitně převést na <xref:System.Xml.Linq.XName>.|

  - Vložený výraz formuláře `<%= nameExp %>`. Typ `nameExp` musí být `String` nebo typ implicitně převoditelné na <xref:System.Xml.Linq.XName>. Vložený výraz není povolený v uzavírací značce elementu.

- `attributeList`

  Volitelná. Seznam atributů deklarovaných v literálu

  `attribute [ attribute ... ]`

  Každý `attribute` má jednu z následujících syntaxí:

  - Přiřazení atributu `[aPrefix:]aName=aValue`formuláře, kde:

    |Částí|Popis|
    |---|---|
    |`aPrefix`|Volitelná. Předpona oboru názvů XML pro atribut Musí být globální obor názvů XML, který je definován pomocí příkazu `Imports`, nebo místní obor názvů XML, který je definován v tomto elementu nebo v nadřazeném elementu.|
    |`aName`|Požadováno. Název atributu Formát je jeden z následujících:<br /><br /> -Literal text. Viz [Názvy deklarovaných elementů XML a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />– Vložený výraz formuláře `<%= aNameExp %>`. Typ `aNameExp` musí být `String` nebo typ, který lze implicitně převést na <xref:System.Xml.Linq.XName>.|
    |`aValue`|Volitelná. Hodnota atributu Formát je jeden z následujících:<br /><br /> -Literal text uzavřený v uvozovkách.<br />– Vložený výraz formuláře `<%= aValueExp %>`. Je povolen libovolný typ.|

  - Vložený výraz formuláře `<%= aExp %>`.

- `/>`

  Volitelná. Označuje, že element je prázdný prvek bez obsahu.

- `>`

  Požadováno. Ukončí značku začátku nebo prázdného prvku.

- `elementContents`

  Volitelná. Obsah elementu

  `content [ content ... ]`

  Každá `content` může být jedna z následujících:

  - Textový literál Všechny prázdné znaky v `elementContents` budou významné, pokud je nějaký textový literál.

  - Vložený výraz formuláře `<%= contentExp %>`.

  - Literál elementu XML.

  - Literál komentáře XML Viz [literál komentáře XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).

  - Literál instrukcí pro zpracování XML Viz [literál instrukcí pro zpracování XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).

  - Literál XML CDATA. Viz [literál XML CDATA](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).

- `</[name]>`

  Volitelná. Představuje uzavírací značku elementu. Nepovinný parametr `name` není povolený, pokud se jedná o výsledek vloženého výrazu.

## <a name="return-value"></a>Návratová hodnota

Objekt <xref:System.Xml.Linq.XElement>.

## <a name="remarks"></a>Poznámky

Můžete použít syntaxi literálu elementu XML k vytvoření <xref:System.Xml.Linq.XElement> objektů ve vašem kódu.

> [!NOTE]
> Literál XML může zahrnovat více řádků bez použití znaků pro pokračování řádku. Tato funkce umožňuje kopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.

Vložené výrazy formuláře `<%= exp %>` umožňují přidat dynamické informace do literálu elementu XML. Další informace najdete v tématu [vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).

Kompilátor Visual Basic převádí literál elementu XML na volání konstruktoru <xref:System.Xml.Linq.XElement.%23ctor%2A> a v případě potřeby konstruktor <xref:System.Xml.Linq.XAttribute.%23ctor%2A>.

## <a name="xml-namespaces"></a>XML – obory názvů

Předpony oboru názvů XML jsou užitečné v případě, že je nutné vytvořit literály XML s prvky ze stejného oboru názvů, kolikrát je kód. Můžete použít globální předpony oboru názvů XML, které definujete pomocí příkazu `Imports`, nebo místní předpony, které definujete pomocí `xmlns:xmlPrefix="xmlNamespace"` syntaxe atributu. Další informace naleznete v tématu [příkaz Imports (obor názvů XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).

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

Všimněte si, že kompilátor převedl předponu globálního oboru názvů XML do definice předpony pro obor názvů XML. Element \<NS: Middle > předefinuje předponu oboru názvů XML pro element \<NS: inner1 >. Nicméně element \<NS: inner2 > používá obor názvů definovaný příkazem `Imports`.

## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement>
- [Názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [Literál komentáře XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [Literál XML CDATA](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytváření XML v Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Příkaz Imports (obor názvů XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
