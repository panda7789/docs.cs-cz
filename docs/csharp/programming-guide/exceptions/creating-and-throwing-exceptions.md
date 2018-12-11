---
title: Vytváření a vyvolávání výjimek - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: c7775de75ddbf274f3a1555c9f0daaf63bbee713
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235342"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Vytváření a vyvolávání výjimek (Průvodce programováním v C#)
Výjimky jsou slouží k označení, že došlo k chybě při spuštění programu. Jsou vytvořeny objektech výjimek, které popisují chybu a pak *vyvolána* s [throw](../../../csharp/language-reference/keywords/throw.md) – klíčové slovo. Modul runtime hledá pak nejkompatibilnější obslužná rutina výjimky.  
  
 Programátoři vyvoláním výjimky, pokud jeden nebo více z následujících podmínek jsou splněny:  
  
-   Metoda nemůže dokončit jeho definované funkce.  
  
     Například, pokud má neplatnou hodnotu parametru do metody:  
  
     [!code-csharp[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]  
  
-   Je provedeno nevhodný volání na objekt, na základě stavu objektu.  
  
     Jedním z příkladů může být pokusu o zápis do souboru jen pro čtení. V případech, kdy stav objektu neumožňuje operaci throw instance <xref:System.InvalidOperationException> nebo objekt podle odvození z této třídy. Toto je příklad, který vyvolá metodu <xref:System.InvalidOperationException> objektu:  
  
     [!code-csharp[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]  
  
-   Pokud argument metody způsobí výjimku.  
  
     V takovém případě by měl být původní výjimka zachycena a <xref:System.ArgumentException> by měla být vytvořena instance. Původní výjimky by měly být předány konstruktoru <xref:System.ArgumentException> jako <xref:System.Exception.InnerException%2A> parametr:  
  
     [!code-csharp[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]  
  
 Výjimky obsahovat vlastnost s názvem <xref:System.Exception.StackTrace%2A>. Tento řetězec obsahuje název metody na aktuální zásobník volání, společně s souboru název a číslo řádku kde byla výjimka vydána pro jednotlivé metody. A <xref:System.Exception.StackTrace%2A> modulem common language runtime (CLR) od bodu je automaticky vytvořen objekt `throw` příkaz, aby výjimky musí být vyvolány z bodu, ve kterém chcete spustit trasování zásobníku.  
  
 Všechny výjimky obsahovat vlastnost s názvem <xref:System.Exception.Message%2A>. Řetězec by měl být nastaven na vysvětluje důvod výjimky. Všimněte si, že informace, které jsou citlivé na zabezpečení by neměl umístěny v textu zprávy. Kromě <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> obsahuje vlastnost s názvem <xref:System.ArgumentException.ParamName%2A> , který musí být nastavená na název argumentu, která způsobila vyvolání výjimky. V případě vlastnost setter <xref:System.ArgumentException.ParamName%2A> by mělo být nastavené `value`.  
  
 Veřejné a chráněné metody by měla vyvolat výjimky pokaždé, když se jejich odpovídající funkce, nelze provést. Třída výjimky, která je vyvolána by měla být k dispozici, který vyhovuje chybové stavy nejvíce specifické výjimky. Tyto výjimky musí být zdokumentována jako součást funkce třídy a odvozené třídy nebo aktualizace původní třídy musí zachovat stejné chování z důvodu zpětné kompatibility.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>Se vyvarovat při vyvolávání výjimek  
 Následující seznam uvádí nedoporučované postupy při vyvolání výjimky:  
  
-   Výjimky by neměly použít ke změně tok programu jako součást běžné provedení. Výjimky by měla sloužit pouze k hlášení a zpracování podmínek chyby.  
  
-   Výjimky by neměl vrátit jako návratová hodnota nebo parametr namísto vyvolání.  
  
-   Nevyvolávat <xref:System.Exception?displayProperty=nameWithType>, <xref:System.SystemException?displayProperty=nameWithType>, <xref:System.NullReferenceException?displayProperty=nameWithType>, nebo <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> záměrně ze zdrojového kódu.  
  
-   Nevytvářejte výjimky, které mohou být vyvolány v režimu ladění, ale ne ve verzi. K identifikaci chyby za běhu ve vývojové fázi, použijte kontrolní výraz ladění.  
  
## <a name="defining-exception-classes"></a>Definování třídy výjimek  
 Programy může vrátit třídu předdefinovaná výjimka <xref:System> oboru názvů (s výjimkou tam, kde si předtím poznamenali), nebo vytvořit vlastní výjimky třídy odvozené z <xref:System.Exception>. Odvozené třídy by měl definovat alespoň čtyři konstruktory: jeden výchozí konstruktor, ten, který nastaví vlastnost zprávy a ten, který nastaví i <xref:System.Exception.Message%2A> a <xref:System.Exception.InnerException%2A> vlastnosti. Čtvrtý konstruktor se používá k serializaci výjimku. Nové třídy výjimky by měly být serializovatelný. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]  
  
 Data, která poskytují slouží k vytvoření řešení výjimky by měly nové vlastnosti pouze přidat třídu výjimky. Pokud jsou přidány nové vlastnosti do třídy odvozená výjimka `ToString()` by měla být potlačena za účelem vrácení byly přidané informace.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace najdete v tématu [výjimky](~/_csharplang/spec/exceptions.md) a [příkazu throw](~/_csharplang/spec/statements.md#the-throw-statement) v [ C# specifikace jazyka](../../language-reference/language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Výjimky a jejich zpracování](../../../csharp/programming-guide/exceptions/index.md)  
- [Hierarchie výjimek](../../../standard/exceptions/index.md)  
- [Zpracování výjimek](../../../csharp/programming-guide/exceptions/exception-handling.md)
