---
title: Účinné používání datových typů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: 68371a9f8d4dcc5d0a2b67955d5e88943a83b085
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631104"
---
# <a name="efficient-use-of-data-types-visual-basic"></a>Účinné používání datových typů (Visual Basic)
Nedeklarované proměnné a proměnné deklarované bez datového typu jsou přiřazeny k `Object` datovému typu. To usnadňuje psaní programů rychleji, ale může způsobit pomalejší spouštění.

## <a name="strong-typing"></a>Silné zadání
 Zadání datových typů pro všechny proměnné se označuje jako *silné zadání*. Použití silného psaní má několik výhod:

- Umožňuje podporu technologie IntelliSense pro vaše proměnné. To umožňuje zobrazit jejich vlastnosti a další členy při psaní do kódu.

- Využívá kontrolu typu kompilátoru. Tato zachycení příkazy, které mohou selhat v době běhu z důvodu chyb, jako je například přetečení. Také zachytí volání metod pro objekty, které je nepodporují.

- Výsledkem je rychlejší provádění kódu.

## <a name="most-efficient-data-types"></a>Nejúčinnější datové typy
 Pro proměnné, které nikdy neobsahují zlomky, jsou integrální datové typy efektivnější než Neceločíselné typy. V Visual Basic `Integer` a `UInteger` jsou nejúčinnější číselné typy.

 Pro zlomková čísla `Double` je nejúčinnější datový typ, protože procesory na současných platformách provádějí operace s plovoucí desetinnou čárkou s dvojitou přesností. Operace s `Double` ale nejsou stejně rychlé jako u integrálních typů `Integer`, jako je.

## <a name="specifying-data-type"></a>Určení datového typu
 Použijte [příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) k deklaraci proměnné konkrétního typu. Úroveň přístupu můžete určit současně pomocí klíčového slova [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)nebo [Private](../../../../visual-basic/language-reference/modifiers/private.md) , jak je uvedeno v následujícím příkladu.

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a>Převod znaků
 Funkce `AscW` a`ChrW` fungují v kódování Unicode. Měli byste je používat v předvolbách `Asc` a `Chr`, které se musí překládat do kódování Unicode a z něj.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Číselné datové typy](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Používání atributu IntelliSense](/visualstudio/ide/using-intellisense)
