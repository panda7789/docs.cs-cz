---
title: Imports – příkaz - Namespace XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 97d08113a37477add9d770b0a680c303fe7e3040
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638954"
---
# <a name="imports-statement-xml-namespace"></a>Imports – Příkaz (obor názvů XML)
Importuje předpon názvového prostoru XML pro použití v literály XML a vlastnosti OS XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a>Součásti  
 `xmlNamespacePrefix`  
 Volitelné. Řetězec, ve které XML elementů a atributů mohou odkazovat na `xmlNamespaceName`. Pokud ne `xmlNamespacePrefix` je zadán, importované oboru názvů XML je výchozí obor názvů XML. Musí být platný identifikátor XML. Další informace najdete v tématu [názvy z deklarované XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).  
  
 `xmlNamespaceName`  
 Povinný parametr. Řetězec, který identifikuje importované oboru názvů XML.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `Imports` příkaz k definování globálními názvovými prostory XML, který vám pomůže s literály XML a vlastnosti OS XML, nebo jako parametry předat `GetXmlNamespace` operátor. (Další informace o použití `Imports` smlouvu pro import alias, který je možné, kde se používají názvy typů ve vašem kódu, naleznete v tématu [příkaz Imports (Namespace .NET a typ)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) Syntaxe pro deklarování obor názvů XML s použitím `Imports` příkaz je stejná jako syntaxe používané ve formátu XML. Proto, můžete zkopírovat deklarace oboru názvů ze souboru XML a použít ho `Imports` příkazu.  
  
 Předpony oboru názvů XML jsou užitečné, pokud chcete vytvořit opakovaně elementů XML, které pocházejí ze stejného oboru názvů. Předpona oboru názvů XML deklarována s `Imports` příkaz je globální v tom smyslu, že je k dispozici pro všechen kód v souboru. Můžete ho používat při vytváření elementu literály XML a při přístupu k vlastnosti osy XML. Další informace najdete v tématu [literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) a [vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/index.md).  
  
 Pokud můžete definovat globální obor názvů XML bez předpony oboru názvů (například `Imports <xmlns="http://SomeNameSpace>"`), tento obor názvů se považuje za výchozí obor názvů XML. Výchozí obor názvů XML se používá pro jakoukoli element literály XML a vlastnosti osy atributu XML, které není explicitně zadán obor názvů. Výchozí obor názvů se také používá, pokud zadaný obor názvů není prázdný obor názvů (to znamená `xmlns=""`). Výchozí obor názvů XML se nevztahuje k atributům XML v literálech XML a vlastnosti osy atributu XML, které nemají žádný obor názvů.  
  
 Obory názvů XML, které jsou definovány v XML literál, který se nazývá *místní obory názvů XML*, přednost před obory názvů XML, které jsou definovány `Imports` příkaz jako globální. Obory názvů XML, které jsou definovány `Imports` příkaz přednost importovat pro projekt jazyka Visual Basic obory názvů XML. Pokud literál XML definuje obor názvů XML, že místní obor názvů se nevztahují na vložené výrazy.  
  
 Globálními názvovými prostory XML řídit stejnými pravidly určení oboru a definice jako obory názvů rozhraní .NET Framework. V důsledku toho může obsahovat `Imports` příkaz k definování globální obor názvů XML kdekoli můžete importovat obor názvů rozhraní .NET Framework. To zahrnuje soubory s kódem a importovaných oborů názvů na úrovni projektu. Informace o importovaných oborů názvů na úrovni projektu, naleznete v tématu [odkazy na stránky, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).  
  
 Každý zdrojový soubor může obsahovat libovolný počet `Imports` příkazy. Tyto musí následovat možnost deklarace, jako `Option Strict` příkaz a musí předcházet programovací element deklarace, jako například `Module` nebo `Class` příkazy.  
  
## <a name="example"></a>Příklad  
 Následující příklad importuje výchozí názvový prostor XML a obor názvů XML identifikovat s předponou `ns`. Potom vytvoří literály XML, které používají oba obory názvů.  
  
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
 Následující příklad importuje předponu oboru názvů XML `ns`. Potom vytvoří literál XML, který používá předponu oboru názvů a zobrazí poslední formulář daného elementu.  
  
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
  
 Všimněte si, že kompilátor převést předponu oboru názvů XML z globální předpony s definicí místní předponu.  
  
## <a name="example"></a>Příklad  
 Následující příklad importuje předponu oboru názvů XML `ns`. Poté použije předponu oboru názvů XML vytvoření literálu a přístup k první podřízený uzel s kvalifikovaným názvem `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 Tento kód zobrazí následující text:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Viz také:

- [Literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [Operátor GetXmlNamespace](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
