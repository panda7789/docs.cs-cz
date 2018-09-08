---
title: 'Postupy: Spuštění kódu čištění pomocí příkazu finally (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 47e9bb368deb077ef10ce474683d81e0cb56cef8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183782"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Postupy: Spuštění kódu čištění pomocí příkazu finally (Průvodce programováním v C#)
Účel `finally` příkaz je zajistit, že potřebné vyčištění objektů, obvykle objekty, které blokují dokončení externích zdrojů, začne okamžitě, i v případě, že dojde k výjimce. Příkladem takových vyčištění je volání <xref:System.IO.Stream.Close%2A> na <xref:System.IO.FileStream> okamžitě po použití místo abyste čekali, objekt, který má být uvolněn z paměti modulem common language runtime, následujícím způsobem:  
  
 [!code-csharp[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]  
  
## <a name="example"></a>Příklad  
 Chcete-li do předchozího kódu `try-catch-finally` prohlášení, kód pro vyčištění je oddělená od funkční kód následujícím způsobem.  
  
 [!code-csharp[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]  
  
 Protože může dojít k výjimce v každém okamžiku v rámci `try` blokovat před `OpenWrite()` volání, nebo `OpenWrite()` volání sebe sama, může selhat, jsme není zaručeno, že je soubor otevřen při Snažíme se ho zavřít. `finally` Bloku přidá kontrolu a ujistěte se, že <xref:System.IO.FileStream> objekt není `null` před voláním <xref:System.IO.Stream.Close%2A> metody. Bez `null` zkontrolovat, `finally` bloku může vyvolat vlastní <xref:System.NullReferenceException>, ale vyvolává výjimky `finally` bloky, mělo by se vyhnout, pokud je to možné.  
  
 Připojení k databázi je jiný vhodným kandidátem pro jeho uzavírání `finally` bloku. Vzhledem k tomu, že počet povolených připojení k serveru databáze je někdy omezený, by měl co nejrychleji zavřete připojení k databázi. Pokud je vyvolána výjimka, před uzavřením připojení, to je dalším užitečným kdy použití `finally` bloku je obecně lepší než čekání na uvolňování paměti.  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Výjimky a jejich zpracování](../../../csharp/programming-guide/exceptions/index.md)  
- [Zpracování výjimek](../../../csharp/programming-guide/exceptions/exception-handling.md)  
- [using – příkaz](../../../csharp/language-reference/keywords/using-statement.md)  
- [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
- [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
- [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
