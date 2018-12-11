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
ms.openlocfilehash: 3a1921f1a0f0e724bfc8d8289ac1b654cc8198d2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152380"
---
# <a name="asynchronous-programming-model-apm"></a>Model asynchronního programování (APM)
Asynchronní operace, která používá <xref:System.IAsyncResult> vzoru návrhu je implementovaný jako dvě metody s názvem `BeginOperationName` a `EndOperationName` , začínat a končit asynchronní operace *OperationName* v uvedeném pořadí. Například <xref:System.IO.FileStream> třída poskytuje <xref:System.IO.FileStream.BeginRead%2A> a <xref:System.IO.FileStream.EndRead%2A> metody pro asynchronní čtení bajtů ze souboru. Tyto metody implementovat asynchronní verze <xref:System.IO.FileStream.Read%2A> metody.  
  
> [!NOTE]
>  Od verze rozhraní .NET Framework 4, poskytuje Task Parallel Library nový model pro asynchronní a paralelní programování. Další informace najdete v tématu [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) a [úkolově orientovanou asynchronní vzor (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)).  
  
 Po volání `BeginOperationName`, aplikace může pokračovat v provádění pokyny na volajícím vlákně, zatímco probíhá asynchronní operace v jiném vlákně. Pro každé volání `BeginOperationName`, také by aplikace měla zavolat `EndOperationName` získat výsledky operace.  
  
## <a name="beginning-an-asynchronous-operation"></a>Od asynchronní operace  
 `BeginOperationName` Metoda zahájí asynchronní operaci *OperationName* a vrátí objekt, který implementuje <xref:System.IAsyncResult> rozhraní. <xref:System.IAsyncResult> objekty ukládání informací o asynchronní operaci. V následující tabulce jsou uvedeny informace o asynchronní operaci.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Volitelný objekt specifické pro aplikaci, která obsahuje informace o asynchronní operaci.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|A <xref:System.Threading.WaitHandle> , který lze použít k blokování provádění aplikací až po dokončení asynchronní operace.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Hodnota, která určuje, zda asynchronní operace se dokončila ve vlákně použít k volání `BeginOperationName` místo dokončení na samostatném <xref:System.Threading.ThreadPool> vlákna.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Hodnota, která určuje, zda asynchronní operace byla dokončena.|  
  
 A `BeginOperationName` metoda přijímá všechny parametry deklarovanými jako v podpisu synchronní verzi metody, které jsou předány podle hodnoty nebo odkazu. Žádné výstupní parametry nejsou součástí `BeginOperationName` podpis metody. `BeginOperationName` Podpis metody zahrnuje také dvě další parametry. První z těchto definuje <xref:System.AsyncCallback> delegáta, který odkazuje na metodu, která je volána po dokončení asynchronní operace. Můžete určit volající `null` (`Nothing` v jazyce Visual Basic) Pokud nechce metodou vyvolán po dokončení operace. Druhý parametr další je uživatelsky definovaného objektu. Tento objekt slouží k předání informací o stavu specifické pro aplikaci metodou vyvolán po dokončení asynchronní operace. Pokud `BeginOperationName` metoda přijímá další parametry specifické pro operace, například bajtové pole pro uložení načtených ze souboru, bajtů <xref:System.AsyncCallback> a objekt stavu aplikace jsou posledními parametry v `BeginOperationName` podpis metody.  
  
 `BeginOperationName` vrátí ovládací prvek do volajícího vlákna okamžitě. Pokud `BeginOperationName` metoda vyvolá výjimek, výjimky jsou vyvolány před spuštěním asynchronní operace. Pokud `BeginOperationName` metoda vyvolá výjimky, není vyvolána metoda zpětného volání.  
  
## <a name="ending-an-asynchronous-operation"></a>Ukončení asynchronní operace  
 `EndOperationName` Metoda ukončí asynchronní operaci *OperationName*. Návratová hodnota `EndOperationName` metoda má stejný typ vrácený jejího synchronního protějšku a je specifické pro asynchronní operace. Například <xref:System.IO.FileStream.EndRead%2A> metoda vrátí počet bajtů přečtených z <xref:System.IO.FileStream> a <xref:System.Net.Dns.EndGetHostByName%2A> vrátí metoda <xref:System.Net.IPHostEntry> objekt, který obsahuje informace o hostitelském počítači. `EndOperationName` Metoda přijímá libovolné navýšení kapacity nebo parametry předávané odkazem deklarované v podpisu verzi pro synchronní metody. Kromě parametrů z synchronní metody `EndOperationName` metoda zahrnuje také <xref:System.IAsyncResult> parametru. Volající musejí předat instanci vrácenou odpovídající volání `BeginOperationName`.  
  
 Pokud asynchronní operace reprezentována <xref:System.IAsyncResult> objektu nebyl dokončen, když `EndOperationName` je volána, `EndOperationName` blokuje volající vlákno, dokud se asynchronní operace nebude dokončena. Výjimky vyvolané asynchronní operace jsou vyvolány z `EndOperationName` metody. Efekt volání `EndOperationName` metoda víckrát se stejným <xref:System.IAsyncResult> není definován. Podobně, volání `EndOperationName` metodou <xref:System.IAsyncResult> nevrátil související Begin také není definována metoda.  
  
> [!NOTE]
>  Buď nedefinované scénářů pro implementátory zvažte vyvolání <xref:System.InvalidOperationException>.  
  
> [!NOTE]
>  Implementátoři tohoto vzoru návrhu by měl oznámit volajícímu, dokončení asynchronní operace tak, že nastavíte <xref:System.IAsyncResult.IsCompleted%2A> na hodnotu true, volá metodu asynchronní zpětné volání (Pokud je zadaný) a signalizace <xref:System.IAsyncResult.AsyncWaitHandle%2A>.  
  
 Vývojáři aplikací k dispozici několik možností návrhu pro přístup k výsledky asynchronní operace. Správný výběr závisí na tom, jestli má aplikace pokyny, které můžete provést při dokončení operace. Pokud aplikace nemůže provádět žádné další práce, dokud přijímá výsledky asynchronní operaci, musí aplikace blokovat, dokud výsledky jsou k dispozici. Blokovat, dokud se asynchronní operace skončí, můžete použít jednu z následujících postupů:  
  
-   Volání `EndOperationName` z hlavního vlákna aplikace, je blokování provádění aplikací, dokud nebude operace dokončena. Příklad, který znázorňuje tuto techniku, naleznete v tématu [blokování provádění aplikace ukončením asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
-   Použití <xref:System.IAsyncResult.AsyncWaitHandle%2A> k provádění aplikace bloku, dokud nebudou dokončeny jednu nebo více operací. Příklad, který znázorňuje tuto techniku, naleznete v tématu [blokování aplikace spuštění pomocí vlastnosti AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikace, které není potřeba blokovat, zatímco se dokončují asynchronní operace můžete použít jednu z následujících postupů:  
  
-   Dotazování na provozní stav dokončení kontrolou <xref:System.IAsyncResult.IsCompleted%2A> vlastnost pravidelně a volání `EndOperationName` po dokončení operace. Příklad, který znázorňuje tuto techniku, naleznete v tématu [dotazování na stav asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
-   Použití <xref:System.AsyncCallback> delegáta určíte metodu má být volána po dokončení operace. Příklad, který znázorňuje tuto techniku, naleznete v tématu [použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [Asynchronní volání synchronních metod](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
- [Použití delegáta AsyncCallback a stavového objektu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
