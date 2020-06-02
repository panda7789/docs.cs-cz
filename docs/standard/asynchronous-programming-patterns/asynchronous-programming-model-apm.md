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
ms.openlocfilehash: 96ad18e613d68ee97f4e5666afe77febadc6f991
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289977"
---
# <a name="asynchronous-programming-model-apm"></a>Model asynchronního programování (APM)
Asynchronní operace, která používá <xref:System.IAsyncResult> vzor návrhu, je implementována jako dvě metody s názvem `BeginOperationName` `EndOperationName` , které začínají a končí *operací* asynchronní operace. Například <xref:System.IO.FileStream> Třída poskytuje <xref:System.IO.FileStream.BeginRead%2A> <xref:System.IO.FileStream.EndRead%2A> metody a pro asynchronní čtení bajtů ze souboru. Tyto metody implementují asynchronní verze <xref:System.IO.FileStream.Read%2A> metody.  
  
> [!NOTE]
> Počínaje .NET Framework 4 poskytuje úloha paralelní knihovna nový model pro asynchronní a paralelní programování. Další informace naleznete v tématu [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) a [asynchronní vzor založený na úlohách (klepněte)](task-based-asynchronous-pattern-tap.md)).  
  
 Po volání `BeginOperationName` může aplikace pokračovat ve zpracování instrukcí volajícího vlákna, zatímco asynchronní operace probíhá v jiném vlákně. Pro každé volání `BeginOperationName` aplikace by měla aplikace také volat, `EndOperationName` aby získala výsledky operace.  
  
## <a name="beginning-an-asynchronous-operation"></a>Zahájení asynchronní operace  
 `BeginOperationName`Metoda spustí *operaci* asynchronní operace a vrátí objekt, který implementuje <xref:System.IAsyncResult> rozhraní. <xref:System.IAsyncResult>objekty ukládají informace o asynchronní operaci. Následující tabulka obsahuje informace o asynchronní operaci.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Volitelný objekt specifický pro aplikaci, který obsahuje informace o asynchronní operaci.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|Objekt <xref:System.Threading.WaitHandle> , který lze použít k blokování provádění aplikace až do dokončení asynchronní operace.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Hodnota, která označuje, zda byla asynchronní operace dokončena ve vlákně použitém pro volání `BeginOperationName` namísto dokončení v samostatném <xref:System.Threading.ThreadPool> vlákně.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Hodnota, která označuje, zda byla asynchronní operace dokončena.|  
  
 `BeginOperationName`Metoda přebírá všechny parametry deklarované v signatuře synchronní verze metody, která je předána hodnotou nebo odkazem. Parametry out nejsou součástí `BeginOperationName` signatury metody. `BeginOperationName`Signatura metody také obsahuje dva další parametry. První z těchto definuje <xref:System.AsyncCallback> delegát, který odkazuje na metodu, která je volána po dokončení asynchronní operace. Volající může určit `null` ( `Nothing` v Visual Basic), pokud nechce, aby metoda vyvolala po dokončení operace. Druhým dalším parametrem je objekt definovaný uživatelem. Tento objekt lze použít k předání informací o stavu specifického pro aplikaci do metody vyvolané při dokončení asynchronní operace. Pokud `BeginOperationName` Metoda přijímá další parametry specifické pro operaci, jako je například bajtové pole pro uložení bajtů čtených ze souboru, <xref:System.AsyncCallback> objekt stavu aplikace a jsou poslední parametry v `BeginOperationName` signatuře metody.  
  
 `BeginOperationName`vrátí řízení volajícímu vláknu okamžitě. Pokud `BeginOperationName` metoda vyvolá výjimky, výjimky jsou vyvolány před zahájením asynchronní operace. Pokud `BeginOperationName` metoda vyvolá výjimky, metoda zpětného volání není vyvolána.  
  
