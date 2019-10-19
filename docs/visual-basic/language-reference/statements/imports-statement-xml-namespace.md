---
title: Příkaz Imports – obor názvů XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 0fca0caecfd69580510a539317856209108e5a32
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581770"
---
# <a name="imports-statement-xml-namespace"></a>Imports – Příkaz (obor názvů XML)

Importuje předpony oboru názvů XML pro použití v literálech XML a vlastnostech osy XML.

## <a name="syntax"></a>Syntaxe

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a>Součásti

`xmlNamespacePrefix`  
Volitelné. Řetězec, podle kterého mohou prvky a atributy XML odkazovat na `xmlNamespaceName`. Pokud není zadán žádný `xmlNamespacePrefix`, je importovaný obor názvů XML výchozím oborem názvů XML. Musí být platný identifikátor XML. Další informace najdete v tématu [Názvy deklarovaných elementů XML a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).

`xmlNamespaceName`  
Požadováno. Řetězec identifikující obor názvů XML, který se má importovat

## <a name="remarks"></a>Poznámky

Pomocí příkazu `Imports` můžete definovat globální obory názvů XML, které lze použít s literály XML a vlastnostmi osy XML, nebo jako parametry předané do operátoru `GetXmlNamespace`. (Informace o použití příkazu `Imports` pro import aliasu, který lze použít, kde se používají názvy typů ve vašem kódu, naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) Syntaxe pro deklaraci oboru názvů XML pomocí příkazu `Imports` je shodná se syntaxí použitou v jazyce XML. Proto můžete zkopírovat deklaraci oboru názvů ze souboru XML a použít ho v příkazu `Imports`.

Předpony oboru názvů XML jsou užitečné, pokud chcete opakovaně vytvářet elementy XML, které se nacházejí ve stejném oboru názvů. Předpona oboru názvů XML deklarovaná pomocí příkazu `Imports` je globální v tom smyslu, že je k dispozici pro veškerý kód v souboru. Můžete ji použít při vytváření literálů elementů XML a při přístupu k vlastnostem osy XML. Další informace naleznete v tématu vlastnosti [literálu elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) a [osy XML](../../../visual-basic/language-reference/xml-axis/index.md).

Definujete-li globální obor názvů XML bez předpony oboru názvů (například `Imports <xmlns="http://SomeNameSpace>"`), tento obor názvů je považován za výchozí obor názvů XML. Výchozí obor názvů XML se používá pro všechny literály elementu XML nebo vlastnosti osy atributu XML, které explicitně neurčují obor názvů. Výchozí obor názvů se používá také v případě, že zadaný obor názvů je prázdným oborem názvů (tj. `xmlns=""`). Výchozí obor názvů XML se nevztahuje na atributy XML v literálech XML nebo na Vlastnosti osy atributu XML, které nemají obor názvů.

Obory názvů XML, které jsou definovány v literálu XML, které se nazývají *místní obory názvů XML*, mají přednost před obory názvů XML, které jsou definovány příkazem `Imports` jako globální. Obory názvů XML, které jsou definovány příkazem `Imports`, mají přednost před obory názvů XML importovanými pro projekt Visual Basic. Pokud literál XML definuje obor názvů XML, tento místní obor názvů neplatí pro vložené výrazy.

Globální obory názvů XML dodržují stejná pravidla pro obor a definici jako obory názvů .NET Framework. V důsledku toho můžete zahrnout příkaz `Imports` pro definování globálního oboru názvů XML kdekoli můžete importovat .NET Framework obor názvů. To zahrnuje jak soubory kódu, tak importované obory názvů na úrovni projektu. Informace o importovaných oborech názvů na úrovni projektu naleznete na [stránce odkazy, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).

Každý zdrojový soubor může obsahovat libovolný počet příkazů `Imports`. Musí následovat po deklaracích možností, jako je například příkaz `Option Strict`, a musí předcházet deklarace programovacích prvků, jako jsou například `Module` nebo `Class` příkazy.

## <a name="example"></a>Příklad

Následující příklad importuje výchozí obor názvů XML a obor názvů XML identifikovaný předponou `ns`. Potom vytvoří literály XML, které používají oba obory názvů.

[!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]

Tento kód zobrazí následující text:

```xml
<ns:outer xmlns="http://DefaultNamespace"
          xmlns:ns="http://NewNamespace">
  <ns:innerElement></ns:innerElement>
  <siblingElement></siblingElement>
  <innerElement />
</ns:outer>
```

## <a name="example"></a>Příklad

Následující příklad importuje předponu oboru názvů XML `ns`. Potom vytvoří literál XML, který používá předponu oboru názvů a zobrazí konečný formulář elementu.

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

Všimněte si, že kompilátor převedl předponu oboru názvů XML z globální předpony na definici místní předpony.

## <a name="example"></a>Příklad

Následující příklad importuje předponu oboru názvů XML `ns`. Poté pomocí předpony oboru názvů vytvoří literál XML a přístup k prvnímu podřízenému uzlu s kvalifikovaným názvem `ns:name`.

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

Tento kód zobrazí následující text:

`Patrick Hines`

## <a name="see-also"></a>Viz také:

- [Literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [Operátor GetXmlNamespace](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
