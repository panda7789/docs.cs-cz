---
title: Throw – příkaz
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
ms.openlocfilehash: 95572b1739490e90f53da6b6ec283bfb532c46d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404132"
---
# <a name="throw-statement-visual-basic"></a>Throw – příkaz (Visual Basic)

Vyvolá výjimku v rámci procedury.

## <a name="syntax"></a>Syntaxe

```vb
Throw [ expression ]
```

## <a name="part"></a>Část

`expression`\
Poskytuje informace o výjimce, která má být vyvolána. Volitelné, pokud je umístěn v `Catch` příkazu, v opačném případě vyžadováno.

## <a name="remarks"></a>Poznámky

`Throw`Příkaz vyvolá výjimku, kterou lze zpracovat pomocí strukturovaného kódu zpracování výjimek (.. `Try` . `Catch` ...`Finally`) nebo nestrukturovaný kód pro zpracování výjimek ( `On Error GoTo` ). Můžete použít `Throw` příkaz k zachycení chyb v rámci kódu, protože Visual Basic přesune zásobník volání, dokud nenajde příslušný kód pro zpracování výjimek.

`Throw`Příkaz bez výrazu lze použít pouze v `Catch` příkazu. v takovém případě příkaz znovu vyvolá výjimku, která je aktuálně zpracována `Catch` příkazem.

`Throw`Příkaz obnoví zásobník volání pro `expression` výjimku. Pokud není `expression` zadán, zásobník volání zůstane beze změny. Můžete získat přístup k zásobníku volání pro výjimku prostřednictvím <xref:System.Exception.StackTrace%2A> Vlastnosti.

## <a name="example"></a>Příklad

Následující kód používá `Throw` příkaz k vyvolání výjimky:

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a>Viz také

- [Try...Catch....Finally – příkaz](try-catch-finally-statement.md)
- [On Error – příkaz](on-error-statement.md)
