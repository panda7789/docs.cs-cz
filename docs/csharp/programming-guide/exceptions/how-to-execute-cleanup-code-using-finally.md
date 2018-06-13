---
title: 'Postupy: Spuštění kódu čištění pomocí příkazu finally (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 948281af45d04714ed6fc308b60341e87abeb830
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331705"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Postupy: Spuštění kódu čištění pomocí příkazu finally (Průvodce programováním v C#)
Účel `finally` příkaz je aby se zajistilo nezbytné čištění objektů, obvykle objekty, které jsou externí prostředky, která uchovává okamžitě, i když je vyvolána výjimka. Příkladem takových čištění volá <xref:System.IO.Stream.Close%2A> na <xref:System.IO.FileStream> okamžitě po použití místo abyste čekali, objekt, který má být uvolnění z paměti modulem common language runtime, následujícím způsobem:  
  
 [!code-csharp[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]  
  
## <a name="example"></a>Příklad  
 Chcete-li do předchozí kód `try-catch-finally` příkaz kód čištění je oddělená od kód pracovní následujícím způsobem.  
  
 [!code-csharp[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]  
  
 Vzhledem k tomu může dojít k výjimce, kdykoli v rámci `try` před zablokovat `OpenWrite()` volat, nebo `OpenWrite()` volání sebe sama se možná nepovede, jsme se nezaručuje, že soubor je při pokusu o zavřete ho otevřete. `finally` Bloku přidá kontrola Ujistěte se, že <xref:System.IO.FileStream> objekt není `null` před voláním <xref:System.IO.Stream.Close%2A> metoda. Bez `null` zkontrolovat, `finally` bloku může vyvolat vlastní <xref:System.NullReferenceException>, ale vyvolávání výjimek `finally` bloky je nutno, pokud je to možné.  
  
 Připojení k databázi je pro dochází k uzavření jiné vhodným kandidátem `finally` bloku. Počet připojení povolená pro databázový server, který je někdy omezená, a proto měli co nejrychleji zavřete připojení databáze. Pokud před uzavřením připojení, je vyvolána výjimka, je to jiné případ kde pomocí `finally` bloku je lepší, než čekání uvolňování paměti.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Výjimky a jejich zpracování](../../../csharp/programming-guide/exceptions/index.md)  
 [Zpracování výjimek](../../../csharp/programming-guide/exceptions/exception-handling.md)  
 [using – příkaz](../../../csharp/language-reference/keywords/using-statement.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
