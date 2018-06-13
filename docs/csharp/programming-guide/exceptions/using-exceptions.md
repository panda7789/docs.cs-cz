---
title: Použití výjimek (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 43012ec1190117b1905b5e44010d5f57a1e543aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339823"
---
# <a name="using-exceptions-c-programming-guide"></a>Použití výjimek (Průvodce programováním v C#)
V jazyce C# chyby v programu v době běhu rozšířeny prostřednictvím programu pomocí mechanismus názvem výjimky. Výjimky vyvolané kód, který dojde k chybě a zachytila kód, který můžete chybu opravit. Výjimky může být vyvolána pomocí rozhraní .NET Framework common language runtime (CLR) nebo pomocí kódu v programu. Jakmile je vyvolána výjimka, rozšíří zásobníkem volání až `catch` se nachází příkaz pro výjimku. Nezachycená výjimky jsou zpracovávány obslužná rutina obecná výjimka poskytované systémem, který se zobrazí dialogové okno.  
  
 Výjimky jsou reprezentované pomocí třídy odvozené od třídy <xref:System.Exception>. Tato třída identifikuje typ výjimky a obsahuje vlastnosti, které mají podrobnosti o výjimce. Došlo k výjimce zahrnuje vytvoření instance třídy odvozené výjimky, volitelně konfigurace vlastností výjimky a pak vyvolání objekt pomocí `throw` – klíčové slovo. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#1](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_1.cs)]  
  
 Jakmile je vyvolána výjimka, modul runtime zkontroluje aktuální příkaz a zkontrolujte, zda je v rámci `try` bloku. Pokud se jedná, všechny `catch` bloky přidružené `try` bloku se kontroluje, zda jejich zachycení výjimky. `Catch` bloky obvykle zadat typy výjimek; Pokud typ `catch` blok je stejného typu jako výjimka nebo základní třída výjimky, `catch` bloku dokáže zpracovat metodu. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#2](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_2.cs)]  
  
 Pokud příkaz, který vyvolá výjimku, není v `try` bloku nebo, pokud `try` bloku, která obklopuje ho má neexistuje odpovídající `catch` bloku, modul runtime zkontroluje volání metody pro `try` příkaz a `catch` bloky. Modul runtime pokračuje v až zásobník volání hledání kompatibilní `catch` bloku. Po `catch` bloku nalezen a provést, ovládací prvek předává do další příkazu, po který `catch` bloku.  
  
 A `try` příkaz může obsahovat více než jednu `catch` bloku. První `catch` je spustit příkaz, který může zpracovat výjimku; všechny následující `catch` příkazy, i když jsou kompatibilní, jsou ignorovány. Proto catch – bloky je vždy třeba seřadit od nejvíce konkrétní (nebo většinou odvozených) nejméně specifická. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#3](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_3.cs)]  
  
 Před `catch` bloku se spustí, zkontroluje modulu runtime pro `finally` bloky. `Finally` bloky povolit programátorů vyčistit všechny nejednoznačný stavu, který může být zbyly ze přerušené `try` bloku, nebo chcete-li uvolnit všechny externí prostředky (například zpracovává grafiky, připojení databáze nebo souboru datové proudy) bez čekání uvolňování paměti kolekce v modulu runtime pro dokončení objekty. Příklad:  
  
 [!code-csharp[csProgGuideExceptions#4](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_4.cs)]  
  
 Pokud `WriteByte()` došlo k výjimce, kód za sekundu `try` blok, který se pokusí znovu otevřete soubor selže, pokud `file.Close()` není volán, a soubor by zůstat zamčené. Protože `finally` bloky provedení i v případě, že je vyvolána výjimka, `finally` bloku v předchozím příkladu umožňuje pro soubor, který má být správně uzavřený a pomáhá zabránit k chybě.  
  
 Pokud žádné kompatibilní `catch` bloku se nachází v zásobníku volání po je vyvolána výjimka, dojde k jedné z následujících způsobů:  
  
-   Pokud byla výjimka v rámci finalizační metody, finalizační metodu byla přerušena a základní finalizační metodu, pokud existuje, je volána.  
  
-   Pokud obsahuje zásobník volání statického konstruktoru nebo inicializátoru statické pole <xref:System.TypeInitializationException> je vyvolána, s výjimkou původní přiřazené <xref:System.Exception.InnerException%2A> vlastnost novou výjimku.  
  
-   Když je dosaženo začátku vlákno, je ukončen vlákno.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Výjimky a jejich zpracování](../../../csharp/programming-guide/exceptions/index.md)
