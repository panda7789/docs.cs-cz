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
ms.openlocfilehash: 0a9ea3c8c9c589bb5954fa9771ffd1bb095f6d73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140139"
---
# <a name="asynchronous-programming-model-apm"></a>Model asynchronního programování (APM)
Asynchronní operace, která <xref:System.IAsyncResult> používá návrhový vzor je `BeginOperationName` `EndOperationName` implementována jako dvě metody s názvem a které začínají a ukončují asynchronní operaci *OperationName* v uvedeném pořadí. Například <xref:System.IO.FileStream> třída poskytuje <xref:System.IO.FileStream.BeginRead%2A> a <xref:System.IO.FileStream.EndRead%2A> metody asynchronně číst bajty ze souboru. Tyto metody implementují asynchronní <xref:System.IO.FileStream.Read%2A> verzi metody.  
  
> [!NOTE]
> Počínaje rozhraním .NET Framework 4 poskytuje paralelní knihovna úloh nový model pro asynchronní a paralelní programování. Další informace naleznete v [tématu Paralelní knihovna úloh (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) a [Asynchronní vzor založený na úlohách (TAP).](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
  
 Po `BeginOperationName`volání aplikace můžete pokračovat v provádění pokynů na volající vlákno, zatímco asynchronní operace probíhá v jiném vlákně. Pro každé `BeginOperationName`volání aplikace by `EndOperationName` měla také volat získat výsledky operace.  
  
## <a name="beginning-an-asynchronous-operation"></a>Zahájení asynchronní operace  
 Metoda `BeginOperationName` spustí asynchronní operaci *OperationName* a vrátí objekt, <xref:System.IAsyncResult> který implementuje rozhraní. <xref:System.IAsyncResult>objekty ukládají informace o asynchronní operaci. V následující tabulce jsou uvedeny informace o asynchronní operaci.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Volitelný objekt specifický pro aplikaci, který obsahuje informace o asynchronní operaci.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|A, <xref:System.Threading.WaitHandle> který lze použít k zablokování spuštění aplikace, dokud nebude dokončena asynchronní operace.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Hodnota, která označuje, zda asynchronní operace dokončena `BeginOperationName` ve vlákně <xref:System.Threading.ThreadPool> slouží k volání namísto dokončení v samostatném vlákně.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Hodnota, která označuje, zda byla dokončena asynchronní operace.|  
  
 Metoda `BeginOperationName` přebírá všechny parametry deklarované v podpisu synchronní verze metody, které jsou předány hodnotou nebo odkazem. Všechny out parametry nejsou `BeginOperationName` součástí podpisu metody. Podpis `BeginOperationName` metody také obsahuje dva další parametry. První z nich definuje <xref:System.AsyncCallback> delegáta, který odkazuje na metodu, která je volána po dokončení asynchronní operace. Volající může `null` určit`Nothing` (v jazyce Visual Basic), pokud nechce, aby byla metoda vyvolána po dokončení operace. Druhý další parametr je uživatelem definovaný objekt. Tento objekt lze předat informace o stavu specifické pro aplikaci na metodu vyvolána po dokončení asynchronní operace. Pokud `BeginOperationName` metoda trvá další parametry specifické pro operaci, jako je například bajtové <xref:System.AsyncCallback> pole pro uložení bajtů `BeginOperationName` číst ze souboru, a objekt stavu aplikace jsou poslední parametry v podpisu metody.  
  
 `BeginOperationName`okamžitě vrátí ovládací prvek volajícímu vláknu. Pokud `BeginOperationName` metoda vyvolá výjimky, výjimky jsou vyvolány před spuštěním asynchronní operace. Pokud `BeginOperationName` metoda vyvolá výjimky, metoda zpětného volání není vyvolána.  
  
## <a name="ending-an-asynchronous-operation"></a>Ukončení asynchronní operace  
 Metoda `EndOperationName` ukončí asynchronní operaci *OperationName*. Vrácená hodnota `EndOperationName` metody je stejný typ vrácený jeho synchronní protějšek a je specifické pro asynchronní operace. <xref:System.IO.FileStream.EndRead%2A> Metoda například vrátí počet bajtů přečtených <xref:System.IO.FileStream> z <xref:System.Net.Dns.EndGetHostByName%2A> a <xref:System.Net.IPHostEntry> a metoda vrátí objekt, který obsahuje informace o hostitelském počítači. Metoda `EndOperationName` přebírá všechny out nebo ref parametry deklarované v podpisu synchronní verze metody. Kromě parametrů ze synchronní metody `EndOperationName` metoda zahrnuje také <xref:System.IAsyncResult> parametr. Volající musí předat instanci vrácenou `BeginOperationName`odpovídajícím voláním společnosti .  
  
 Pokud asynchronní operace reprezentovaná <xref:System.IAsyncResult> objektem nebyla dokončena, když `EndOperationName` je volána, `EndOperationName` blokuje volající vlákno, dokud není dokončena asynchronní operace. Výjimky vyzývané asynchronní operace `EndOperationName` jsou vyvolány z metody. Účinek volání `EndOperationName` metody vícekrát se <xref:System.IAsyncResult> stejným není definován. Podobně volání `EndOperationName` metody s, <xref:System.IAsyncResult> která nebyla vrácena související Begin metoda také není definována.  
  
> [!NOTE]
> Pro některý z nedefinovaných scénářů by <xref:System.InvalidOperationException>měli implementátoři zvážit vyvolání .  
  
> [!NOTE]
> Implementátoři tohoto návrhového vzoru by měli volajícímu oznámit, <xref:System.IAsyncResult.IsCompleted%2A> že asynchronní operace byla dokončena nastavením na hodnotu <xref:System.IAsyncResult.AsyncWaitHandle%2A>true, voláním metody zpětného volání asynchronní (pokud byla zadána) a signalizací .  
  
 Vývojáři aplikací mají několik možností návrhu pro přístup k výsledkům asynchronní operace. Správná volba závisí na tom, zda aplikace obsahuje pokyny, které lze spustit po dokončení operace. Pokud aplikace nemůže provádět žádné další práce, dokud neobdrží výsledky asynchronní operace, aplikace musí blokovat, dokud výsledky nejsou k dispozici. Chcete-li blokovat, dokud nebude dokončena asynchronní operace, můžete použít jeden z následujících přístupů:  
  
- Volání `EndOperationName` z hlavního vlákna aplikace, blokování spuštění aplikace, dokud není operace dokončena. Příklad, který ilustruje tuto techniku, naleznete [v tématu blokování spuštění aplikace ukončením asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
- Použijte <xref:System.IAsyncResult.AsyncWaitHandle%2A> k zablokování spuštění aplikace, dokud nebude dokončena jedna nebo více operací. Příklad, který ilustruje tuto techniku, naleznete [v tématu blokování spuštění aplikace pomocí AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikace, které není nutné blokovat, zatímco asynchronní operace dokončí můžete použít jeden z následujících přístupů:  
  
- Dotazování pro dokončení operace <xref:System.IAsyncResult.IsCompleted%2A> stavu pravidelně kontrolu `EndOperationName` vlastnosti a volání po dokončení operace. Příklad, který ilustruje tuto techniku, naleznete [v tématu Dotazování pro stav asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
- <xref:System.AsyncCallback> Delegát slouží k určení metody, která má být vyvolána po dokončení operace. Příklad, který ilustruje tuto techniku, naleznete [v tématu použití asyncCallback delegát a ukončit asynchronní operaci](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Asynchronní volání synchronních metod](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [Použití delegáta AsyncCallback a stavového objektu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
