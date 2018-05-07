---
title: Throw – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: cfa53b3585846da25711739fb7af4bde21746b29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="throw-statement-visual-basic"></a>Throw – příkaz (Visual Basic)
Vyvolá výjimku, v rámci procedury.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a>Část  
 `expression`  
 Poskytuje informace o vyvolání výjimky. Volitelné, při které se nacházejí v `Catch` příkaz, jinak vyžaduje.  
  
## <a name="remarks"></a>Poznámky  
 `Throw` Příkaz vyvolá výjimku, která dokáže zpracovat kódem strukturované zpracování výjimek (`Try`... `Catch`... `Finally`) nebo nestrukturovaných kódu zpracování výjimek (`On Error GoTo`). Můžete použít `Throw` příkaz na depeše chyb v kódu, protože jazyka Visual Basic přesune nahoru zásobníku volání, dokud nenajde odpovídající kód zpracování výjimek.  
  
 A `Throw` příkaz s žádný výraz lze použít pouze v `Catch` příkaz, ve kterém případ příkaz znovu vyvolá výjimku aktuálně zpracovanou pomocí `Catch` příkaz.  
  
 `Throw` Příkaz obnoví zásobníku volání pro `expression` výjimka. Pokud `expression` není k dispozici, zásobník volání ponecháno změny. Dostanete zásobníku volání pro výjimky prostřednictvím <xref:System.Exception.StackTrace%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující kód používá `Throw` příkaz, který má být vyvolána výjimka:  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## <a name="requirements"></a>Požadavky  
 **Namespace:** [Microsoft.VisualBasic –](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Modul:** `Interaction`  
  
 **Sestavení:** jazyka Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Příkaz On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
