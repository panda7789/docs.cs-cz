---
title: Výjimky a zpracování výjimek – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: 0ba123fa9f9aacd0876f07bdf3ae7bb9159a6834
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241705"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Výjimky a jejich zpracování (Průvodce programováním v C#)

Funkce zpracování výjimek v jazyce C# vám pomůžou při práci s případnými neočekávanými nebo mimořádnými situacemi, ke kterým dochází při spuštění programu. Zpracování výjimek používá `try` `catch` `finally` klíčová slova, a k vyzkoušení akcí, které nemusí být úspěšné, pro zpracování selhání, pokud se rozhodnete, že je to vhodné, a za účelem vyčištění prostředků. Výjimky mohou být generovány modulem CLR (Common Language Runtime), rozhraním .NET nebo knihovnami třetích stran nebo pomocí kódu aplikace. Výjimky jsou vytvářeny pomocí `throw` klíčového slova.

V mnoha případech může být výjimka vyvolána metodou, kterou váš kód volá přímo, ale jinou metodou v zásobníku volání. Pokud k tomu dojde, modul CLR zruší zásobník zpět, hledá metodu s `catch` blokem pro konkrétní typ výjimky a spustí první takový `catch` blok, který nalezne. Pokud nenajde žádný odpovídající `catch` blok kdekoli v zásobníku volání, ukončí proces a zobrazí uživateli zprávu.

V tomto příkladu metoda Testuje dělení nulou a zachytí chybu. Bez zpracování výjimek by tento program byl ukončen s **DivideByZeroException** chybou.

[!code-csharp[csProgGuideExceptions#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#18)]

## <a name="exceptions-overview"></a>Přehled výjimek

Výjimky mají následující vlastnosti:

- Výjimky jsou typy, ze kterých jsou nakonec odvozeny `System.Exception` .
- Použijte `try` blok kolem příkazů, které mohou vyvolat výjimky.
- Jakmile v bloku dojde k výjimce `try` , tok řízení přejde na první přidruženou obslužnou rutinu výjimky, která je přítomna kdekoli v zásobníku volání. V jazyce C# se `catch` klíčové slovo používá k definování obslužné rutiny výjimky.
- Pokud není k dispozici žádná obslužná rutina výjimky pro danou výjimku, program zastaví provádění s chybovou zprávou.
- Nezachytit výjimku, pokud ji nemůžete zpracovat a opustit aplikaci ve známém stavu. Pokud zachytíte `System.Exception` , znovu ji vyvolejte pomocí `throw` klíčového slova na konci `catch` bloku.
- Pokud `catch` blok definuje proměnnou výjimky, můžete ji použít k získání dalších informací o typu výjimky, ke které došlo.
- Výjimky mohou být explicitně generovány programem pomocí `throw` klíčového slova.
- Objekty výjimek obsahují podrobné informace o chybě, jako je například stav zásobníku volání a textový popis chyby.
- Kód v `finally` bloku je proveden i v případě, že je vyvolána výjimka. Použijte `finally` blok k uvolnění prostředků, například pro zavření všech datových proudů nebo souborů, které byly otevřeny v `try` bloku.
- Spravované výjimky v rozhraní .NET jsou implementovány nad mechanismem zpracování strukturované výjimky Win32. Další informace naleznete v tématu [strukturované zpracování výjimek (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) a [průběh selhání na hloubkách zpracování strukturované výjimky Win32](http://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).

## <a name="related-sections"></a>Související oddíly

Další informace o zpracování výjimek a výjimek naleznete v následujících článcích:

- [Použití výjimek](using-exceptions.md)
- [Zpracování výjimek](exception-handling.md)
- [Vytváření a vyvolávání výjimek](creating-and-throwing-exceptions.md)
- [Výjimky generované kompilátorem](compiler-generated-exceptions.md)
- [Postup zpracování výjimky pomocí try/catch (Průvodce programováním v C#)](how-to-handle-an-exception-using-try-catch.md)
- [Jak provést vyčištění kódu pomocí příkazu finally](how-to-execute-cleanup-code-using-finally.md)
- [Jak zachytit výjimku nekompatibilní se specifikací CLS](how-to-catch-a-non-cls-exception.md)

## <a name="c-language-specification"></a>Specifikace jazyka C#

Další informace naleznete v tématu [výjimky](~/_csharplang/spec/exceptions.md) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také

- <xref:System.SystemException>
- [Průvodce programováním v C#](../index.md)
- [Klíčová slova jazyka C#](../../language-reference/keywords/index.md)
- [throw](../../language-reference/keywords/throw.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [Výjimky](../../../standard/exceptions/index.md)
