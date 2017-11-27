---
title: "Vytváření a vyvolávání výjimek (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4008323d264c02e0417e775077958f857ceed31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Vytváření a vyvolávání výjimek (Průvodce programováním v C#)
Výjimky jsou slouží k určení, že došlo k chybě při spuštění programu. Objekty výjimek, které popisují chybu vytvářejí a potom *vyvolána* s [throw](../../../csharp/language-reference/keywords/throw.md) – klíčové slovo. Modul runtime pak hledá nejvíce kompatibilní obslužná rutina výjimky.  
  
 Programátory by měla vyvolat výjimky, pokud jeden nebo více z následujících podmínek jsou splněny:  
  
-   Metodu nelze dokončit jeho definované funkce.  
  
     Například, pokud parametr, který se metoda má neplatnou hodnotu:  
  
     [!code-csharp[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]  
  
-   Nevhodných k objektu přišla, na základě stavu objektu.  
  
     Příkladem může být pokusu o zápis do souboru jen pro čtení. V případech, kde stav objektu neumožňuje operaci, throw instanci <xref:System.InvalidOperationException> nebo objektu na základě odvození této třídy. Jedná se o příklad metodu, která způsobí výjimku, <xref:System.InvalidOperationException> objektu:  
  
     [!code-csharp[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]  
  
-   Argument pro metodu když dojde k výjimce.  
  
     V takovém případě by měl být původní výjimka zachycena a <xref:System.ArgumentException> by měla být vytvořena instance. Původní výjimka by měla být předána konstruktoru <xref:System.ArgumentException> jako <xref:System.Exception.InnerException%2A> parametr:  
  
     [!code-csharp[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]  
  
 Výjimky obsahovat vlastnost s názvem <xref:System.Exception.StackTrace%2A>. Tento řetězec obsahuje název metody v zásobníku volání, aktuální, společně s název a řádek číslo souboru kde byla výjimka vydána pro každou metodu. A <xref:System.Exception.StackTrace%2A> objektu je vytvářena automaticky nástrojem modul CLR (CLR) od bodu `throw` příkaz tak, aby musí být vyvolány výjimky z bodu, kde by měl začínat trasování zásobníku.  
  
 Všechny výjimky obsahovat vlastnost s názvem <xref:System.Exception.Message%2A>. Tento řetězec je třeba nastavit vysvětlit důvod výjimky. Všimněte si, že informace, které jsou citlivé na zabezpečení by neměl být umístit do text zprávy. Kromě <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> obsahuje vlastnost s názvem <xref:System.ArgumentException.ParamName%2A> , musí být nastavena na název argument, který způsobil vyvolání výjimky. V případě zdroj vlastnosti <xref:System.ArgumentException.ParamName%2A> musí být nastavena na `value`.  
  
 Členy veřejné a chráněné metody by měla vyvolat výjimky, vždy, když se nemůže dokončit jejich zamýšlený funkce. Výjimka třídu, která je vyvolána by měl být k dispozici, který nejlépe odpovídá chybové stavy nejvíce výjimka. Tyto výjimky musí být zdokumentována jako součást funkcí třída a odvozené třídy nebo aktualizace původní třída musí zachovat stejné chování pro zpětnou kompatibilitu.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>Věcí, abyste se vyhnuli při vyvolání výjimek  
 Následující seznam uvádí postupy, abyste se vyhnuli při vyvolání výjimky:  
  
-   Výjimky by neměl používat ke změně toku programu jako součást obyčejnou provádění. Výjimky by měla používat jenom k vytvoření sestavy a zpracovávat chybové stavy.  
  
-   Výjimky by neměl být vrácen jako návratová hodnota nebo parametr místo hlášeny.  
  
-   Nevyvolá výjimku <xref:System.Exception?displayProperty=nameWithType>, <xref:System.SystemException?displayProperty=nameWithType>, <xref:System.NullReferenceException?displayProperty=nameWithType>, nebo <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> záměrně ze zdrojového kódu.  
  
-   Nevytvářejte výjimky, které může být vyvolána v režimu ladění, ale není režimu vydání. Běhové chyby během fáze vývoje lze zjistit ladění Assert místo.  
  
## <a name="defining-exception-classes"></a>Definování třídy výjimek  
 Programy můžete vyvolat třídu předdefinovaná výjimka <xref:System> obor názvů (s výjimkou tam, kde v předchozí části), nebo vytvořit vlastní třídy výjimek odvozené z <xref:System.Exception>. Odvozené třídy musí definovat alespoň čtyři konstruktory: jeden výchozí konstruktor, ten, který nastaví vlastnosti zprávy a ten, který nastaví i <xref:System.Exception.Message%2A> a <xref:System.Exception.InnerException%2A> vlastnosti. Čtvrtý konstruktor se používá k serializaci výjimku. Nové třídy výjimky by měla být serializovatelný. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]  
  
 Vlastnosti nového musí pouze přidaní do třídy výjimek, když jsou data, které poskytují užitečné řešení výjimku. Pokud jsou přidány nové vlastnosti do třídy odvozené výjimka `ToString()` by měla být potlačena za účelem vrátit byly přidané informace.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Výjimky a jejich zpracování](../../../csharp/programming-guide/exceptions/index.md)  
 [Hierarchie výjimek](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b)  
 [Zpracování výjimek](../../../csharp/programming-guide/exceptions/exception-handling.md)
