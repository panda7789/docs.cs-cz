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
ms.openlocfilehash: beb54cf6c4e6dc87b9a08b81586b24d72f92b84b
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001419"
---
# <a name="try-finally-c-reference"></a>try-finally (Referenční dokumentace jazyka C#)
Pomocí `finally` blok, můžete vyčistit všechny prostředky, které jsou přiděleny v [zkuste](../../../csharp/language-reference/keywords/try-catch.md) blok a kód můžete spustit i v případě, že dojde k výjimce v `try` bloku. Obvykle, prohlášení o `finally` blok spustit, jakmile opustí ovládací prvek `try` příkazu. Přenos řízení může nastat v důsledku normálního provedení, provedení `break`, `continue`, `goto`, nebo `return` příkazu, nebo šíření výjimky z `try` příkazu.  
  
 V rámci zpracování výjimek, přidružené `finally` bloku je zaručen běh. Nicméně pokud není výjimka ošetřena, provedení `finally` bloku je závislá na jak operace unwind výjimek se aktivuje. Která je dále závislé na nastavení v počítači.
  
 Obvykle po neošetřené výjimce ukončení aplikaci, která určuje, jestli `finally` spustit blok není důležité. Však máte příkazy v `finally` blok, který musí být spuštěn i v této situaci, jedním řešením je přidat `catch` bloku `try` - `finally` příkazu. Alternativně můžete zachytit výjimku, která by mohla být vyvolána v `try` bloku `try` - `finally` výše v zásobníku volání. To znamená, můžete zachytit výjimku v metodě, která volá metodu, která obsahuje `try` - `finally` příkazu, nebo v metodě, která volá tuto metodu, nebo v jakékoli metodě v zásobníku volání. Pokud není výjimka zachycena, provádění `finally` bloku závisí na tom, jestli operační systém zvolí pro spuštění výjimky operaci unwind.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu způsobuje neplatný výraz převodu `System.InvalidCastException` výjimky. Výjimka neošetřená.  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 V následujícím příkladu, výjimka `TryCast` metoda je zachycena v metodě hlouběji v zásobníku volání.  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 Další informace o `finally`, naleznete v tématu [konstrukce try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).  
  
 C# obsahuje také [příkaz using](../../../csharp/language-reference/keywords/using-statement.md), který poskytuje podobné funkce pro <xref:System.IDisposable> objekty pomocí pohodlné syntaxe.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [try, throw a catch – příkazy (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)  
- [Příkazy zpracování výjimek](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
- [throw](../../../csharp/language-reference/keywords/throw.md)  
- [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
- [Postupy: Explicitní generování výjimek](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
