---
title: Seznam atributů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: 35d031722a5eddd6adce5e32df62b86c500d305b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604067"
---
# <a name="attribute-list-visual-basic"></a>Seznam atributů (Visual Basic)
Určuje atributy, které se použijí na deklarované programovací element. Více atributů jsou oddělené čárkami. Toto je syntaxe pro jeden atribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>Součásti  
 `attributemodifier`  
 Vyžaduje se pro atributy použité na začátku zdrojového souboru. Může být [sestavení](../../../visual-basic/language-reference/modifiers/assembly.md) nebo [modulu](../../../visual-basic/language-reference/modifiers/module-keyword.md).  
  
 `attributename`  
 Požadováno. Název atributu.  
  
 `attributearguments`  
 Volitelné. Seznam argumentů umístění pro tento atribut. Více argumentů jsou oddělené čárkami.  
  
 `attributeinitializer`  
 Volitelné. Seznam inicializátory proměnné nebo vlastnosti pro tento atribut. Více inicializátory jsou oddělené čárkami.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít jeden nebo více atributů na téměř všechny programovací element (typy, postupy, vlastnosti a tak dále). Atributy se zobrazí v metadatech vaše sestavení a pomohou vám opatřit poznámkami kódu nebo zadejte, jak používat určitý programovací element. Můžete použít atributy definované ve Visual Basic a rozhraní .NET Framework a je možné definovat vlastní atributy.  

 Další informace o použití atributů naleznete v tématu [atributy přehled](../../../visual-basic/programming-guide/concepts/attributes/index.md). Informace o názvech atributů najdete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Pravidla  
  
-   **Umístění.** Atributy můžete použít k nejvíce deklarované elementům programování. Chcete-li použít jeden nebo více atributů, umístěte *atribut bloku* na začátku prohlášení element. Každá položka v seznamu atributů určuje atribut, který chcete použít a modifikátor a argumenty, které používáte pro toto volání atributu.  
  
-   **Lomené závorky.** Pokud zadáte jenom seznam atributů, je nutné uzavřít do lomené závorky ("`<`"a"`>`").  
  
-   **Součástí deklarace.** Atribut musí být součástí deklaraci elementu, nikoli samostatný příkaz. Můžete použít posloupnost pokračování řádku (" `_`") k rozšíření příkaz deklarace na více řádků zdrojového kódu.  
  
-   **Modifikátory.** Atributu – modifikátor (`Assembly` nebo `Module`) je potřeba na každý atribut použitý programovací element na začátku zdrojového souboru. Modifikátory atribut nejsou povoleny u atributů použitých na elementy, které nejsou na začátku zdrojového souboru.  
  
-   **Argumenty.** Všechny argumenty poziční atributu musí předcházet inicializátory všechny proměnné nebo vlastnosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad se vztahuje <xref:System.Runtime.InteropServices.DllImportAttribute> atribut kostru definice `Function` postupu.  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> Označuje, že s atributy postup představuje vstupní bod v nespravované dynamická knihovna (DLL). Atribut poskytuje název DLL jako poziční argument a dalších informací jako proměnné inicializátory.  
  
## <a name="see-also"></a>Viz také  
 [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)  
 [Modul \<– klíčové slovo >](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [Postupy: Přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
