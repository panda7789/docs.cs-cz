---
title: Jak spustit kód vyčištění pomocí finally - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: d1ba761e64053d656ad4cd004133fc455a57c6f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705272"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Jak spustit vyčištění kódu pomocí finally (C# Programovací průvodce)
Účelem příkazu `finally` je zajistit, aby nezbytné vyčištění objektů, obvykle objekty, které jsou v držení externích prostředků, dojde okamžitě, i v případě, že je vyvolána výjimka. Jedním z příkladů takového <xref:System.IO.Stream.Close%2A> vyčištění <xref:System.IO.FileStream> je volání na ihned po použití namísto čekání na objekt, který má být uvolněna systémem runtime společného jazyka, takto:  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a>Příklad  
 Chcete-li změnit předchozí `try-catch-finally` kód na příkaz, kód vyčištění je oddělen od pracovního kódu, následujícím způsobem.  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 Vzhledem k tomu, že `try` k výjimce může dojít kdykoli v rámci bloku před voláním `OpenWrite()` nebo samotné `OpenWrite()` volání může selhat, není zaručeno, že soubor je otevřen při pokusu o jeho zavření. Blok `finally` přidá kontrolu, abyste se <xref:System.IO.FileStream> ujistili, že objekt není `null` před voláním <xref:System.IO.Stream.Close%2A> metody. Bez `null` kontroly `finally` by blok mohl <xref:System.NullReferenceException>vyvolat vlastní , `finally` ale vyvolání výjimky v blocích je třeba se vyhnout, pokud je to možné.  
  
 Připojení k databázi je dalším dobrým `finally` kandidátem pro zavření v bloku. Vzhledem k tomu, že počet připojení povolených k databázovému serveru je někdy omezen, měli byste co nejrychleji ukončit připojení k databázi. Pokud je vyvolána výjimka před ukončením připojení, je `finally` to jiný případ, kdy pomocí bloku je lepší než čekání na uvolnění paměti.  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Výjimky a zpracování výjimek](./index.md)
- [Zpracování výjimek](./exception-handling.md)
- [using – příkaz](../../language-reference/keywords/using-statement.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
