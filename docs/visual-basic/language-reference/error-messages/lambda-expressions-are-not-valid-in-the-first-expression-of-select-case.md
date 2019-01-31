---
title: Použití výrazů lambda v prvním výrazu příkazu 'Select Case' je neplatné.
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: d56515093020a4c987d132491957ce6db9e21683
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287791"
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
