---
title: Jak spustit čistící kód pomocí Průvodce pro C# nakonec programování
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: d1ba761e64053d656ad4cd004133fc455a57c6f6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705272"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Jak spustit čistící kód pomocí finally (C# Průvodce programováním)
Účelem příkazu `finally` je zajistit, že nezbytné vyčištění objektů, obvykle objekty, které jsou uchovávány na externích zdrojích, dochází okamžitě, i když je vyvolána výjimka. Jedním z příkladů takového vyčištění je volání <xref:System.IO.Stream.Close%2A> na <xref:System.IO.FileStream> ihned po použití namísto čekání na uvolnění objektu modulem CLR (Common Language Runtime), a to takto:  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a>Příklad  
 Chcete-li převést předchozí kód na příkaz `try-catch-finally`, je kód pro vyčištění oddělen od pracovního kódu, jak je znázorněno níže.  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 Vzhledem k tomu, že výjimka může nastat kdykoli v rámci `try` bloku před voláním `OpenWrite()`, `OpenWrite()` nebo může selhání samotného volání selhat, nezaručujeme, že soubor je otevřený, když ho zkusíme zavřít. Blok `finally` přidá kontrolu pro ujištění, že objekt <xref:System.IO.FileStream> není `null` před voláním metody <xref:System.IO.Stream.Close%2A>. Bez kontroly `null` může blok `finally` vyvolat svůj vlastní <xref:System.NullReferenceException>, ale vyvolání výjimek v `finally` blocích by se mělo vyhnout, pokud je to možné.  
  
 Připojení k databázi je dalším vhodným kandidátem na uzavření v rámci `finally`ho bloku. Vzhledem k tomu, že počet připojení povolených pro databázový server je někdy omezený, měli byste připojení databáze co nejrychleji zavřít. Pokud je vyvolána výjimka předtím, než budete moci uzavřít připojení, jedná se o další případ, kdy použití bloku `finally` je lepší než čekání na uvolňování paměti.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Výjimky a jejich zpracování](./index.md)
- [Zpracování výjimek](./exception-handling.md)
- [using – příkaz](../../language-reference/keywords/using-statement.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
