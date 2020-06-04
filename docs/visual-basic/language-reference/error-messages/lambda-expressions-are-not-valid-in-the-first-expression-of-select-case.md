---
title: Použití výrazů lambda v prvním výrazu příkazu 'Select Case' je neplatné.
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: 08f7cd9dd95a10cad0df6539ba43122495347bae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397360"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a>Použití výrazů lambda v prvním výrazu příkazu 'Select Case' je neplatné.
Výraz lambda nelze použít pro výraz testu v `Select Case` příkazu. Definice výrazů lambda vrací funkce a výraz testu `Select Case` příkazu musí být základní datový typ.  
  
 Následující kód způsobuje tuto chybu:  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **ID chyby:** BC36635  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Projděte si kód, abyste zjistili, jestli pro vás funguje jiná podmíněná konstrukce, jako je třeba `If...Then...Else` příkaz.  
  
- Možná budete chtít zavolat funkci, jak je znázorněno v následujícím kódu:  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a>Viz také

- [Výrazy lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [If...Then...Else – příkaz](../statements/if-then-else-statement.md)
- [Select...Case – příkaz](../statements/select-case-statement.md)
