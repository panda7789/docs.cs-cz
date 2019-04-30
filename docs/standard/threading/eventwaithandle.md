---
title: EventWaitHandle
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], EventWaitHandle class
- EventWaitHandle class
- event wait handles [.NET Framework]
- threading [.NET Framework], cross-process synchronization
ms.assetid: 11ee0b38-d663-4617-b793-35eb6c64e9fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc2ed1a450921452dee894caeb52c477d501b573
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61926347"
---
# <a name="eventwaithandle"></a>EventWaitHandle
<xref:System.Threading.EventWaitHandle> Třída umožňuje vlákna ke komunikaci mezi sebou signalizace a čeká na signál. Obslužné rutiny události čekání (také označované jednoduše jako události) jsou obslužné rutiny čekání, které mohou být signalizovanými, aby verze jednoho nebo více čekajících vláken. Po to bylo signalizováno, popisovače čekání události se vynuluje, ručně nebo automaticky. <xref:System.Threading.EventWaitHandle> Může představovat buď místní události popisovač čekání (místní události), nebo událost s názvem systému počkat popisovač (s názvem události nebo viditelné pro všechny procesy systémové události).  
  
> [!NOTE]
>  Obslužné rutiny čekání událostí nejsou .NET [události](../events/index.md). Neexistují žádné delegáty nebo obslužné rutiny události zahrnuté. Slova "událost" slouží k popisu je vzhledem k tomu, že se mají tradičně se označuje jako událostí operačního systému, a vzhledem k tomu, že v rámci signalizace popisovač čekání znamená čekajících vláken, která došlo k události.  
  
 Obslužné rutiny čekání i místní a pojmenované události pomocí synchronizace systémové objekty, které jsou chráněny <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> obálky zajistit uvolnění prostředků. Můžete použít <xref:System.Threading.WaitHandle.Dispose%2A> metodu pro uvolnění prostředků ihned po dokončení používání objektu.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Obslužné rutiny čekání události, které automaticky obnovit  
 Vytvořit událost automatického obnovení tak, že zadáte <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> při vytváření <xref:System.Threading.EventWaitHandle> objektu. Jak již název napovídá, tato událost synchronizace obnoví automaticky při signalizován po uvolnění jedno vlákno čekání. Signalizuje, že události po zavolání jeho <xref:System.Threading.EventWaitHandle.Set%2A> metoda.  
  
 Automatický reset události se obvykle používají k poskytování exkluzivní přístup k prostředku pro jedno vlákno v čase. Vlákno požadavek na prostředek voláním <xref:System.Threading.WaitHandle.WaitOne%2A> metody. Pokud žádné jiné vlákno drží popisovač čekání, metoda vrátí `true` a volajícího vlákna má ovládací prvek prostředku.  
  
> [!IMPORTANT]
>  Stejně jako u všech mechanismů synchronizace, musíte zajistit, že všechny cesty kódu čekání na popisovač odpovídající čekání před přístupem k chráněnému prostředku. Synchronizace vláken je kooperativní.  
  
 Pokud automatický reset událost je signalizována při žádná vlákna čekající, zůstane signalizovaného, dokud vlákno pokusy o čekání na něj. Události uvolní vlákna a okamžitě resetuje, blokování následné vlákna.  
  
