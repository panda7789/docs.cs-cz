---
title: Výjimky a zpracování výjimek – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: 1442daf646a29c3822d06d0b649f462b37523fe2
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002111"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Výjimky a jejich zpracování (Průvodce programováním v C#)

Funkce C# zpracování výjimek jazyka vám pomůžou pracovat s případnými neočekávanými nebo mimořádnými situacemi, ke kterým dochází při spuštění programu. Zpracování výjimek používá klíčová slova `try`, `catch` a `finally` k vyzkoušení akcí, které nemusí být úspěšné, ke zpracování selhání, pokud se rozhodnete, že je to vhodné, a k vyčištění prostředků poté. Výjimky mohou být generovány modulem CLR (Common Language Runtime), .NET Framework nebo jinými knihovnami třetích stran nebo pomocí kódu aplikace. Výjimky jsou vytvářeny pomocí klíčového slova `throw`.

V mnoha případech může být výjimka vyvolána metodou, kterou váš kód volá přímo, ale jinou metodou v zásobníku volání. Pokud k tomu dojde, modul CLR zruší zásobník zpět a hledá metodu s blokem `catch` pro konkrétní typ výjimky a spustí první takový blok `catch`, který nalezne. Pokud v zásobníku volání nenajde žádný odpovídající @no__t blok-0, proces se ukončí a zobrazí se uživateli zpráva.

V tomto příkladu metoda Testuje dělení nulou a zachytí chybu. Bez zpracování výjimek by tento program byl ukončen s **DivideByZeroException** chybou.

[!code-csharp[csProgGuideExceptions#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#18)]

## <a name="exceptions-overview"></a>Přehled výjimek

Výjimky mají následující vlastnosti:  

- Výjimky jsou typy, které nakonec jsou odvozeny z `System.Exception`.
- Použijte blok `try` kolem příkazů, které mohou vyvolat výjimky.
- Jakmile dojde k výjimce v bloku `try`, tok řízení přejde na první přidruženou obslužnou rutinu výjimky, která je přítomna kdekoli v zásobníku volání. V C#rozhraní se klíčové slovo `catch` používá k definování obslužné rutiny výjimky.
- Pokud není k dispozici žádná obslužná rutina výjimky pro danou výjimku, program zastaví provádění s chybovou zprávou.
- Nezachytit výjimku, pokud ji nemůžete zpracovat a opustit aplikaci ve známém stavu. Pokud zachytíte `System.Exception`, znovu ji vyvolejte pomocí klíčového slova `throw` na konci bloku `catch`.
- Pokud blok `catch` definuje proměnnou výjimky, můžete ji použít k získání dalších informací o typu výjimky, ke které došlo.
- Výjimky mohou být explicitně generovány programem pomocí klíčového slova `throw`.
- Objekty výjimek obsahují podrobné informace o chybě, jako je například stav zásobníku volání a textový popis chyby.
- Kód v bloku `finally` je proveden i v případě, že je vyvolána výjimka. K uvolnění prostředků použijte blok `finally`, například zavřete všechny datové proudy nebo soubory, které byly otevřeny v bloku `try`.
- Spravované výjimky v .NET Framework jsou implementovány nad mechanismem zpracování strukturované výjimky Win32. Další informace naleznete v tématu [strukturované zpracování výjimek (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) a [průběh selhání na hloubkách zpracování strukturované výjimky Win32](https://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).

## <a name="related-sections"></a>Související oddíly

Další informace o zpracování výjimek a výjimek naleznete v následujících článcích:

- [Použití výjimek](using-exceptions.md)
- [Zpracování výjimek](exception-handling.md)
- [Vytváření a vyvolávání výjimek](creating-and-throwing-exceptions.md)
- [Výjimky generované kompilátorem](compiler-generated-exceptions.md)
- [Postupy: zpracování výjimky pomocí bloku try/catch (C# Průvodce programováním)](how-to-handle-an-exception-using-try-catch.md)
- [Postupy: Spuštění kódu čištění pomocí příkazu finally](how-to-execute-cleanup-code-using-finally.md)
- [Postupy: Zachycení výjimky nekompatibilní se specifikací CLS](how-to-catch-a-non-cls-exception.md)

## <a name="c-language-specification"></a>Specifikace jazyka C#

Další informace naleznete v tématu [výjimky](~/_csharplang/spec/exceptions.md) ve [ C# specifikaci jazyka](../../language-reference/language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- <xref:System.SystemException>
- [Průvodce programováním v jazyce C#](../index.md)
- [Klíčová slova jazyka C#](../../language-reference/keywords/index.md)
- [throw](../../language-reference/keywords/throw.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [Výjimky](../../../standard/exceptions/index.md)
