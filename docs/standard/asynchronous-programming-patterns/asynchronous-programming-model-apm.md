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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140139"
---
# <a name="asynchronous-programming-model-apm"></a>Model asynchronního programování (APM)
Asynchronní operace, která používá model návrhu <xref:System.IAsyncResult>, je implementována jako dvě metody s názvem `BeginOperationName` a `EndOperationName`, které začínají a končí *operací* asynchronní operace. Například třída <xref:System.IO.FileStream> poskytuje metody <xref:System.IO.FileStream.BeginRead%2A> a <xref:System.IO.FileStream.EndRead%2A> pro asynchronní čtení bajtů ze souboru. Tyto metody implementují asynchronní verzi metody <xref:System.IO.FileStream.Read%2A>.  
  
> [!NOTE]
> Počínaje .NET Framework 4 poskytuje úloha paralelní knihovna nový model pro asynchronní a paralelní programování. Další informace naleznete v tématu [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) a [asynchronní vzor založený na úlohách (klepněte)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)).  
  
 Po volání `BeginOperationName`může aplikace pokračovat ve zpracování instrukcí volajícího vlákna, zatímco asynchronní operace probíhá v jiném vlákně. Pro každé volání `BeginOperationName`by měla aplikace také volat `EndOperationName`, aby získala výsledky operace.  
  
## <a name="beginning-an-asynchronous-operation"></a>Zahájení asynchronní operace  
 Metoda `BeginOperationName` zahájí asynchronní operaci *Operational a vrátí* objekt, který implementuje rozhraní <xref:System.IAsyncResult>. <xref:System.IAsyncResult> objekty ukládají informace o asynchronní operaci. Následující tabulka obsahuje informace o asynchronní operaci.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Volitelný objekt specifický pro aplikaci, který obsahuje informace o asynchronní operaci.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|<xref:System.Threading.WaitHandle>, které lze použít k blokování provádění aplikace, dokud se asynchronní operace nedokončí.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Hodnota, která označuje, zda byla asynchronní operace dokončena ve vlákně použitém pro volání `BeginOperationName` namísto dokončení na samostatném vlákně <xref:System.Threading.ThreadPool>.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Hodnota, která označuje, zda byla asynchronní operace dokončena.|  
  
 Metoda `BeginOperationName` přebírá všechny parametry deklarované v signatuře synchronní verze metody, která je předána hodnotou nebo odkazem. Parametry out nejsou součástí signatury metody `BeginOperationName`. Signatura metody `BeginOperationName` také obsahuje dva další parametry. První z nich definuje delegáta <xref:System.AsyncCallback>, který odkazuje na metodu, která je volána po dokončení asynchronní operace. Volající může určit `null` (`Nothing` v Visual Basic), pokud nechce, aby metoda vyvolala po dokončení operace. Druhým dalším parametrem je objekt definovaný uživatelem. Tento objekt lze použít k předání informací o stavu specifického pro aplikaci do metody vyvolané při dokončení asynchronní operace. Pokud metoda `BeginOperationName` přebírá další parametry specifické pro operaci, jako je například bajtové pole pro uložení bajtů čtených ze souboru, objekt stavu <xref:System.AsyncCallback> a aplikace jsou poslední parametry v signatuře metody `BeginOperationName`.  
  
 `BeginOperationName` vrátí řízení volajícímu vláknu okamžitě. Pokud metoda `BeginOperationName` vyvolá výjimky, výjimky jsou vyvolány před zahájením asynchronní operace. Pokud metoda `BeginOperationName` vyvolá výjimky, metoda zpětného volání není vyvolána.  
  
## <a name="ending-an-asynchronous-operation"></a>Ukončení asynchronní operace  
 Metoda `EndOperationName` ukončí *operaci operace*asynchronní operace. Návratová hodnota metody `EndOperationName` je stejný typ vrácený jeho synchronním protějškem a je specifický pro asynchronní operaci. Například metoda <xref:System.IO.FileStream.EndRead%2A> vrátí počet přečtených bajtů z <xref:System.IO.FileStream> a metoda <xref:System.Net.Dns.EndGetHostByName%2A> vrátí objekt <xref:System.Net.IPHostEntry>, který obsahuje informace o hostitelském počítači. Metoda `EndOperationName` přebírá jakékoli nebo ref parametry deklarované v signatuře synchronní verze metody. Kromě parametrů z synchronní metody `EndOperationName` metoda také obsahuje parametr <xref:System.IAsyncResult>. Volající musí předat instanci vrácenou odpovídajícím voláním `BeginOperationName`.  
  
 Pokud asynchronní operace reprezentované objektem <xref:System.IAsyncResult> nebyla při volání `EndOperationName` dokončena, `EndOperationName` blokuje volající vlákno, dokud nebude dokončena asynchronní operace. Výjimky vyvolané asynchronní operací jsou vyvolány z metody `EndOperationName`. Účinek volání metody `EndOperationName` několikrát se stejným <xref:System.IAsyncResult> není definován. Stejně tak volání metody `EndOperationName` s <xref:System.IAsyncResult>, která nebyla vrácena související metodou Begin, není definována také.  
  
> [!NOTE]
> Pro některý z nedefinovaných scénářů by implementátor měli zvážit vyvolání <xref:System.InvalidOperationException>.  
  
> [!NOTE]
> Implementátori tohoto vzoru návrhu by měli oznámit volajícímu, že asynchronní operace byla dokončena, nastavením <xref:System.IAsyncResult.IsCompleted%2A> na hodnotu true, volání asynchronní metody zpětného volání (Pokud byla zadána) a signalizace <xref:System.IAsyncResult.AsyncWaitHandle%2A>.  
  
 Vývojáři aplikací mají několik možností návrhu pro přístup k výsledkům asynchronní operace. Správná volba závisí na tom, zda má aplikace pokyny, které mohou být provedeny při dokončení operace. Pokud aplikace nemůže provést žádnou další práci, dokud neobdrží výsledky asynchronní operace, aplikace musí blokovat, dokud nebudou k dispozici výsledky. Chcete-li zablokovat až po dokončení asynchronní operace, můžete použít jeden z následujících přístupů:  
  
- Volání `EndOperationName` z hlavního vlákna aplikace, blokování spuštění aplikace až do dokončení operace. Příklad, který znázorňuje tuto techniku, naleznete v tématu [blokování provádění aplikace ukončením asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
- Použijte <xref:System.IAsyncResult.AsyncWaitHandle%2A> k blokování provádění aplikace, dokud nebude dokončena jedna nebo více operací. Příklad, který znázorňuje tuto techniku, naleznete v tématu [blokování spuštění aplikace pomocí AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikace, které nepotřebují blokovat během dokončení asynchronní operace, mohou použít jeden z následujících přístupů:  
  
- Cyklické dotazování na stav dokončení operace zaškrtnutím vlastnosti <xref:System.IAsyncResult.IsCompleted%2A> pravidelně a volání `EndOperationName` po dokončení operace. Příklad, který znázorňuje tuto techniku, naleznete v tématu [cyklické dotazování na stav asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
- Použijte delegáta <xref:System.AsyncCallback> k určení metody, která se má vyvolat po dokončení operace. Příklad, který znázorňuje tuto techniku, naleznete v tématu [použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Asynchronní volání synchronních metod](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [Použití delegáta AsyncCallback a stavového objektu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
