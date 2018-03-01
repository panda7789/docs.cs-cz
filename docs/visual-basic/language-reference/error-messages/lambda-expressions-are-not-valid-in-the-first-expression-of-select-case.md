---
title: "Lambda – výrazy nejsou platné v prvním výrazu a & č. 39; Vyberte případ & č. 39; příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e91401d6891d4e38014bb716a337560885cf73a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a>Lambda – výrazy nejsou platné v prvním výrazu a & č. 39; Vyberte případ & č. 39; příkaz
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
 [Lambda – výrazy](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [If... Potom... Else – příkaz](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Vyberte... Case – příkaz](../../../visual-basic/language-reference/statements/select-case-statement.md)
