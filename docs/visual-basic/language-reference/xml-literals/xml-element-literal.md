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
ms.openlocfilehash: 55d5d1410a65ea8c800bbd2b310907a6d6a61c61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
  
     Požadováno. Otevře se počáteční značky elementu.  
  
-   `name`  
  
     Požadováno. Název elementu. Formát je jedním z těchto:  
  
    -   Literál text pro název elementu, formuláře `[ePrefix:]eName`, kde:  
  
        |Část|Popis|  
        |---|---|  
        |`ePrefix`|Volitelné. Předpona oboru názvů XML pro element. Musí být globální obor názvů XML, který je definován s `Imports` příkaz v souboru nebo na úrovni projektu nebo místní obor názvů XML, který je definován v tento element nebo nadřazený element.|  
        |`eName`|Požadováno. Název elementu. Formát je jedním z těchto:<br /><br /> – Text literál. V tématu [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Vložených výrazu ve formátu `<%= eNameExp %>`. Typ `eNameExp` musí být `String` , nebo je implicitně převést na typ <xref:System.Xml.Linq.XName>.|  
  
    -   Vložené výrazu ve formátu `<%= nameExp %>`. Typ `nameExp` musí být `String` nebo implicitně převést na typ <xref:System.Xml.Linq.XName>. Vložené výraz není povolen v uzavírací značka elementu.  
  
-   `attributeList`  
  
     Volitelné. Seznam atributů deklarované v literál.  
  
     `attribute [ attribute ... ]`  
  
     Každý `attribute` obsahuje jednu z následujících syntaxí:  
  
    -   Atribut přiřazení formuláře `[aPrefix:]aName=aValue`, kde:  
  
        |Část|Popis|  
        |---|---|  
        |`aPrefix`|Volitelné. Předpona oboru názvů XML pro atribut. Musí být globální obor názvů XML, který je definován s `Imports` příkaz nebo místní obor názvů XML, který je definován v tento element nebo nadřazený element.|  
        |`aName`|Požadováno. Název atributu. Formát je jedním z těchto:<br /><br /> – Text literál. V tématu [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Vložených výrazu ve formátu `<%= aNameExp %>`. Typ `aNameExp` musí být `String` , nebo je implicitně převést na typ <xref:System.Xml.Linq.XName>.|  
        |`aValue`|Volitelné. Hodnota atributu. Formát je jedním z těchto:<br /><br /> -Literálu textu v uvozovkách.<br />-Vložených výrazu ve formátu `<%= aValueExp %>`. Je povolen libovolný typ.|  
  
    -   Vložené výrazu ve formátu `<%= aExp %>`.  
  
-   `/>`  
  
     Volitelné. Označuje, že element je prázdný element, bez obsahu.  
  
-   `>`  
  
     Požadováno. Ukončí značky elementu počáteční nebo je prázdný.  
  
-   `elementContents`  
  
     Volitelné. Obsah elementu.  
  
     `content [ content ... ]`  
  
     Každý `content` může být jedna z následujících akcí:  
  
    -   Literál text. Prázdné znaky v `elementContents` stane důležité, pokud je literál textu.  
  
    -   Vložené výrazu ve formátu `<%= contentExp %>`.  
  
    -   Literál XML elementu.  
  
    -   Literál komentáře XML. V tématu [literál komentáře XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).  
  
    -   XML literál instrukcí pro zpracování. V tématu [literál instrukcí pro zpracování XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).  
  
    -   Literál XML CDATA. V tématu [literál XML CDATA](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).  
  
-   `</[name]>`  
  
     Volitelné. Představuje koncová značka elementu. Volitelné `name` parametr není povolen, pokud je výsledkem výrazu embedded.  
  
## <a name="return-value"></a>Návratová hodnota  
 <xref:System.Xml.Linq.XElement> Objektu.  
  
## <a name="remarks"></a>Poznámky  
 Syntaxe literál XML elementu slouží k vytvoření <xref:System.Xml.Linq.XElement> objekty v kódu.  
  
> [!NOTE]
>  Literál XML může zahrnovat více řádků bez použití znaky pokračování řádku. Tato funkce umožňuje kopírovat obsah z dokumentu XML a vložte jej přímo do programu Visual Basic.  
  
 Vložené výrazy ve tvaru `<%= exp %>` vám umožní přidat dynamické informace literál XML elementu. Další informace najdete v tématu [vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Visual Basic – kompilátor převede literál XML elementu volání <xref:System.Xml.Linq.XElement.%23ctor%2A> konstruktor a pokud se vyžaduje, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> konstruktor.  
  
## <a name="xml-namespaces"></a>Obory názvů XML  
 XML – předpony oboru názvů jsou užitečné při vytváření literálů XML s elementy ze stejného oboru názvů mnohokrát v kódu. Můžete použít globální předpony oboru názvů XML, které definují pomocí `Imports` příkaz nebo místní předpony, které definují pomocí `xmlns:xmlPrefix="xmlNamespace"` atribut syntaxe. Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
 Místní předpony v souladu s oboru pravidla pro obory názvů XML, mají přednost před globální předpony. Ale pokud literál XML definuje obor názvů XML, tento obor názvů není k dispozici na výrazy, které se zobrazují v embedded výrazu. Vložené výraz můžete přistupovat pouze globální obor názvů XML.  
  
 Visual Basic – kompilátor převede každý globální obor názvů XML, který je používán literál XML do jednu definici místní obor názvů v generovaného kódu. Globální obory názvů XML, které nepoužívají se nezobrazí v generovaného kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit jednoduché element XML, který má dva vnořené prázdné prvky.  
  
 [!code-vb[VbXMLSamples#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]  
  
 V příkladu se zobrazí následující text. Všimněte si, že je literál zachovává strukturu prázdné prvky.  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat vložené výrazy k názvu elementu a vytvořte atributy.  
  
 [!code-vb[VbXMLSamples#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]  
  
 Tento kód zobrazí následující text:  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje `ns` jako předponu oboru názvů XML. Poté používá předponu oboru názvů k vytvoření literál XML a zobrazí poslední formulář elementu.  
  
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
  
 Všimněte si, že kompilátor převést předponu globální obor názvů XML do definice předponu pro obor názvů XML. \<Ns:middle > přináší Předpona oboru názvů XML pro element \<ns:inner1 > elementu. Ale \<ns:inner2 > element používá obor názvů definované `Imports` příkaz.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XElement>  
 [Názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [Literál komentáře XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [Literál XML CDATA](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)  
 [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Příkaz Imports (obor názvů XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
