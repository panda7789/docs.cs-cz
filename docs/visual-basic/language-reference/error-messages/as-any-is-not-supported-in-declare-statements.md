---
title: Výraz 'As Any' již není podporován v příkazech 'Declare'.
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: c6c792e02bb655dc8a9544c4b5b46a64210556f6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839922"
---
# <a name="as-any-is-not-supported-in-declare-statements"></a>Výraz 'As Any' již není podporován v příkazech 'Declare'.
`Any` Datový typ byl použit s `Declare` příkazy ve Visual Basicu 6.0 a starší verze, tak, aby povolovala použití argumentů, které by mohly obsahovat jakýkoli typ dat. Přetížení, ale podporuje jazyka Visual Basic a tak provede `Any` datového typu zastaralá.  
  
 **ID chyby:** BC30828  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Deklarovat parametry konkrétní typ, který chcete použít; např.  
  
     [!code-vb[VbVbalrStatements#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#95)]  
  
2.  Použití <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributy `As Any` při `Void*` datacommand procedura volána.  
  
     [!code-vb[VbVbalrStatements#96](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#96)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Návod: Volání rozhraní API systému Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Vytváření prototypů ve spravovaném kódu](../../../framework/interop/creating-prototypes-in-managed-code.md)
