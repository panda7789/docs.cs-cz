---
title: Lambda – výrazy nejsou platné v prvním výrazu &#39;Select Case&#39; – příkaz
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: c492615850ec089fe35c1ae4eaba90a741e30f42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a>Lambda – výrazy nejsou platné v prvním výrazu &#39;Select Case&#39; – příkaz
Výraz lambda nelze použít pro výraz testu v `Select Case` příkaz. Definice výrazu lambda vrátí funkce a testovací výraz `Select Case` příkaz musí být základní datového typu.  
  
 Následující kód způsobí, že tuto chybu:  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **ID chyby:** BC36635  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zkontrolujte v kódu k určení, zda jiný podmíněné konstrukce, jako například `If...Then...Else` by pro vás pracovní příkaz.  
  
-   Pro volání funkce, můžete mít určen, jak je znázorněno v následujícím kódu:  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Příkaz Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)
