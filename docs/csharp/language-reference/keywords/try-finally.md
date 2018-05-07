---
title: try-finally (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 696eb531fe3e340f7fe0ae12483648119cf5a7eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="try-finally-c-reference"></a>try-finally (Referenční dokumentace jazyka C#)
Pomocí `finally` blok, můžete vyčistit všechny prostředky, které jsou přiděleny v [zkuste](../../../csharp/language-reference/keywords/try-catch.md) blok a kód můžete spustit i v případě, že dojde k výjimce v `try` bloku. Obvykle prohlášení o `finally` bloku spustit, když opustí řízení `try` příkaz. Přenos řízení může nastat v důsledku normální spuštění, spuštění `break`, `continue`, `goto`, nebo `return` prohlášení, nebo propagace výjimku z `try` příkaz.  
  
 V rámci zpracování výjimek, přidruženého `finally` bloku záruku, že chcete spustit. Ale pokud neošetřená výjimka, provádění `finally` blok je závislá na jak výjimka unwind operace se aktivuje. Pak je závislá na nastavení počítače.
  
 Obvykle při k neošetřené výjimce ukončení aplikace, zda `finally` bloku běží, není důležité. Ale pokud máte příkazy ve `finally` blok, který se musí spustit i v takovém případě jedno řešení je přidání `catch` zablokujte `try` - `finally` příkaz. Alternativně můžete zachytit výjimku, která může být vyvolána v `try` blokovat z `try` - `finally` příkaz vyšší zásobníkem volání. To znamená, můžete zachytit výjimka v metodě, která volá metodu, která obsahuje `try` - `finally` prohlášení, nebo v metodu, která volá tuto metodu, nebo v jakékoli metody v zásobníku volání. Pokud není výjimka zachycena, provádění `finally` bloku závisí na tom, jestli operační systém rozhodne pro spuštění výjimky unwind operace.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu příkazu Neplatný převod způsobí, že `System.InvalidCastException` výjimka. Neošetřené výjimky.  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 V následujícím příkladu, výjimku z `TryCast` metoda je místo zachycení metoda dále zásobníkem volání.  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 Další informace o `finally`, najdete v části [try-catch-finally –](../../../csharp/language-reference/keywords/try-catch-finally.md).  
  
 C# obsahuje také [pomocí příkazu](../../../csharp/language-reference/keywords/using-statement.md), který poskytuje podobné funkce pro <xref:System.IDisposable> objekty v vhodné syntaxe.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [try, throw a catch – příkazy (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [Příkazy zpracování výjimek](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [throw](../../../csharp/language-reference/keywords/throw.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [Postupy: Explicitní generování výjimek](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
