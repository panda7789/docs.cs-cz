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
ms.openlocfilehash: c17adc6df0f8cf94f06547b48a32b2ffb8f303ca
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973480"
---
# <a name="throw-statement-visual-basic"></a>Throw – příkaz (Visual Basic)
Generuje výjimku uvnitř procedury.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a>Část  
 `expression`  
 Poskytuje informace o vyvolání výjimky. Volitelné, při které se nacházejí v `Catch` příkaz, jinak povinné.  
  
## <a name="remarks"></a>Poznámky  
 `Throw` Příkazu vyvolá výjimku, který dokáže pracovat s kódem strukturované zpracování výjimek (`Try`... `Catch`... `Finally`) nebo nestrukturovaných kód zpracování výjimek (`On Error GoTo`). Můžete použít `Throw` příkaz zachytávat chyby v kódu, protože Visual Basic přesune výše v zásobníku volání, dokud nenajde odpovídající kód zpracování výjimek.  
  
 A `Throw` příkazem žádný výraz lze použít pouze v `Catch` příkazu, ve kterém příkazu case znovu vyvolá výjimku, teď nezpracovává nástrojem `Catch` příkazu.  
  
 `Throw` Příkaz obnoví zásobník volání pro `expression` výjimky. Pokud `expression` není k dispozici, zásobník volání je vlevo beze změny. Zásobník volání výjimky prostřednictvím můžete přistupovat <xref:System.Exception.StackTrace%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující kód používá `Throw` příkaz vyvolání výjimky:  
  
 [!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]  
  
## <a name="requirements"></a>Požadavky  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Modul:** `Interaction`  
  
 **Sestavení:** Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Příkaz On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
