---
title: Doporučené postupy pro návrhový vzor Pozorovatel
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- observer design pattern [.NET Framework], best practices
- best practices [.NET Framework], observer design pattern
ms.assetid: c834760f-ddd4-417f-abb7-a059679d5b8c
ms.openlocfilehash: 2da29e0baf429142707d0ddd39b1a11c13a17a90
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141535"
---
# <a name="observer-design-pattern-best-practices"></a>Doporučené postupy pro návrhový vzor Pozorovatel
V .NET Framework je vzor návrhu pozorovatele implementovaný jako sada rozhraní. Rozhraní <xref:System.IObservable%601?displayProperty=nameWithType> představuje poskytovatele dat, který je také zodpovědný za poskytování <xref:System.IDisposable> implementace, která umožňuje pozorovatelům zrušit odběr oznámení. Rozhraní <xref:System.IObserver%601?displayProperty=nameWithType> představuje pozorovatele. Toto téma popisuje osvědčené postupy, které by se měly vývojáři řídit při implementaci vzorového vzoru pozorovatele pomocí těchto rozhraní.  
  
## <a name="threading"></a>Dělení na vlákna  
 Poskytovatel obvykle implementuje metodu <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> přidáním konkrétního pozorovatele do seznamu odběratelů, který je reprezentován nějakým objektem kolekce, a implementuje metodu <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> odebráním konkrétního pozorovatele ze seznamu předplatitelů. Pozorovatel může tyto metody kdykoli zavolat. Vzhledem k tomu, že kontrakt poskytovatele/pozorovatele neurčí, kdo zodpovídá za zrušení odběru po <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> metody zpětného volání, může se stát, že se zprostředkovatel a pozorovatel pokusí odebrat stejného člena ze seznamu. Z důvodu této možnosti by měly být obě metody <xref:System.IObservable%601.Subscribe%2A> i <xref:System.IDisposable.Dispose%2A> bezpečné pro přístup z více vláken. Obvykle to zahrnuje použití [Souběžné kolekce](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md) nebo zámku. Implementace, které nejsou bezpečné pro přístup z více vláken, by měly explicitně zdokumentovat, že nejsou.  
  
 Jakékoli další záruky musí být zadány ve vrstvě nad smlouvou poskytovatele/pozorovatele. Implementátori by se jasně museli volat při zavedení dalších požadavků, aby nedocházelo k záměně uživatele pozorovatele.  
  
## <a name="handling-exceptions"></a>Zpracování výjimek  
 Z důvodu volného spojení mezi poskytovatelem dat a pozorovatelem mají výjimky v rámci vzoru pozorovatele informativní charakter. To má vliv na to, jak poskytovatelé a pozorovatelé zpracovávají výjimky v modelu návrhu pozorovatele.  
  
### <a name="the-provider----calling-the-onerror-method"></a>Zprostředkovatel – volání metody Error  
 Metoda <xref:System.IObserver%601.OnError%2A> je určena jako informační zpráva pozorovatelům, podobně jako <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> metoda. Metoda <xref:System.IObserver%601.OnNext%2A> je však navržena tak, aby poskytovala pozorovatele aktuálními nebo aktualizovanými daty, zatímco metoda <xref:System.IObserver%601.OnError%2A> je navržena tak, aby označovala, že zprostředkovatel nemůže poskytnout platná data.  
  
 Poskytovatel by měl dodržovat tyto osvědčené postupy při zpracování výjimek a volání metody <xref:System.IObserver%601.OnError%2A>:  
  
- Poskytovatel musí zpracovat své vlastní výjimky, pokud má konkrétní požadavky.  
  
- Poskytovatel by neměl očekávat nebo vyžadovat, aby pozorovatelé zpracovávala výjimky jakýmkoli způsobem.  
  
- Poskytovatel by měl volat metodu <xref:System.IObserver%601.OnError%2A>, když zpracovává výjimku, která by ohrozila schopnost poskytovat aktualizace. Informace o takových výjimkách mohou být předány pozorovateli. V jiných případech není nutné upozorňovat pozorovatele na výjimku.  
  
 Jakmile zprostředkovatel zavolá metodu <xref:System.IObserver%601.OnError%2A> nebo <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, neměla by existovat žádná další oznámení a poskytovatel může zrušit odběr svých pozorovatelů. Pozorovatelé ale můžou kdykoli zrušit odběr, včetně před i po obdržení <xref:System.IObserver%601.OnError%2A> nebo <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> oznámení. Návrhový vzor pozorovatele neurčuje, jestli je poskytovatel nebo pozorovatel zodpovědný za zrušení odběru; Proto existuje možnost, že se může pokusit odhlásit odběr. Při zrušení odběru pozorovatelé se obvykle odeberou z kolekce předplatitelů. V aplikaci s jedním vláknem by implementace <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> měla zajistit, že odkaz na objekt je platný a že objekt je členem kolekce předplatitelů před pokusem o jeho odebrání. V aplikaci s více vlákny by se měl použít objekt kolekce bezpečný pro přístup z více vláken, například objekt <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.  
  
### <a name="the-observer----implementing-the-onerror-method"></a>Pozorovatel – Implementace metody Error  
 Když pozorovatel obdrží oznámení o chybě od poskytovatele, pozorovatel by měl tuto výjimku považovat za informativní a neměl by se vyžadovat, aby provedl určitou akci.  
  
 Pozorovatel by měl dodržovat tyto osvědčené postupy při reagování na volání metody <xref:System.IObserver%601.OnError%2A> od poskytovatele:  
  
- Pozorovatel by neměl vyvolávat výjimky z jeho implementací rozhraní, například <xref:System.IObserver%601.OnNext%2A> nebo <xref:System.IObserver%601.OnError%2A>. Nicméně pokud pozorovatel vyvolá výjimky, by měl očekávat, že tyto výjimky jsou neošetřené.  
  
- Aby bylo možné zachovat zásobník volání, pozorovatel, který chce vyvolat objekt <xref:System.Exception>, který byl předán metodě <xref:System.IObserver%601.OnError%2A>, by měl před vyvoláním výjimky zabalit výjimku. Pro tento účel by měl být použit standardní objekt výjimky.  
  
## <a name="additional-best-practices"></a>Další osvědčené postupy  
 Pokus o zrušení registrace v metodě <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> může mít za následek odkaz s hodnotou null. Proto doporučujeme vyhnout se této praxi.  
  
 I když je možné připojit pozorovatele k více poskytovatelům, je doporučeným vzorem připojení instance <xref:System.IObserver%601> pouze k jedné instanci <xref:System.IObservable%601>.  
  
## <a name="see-also"></a>Viz také:

- [Návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern.md)
- [Postupy: Implementace pozorovatele](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Postupy: Implementace poskytovatele](../../../docs/standard/events/how-to-implement-a-provider.md)