## <a name="ending-an-asynchronous-operation"></a>Ukončení asynchronní operace  
 `EndOperationName`Metoda ukončí *operaci*asynchronní operace. Návratová hodnota `EndOperationName` metody je stejný typ vrácený jeho synchronním protějškem a je specifický pro asynchronní operaci. Například <xref:System.IO.FileStream.EndRead%2A> Metoda vrátí počet bajtů načtených z <xref:System.IO.FileStream> a a <xref:System.Net.Dns.EndGetHostByName%2A> Metoda vrátí <xref:System.Net.IPHostEntry> objekt, který obsahuje informace o hostitelském počítači. `EndOperationName`Metoda přebírá jakékoli nebo ref parametry deklarované v signatuře synchronní verze metody. Kromě parametrů z synchronní metody `EndOperationName` obsahuje metoda také <xref:System.IAsyncResult> parametr. Volající musí předat instanci vrácenou odpovídajícím voláním metody `BeginOperationName` .  
  
 Pokud se asynchronní operace reprezentované <xref:System.IAsyncResult> objektem nedokončila při `EndOperationName` volání metody, `EndOperationName` blokuje volající vlákno, dokud nebude dokončena asynchronní operace. Výjimky vyvolané asynchronní operací jsou vyvolány z `EndOperationName` metody. Účinek volání `EndOperationName` metody víckrát se stejným způsobem není <xref:System.IAsyncResult> definován. Podobně není `EndOperationName` definováno volání metody s objektem <xref:System.IAsyncResult> , který nebyl vrácen související metodou Begin.  
  
> [!NOTE]
> Pro některý z nedefinovaných scénářů by měly implementátori zvážit vyvolání <xref:System.InvalidOperationException> .  
  
> [!NOTE]
> Implementátori tohoto návrhového vzoru by měl oznámit volajícímu, že asynchronní operace byla dokončena <xref:System.IAsyncResult.IsCompleted%2A> , nastavením na hodnotu true, volání asynchronní metody zpětného volání (Pokud byla zadána) a signalizace <xref:System.IAsyncResult.AsyncWaitHandle%2A> .  
  
 Vývojáři aplikací mají několik možností návrhu pro přístup k výsledkům asynchronní operace. Správná volba závisí na tom, zda má aplikace pokyny, které mohou být provedeny při dokončení operace. Pokud aplikace nemůže provést žádnou další práci, dokud neobdrží výsledky asynchronní operace, aplikace musí blokovat, dokud nebudou k dispozici výsledky. Chcete-li zablokovat až po dokončení asynchronní operace, můžete použít jeden z následujících přístupů:  
  
- Zavolejte `EndOperationName` z hlavního vlákna aplikace a zablokujte spuštění aplikace až do dokončení operace. Příklad, který znázorňuje tuto techniku, naleznete v tématu [blokování provádění aplikace ukončením asynchronní operace](blocking-application-execution-by-ending-an-async-operation.md).  
  
- Použijte <xref:System.IAsyncResult.AsyncWaitHandle%2A> k blokování provádění aplikace, dokud nebude dokončena jedna nebo více operací. Příklad, který znázorňuje tuto techniku, naleznete v tématu [blokování spuštění aplikace pomocí AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikace, které nepotřebují blokovat během dokončení asynchronní operace, mohou použít jeden z následujících přístupů:  
  
- Cyklické dotazování na stav dokončení operace zaškrtnutím <xref:System.IAsyncResult.IsCompleted%2A> vlastnosti pravidelně a volání `EndOperationName` po dokončení operace. Příklad, který znázorňuje tuto techniku, naleznete v tématu [cyklické dotazování na stav asynchronní operace](polling-for-the-status-of-an-asynchronous-operation.md).  
  
- Použijte <xref:System.AsyncCallback> delegáta k určení metody, která se má vyvolat po dokončení operace. Příklad, který znázorňuje tuto techniku, naleznete v tématu [použití delegáta AsyncCallback k ukončení asynchronní operace](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na událostech (EAP)](event-based-asynchronous-pattern-eap.md)
- [Asynchronní volání synchronních metod](calling-synchronous-methods-asynchronously.md)
- [Použití delegáta AsyncCallback a stavového objektu](using-an-asynccallback-delegate-and-state-object.md)
