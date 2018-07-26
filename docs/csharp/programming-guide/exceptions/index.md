---
title: Výjimky a jejich zpracování (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: de396ca4da2e115d221036d3ec49fb7b43d3d21d
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244264"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Výjimky a jejich zpracování (Průvodce programováním v C#)
Funkce nápovědy pro zpracování výjimek jazyka C# zacházet s nečekaným nebo výjimečné situace, ke kterým dochází při spuštění programu. Používá pro zpracování výjimek `try`, `catch`, a `finally` klíčová slova vyzkoušet akce, které nemusí proběhnout úspěšně, zpracování selhání, pokud se rozhodnete, že je přijatelné, provedete to tak a následně vyčistit prostředky. Výjimky mohou být generovány modulem common language runtime (CLR), rozhraní .NET Framework nebo jakékoli knihovny třetích stran nebo kódem aplikace. Výjimky jsou vytvářeny instalační sadou `throw` – klíčové slovo.  
  
 V mnoha případech výjimky mohou být vyvolány nejsou metodu, která obsahuje váš kód volat přímo, ale jinou metodou níže v zásobníku volání. Pokud k tomu dojde, modul CLR bude vrátit zásobník, hledají metodu s `catch` block pro konkrétním typem výjimky a provede první takové `catch` blokovat, že pokud najde. Pokud najde žádné odpovídající `catch` blokovat kdekoli v zásobníku volání, bude proces ukončit a zobrazit zprávu uživateli.  
  
 V tomto příkladu metoda testů pro dělení nulou a zachytí chyby. Bez zpracování výjimek, tento program by jej měla ukončit s **dividebyzeroexception – neošetřené** chyby.  
  
 [!code-csharp[csProgGuideExceptions#18](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exceptions-and-exception-handling_1.cs)]  
  
## <a name="exceptions-overview"></a>Přehled výjimek  
 Výjimky mají následující vlastnosti:  
  
-   Výjimky jsou typy, které jsou odvozeny všechny nakonec z `System.Exception`.  
  
-   Použití `try` bloku kolem příkazy, které můžou vyvolat výjimku.  
  
-   Jakmile dojde k výjimce v `try` blokovat, toku řízení přeskočí první obslužná rutina přidružené výjimky, která je k dispozici kdekoli v zásobníku volání. V jazyce C# `catch` – klíčové slovo se používá k definování obslužné rutiny výjimky.  
  
-   Pokud je k dispozici žádná obslužná rutina výjimky pro danou výjimku, program se zastaví provádění s chybovou zprávou.  
  
-   Nezachycujte výjimky, pokud jste ji zpracovat a nechte aplikaci do známého stavu. Při zachycení `System.Exception`, znovu ho pomocí `throw` klíčového slova na konci `catch` bloku.  
  
-   Pokud `catch` bloku definuje proměnnou výjimek, použijte ho k získání dalších informací o typu výjimky, ke které došlo.  
  
-   Výjimky mohou být explicitně generovány programu pomocí `throw` – klíčové slovo.  
  
-   Objekty výjimky obsahují podrobné informace o chybě, jako je například stav zásobník volání a textový popis chyby.  
  
-   V kódu `finally` blok je spuštěn i v případě, že dojde k výjimce. Použití `finally` bloku k uvolnění prostředků, třeba když chcete zavřít všechny datové proudy nebo soubory, které byly otevřeny `try` bloku.  
  
-   Spravované výjimky v rozhraní .NET Framework se implementuje nad mechanismus zpracování výjimek strukturované Win32. Další informace najdete v tématu [strukturovaného zpracování výjimek (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) a [A havárií kurz na Hlubin systému Win32 strukturovaného zpracování výjimek](http://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).  
  
## <a name="related-sections"></a>Související oddíly  
 Zobrazit další informace o výjimkách a zpracování výjimek v následujících tématech:  
  
-   [Použití výjimek](../../../csharp/programming-guide/exceptions/using-exceptions.md)  
  
-   [Zpracování výjimek](../../../csharp/programming-guide/exceptions/exception-handling.md)  
  
-   [Vytváření a vyvolávání výjimek](../../../csharp/programming-guide/exceptions/creating-and-throwing-exceptions.md)  
  
-   [Výjimky generované kompilátorem](../../../csharp/programming-guide/exceptions/compiler-generated-exceptions.md)  
  
-   [Postupy: zpracování výjimky pomocí bloku try/catch (C# Programming Guide)](../../../csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md)  
  
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
