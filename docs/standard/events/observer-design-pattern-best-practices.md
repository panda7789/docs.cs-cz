---
title: Doporučené postupy pro návrhový vzor Pozorovatel
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- observer design pattern [.NET Framework], best practices
- best practices [.NET Framework], observer design pattern
ms.assetid: c834760f-ddd4-417f-abb7-a059679d5b8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03b77074323346e1a26fa07dc1ec873152da356b
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519666"
---
# <a name="observer-design-pattern-best-practices"></a>Doporučené postupy pro návrhový vzor Pozorovatel
V rozhraní .NET Framework návrhový vzor pozorovatel implementované jako sada rozhraní. <xref:System.IObservable%601?displayProperty=nameWithType> Rozhraní představuje poskytovatele dat, který je také odpovídají za poskytování <xref:System.IDisposable> implementace, která umožňuje zrušit odběr oznámení pozorovatele. <xref:System.IObserver%601?displayProperty=nameWithType> Rozhraní představuje pozorovatele. Toto téma popisuje osvědčené postupy, které vývojáři by měly dodržovat při implementaci návrhový vzor pozorovatel pomocí těchto rozhraní.  
  
## <a name="threading"></a>Dělení na vlákna  
 Obvykle zprostředkovatele implementuje <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> implementuje metodu tak, že přidáte konkrétní pozorovatel k odběrateli seznamu, která je reprezentována některý objekt kolekce a <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metoda odebráním konkrétní pozorovatel ze seznamu odběratele. Pozorovatel může volat tyto metody kdykoli. Kromě toho, protože kontrakt poskytovatele/pozorovatel neurčuje kdo zodpovídá za registraci po <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> metoda zpětného volání, zprostředkovatele a pozorovatel může i pokuste se odebrat stejného člena ze seznamu. Z důvodu tuto možnost jak <xref:System.IObservable%601.Subscribe%2A> a <xref:System.IDisposable.Dispose%2A> metody by měly být bezpečné pro vlákna. Obvykle to zahrnuje použití [souběžných kolekcích](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md) nebo zámek. Implementace, které nejsou bezpečné pro vlákna musí explicitně dokumentů, které nejsou.  
  
 Žádné další záruky muset zadat ve vrstvě nad poskytovatele/pozorovatel kontraktu. Implementátory by měly volat jasně navýšení kapacity, při další požadavky, aby nedocházelo k záměně uživatele o smlouvě pozorovatel ukládají.  
  
## <a name="handling-exceptions"></a>Zpracování výjimek  
 Z důvodu volné párování mezi zprostředkovatele dat a pozorovatel výjimky v návrhovém vzoru pozorovatel mají být informativní. Tato akce ovlivní, jak poskytovatelů a pozorovatele zpracování výjimek v návrhovém vzoru pozorovatel.  
  
### <a name="the-provider----calling-the-onerror-method"></a>Poskytovatel--Volání onerror – metoda  
 <xref:System.IObserver%601.OnError%2A> Metoda je určena jako informační zpráva pro pozorovatelé, podobně jako <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> metody. Ale <xref:System.IObserver%601.OnNext%2A> metoda je navržené pro poskytování pozorovatel s aktuální nebo aktualizovaná data, zatímco <xref:System.IObserver%601.OnError%2A> metody slouží k označení, že je poskytovatel nemohl poskytnout platná data.  
  
 Poskytovatel by měl postupujte podle těchto osvědčených postupů při zpracování výjimek a volání <xref:System.IObserver%601.OnError%2A> metody:  
  
-   Zprostředkovatel musí zpracovávat své vlastní výjimky, pokud nemá žádné zvláštní požadavky.  
  
-   Poskytovatel by neměl neočekává ani nevyžaduje, pozorovatelé zpracování výjimek v konkrétním způsobem.  
  
-   Poskytovatel by měly volat <xref:System.IObserver%601.OnError%2A> metoda při zpracování výjimku, která ohrožuje schopnost poskytovat aktualizace. Informace o takové výjimky může být předán pozorovatele. V ostatních případech není nutné upozornit pozorovatelů výjimku.  
  
 Po volání zprostředkovatele <xref:System.IObserver%601.OnError%2A> nebo <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> metoda, měla by existovat žádná další upozornění a zprostředkovatele můžete zrušit jeho pozorovatelů. Ale pozorovatelů můžete také kdykoli sami, včetně před a po přijetí <xref:System.IObserver%601.OnError%2A> nebo <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> oznámení. Návrhový vzor pozorovatel není určovat, zda zprostředkovatel nebo pozorovatel zodpovídá za registraci; Proto je možné, že oba může pokus o odhlášení odběru. Obvykle když pozorovatelů zrušení odběru, jsou odebrány z kolekce předplatitele. V aplikaci s jedním vláknem <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace se ujistěte, že je odkaz na objekt platný a že objekt je členem kolekce předplatitele před pokusem o jeho odstranění. Ve vícevláknových aplikacích kolekce bezpečné pro vlákna objektu, například <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objektu, by měla sloužit.  
  
### <a name="the-observer----implementing-the-onerror-method"></a>Pozorovatel – Implementace onerror – metoda  
 Když pro pozorovatele, který obdrží oznámení o chybě od poskytovatele, pozorovatel měli považovat za výjimku informační a by neměl muset provádět žádnou konkrétní akci.  
  
 Pozorovatel by měl dodržovat tyto osvědčené postupy při odpovídání na <xref:System.IObserver%601.OnError%2A> volání metody ze zprostředkovatele:  
  
-   Pozorovatel by neměla vyvolávat výjimky z jeho implementací rozhraní, jako například <xref:System.IObserver%601.OnNext%2A> nebo <xref:System.IObserver%601.OnError%2A>. Pokud pozorovatel vyvolat výjimky, ho byste však očekávat tyto výjimky přejít neošetřená.  
  
-   Pro zachování zásobník volání, pozorovatele, který chce throw <xref:System.Exception> objekt, který byl předán jeho <xref:System.IObserver%601.OnError%2A> metoda zalamován výjimky před vyvoláním ho. Standardní výjimka objektu by měla sloužit pro tento účel.  
  
## <a name="additional-best-practices"></a>Další doporučené postupy  
 Pokus o zrušení registrace v <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metoda může mít za následek odkaz s hodnotou null. Proto doporučujeme, abyste tento postup.  
  
 I když je možné se připojit k více poskytovatelů pozorovatele, je doporučený model pro připojení <xref:System.IObserver%601> instance má pouze jeden <xref:System.IObservable%601> instance.  
  
## <a name="see-also"></a>Viz také:

- [Návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern.md)  
- [Postupy: Implementace pozorovatele](../../../docs/standard/events/how-to-implement-an-observer.md)  
- [Postupy: Implementace poskytovatele](../../../docs/standard/events/how-to-implement-a-provider.md)
