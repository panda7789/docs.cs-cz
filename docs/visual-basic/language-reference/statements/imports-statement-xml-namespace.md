---
title: Imports – Příkaz (obor názvů XML)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: ba7475416d8a4e2eb3c892d457c03eeb695045eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604559"
---
# <a name="imports-statement-xml-namespace"></a>Imports – Příkaz (obor názvů XML)
Importuje předpon oboru názvů XML pro použití v literály XML a vlastnosti osy XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a>Součásti  
 `xmlNamespacePrefix`  
 Volitelné. Řetězec, ve které XML elementů a atributů může odkazovat na `xmlNamespaceName`. Pokud žádné `xmlNamespacePrefix` je uvedený importované obor názvů XML je výchozí obor názvů XML. Musí být platný identifikátor XML. Další informace najdete v tématu [názvy z deklarovaný XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).  
  
 `xmlNamespaceName`  
 Požadováno. Řetězec identifikující importovaných obor názvů XML.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `Imports` příkaz k definování globální obory názvů XML, který můžete použít s literály XML a vlastnosti osy XML nebo jako parametry předat `GetXmlNamespace` operátor. (Informace o používání `Imports` příkaz pro import alias, který je možné, kdy se používá název typu ve vašem kódu najdete v části [příkaz Imports (Namespace .NET a typ)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) Syntaxe deklarace oboru názvů XML s použitím `Imports` příkaz je shodná se syntaxí používá v kódu XML. Proto můžete zkopírovat deklaraci oboru názvů ze souboru XML a použít ho `Imports` příkaz.  
  
 XML – předpony oboru názvů jsou užitečné, pokud chcete vytvořit opakovaně elementů XML, které jsou ze stejného oboru názvů. Předpona oboru názvů XML deklarovat s `Imports` příkaz je globální v tom smyslu, že je k dispozici všechny kód v souboru. Můžete ho použít při vytváření element literály XML a při přístup k vlastnosti osy XML. Další informace najdete v tématu [literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) a [vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).  
  
 Pokud definujete globální obor názvů XML bez předpony oboru názvů (například `Imports <xmlns="http://SomeNameSpace>"`), tento obor názvů se považuje za výchozí obor názvů XML. U elementu XML – literály nebo vlastnosti osy atributu XML, které explicitně nezadávejte obor názvů se používá výchozí obor názvů XML. Výchozí obor názvů se také používá, pokud je zadaný obor názvů prázdného oboru názvů (tedy `xmlns=""`). Výchozí obor názvů XML nevztahuje atributům XML v literálech XML a vlastnosti osy atributu XML, které nemají obor názvů.  
  
 XML obory názvů, které jsou definovány v XML literálu, které se nazývají *místní obory názvů XML*, mají přednost před obory názvů XML, které jsou definovány `Imports` příkaz jako globální. Obory názvů XML, které jsou definovány `Imports` příkaz mají přednost před obory názvů XML importu projektu jazyka Visual Basic. Pokud literál XML definuje obor názvů XML, že místní obor názvů se nevztahuje na vložené výrazy.  
  
 Globální obory názvů XML použijte stejná nastavení oboru a definice pravidla jako obory názvů v rozhraní .NET Framework. V důsledku toho můžete použít `Imports` příkaz k definování globální obor názvů XML kdekoli můžete importovat obor názvů rozhraní .NET Framework. To zahrnuje soubory kódu a importovaných oborů názvů úrovni projektu. Informace o úrovni projektu importovaných oborů názvů najdete v tématu [stránka odkazy, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).  
  
 Každý zdrojový soubor může obsahovat libovolný počet `Imports` příkazy. Tyto postupujte možnost deklarace, jako `Option Strict` příkaz a musí předcházet programovací element deklarace, jako například `Module` nebo `Class` příkazy.  
  
## <a name="example"></a>Příklad  
 Následující příklad importuje výchozí obor názvů XML a označeny předponu oboru názvů XML `ns`. Pak vytvoří literálů XML, které používají oba obory názvů.  
  
 [!code-vb[VbXMLSamples#45](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]  
  
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
 Následující příklad importuje Předpona oboru názvů XML `ns`. Pak vytvoří literálu kód XML, který používá Předpona oboru názvů a zobrazí poslední formulář elementu.  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]  
  
 Tento kód zobrazí následující text:  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 Všimněte si, že kompilátor převést Předpona oboru názvů XML z globální předpony na definici místní předponu.  
  
## <a name="example"></a>Příklad  
 Následující příklad importuje Předpona oboru názvů XML `ns`. Poté použije Předpona oboru názvů k vytvoření literál XML a přístup k první podřízený uzel s kvalifikovaný název `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]  
  
 Tento kód zobrazí následující text:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Viz také  
 [Literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [Názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [Operátor GetXmlNamespace](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
