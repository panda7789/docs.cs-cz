---
title: Jak spustit kód pro vyčištění pomocí Průvodce programováním nakonec v C#
description: Naučte se, jak spustit čistící kód pomocí příkazu finally. Příkazy finally zajistí, že veškeré potřebné čištění objektů bude okamžitě provedeno.
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 148c1f9fba67659a07c667bb15619d6f3f7c3b2f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302019"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Jak spustit čistící kód pomocí finally (Průvodce programováním v C#)
Účelem `finally` příkazu je zajistit, aby bylo nutné vyčistit objekty, obvykle objekty, které jsou uchovávány v externích prostředcích, dochází okamžitě, i když je vyvolána výjimka. Jedním z příkladů takového vyčištění je volání <xref:System.IO.Stream.Close%2A> <xref:System.IO.FileStream> ihned po použití namísto čekání na uvolnění objektu modulem CLR (Common Language Runtime), a to takto:  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a>Příklad  
 Chcete-li převést předchozí kód do `try-catch-finally` příkazu, je kód pro vyčištění oddělen od pracovního kódu, jak je znázorněno níže.  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 Vzhledem k tomu, že výjimka může nastat kdykoli v rámci `try` bloku před `OpenWrite()` voláním nebo se může stát, že `OpenWrite()` by volání nebylo úspěšné, nezaručujeme, že soubor je otevřený, když se ho pokusíme zavřít. `finally`Blok přidá kontrolu pro ujištění, že objekt není <xref:System.IO.FileStream> `null` před voláním <xref:System.IO.Stream.Close%2A> metody. Bez `null` kontroly `finally` může blok vyvolat svou vlastní hodnotu <xref:System.NullReferenceException> , ale vyvolání výjimek v `finally` blocích by se mělo vyhnout, pokud je to možné.  
  
 Připojení k databázi je dalším vhodným kandidátem na uzavření v `finally` bloku. Vzhledem k tomu, že počet připojení povolených pro databázový server je někdy omezený, měli byste připojení databáze co nejrychleji zavřít. Pokud je vyvolána výjimka před zavřením připojení, jedná se o jiný případ, kdy použití `finally` bloku je lepší než čekání na uvolňování paměti.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Výjimky a zpracování výjimek](./index.md)
- [Zpracování výjimek](./exception-handling.md)
- [using – příkaz](../../language-reference/keywords/using-statement.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
