---
title: Výraz 'As Any' již není podporován v příkazech 'Declare'.
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: 3593f238c72cbcce911c72e42552d6a75188b628
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310691"
---
# <a name="as-any-is-not-supported-in-declare-statements"></a>Výraz 'As Any' již není podporován v příkazech 'Declare'.
`Any` Datový typ byl použit s `Declare` příkazy ve Visual Basicu 6.0 a starší verze, tak, aby povolovala použití argumentů, které by mohly obsahovat jakýkoli typ dat. Přetížení, ale podporuje jazyka Visual Basic a tak provede `Any` datového typu zastaralá.  
  
 **ID chyby:** BC30828  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Deklarovat parametry konkrétní typ, který chcete použít; např.  
  
     [!code-vb[VbVbalrStatements#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#95)]  
  
2. Použití <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributy `As Any` při `Void*` datacommand procedura volána.  
  
     [!code-vb[VbVbalrStatements#96](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#96)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Návod: Volání rozhraní Windows API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Vytváření prototypů ve spravovaném kódu](../../../framework/interop/creating-prototypes-in-managed-code.md)
