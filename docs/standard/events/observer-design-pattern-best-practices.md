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
ms.openlocfilehash: 030b62688ba8985a2659769fe20b6ae527471df5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="observer-design-pattern-best-practices"></a>Doporučené postupy pro návrhový vzor Pozorovatel
Návrhový vzor pozorovatel je v rozhraní .NET Framework, implementované jako sada rozhraní. <xref:System.IObservable%601?displayProperty=nameWithType> Rozhraní představuje poskytovatele dat, který je také zajišťuje <xref:System.IDisposable> implementace, která umožňuje pozorovatelů zrušit odběr oznámení. <xref:System.IObserver%601?displayProperty=nameWithType> Rozhraní představuje pozorovatele. Toto téma popisuje osvědčené postupy, které vývojáři postupujte při implementaci návrhový vzor pozorovatel pomocí těchto rozhraní.  
  
## <a name="threading"></a>Dělení na vlákna  
 Obvykle se implementuje poskytovatele <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metoda přidáním konkrétní pozorovatel k seznamu odběratelů, která je reprezentována některé objektu kolekce a implementuje <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metoda odebráním konkrétní pozorovatel ze seznamu odběratele. Pozorovatel můžete kdykoli volání těchto metod. Kromě toho, protože kontrakt poskytovatele/pozorovatel neurčuje který zodpovídá za po odhlášení musí být <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> metoda zpětného volání, zprostředkovatele a pozorovatel obě pokusit stejného člena odebrat ze seznamu. Z důvodu této možnosti jak <xref:System.IObservable%601.Subscribe%2A> a <xref:System.IDisposable.Dispose%2A> metody by měly být bezpečné pro přístup z více vláken. Obvykle to zahrnuje použití [souběžných kolekce](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md) nebo zámek. Implementace, které nejsou bezpečné pro přístup z více vláken musí explicitně dokumentů, které nejsou.  
  
 Žádné další záruky nutné zadávat ve vrstvě nad poskytovatele/pozorovatel kontrakt. Implementátory by měly volat jasně, když ukládají další požadavky, aby nedocházelo k záměně uživatele o smlouvě pozorovatel.  
  
## <a name="handling-exceptions"></a>Zpracování výjimek  
 Z důvodu volné párování mezi zprostředkovatele dat a pozorovatele výjimky v návrhovém vzoru pozorovatel měla být informační. To má vliv jak zprostředkovatelé a pozorovatelů zpracování výjimek v návrhovém vzoru pozorovatel.  
  
### <a name="the-provider----calling-the-onerror-method"></a>Poskytovatel--Volání OnError – metoda  
 <xref:System.IObserver%601.OnError%2A> Metoda je určena jako informační zpráva k pozorovatelů, podobně jako <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> metoda. Ale <xref:System.IObserver%601.OnNext%2A> metoda je určená k poskytnutí pozorovatele s aktuální nebo aktualizovaná data, zatímco <xref:System.IObserver%601.OnError%2A> metoda slouží k označení, že je zprostředkovatel nepodařilo poskytnout platná data.  
  
 Zprostředkovatel postupujte tyto osvědčené postupy při zpracování výjimek a volání <xref:System.IObserver%601.OnError%2A> metoda:  
  
-   Zprostředkovatel musí zpracovávat své vlastní výjimky, pokud má žádné zvláštní požadavky.  
  
-   Zprostředkovatel by neměl očekávat nebo vyžadovat, aby pozorovatelů zpracování výjimek žádným způsobem konkrétní.  
  
-   Zprostředkovatel by měly volat <xref:System.IObserver%601.OnError%2A> metoda při zpracování výjimka, která ohrožuje jeho schopnost poskytovat aktualizace. Informace o takové výjimky mohou být předána do pozorovatel. V ostatních případech je třeba oznamovat pozorovatelů výjimku.  
  
 Po volání zprostředkovatele <xref:System.IObserver%601.OnError%2A> nebo <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> metoda, měla by existovat žádná další oznámení a zprostředkovatele můžete zrušit jeho pozorovatelů. Však pozorovatelů můžete taky kdykoli sami, včetně i před a po přijetí <xref:System.IObserver%601.OnError%2A> nebo <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> oznámení. Návrhový vzor pozorovatel není určují, zda zprostředkovatel nebo pozorovatel je zodpovědná za odhlášením; Proto je možné, že oba pokusit k odhlášení odběru. Obvykle když pozorovatelů odhlásit, jsou odebrány z kolekce odběratele. V aplikaci jednovláknové <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace se ujistěte, že je odkaz na objekt platný a že objekt je členem kolekce odběratele před pokusem o jeho odebrání. V aplikaci s více vlákny, kolekce bezpečné pro přístup z více vláken objektu, například <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objektu, by měla být použita.  
  
### <a name="the-observer----implementing-the-onerror-method"></a>Pozorovatel – Implementace OnError – metoda  
 Když pozorovatele obdrží oznámení o chybě od poskytovatele, pozorovatel měli považovat za výjimku informační a neměli nutné provádět žádnou zvláštní akci.  
  
 Pozorovatel postupujte při odpovědi na tyto osvědčené postupy <xref:System.IObserver%601.OnError%2A> volání metody od zprostředkovatele:  
  
-   Pozorovatel nesmí vyvolat výjimky z jeho implementace rozhraní, jako <xref:System.IObserver%601.OnNext%2A> nebo <xref:System.IObserver%601.OnError%2A>. Ale pokud pozorovatel generování výjimek, by měl očekávat tyto přejděte neošetřené výjimky.  
  
-   Pro zachování zásobníku volání, pozorovatele, který chce throw <xref:System.Exception> objekt, který byl předán jeho <xref:System.IObserver%601.OnError%2A> metoda má obtékat výjimka před vyvoláním ho. Objekt standardní výjimky by měla použít pro tento účel.  
  
## <a name="additional-best-practices"></a>Další doporučené postupy  
 Probíhá pokus o zrušení registrace v <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metoda může mít za následek odkaz s hodnotou null. Proto doporučujeme, abyste tento postup.  
  
 Přestože je možné připojit k více poskytovatelů pozorovatele, doporučené vzor je pro připojení <xref:System.IObserver%601> instance, která má jenom jeden <xref:System.IObservable%601> instance.  
  
## <a name="see-also"></a>Viz také  
 [Návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern.md)  
 [Postupy: Implementace pozorovatele](../../../docs/standard/events/how-to-implement-an-observer.md)  
 [Postupy: Implementace poskytovatele](../../../docs/standard/events/how-to-implement-a-provider.md)
