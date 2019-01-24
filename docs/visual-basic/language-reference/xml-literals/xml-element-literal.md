---
title: Literál XML elementu (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: 54ad162a1a720a1645a3b413e6518d2ccfd37bbe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595913"
---
# <a name="xml-element-literal-visual-basic"></a>Literál XML elementu (Visual Basic)

Literál, který představuje <xref:System.Xml.Linq.XElement> objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a>Součásti  
  
-   `<`  
  
     Povinný parametr. Otevře se počáteční značky elementu.  
  
-   `name`  
  
     Povinný parametr. Název elementu. Formát je jeden z následujících akcí:  
  
    -   Prostý text pro název elementu, formuláře `[ePrefix:]eName`, kde:  
  
        |Část|Popis|  
        |---|---|  
        |`ePrefix`|Volitelné. Předpona oboru názvů XML pro prvek. Musí být globální obor názvů XML, který je definován s `Imports` prohlášení v souboru nebo na úrovni projektu, nebo místní obor názvů XML, který je definován v tomto elementu nebo nadřazený element.|  
        |`eName`|Povinný parametr. Název elementu. Formát je jeden z následujících akcí:<br /><br /> -Prostý text. Zobrazit [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />– Vložený výraz ve tvaru `<%= eNameExp %>`. Typ `eNameExp` musí být `String` nebo typ, který je implicitně převést na <xref:System.Xml.Linq.XName>.|  
  
    -   Vložený výraz ve tvaru `<%= nameExp %>`. Typ `nameExp` musí být `String` nebo implicitně převést na typ <xref:System.Xml.Linq.XName>. Vložený výraz není povolen v ukončovací značky elementu.  
  
-   `attributeList`  
  
     Volitelné. Seznam atributů deklarované v literálu.  
  
     `attribute [ attribute ... ]`  
  
     Každý `attribute` má jednu z následujících syntaxí:  
  
    -   Atribut přiřazení formuláře `[aPrefix:]aName=aValue`, kde:  
  
        |Část|Popis|  
        |---|---|  
        |`aPrefix`|Volitelné. Předpona oboru názvů XML pro atribut. Musí být globální obor názvů XML, který je definován s `Imports` příkazu nebo místní obor názvů XML, který je definován v tomto elementu nebo nadřazený element.|  
        |`aName`|Povinný parametr. Název atributu. Formát je jeden z následujících akcí:<br /><br /> -Prostý text. Zobrazit [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />– Vložený výraz ve tvaru `<%= aNameExp %>`. Typ `aNameExp` musí být `String` nebo typ, který je implicitně převést na <xref:System.Xml.Linq.XName>.|  
        |`aValue`|Volitelné. Hodnota atributu. Formát je jeden z následujících akcí:<br /><br /> – Literál textu v uvozovkách.<br />– Vložený výraz ve tvaru `<%= aValueExp %>`. Jakýkoli typ je povolen.|  
  
    -   Vložený výraz ve tvaru `<%= aExp %>`.  
  
-   `/>`  
  
     Volitelné. Určuje, zda elementu je prázdný element, bez obsahu.  
  
-   `>`  
  
     Povinný parametr. Ukončí značky elementu počáteční nebo je prázdný.  
  
-   `elementContents`  
  
     Volitelné. Obsah elementu.  
  
     `content [ content ... ]`  
  
     Každý `content` může být jedna z následujících akcí:  
  
    -   Prostý text. Všechny prázdné znaky v `elementContents` stane, když je text literálu.  
  
    -   Vložený výraz ve tvaru `<%= contentExp %>`.  
  
    -   Literál XML elementu.  
  
    -   Literál komentáře XML. Zobrazit [literál komentáře XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).  
  
    -   XML literál instrukcí pro zpracování. Zobrazit [literál instrukcí pro zpracování XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).  
  
    -   Literál XML CDATA. Zobrazit [literál XML CDATA](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).  
  
-   `</[name]>`  
  
     Volitelné. Představuje uzavírací značka pro element. Volitelný `name` parametr není povolený. Pokud bude výsledek vložený výraz.  
  
## <a name="return-value"></a>Návratová hodnota  
 <xref:System.Xml.Linq.XElement> Objektu.  
  
## <a name="remarks"></a>Poznámky  
 Syntaxe literál – element XML slouží k vytvoření <xref:System.Xml.Linq.XElement> objektů ve vašem kódu.  
  
> [!NOTE]
>  Literál XML může zahrnovat více řádků bez použití znaků pokračování řádku. Tato funkce umožňuje kopírovat obsah z dokumentu XML a vložte ho přímo do programu Visual Basic.  
  
 Vložené výrazy formuláře `<%= exp %>` vám umožní přidat dynamické informace do literálů XML element. Další informace najdete v tématu [vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Kompilátor jazyka Visual Basic převede literál XML elementu na volání <xref:System.Xml.Linq.XElement.%23ctor%2A> konstruktor a je-li vyžadován, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> konstruktoru.  
  
## <a name="xml-namespaces"></a>Obory názvů XML  
 Předpony oboru názvů XML jsou užitečné, když máte k vytváření literálů XML s prvky z stejný obor názvů v mnoha případech v kódu. Můžete použít globální předpony oboru názvů XML, které definujete pomocí `Imports` příkazu nebo místní předpony, které definujete pomocí `xmlns:xmlPrefix="xmlNamespace"` syntaxe atributu. Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
 V souladu s pravidla oboru oborů názvů XML má místní předpony přednost před globální předpony. Ale pokud literál XML definuje obor názvů XML, tento obor názvů není k dispozici na výrazy, které se zobrazují v vložený výraz. Vložený výraz můžete přistupovat pouze globální obor názvů XML.  
  
 Kompilátor jazyka Visual Basic převede každý globální obor názvů XML, který používá literál XML do jedné definice místní obor názvů v generovaném kódu. Globálními názvovými prostory XML, které se nepoužívají se nezobrazují v generovaném kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit jednoduchý prvek XML, který má dvě vnořené prázdné prvky.  
  
 [!code-vb[VbXMLSamples#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]  
  
 V příkladu se zobrazí následující text. Všimněte si, že je literál zachovává strukturu prázdné prvky.  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat vložené výrazy pro název elementu a vytvořit atributy.  
  
 [!code-vb[VbXMLSamples#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]  
  
 Tento kód zobrazí následující text:  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje `ns` jako předponu oboru názvů XML. Potom k vytvoření literálu XML používá předponu oboru názvů a zobrazí poslední formulář elementu.  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]  
  
 Tento kód zobrazí následující text:  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 Všimněte si, že kompilátor převést předponu globálního oboru názvů XML na definici předpony oboru názvů XML. \<Ns:middle > předefinuje předponu oboru názvů XML pro prvek \<ns:inner1 > element. Ale \<ns:inner2 > element používá obor názvů definovaný smyčkou `Imports` příkazu.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Xml.Linq.XElement>
- [Názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [Literál komentáře XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [Literál XML CDATA](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Příkaz Imports (obor názvů XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
