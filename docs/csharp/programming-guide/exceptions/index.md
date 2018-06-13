---
title: Výjimky a jejich zpracování (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: de396ca4da2e115d221036d3ec49fb7b43d3d21d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335261"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Výjimky a jejich zpracování (Průvodce programováním v C#)
Zpracování funkce nápovědy výjimek jazyka C# můžete řešit neočekávané nebo výjimečně vysoké počty případy, které nastat, pokud je program spuštěn. Používá zpracování výjimek `try`, `catch`, a `finally` klíčová slova a zkuste to akce, které nemusí být úspěšné, pro zpracování chyby, pokud se rozhodnete, že je možné logicky Uděláte to tak a následně vyčištění prostředků. Výjimky může být generována modul CLR (CLR), rozhraní .NET Framework nebo knihovny jakékoli třetí strany, nebo kód aplikace. Výjimky jsou vytvořeny pomocí `throw` – klíčové slovo.  
  
 V mnoha případech výjimku mohou být vyvolány není metodu, která má váš kód volat přímo, ale jinou metodou další dolů v zásobníku volání. Pokud k tomu dojde, modul CLR bude unwind zásobníku, hledají metodu s `catch` blokovat pro typ určité výjimky a provede první takové `catch` blokovat, že pokud najde. Pokud najde žádné odpovídající `catch` blokovat kdekoli v zásobníku volání, bude ukončit proces a zobrazit zprávu pro uživatele.  
  
 V tomto příkladu metoda testů pro dělení nulou a zachytí chyby. Bez výjimek, by tento program ukončit s **DivideByZeroException neošetřené** chyby.  
  
 [!code-csharp[csProgGuideExceptions#18](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exceptions-and-exception-handling_1.cs)]  
  
## <a name="exceptions-overview"></a>Přehled výjimek  
 Výjimky mít následující vlastnosti:  
  
-   Výjimky jsou typy všechny nakonec odvozené od `System.Exception`.  
  
-   Použití `try` bloku kolem příkazů, které může vyvolat výjimky.  
  
-   Jakmile dojde k výjimce v `try` blok toku řízení přeskočí první obslužná rutina přidružená výjimka, která je k dispozici kdekoli v zásobníku volání. V jazyce C# `catch` – klíčové slovo se používá k definování obslužné rutiny výjimek.  
  
-   Pokud je k dispozici žádná obslužná rutina výjimky pro danou výjimku, program se zastaví, provádění s chybovou zprávou.  
  
-   Pokud jste ji zpracovat a nechte aplikaci v známého stavu není zachycení výjimek. Pokud jste catch `System.Exception`, opětovné pomocí `throw` – klíčové slovo na konci `catch` bloku.  
  
-   Pokud `catch` bloku definuje proměnnou výjimky, ve kterém můžete získat další informace o typu výjimka, ke které došlo k chybě.  
  
-   Výjimky může být explicitně generována program pomocí `throw` – klíčové slovo.  
  
-   Objekty výjimek obsahují podrobné informace o této chybě, jako je například stav zásobník volání a textový popis chyby.  
  
-   Kód na `finally` bloku se spustí i v případě, že je vyvolána výjimka. Použití `finally` blok k uvolnění prostředků, např. Zavřete všechny datové proudy nebo soubory, které byly otevřeny `try` bloku.  
  
-   Spravované výjimky v rozhraní .NET Framework se implementují nad zpracování mechanismus výjimek Win32 strukturovaná. Další informace najdete v tématu [strukturované zpracování výjimek (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) a [A havárií během na Depths systému Win32 strukturované zpracování výjimek](http://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).  
  
## <a name="related-sections"></a>Související oddíly  
 Najdete v následujících tématech pro další informace o výjimky a jejich zpracování:  
  
-   [Použití výjimek](../../../csharp/programming-guide/exceptions/using-exceptions.md)  
  
-   [Zpracování výjimek](../../../csharp/programming-guide/exceptions/exception-handling.md)  
  
-   [Vytváření a vyvolávání výjimek](../../../csharp/programming-guide/exceptions/creating-and-throwing-exceptions.md)  
  
-   [Výjimky generované kompilátorem](../../../csharp/programming-guide/exceptions/compiler-generated-exceptions.md)  
  
-   [Postupy: zpracování výjimky pomocí bloku try/catch (C# Průvodce programováním)](../../../csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md)  
  
-   [Postupy: Spuštění kódu čištění pomocí příkazu finally](../../../csharp/programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.SystemException>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [throw](../../../csharp/language-reference/keywords/throw.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)  
 [Výjimky](../../../standard/exceptions/index.md)  