## <a name="event-wait-handles-that-reset-manually"></a>Obslužné rutiny čekání události, které ručně obnovit  
 Vytvoření ruční vynulování události tak, že zadáte <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> při vytváření <xref:System.Threading.EventWaitHandle> objektu. Jak již název napovídá, tato událost synchronizace musíte obnovit ručně, jakmile bylo signalizováno. Dokud se vynuluje, voláním jeho <xref:System.Threading.EventWaitHandle.Reset%2A> metoda, vlákna, která čekání na popisovač události okamžitě pokračovat bez blokování.  
  
 Ruční obnovení události úkony jako brány corral. Pokud není signalizován události, zablokovat vlákna, počkejte na to, jako koně v corral. Pokud událost signalizován voláním jeho <xref:System.Threading.EventWaitHandle.Set%2A> metoda, všechny čekajících vláken jsou zdarma, aby bylo možné pokračovat. Události zůstane až do signalizovaného jeho <xref:System.Threading.EventWaitHandle.Reset%2A> metoda je volána. Díky tomu Ruční vynulování události ideální způsob, jak zdržet vlákna, které je třeba počkat, až se dokončí úkol jedno vlákno.  
  
 Stejně jako byste museli opustit corral koně nějakou dobu trvá vydané vlákna, k naplánování podle operačního systému a pokračovat v provádění. Pokud <xref:System.Threading.EventWaitHandle.Reset%2A> metoda je volána před všechna vlákna mít obnovil provádění, zbývající vlákna znovu blokovat. Které opětovné spuštění vlákna a které bloku vláken závisí na náhodných faktorů, jako je zatížení systému, počet vláken čeká se na Plánovač a tak dále. To není problém, pokud podproces, který signalizuje událost skončí po ohlášení, což je nejběžnější vzor využití. Pokud chcete, aby vlákno, které signál události po všech zahájíte nový úkol, čekání, které mají obnoveno vlákna, musíte zablokovat dokud čekajících vláken mít obnoveno. V opačném případě máte časování a nepředvídatelné chování kódu.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Běžné funkce na automatické a ruční události  
 Obvykle zablokovat jednu nebo více vláken <xref:System.Threading.EventWaitHandle> dokud odblokované vlákna volání <xref:System.Threading.EventWaitHandle.Set%2A> metodu, která uvolní jeden čekajících vláken (v případě události automatického resetu) nebo všechny z nich (v případě ruční obnovení události). Vlákna mohou signalizovat <xref:System.Threading.EventWaitHandle> a pak blokování, jako atomickou operaci, voláním statické <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType> metody.  
  
 <xref:System.Threading.EventWaitHandle> objekty lze použít s statické <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> a <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> metody. Protože <xref:System.Threading.EventWaitHandle> a <xref:System.Threading.Mutex> obě třídy odvozovat <xref:System.Threading.WaitHandle>, můžete použít obě třídy s těmito metodami.  
  
### <a name="named-events"></a>Pojmenované události  
 Operační systém Windows umožňuje událost obslužné rutiny čekání mít názvy. Na pojmenovanou událost je v systému. To znamená že po vytvoření pojmenované události je viditelný na všechna vlákna ve všech procesech. Proto je možné pojmenované události pro synchronizaci činností procesy a také vlákna.  
  
 Můžete vytvořit <xref:System.Threading.EventWaitHandle> objekt, který představuje událost s názvem systému pomocí jednoho z konstruktorů, které určuje název události.  
  
> [!NOTE]
>  Protože jsou pojmenované události v systému, je možné mít více <xref:System.Threading.EventWaitHandle> objekty, které představují stejné pojmenované události. Pokaždé, když volat konstruktor, nebo <xref:System.Threading.EventWaitHandle.OpenExisting%2A> metodu, nové <xref:System.Threading.EventWaitHandle> je vytvořen objekt. Zadání se stejným názvem opakovaně vytvoří více objektů, které představují stejné pojmenované události.  
  
 Upozornění se doporučuje při použití s názvem události. Protože jsou v systému, jiný proces, který používá stejný název, můžete zablokovat vlákna neočekávaně. Škodlivý kód, spouští ve stejném počítači může použít jako základ útok s cílem odepření služby.  
  
 Použití řízení přístupu k ochraně <xref:System.Threading.EventWaitHandle> objekt, který reprezentuje na pojmenovanou událost, pokud možno pomocí konstruktoru, který určuje <xref:System.Security.AccessControl.EventWaitHandleSecurity> objektu. Můžete také použít pomocí zabezpečení řízení přístupu <xref:System.Threading.EventWaitHandle.SetAccessControl%2A> metody, ale ponechá okno na ohrožení zabezpečení mezi čas vytvoření události popisovač čekání a je chráněn. Ochrana události pomocí řízení přístupu zabezpečení pomáhá zabránit útoky se zlými úmysly, ale nebyl vyřešen problém kolize názvů neúmyslné.  
  
> [!NOTE]
>  Na rozdíl od <xref:System.Threading.EventWaitHandle> třídy, odvozené třídy <xref:System.Threading.AutoResetEvent> a <xref:System.Threading.ManualResetEvent> můžete představují pouze místní obslužné rutiny čekání. Nelze představují pojmenované systémové události.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.EventWaitHandle>
- <xref:System.Threading.WaitHandle>
- <xref:System.Threading.AutoResetEvent>
- <xref:System.Threading.ManualResetEvent>
