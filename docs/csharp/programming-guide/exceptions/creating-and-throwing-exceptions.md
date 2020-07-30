---
title: Vytváření a vyvolávání výjimek – Průvodce programováním v C#
description: Přečtěte si informace o vytváření a vyvolávání výjimek. Výjimky slouží k označení toho, že při spuštění programu došlo k chybě.
ms.date: 07/20/2015
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: 8ab10dbf686def8d169ef3239492e3b618e9d297
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302045"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Vytváření a vyvolávání výjimek (Průvodce programováním v C#)
Výjimky se používají k označení toho, že při spuštění programu došlo k chybě. Objekty výjimek, které popisují chybu, jsou vytvořeny a následně *vyvolány* pomocí klíčového slova [throw](../../language-reference/keywords/throw.md) . Modul runtime pak vyhledá nejvíce kompatibilní obslužnou rutinu výjimky.  
  
 Programátoři by měli vyvolat výjimky, pokud jsou splněné některé z následujících podmínek:  
  
- Metoda nemůže dokončit své definované funkce.  
  
     Například pokud má parametr pro metodu neplatnou hodnotu:  
  
     [!code-csharp[csProgGuideExceptions#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#12)]  
  
- Na základě stavu objektu je provedeno nevhodné volání objektu.  
  
     Jedním příkladem může být pokus o zápis do souboru určeného jen pro čtení. V případech, kdy stav objektu neumožňuje operaci, vyvolat instanci <xref:System.InvalidOperationException> nebo objekt na základě odvození této třídy. Toto je příklad metody, která vyvolá <xref:System.InvalidOperationException> objekt:  
  
     [!code-csharp[csProgGuideExceptions#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#13)]  
  
- Když argument metody způsobí výjimku.  
  
     V takovém případě by měla být zachytila původní výjimka a <xref:System.ArgumentException> měla by být vytvořena instance. Původní výjimka by měla být předána konstruktoru <xref:System.ArgumentException> jako <xref:System.Exception.InnerException%2A> parametr:  
  
     [!code-csharp[csProgGuideExceptions#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#14)]  
  
 Výjimky obsahují vlastnost s názvem <xref:System.Exception.StackTrace%2A> . Tento řetězec obsahuje název metod v aktuálním zásobníku volání spolu s názvem souboru a číslem řádku, kde byla výjimka vyvolána pro každou metodu. <xref:System.Exception.StackTrace%2A>Objekt je vytvořen automaticky modulem CLR (Common Language Runtime) z místa `throw` příkazu, takže výjimky musí být vyvolány z místa, kde by mělo být trasování zásobníku zahájeno.  
  
 Všechny výjimky obsahují vlastnost s názvem <xref:System.Exception.Message%2A> . Tento řetězec by měl být nastaven na vysvětlení důvodu výjimky. Všimněte si, že informace, které jsou citlivé na zabezpečení, by neměly být vloženy do textu zprávy. Kromě <xref:System.Exception.Message%2A> <xref:System.ArgumentException> obsahuje vlastnost s názvem <xref:System.ArgumentException.ParamName%2A> , která by měla být nastavena na název argumentu, který způsobil výjimku vyvolání. V případě vlastnosti setter <xref:System.ArgumentException.ParamName%2A> by měla být nastavena na `value` .  
  
 Veřejné a chráněné metody by měly vyvolat výjimky pokaždé, když nemohou dokončit své zamýšlené funkce. Vyvolaná Třída výjimky by měla být nejvíce specifická výjimka, která je dostupná pro chybové podmínky. Tyto výjimky by měly být zdokumentovány jako součást funkce třídy a odvozené třídy nebo aktualizace původní třídy by měly zachovávat stejné chování pro zpětnou kompatibilitu.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>Věci, které je potřeba zabránit při vyvolávání výjimek  
 Následující seznam uvádí postupy, které se vyhne při vyvolávání výjimek:  
  
- Výjimky by neměly být použity ke změně toku programu v rámci běžného provádění. Výjimky by měly být použity pouze k hlášení a zpracování chybových podmínek.  
  
- Výjimky by neměly být vráceny jako návratová hodnota nebo parametr namísto vyvolání.  
  
- Nevolejte <xref:System.Exception?displayProperty=nameWithType> , <xref:System.SystemException?displayProperty=nameWithType> <xref:System.NullReferenceException?displayProperty=nameWithType> nebo <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> úmyslně z vlastního zdrojového kódu.  
  
- Nevytvářejte výjimky, které mohou být vyvolány v režimu ladění, ale ne v režimu vydání. Chcete-li identifikovat běhové chyby během fáze vývoje, použijte místo toho příkaz Debug Assert.  
  
## <a name="defining-exception-classes"></a>Definování tříd výjimek  
 Programy mohou vyvolat předdefinované třídy výjimek v <xref:System> oboru názvů (s výjimkou výše uvedeného) nebo vytvořit vlastní třídy výjimek odvozené z <xref:System.Exception> . Odvozené třídy by měly definovat alespoň čtyři konstruktory: jeden konstruktor bez parametrů, jeden, který nastaví vlastnost Message a jeden, který nastaví <xref:System.Exception.Message%2A> <xref:System.Exception.InnerException%2A> vlastnosti a. Čtvrtý konstruktor slouží k serializaci výjimky. Nové třídy výjimek by měly být serializovatelné. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#15)]  
  
 Nové vlastnosti by měly být přidány do třídy výjimek pouze v případě, že data, která poskytují, jsou užitečná pro vyřešení výjimky. Pokud jsou do odvozené třídy Exception přidány nové vlastnosti, `ToString()` měly by být přepsány, aby vracely přidané informace.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete v tématu [výjimky](~/_csharplang/spec/exceptions.md) a [příkaz throw](~/_csharplang/spec/statements.md#the-throw-statement) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Výjimky a zpracování výjimek](./index.md)
- [Hierarchie výjimek](../../../standard/exceptions/index.md)
- [Zpracování výjimek](./exception-handling.md)
