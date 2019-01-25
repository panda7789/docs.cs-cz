---
title: Výrazy lambda nejsou platné v prvním výrazu &#39;Select Case&#39; – příkaz
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: afefa821f9695dbbfe2a96aee5afd3171ae5b1db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700218"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a>Výrazy lambda nejsou platné v prvním výrazu &#39;Select Case&#39; – příkaz
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
