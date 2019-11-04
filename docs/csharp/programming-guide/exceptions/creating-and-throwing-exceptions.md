---
title: Vytváření a vyvolávání výjimek C# – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: dfc852722531c06f986f54221ad094b13496561f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417940"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Vytváření a vyvolávání výjimek (Průvodce programováním v C#)
Výjimky se používají k označení toho, že při spuštění programu došlo k chybě. Objekty výjimek, které popisují chybu, jsou vytvořeny a následně *vyvolány* pomocí klíčového slova [throw](../../language-reference/keywords/throw.md) . Modul runtime pak vyhledá nejvíce kompatibilní obslužnou rutinu výjimky.  
  
 Programátoři by měli vyvolat výjimky, pokud jsou splněné některé z následujících podmínek:  
  
- Metoda nemůže dokončit své definované funkce.  
  
     Například pokud má parametr pro metodu neplatnou hodnotu:  
  
     [!code-csharp[csProgGuideExceptions#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#12)]  
  
- Na základě stavu objektu je provedeno nevhodné volání objektu.  
  
     Jedním příkladem může být pokus o zápis do souboru určeného jen pro čtení. V případech, kdy stav objektu neumožňuje operaci, vyvolat instanci <xref:System.InvalidOperationException> nebo objekt na základě odvození této třídy. Toto je příklad metody, která vyvolá objekt <xref:System.InvalidOperationException>:  
  
     [!code-csharp[csProgGuideExceptions#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#13)]  
  
- Když argument metody způsobí výjimku.  
  
     V takovém případě by měla být zachycena původní výjimka a měla by být vytvořena instance <xref:System.ArgumentException>. Původní výjimka by měla být předána konstruktoru <xref:System.ArgumentException> jako parametr <xref:System.Exception.InnerException%2A>:  
  
     [!code-csharp[csProgGuideExceptions#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#14)]  
  
 Výjimky obsahují vlastnost s názvem <xref:System.Exception.StackTrace%2A>. Tento řetězec obsahuje název metod v aktuálním zásobníku volání spolu s názvem souboru a číslem řádku, kde byla výjimka vyvolána pro každou metodu. Objekt <xref:System.Exception.StackTrace%2A> je automaticky vytvořen modulem CLR (Common Language Runtime) z místa příkazu `throw`, takže výjimky musí být vyvolány z místa, kde by mělo být trasování zásobníku zahájeno.  
  
 Všechny výjimky obsahují vlastnost s názvem <xref:System.Exception.Message%2A>. Tento řetězec by měl být nastaven na vysvětlení důvodu výjimky. Všimněte si, že informace, které jsou citlivé na zabezpečení, by neměly být vloženy do textu zprávy. Kromě <xref:System.Exception.Message%2A>obsahuje <xref:System.ArgumentException> vlastnost s názvem <xref:System.ArgumentException.ParamName%2A>, která by měla být nastavena na název argumentu, který způsobil výjimku vyvolání. V případě metody setter vlastnosti by <xref:System.ArgumentException.ParamName%2A> měla být nastavena na hodnotu `value`.  
  
 Veřejné a chráněné metody by měly vyvolat výjimky pokaždé, když nemohou dokončit své zamýšlené funkce. Vyvolaná Třída výjimky by měla být nejvíce specifická výjimka, která je dostupná pro chybové podmínky. Tyto výjimky by měly být zdokumentovány jako součást funkce třídy a odvozené třídy nebo aktualizace původní třídy by měly zachovávat stejné chování pro zpětnou kompatibilitu.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>Věci, které je potřeba zabránit při vyvolávání výjimek  
 Následující seznam uvádí postupy, které se vyhne při vyvolávání výjimek:  
  
- Výjimky by neměly být použity ke změně toku programu v rámci běžného provádění. Výjimky by měly být použity pouze k hlášení a zpracování chybových podmínek.  
  
- Výjimky by neměly být vráceny jako návratová hodnota nebo parametr namísto vyvolání.  
  
- Nevolejte <xref:System.Exception?displayProperty=nameWithType>, <xref:System.SystemException?displayProperty=nameWithType>, <xref:System.NullReferenceException?displayProperty=nameWithType>nebo <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> úmyslně z vlastního zdrojového kódu.  
  
- Nevytvářejte výjimky, které mohou být vyvolány v režimu ladění, ale ne v režimu vydání. Chcete-li identifikovat běhové chyby během fáze vývoje, použijte místo toho příkaz Debug Assert.  
  
## <a name="defining-exception-classes"></a>Definování tříd výjimek  
 Programy mohou vyvolat předdefinovanou třídu výjimky v oboru názvů <xref:System> (s výjimkou výše uvedených) nebo vytvořit vlastní třídy výjimek odvozenou z <xref:System.Exception>. Odvozené třídy by měly definovat alespoň čtyři konstruktory: jeden konstruktor bez parametrů, jeden, který nastaví vlastnost Message a jeden, který nastaví <xref:System.Exception.Message%2A> a <xref:System.Exception.InnerException%2A> vlastností. Čtvrtý konstruktor slouží k serializaci výjimky. Nové třídy výjimek by měly být serializovatelné. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#15)]  
  
 Nové vlastnosti by měly být přidány do třídy výjimek pouze v případě, že data, která poskytují, jsou užitečná pro vyřešení výjimky. Pokud jsou do odvozené třídy Exception přidány nové vlastnosti, `ToString()` by měly být přepsány, aby vracely přidané informace.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete v tématu [výjimky](~/_csharplang/spec/exceptions.md) a [příkaz throw](~/_csharplang/spec/statements.md#the-throw-statement) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Výjimky a jejich zpracování](./index.md)
- [Hierarchie výjimek](../../../standard/exceptions/index.md)
- [Zpracování výjimek](./exception-handling.md)
