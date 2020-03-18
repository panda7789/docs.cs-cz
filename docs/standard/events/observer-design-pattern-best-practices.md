---
title: Doporučené postupy pro návrhový vzor Pozorovatel
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- observer design pattern [.NET Framework], best practices
- best practices [.NET Framework], observer design pattern
ms.assetid: c834760f-ddd4-417f-abb7-a059679d5b8c
ms.openlocfilehash: 2da29e0baf429142707d0ddd39b1a11c13a17a90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141535"
---
# <a name="observer-design-pattern-best-practices"></a>Doporučené postupy pro návrhový vzor Pozorovatel
V rozhraní .NET Framework je návrhový vzor pozorovatele implementován jako sada rozhraní. Rozhraní <xref:System.IObservable%601?displayProperty=nameWithType> představuje zprostředkovatele dat, který je <xref:System.IDisposable> také zodpovědný za poskytování implementace, která umožňuje pozorovatelům odhlásit z oznámení. Rozhraní <xref:System.IObserver%601?displayProperty=nameWithType> představuje pozorovatele. Toto téma popisuje osvědčené postupy, které by vývojáři měli dodržovat při implementaci návrhového vzoru pozorovatele pomocí těchto rozhraní.  
  
## <a name="threading"></a>Dělení na vlákna  
 Obvykle zprostředkovatel implementuje <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metodu přidáním konkrétní ho pozorovatele do seznamu odběratelů, který <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> je reprezentován některé objekt kolekce a implementuje metodu odebráním konkrétní pozorovatel ze seznamu odběratelů. Pozorovatel může tyto metody kdykoli volat. Kromě toho vzhledem k tomu, že smlouva zprostředkovatele nebo pozorovatele <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> neurčuje, kdo je zodpovědný za odhlášení po metodě zpětného volání, může se zprostředkovatel i pozorovatel pokusit odebrat stejného člena ze seznamu. Z důvodu této možnosti <xref:System.IDisposable.Dispose%2A> a metody by měly <xref:System.IObservable%601.Subscribe%2A> být bezpečné pro přístup z více vláken. Obvykle to zahrnuje použití [souběžné kolekce](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md) nebo zámek. Implementace, které nejsou bezpečné pro přístup z více vláken, by měly explicitně dokumentovat, že nejsou.  
  
 Jakékoli další záruky musí být specifikovány ve vrstvě nad smlouvou zprostředkovatele/pozorovatele. Implementátoři by měli jasně volat, když ukládají další požadavky, aby se zabránilo záměně uživatelů ohledně smlouvy o pozorovateli.  
  
## <a name="handling-exceptions"></a>Zpracování výjimek  
 Z důvodu volné párování mezi zprostředkovatelem dat a pozorovatele výjimky ve vzoru návrhu pozorovatele jsou určeny jako informační. To má vliv na způsob, jakým zprostředkovatelé a pozorovatelé zpracovávají výjimky ve vzoru návrhu pozorovatele.  
  
### <a name="the-provider----calling-the-onerror-method"></a>Zprostředkovatel – volání metody OnError  
 Metoda <xref:System.IObserver%601.OnError%2A> je určena jako informační zpráva pro pozorovatele, podobně jako <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> metoda. <xref:System.IObserver%601.OnNext%2A> Metoda je však navržena tak, aby poskytla pozorovateli <xref:System.IObserver%601.OnError%2A> aktuální nebo aktualizovaná data, zatímco metoda je navržena tak, aby označovala, že zprostředkovatel není schopen poskytnout platná data.  
  
 Zprostředkovatel by měl dodržovat tyto osvědčené postupy <xref:System.IObserver%601.OnError%2A> při zpracování výjimek a volání metody:  
  
- Zprostředkovatel musí zpracovat své vlastní výjimky, pokud má nějaké zvláštní požadavky.  
  
- Zprostředkovatel by neměl očekávat nebo vyžadovat, aby pozorovatelé zpracovávali výjimky žádným konkrétním způsobem.  
  
- Zprostředkovatel by měl <xref:System.IObserver%601.OnError%2A> volat metodu při zpracovává výjimku, která ohrožuje jeho schopnost poskytovat aktualizace. Informace o těchto výjimkách mohou být předány pozorovateli. V ostatních případech není nutné oznamovat pozorovatelům výjimku.  
  
 Jakmile poskytovatel volá <xref:System.IObserver%601.OnError%2A> <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> nebo metodu, by měla být žádná další oznámení a zprostředkovatel může odhlásit své pozorovatele. Pozorovatelé se však mohou kdykoli odhlásit, a to jak <xref:System.IObserver%601.OnError%2A> <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> před, tak po obdržení oznámení nebo oznámení. Vzor návrhu pozorovatele neurčuje, zda zprostředkovatel nebo pozorovatel je zodpovědný za odhlášení. proto existuje možnost, že se oba mohou pokusit o odhlášení. Obvykle při pozorovatelé odhlásit, jsou odebrány z kolekce odběratelů. V aplikaci s jedním <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> podprocesem by implementace měla zajistit, že odkaz na objekt je platný a že objekt je členem kolekce předplatitelů před pokusem o jeho odebrání. V aplikaci s více vlákny by měl být <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> použit objekt kolekce bezpečný pro přístup z více vláken, například objekt.  
  
### <a name="the-observer----implementing-the-onerror-method"></a>Pozorovatel -- Implementace metody OnError  
 Když pozorovatel obdrží oznámení o chybě od zprostředkovatele, pozorovatel by měl považovat výjimku za informační a nemělo by být požadováno, aby přijalo žádnou konkrétní akci.  
  
 Pozorovatel by měl dodržovat tyto osvědčené <xref:System.IObserver%601.OnError%2A> postupy při odpovídání na volání metody od zprostředkovatele:  
  
- Pozorovatel by neměl vyvolat výjimky z jeho <xref:System.IObserver%601.OnNext%2A> implementace <xref:System.IObserver%601.OnError%2A>rozhraní, například nebo . Však pokud pozorovatel vyvolat výjimky, by měl očekávat, že tyto výjimky přejít neošetřené.  
  
- Chcete-li zachovat zásobník volání, pozorovatel, <xref:System.Exception> který chce vyvolat <xref:System.IObserver%601.OnError%2A> objekt, který byl předán jeho metoda by měla zabalit výjimku před vyvoláním. Pro tento účel by měl být použit objekt standardní výjimky.  
  
## <a name="additional-best-practices"></a>Další doporučené postupy  
 Pokus o zrušení registrace <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> v metodě může mít za následek odkaz null. Proto doporučujeme vyhnout se této praxi.  
  
 I když je možné připojit pozorovatele k více zprostředkovatelům, doporučeným vzorem <xref:System.IObserver%601> je připojení instance pouze k jedné <xref:System.IObservable%601> instanci.  
  
## <a name="see-also"></a>Viz také

- [Návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern.md)
- [Postupy: Implementace pozorovatele](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Postupy: Implementace poskytovatele](../../../docs/standard/events/how-to-implement-a-provider.md)
