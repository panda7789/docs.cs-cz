---
title: 'Postupy: Spustit čistící kód pomocí Průvodce pro C# nakonec programování'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: e6adbb864b0450cdd1dbfcc56abdbad2034c5c7a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590244"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Postupy: Spustit čistící kód pomocí finally (C# Průvodce programováním)
Účelem `finally` příkazu je zajistit, aby bylo nutné vyčistit objekty, obvykle objekty, které jsou uchovávány v externích prostředcích, dochází okamžitě, i když je vyvolána výjimka. Jedním z příkladů takového vyčištění je volání <xref:System.IO.Stream.Close%2A> <xref:System.IO.FileStream> ihned po použití namísto čekání na uvolnění objektu modulem CLR (Common Language Runtime), a to takto:  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a>Příklad  
 Chcete-li převést předchozí kód do `try-catch-finally` příkazu, je kód pro vyčištění oddělen od pracovního kódu, jak je znázorněno níže.  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 Vzhledem k tomu, že výjimka může nastat kdykoli v `try` rámci bloku `OpenWrite()` před voláním nebo se `OpenWrite()` může stát, že by volání nebylo úspěšné, nezaručujeme, že soubor je otevřený, když se ho pokusíme zavřít. Blok přidá kontrolu pro ujištění <xref:System.IO.FileStream> , že objekt `null` není před voláním <xref:System.IO.Stream.Close%2A> metody. `finally` Bez kontroly může blok vyvolat svou vlastní <xref:System.NullReferenceException>hodnotu, ale vyvolání výjimek v `finally` blocích by se mělo vyhnout, pokud je to možné. `finally` `null`  
  
 Připojení k databázi je dalším vhodným kandidátem na uzavření v `finally` bloku. Vzhledem k tomu, že počet připojení povolených pro databázový server je někdy omezený, měli byste připojení databáze co nejrychleji zavřít. Pokud je vyvolána výjimka před zavřením připojení, jedná se o `finally` jiný případ, kdy použití bloku je lepší než čekání na uvolňování paměti.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Výjimky a jejich zpracování](./index.md)
- [Zpracování výjimek](./exception-handling.md)
- [using – příkaz](../../language-reference/keywords/using-statement.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
