---
title: Vytváření a vyvolání výjimek – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: f775a0917560a219f24329adcb1542f605d47dc2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712296"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Vytváření a vyvolávání výjimek (Průvodce programováním v C#)
Výjimky se používají k označení, že došlo k chybě při spuštění programu. Exception objekty, které popisují chybu jsou vytvořeny a pak *vyvolána* s [throw](../../language-reference/keywords/throw.md) klíčové slovo. Runtime pak vyhledá nejvíce kompatibilní obslužnou rutinu výjimky.  
  
 Programátoři by měli vyvolat výjimky, pokud je splněna jedna nebo více z následujících podmínek:  
  
- Metoda nemůže dokončit svou definovanou funkci.  
  
     Například pokud parametr metody má neplatnou hodnotu:  
  
     [!code-csharp[csProgGuideExceptions#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#12)]  
  
- Je provedeno nevhodné volání objektu na základě stavu objektu.  
  
     Jedním z příkladů může být pokus o zápis do souboru jen pro čtení. V případech, kdy stav objektu neumožňuje operaci, vyvolat instanci <xref:System.InvalidOperationException> nebo objekt založený na odvození této třídy. Toto je příklad metody, která <xref:System.InvalidOperationException> vyvolá objekt:  
  
     [!code-csharp[csProgGuideExceptions#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#13)]  
  
- Když argument metody způsobí výjimku.  
  
     V takovém případě by měla být <xref:System.ArgumentException> zachycena původní výjimka a měla by být vytvořena instance. Původní výjimka by měla být předána <xref:System.ArgumentException> <xref:System.Exception.InnerException%2A> konstruktoru jako parametr:  
  
     [!code-csharp[csProgGuideExceptions#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#14)]  
  
 Výjimky obsahují vlastnost <xref:System.Exception.StackTrace%2A>s názvem . Tento řetězec obsahuje název metody v zásobníku aktuální volání, spolu s názvem souboru a číslo řádku, kde byla vyvolána výjimka pro každou metodu. Objekt <xref:System.Exception.StackTrace%2A> je vytvořen automaticky za běhu společného jazyka (CLR) z bodu příkazu, `throw` takže výjimky musí být vyvolána z bodu, kde by měl začít trasování zásobníku.  
  
 Všechny výjimky obsahují <xref:System.Exception.Message%2A>vlastnost s názvem . Tento řetězec by měl být nastaven tak, aby vysvětlil důvod výjimky. Všimněte si, že informace, které jsou citlivé na zabezpečení by neměly být vloženy do textu zprávy. Kromě <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> obsahuje vlastnost <xref:System.ArgumentException.ParamName%2A> s názvem, který by měl být nastaven na název argumentu, který způsobil výjimku vyvolat. V případě setter vlastností, <xref:System.ArgumentException.ParamName%2A> by `value`měla být nastavena na .  
  
 Veřejné a chráněné metody by měly vyvolat výjimky vždy, když nemohou dokončit své zamýšlené funkce. Třída výjimek, která je vyvolána by měla být nejkonkrétnější výjimku k dispozici, která vyhovuje chybové podmínky. Tyto výjimky by měly být dokumentovány jako součást funkce třídy a odvozené třídy nebo aktualizace původní třídy by měly zachovat stejné chování pro zpětnou kompatibilitu.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>Co je třeba se vyhnout při vyvolání výjimky  
 Následující seznam identifikuje postupy, kterým je třeba se vyhnout při vyvolání výjimek:  
  
- Výjimky by neměly být použity ke změně toku programu jako součást běžného spuštění. Výjimky by měly být použity pouze pro hlášení a zpracování chybových stavů.  
  
- Výjimky by neměly být vráceny jako vrácená hodnota nebo parametr namísto vyvolání.  
  
- <xref:System.Exception?displayProperty=nameWithType>Neházejte <xref:System.NullReferenceException?displayProperty=nameWithType>, <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> <xref:System.SystemException?displayProperty=nameWithType>, , nebo úmyslně z vlastního zdrojového kódu.  
  
- Nevytvářejte výjimky, které mohou být vyvolány v režimu ladění, ale ne uvolnění. Chcete-li identifikovat chyby za běhu během fáze vývoje, použijte debug Assert místo.  
  
## <a name="defining-exception-classes"></a>Definování tříd výjimek  
 Programy mohou vyvolat předdefinovanou <xref:System> třídu výjimek v oboru názvů (s výjimkou případů, <xref:System.Exception>kdy je uvedeno dříve) nebo vytvořit vlastní třídy výjimek odvozením z aplikace . Odvozené třídy by měly definovat alespoň čtyři konstruktory: jeden konstruktor bez parametrů, <xref:System.Exception.Message%2A> jeden, který nastaví vlastnost message a ten, který nastaví vlastnost i vlastnosti. <xref:System.Exception.InnerException%2A> Čtvrtý konstruktor se používá k serializaci výjimky. Nové třídy výjimek by měly být serializovatelné. Například:  
  
 [!code-csharp[csProgGuideExceptions#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#15)]  
  
 Nové vlastnosti by měly být přidány do třídy výjimek pouze v případě, že data, která poskytují, jsou užitečná pro vyřešení výjimky. Pokud nové vlastnosti jsou přidány do `ToString()` odvozené třídy výjimek, by měla být přepsána vrátit přidané informace.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete v [tématu Exceptions](~/_csharplang/spec/exceptions.md) and [The throw prohlášení](~/_csharplang/spec/statements.md#the-throw-statement) v [c# specifikace jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Výjimky a zpracování výjimek](./index.md)
- [Hierarchie výjimek](../../../standard/exceptions/index.md)
- [Zpracování výjimek](./exception-handling.md)
