---
title: Model asynchronního programování (APM)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- starting asynchronous operations
- beginning asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming
- stopping asynchronous operations
- asynchronous programming, beginning operations
ms.assetid: c9b3501e-6bc6-40f9-8efd-4b6d9e39ccf0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 992cc1f60ee3f08131b478d2336321bf87d7ef89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573786"
---
# <a name="asynchronous-programming-model-apm"></a>Model asynchronního programování (APM)
Asynchronní operace, která používá <xref:System.IAsyncResult> vzoru návrhu je implementovaný jako dvě metody s názvem **Begin *** OperationName* a **End *** OperationName* , začínat a končit asynchronní operace *OperationName* v uvedeném pořadí. Například <xref:System.IO.FileStream> třída poskytuje <xref:System.IO.FileStream.BeginRead%2A> a <xref:System.IO.FileStream.EndRead%2A> metody asynchronně číst bajty ze souboru. Tyto metody implementovat asynchronní verzi <xref:System.IO.FileStream.Read%2A> metoda.  
  
> [!NOTE]
>  Od verze rozhraní .NET Framework 4, Task Parallel Library poskytuje nový model pro asynchronní a paralelní programování. Další informace najdete v tématu [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) a [založený na úlohách asynchronní vzor (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)).  
  
 Po volání **začít *** OperationName*, aplikace můžete pokračovat v provádění instrukcí na volající vlákno, zatímco probíhá asynchronní operaci na jiném podprocesu. Pro každé volání **začít *** OperationName*, aplikace by měly volat také **End *** OperationName* získat výsledky operace.  
  
## <a name="beginning-an-asynchronous-operation"></a>Od asynchronní operace  
 **Začít *** OperationName* metoda zahájí asynchronní operaci *OperationName* a vrátí objekt, který implementuje <xref:System.IAsyncResult> rozhraní. <xref:System.IAsyncResult> objekty ukládat informace o asynchronní operaci. V následující tabulce jsou uvedeny informace o asynchronní operaci.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Volitelné objekt specifické pro aplikace, který obsahuje informace o asynchronní operaci.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|A <xref:System.Threading.WaitHandle> , můžete se používá k blokování provádění aplikací, až do dokončení asynchronní operaci.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Hodnotu, která určuje, zda asynchronní operace byla dokončena ve vlákně používá k volání **začít *** OperationName* místo dokončení na samostatném <xref:System.Threading.ThreadPool> přístup z více vláken.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Hodnota, která označuje, zda asynchronní operace byla dokončena.|  
  
 A **začít *** OperationName* metoda přebírá parametry deklarované v podpis synchronní verzi metody, které se předávají hodnotou nebo odkazem. Žádné výstupní parametry nejsou součástí **začít *** OperationName* podpis metody. **Začít *** OperationName* podpis metody také obsahuje dva další parametry. Určuje první z nich <xref:System.AsyncCallback> delegáta, který odkazuje na metodu, která je volána při dokončení asynchronní operace. Můžete zadat volající `null` (`Nothing` v jazyce Visual Basic) Pokud nechce metoda volána, když se dokončí. Druhý parametr další je objekt definovaný uživatelem. Tento objekt umožňuje předat informace o stavu specifické pro aplikaci metoda volána, když dokončení asynchronní operace. Pokud **začít *** OperationName* metoda přebírá další parametry specifické pro operaci, jako je například bajtové pole pro uložení bajtů přečtených ze souboru, <xref:System.AsyncCallback> a objekt stavu aplikace jsou poslední parametry v **Začít *** OperationName* podpis metody.  
  
 **Začněte *** OperationName* vrátí prvek na volající vlákno okamžitě. Pokud **začít *** OperationName* metoda vyvolá výjimek, jsou výjimky vyvolány před spuštěním asynchronní operace. Pokud **začít *** OperationName* metoda vyvolá výjimek, není vyvolána metoda zpětného volání.  
  
## <a name="ending-an-asynchronous-operation"></a>Ukončení asynchronní operace  
 **End *** OperationName* metoda ukončí asynchronní operaci *OperationName*. Vrátí hodnotu, která **End *** OperationName* metoda je stejný typ vrácený jeho protějšku synchronní a je specifická pro asynchronní operace. Například <xref:System.IO.FileStream.EndRead%2A> metoda vrátí počet bajtů přečtených z <xref:System.IO.FileStream> a <xref:System.Net.Dns.EndGetHostByName%2A> metoda vrátí <xref:System.Net.IPHostEntry> objekt, který obsahuje informace o hostitelském počítači. **End *** OperationName* metoda přebírá žádný, nebo parametry ref deklarované v podpis synchronní verzi metody. Kromě parametrů z synchronní metoda **End *** OperationName* metoda zahrnuje také <xref:System.IAsyncResult> parametr. Volající musí projít instance vrácený odpovídající volání **začít *** OperationName*.  
  
 Pokud reprezentována asynchronní operaci <xref:System.IAsyncResult> objekt nebyl dokončen při **End *** OperationName* je volána, **End *** OperationName* blokuje volající vlákno až asynchronní operace byla dokončena. Výjimky vyvolané asynchronní operace jsou vyvolány z **End *** OperationName* metoda. Účinek volání **End *** OperationName* metoda víckrát se stejným <xref:System.IAsyncResult> není definován. Podobně volání **End *** OperationName* metoda s <xref:System.IAsyncResult> nebyl vrácený související Begin metoda také není definován.  
  
> [!NOTE]
>  Pro buď nedefinované scénářů, zvažte implementátory vyvolání <xref:System.InvalidOperationException>.  
  
> [!NOTE]
>  Implementátory tohoto vzoru návrhu měli oznámit volající, který asynchronní operaci dokončit nastavení <xref:System.IAsyncResult.IsCompleted%2A> na hodnotu true, volání asynchronní zpětné volání metody (Pokud byl zadán) a signalizace <xref:System.IAsyncResult.AsyncWaitHandle%2A>.  
  
 Vývojáři aplikace k dispozici několik možností návrhu pro přístup k výsledky asynchronní operaci. Správný výběr závisí na tom, jestli má aplikace pokyny, které můžete provést při dokončení operace. Pokud aplikaci nelze provést žádné další kroky, dokud neobdrží výsledky asynchronní operaci, musí aplikace zablokuje, dokud se výsledky jsou k dispozici. Blokování až do dokončení asynchronní operaci, můžete použít jednu z následujících postupů:  
  
-   Volání **End *** OperationName* z hlavního vlákna aplikace, je blokování provádění aplikací, dokud operace dokončena. Příklad, který tento postup ukazuje, naleznete v části [blokování provádění aplikace ukončením asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
-   Použití <xref:System.IAsyncResult.AsyncWaitHandle%2A> k blokování provádění aplikací, dokud nebudou dokončeny jednu nebo více operací. Příklad, který tento postup ukazuje, naleznete v části [blokování aplikace provádění pomocí vlastnosti AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikace, které není potřeba blokovat při dokončení asynchronní operace můžete použít jednu z následujících postupů:  
  
-   Dotazování pro stav dokončení operace kontrolou <xref:System.IAsyncResult.IsCompleted%2A> vlastnost pravidelně a volání **End *** OperationName* po dokončení operace. Příklad, který tento postup ukazuje, naleznete v části [dotazování na stav asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
-   Použijte <xref:System.AsyncCallback> delegáta zadat metodu má být volána po dokončení operace. Příklad, který tento postup ukazuje, naleznete v části [použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Viz také  
 [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Asynchronní volání synchronních metod](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 [Použití delegáta AsyncCallback a stavového objektu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
