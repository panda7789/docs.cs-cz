---
title: Výjimky a zpracování výjimek – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: b883012cf8f72247ff4e0b47a46eee1854e2d534
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76735658"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Výjimky a jejich zpracování (Průvodce programováním v C#)

Funkce zpracování výjimek jazyka C# vám pomohou řešit všechny neočekávané nebo výjimečné situace, ke kterým dochází při spuštění programu. Zpracování výjimek `try` `catch`používá `finally` , a klíčová slova vyzkoušet akce, které nemusí být úspěšné, ke zpracování selhání, když se rozhodnete, že je rozumné tak učinit, a vyčistit prostředky později. Výjimky mohou být generovány cltime jazyka common jazyk (CLR), rozhraním .NET Framework nebo knihovnami třetích stran nebo kódem aplikace. Výjimky jsou vytvářeny `throw` pomocí klíčového slova.

V mnoha případech může být vyvolána výjimka není metodou, která váš kód volá přímo, ale jinou metodou dále v zásobníku volání. V takovém případě CLR unwind zásobníku, hledá metodu s blokem `catch` pro konkrétní typ výjimky a provede první takový `catch` blok, který pokud najde. Pokud najde žádný `catch` vhodný blok kdekoli v zásobníku volání, ukončí proces a zobrazí zprávu uživateli.

V tomto příkladu metoda testuje dělení nulou a zachytí chybu. Bez zpracování výjimky by tento program ukončen s **DivideByZeroException byla neošetřená** chyba.

[!code-csharp[csProgGuideExceptions#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#18)]

## <a name="exceptions-overview"></a>Přehled výjimek

Výjimky mají následující vlastnosti:

- Výjimky jsou typy, které `System.Exception`všechny nakonec pocházejí z .
- Použijte `try` blok kolem příkazy, které mohou vyvolat výjimky.
- Jakmile dojde k výjimce v `try` bloku, tok řízení přeskočí na první přidruženou obslužnou rutinu výjimky, která je k dispozici kdekoli v zásobníku volání. V c# `catch` klíčové slovo se používá k definování obslužné rutiny výjimky.
- Pokud není k dispozici žádná obslužná rutina výjimky pro danou výjimku, program přestane provádět s chybovou zprávou.
- Nezachyťte výjimku, pokud ji nemůžete zpracovat a ponechat aplikaci ve známém stavu. Pokud chytíte `System.Exception`, re-throw `throw` pomocí klíčového `catch` slova na konci bloku.
- Pokud `catch` blok definuje proměnnou výjimky, můžete ji použít k získání dalších informací o typu výjimky, ke které došlo.
- Výjimky mohou být explicitně generovány `throw` programem pomocí klíčového slova.
- Objekty výjimek obsahují podrobné informace o chybě, jako je například stav zásobníku volání a textový popis chyby.
- Kód v `finally` bloku je spuštěn i v případě, že je vyvolána výjimka. Pomocí `finally` bloku uvolněte prostředky, například zavřete všechny datové `try` proudy nebo soubory, které byly otevřeny v bloku.
- Spravované výjimky v rozhraní .NET Framework jsou implementovány nad mechanismus zpracování strukturovaných výjimek Win32. Další informace naleznete [v tématech Strukturované zpracování výjimek (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) a [Crash Course na hloubkách win32 strukturované zpracování výjimek](http://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).

## <a name="related-sections"></a>Související oddíly

Další informace o výjimkách a zpracování výjimek naleznete v následujících článcích:

- [Použití výjimek](using-exceptions.md)
- [Zpracování výjimek](exception-handling.md)
- [Vytváření a vyvolávání výjimek](creating-and-throwing-exceptions.md)
- [Výjimky generované kompilátorem](compiler-generated-exceptions.md)
- [Jak zpracovat výjimku pomocí try/catch (Průvodce programováním jazyka C#)](how-to-handle-an-exception-using-try-catch.md)
- [Jak provést vyčištění kódu pomocí příkazu finally](how-to-execute-cleanup-code-using-finally.md)
- [Jak zachytit výjimku nekompatibilní se specifikací CLS](how-to-catch-a-non-cls-exception.md)

## <a name="c-language-specification"></a>Specifikace jazyka C#

For more information, see [Exceptions](~/_csharplang/spec/exceptions.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také

- <xref:System.SystemException>
- [Programovací příručka jazyka C#](../index.md)
- [C# Klíčová slova](../../language-reference/keywords/index.md)
- [throw](../../language-reference/keywords/throw.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [Výjimky](../../../standard/exceptions/index.md)
