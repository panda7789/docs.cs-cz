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
ms.openlocfilehash: a6d10982cf199e9285334e0d72e6622275d51b4d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626193"
---
# <a name="throw-statement-visual-basic"></a>Throw – příkaz (Visual Basic)
Vyvolá výjimku v rámci procedury.

## <a name="syntax"></a>Syntaxe

```vb
Throw [ expression ]
```

## <a name="part"></a>Částí
 `expression`Poskytuje informace o výjimce, která má být vyvolána. Volitelné, pokud je umístěn v `Catch` příkazu, v opačném případě vyžadováno.
  
## <a name="remarks"></a>Poznámky
 Příkaz vyvolá výjimku, kterou lze zpracovat pomocí strukturovaného kódu zpracování výjimek (`Try`... `Throw` `Catch`... ) nebo nestrukturovaný kód pro ošetření výjimek (`On Error GoTo`). `Finally` Můžete použít `Throw` příkaz k zachycení chyb v rámci kódu, protože Visual Basic přesune zásobník volání, dokud nenajde příslušný kód pro zpracování výjimek.
 
 Příkaz bez výrazu lze použít pouze `Catch` v příkazu. v takovém případě příkaz znovu vyvolá výjimku, která je `Catch` aktuálně zpracována příkazem. `Throw`

 Příkaz obnoví zásobník volání `expression` pro výjimku. `Throw` Pokud `expression` není zadán, zásobník volání zůstane beze změny. Můžete získat přístup k zásobníku volání pro výjimku prostřednictvím <xref:System.Exception.StackTrace%2A> vlastnosti.

## <a name="example"></a>Příklad
 Následující kód používá `Throw` příkaz k vyvolání výjimky:
 
 [!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

  
## <a name="see-also"></a>Viz také:

- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Příkaz On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
