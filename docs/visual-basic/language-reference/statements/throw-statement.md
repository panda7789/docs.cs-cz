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
ms.openlocfilehash: 147345990b625e034e651e69b322bc098d0bd8de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352781"
---
# <a name="throw-statement-visual-basic"></a>Throw – příkaz (Visual Basic)

Vyvolá výjimku v rámci procedury.

## <a name="syntax"></a>Syntaxe

```vb
Throw [ expression ]
```

## <a name="part"></a>Částí

`expression`\
Poskytuje informace o výjimce, která má být vyvolána. Volitelné, pokud je umístěn v příkazu `Catch`, je vyžadováno jinak.

## <a name="remarks"></a>Poznámky

Příkaz `Throw` vyvolá výjimku, kterou lze zpracovat pomocí strukturovaného kódu zpracování výjimek (`Try`...`Catch`...`Finally`) nebo nestrukturovaný kód pro zpracování výjimek (`On Error GoTo`). Můžete použít příkaz `Throw` k zachycení chyb v rámci kódu, protože Visual Basic přesune zásobník volání, dokud nenajde příslušný kód pro zpracování výjimek.

Příkaz `Throw` bez výrazu lze použít pouze v příkazu `Catch`. v takovém případě příkaz znovu vyvolá výjimku, která je aktuálně zpracována příkazem `Catch`.

Příkaz `Throw` obnoví zásobník volání pro výjimku `expression`. Pokud není zadán `expression`, zásobník volání zůstane beze změny. Můžete získat přístup k zásobníku volání pro výjimku prostřednictvím vlastnosti <xref:System.Exception.StackTrace%2A>.

## <a name="example"></a>Příklad

Následující kód používá příkaz `Throw` k vyvolání výjimky:

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a>Viz také:

- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Příkaz On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
