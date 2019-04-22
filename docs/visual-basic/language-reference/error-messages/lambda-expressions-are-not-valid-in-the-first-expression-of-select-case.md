---
title: Použití výrazů lambda v prvním výrazu příkazu 'Select Case' je neplatné.
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: e51ba4ad0910d0db2b927f84303e5c55515f4b84
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843446"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a>Použití výrazů lambda v prvním výrazu příkazu 'Select Case' je neplatné.
Výraz lambda nelze použít pro výraz testů v `Select Case` příkazu. Definice výraz lambda vrátí funkce a testovací výraz `Select Case` příkazu musí být typu základní data.  
  
 Následující kód způsobí, že k této chybě:  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **ID chyby:** BC36635  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Kontrole kódu k určení, zda jiný podmíněné konstrukce, jako například `If...Then...Else` příkazu by pro vás nejvhodnější.  
  
-   Pro volání funkce, budete mít určený, jak je znázorněno v následujícím kódu:  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a>Viz také:

- [Výrazy lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Příkaz Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)
