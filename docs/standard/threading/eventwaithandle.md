---
title: EventWaitHandle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], EventWaitHandle class
- EventWaitHandle class
- event wait handles [.NET Framework]
- threading [.NET Framework], cross-process synchronization
ms.assetid: 11ee0b38-d663-4617-b793-35eb6c64e9fc
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1bd248133bd95ff05246eb36a8e250247fd7ed61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="eventwaithandle"></a>EventWaitHandle
<xref:System.Threading.EventWaitHandle> Třída umožňuje vláken pro komunikaci mezi sebou signalizace a čekání signály. Obslužné rutiny událostí čekání (také označované jako události jednoduše) jsou popisovače čekání, které můžete signál, aby verze jeden nebo více podprocesů čekání. Po to bylo signalizováno, popisovač čekání událostí je obnovit ručně nebo automaticky. <xref:System.Threading.EventWaitHandle> Třída může představovat buď místní události popisovač čekání (místní události) nebo s názvem systémové události počkejte popisovač (s názvem události nebo událostí systému, viditelné pro všechny procesy).  
  
> [!NOTE]
>  Obslužné rutiny čekání na událost nejsou události v tom smyslu, obvykle určená pomocí této aplikace word v rozhraní .NET Framework. Neexistují žádné delegáti nebo obslužné rutiny událostí související se situací. Slova "událost" slouží k popisu je vzhledem k tomu, že budou mít tradičně se označuje jako událostí operačního systému, a vzhledem k tomu, že v rámci signalizace popisovač čekání označuje k čekání vláken, došlo k události.  
  
 Obslužné rutiny čekání oba pojmenované a místní událostí pomocí systému synchronizačními objekty, které jsou chráněny <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> obálky zajistit uvolnění prostředků. Můžete použít <xref:System.Threading.WaitHandle.Dispose%2A> metodu pro uvolnění prostředků hned po dokončení pomocí objektu.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Obslužné rutiny čekání událostí, které automaticky resetovat  
 Vytvoření událostí automatický reset zadáním <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> při vytváření <xref:System.Threading.EventWaitHandle> objektu. Jak již název napovídá, tato událost synchronizace obnoví automaticky při signál po vydání jedním vláknem a čekání. Signál události voláním jeho <xref:System.Threading.EventWaitHandle.Set%2A> metoda.  
  
 Automatické vynulování události se obvykle používají zajistit výhradní přístup k prostředku pro jedno vlákno najednou. Vlákno požadavek na prostředek voláním <xref:System.Threading.WaitHandle.WaitOne%2A> metoda. Pokud žádné jiné vlákno drží popisovač čekání, vrátí metoda `true` a volající vlákno má ovládací prvek prostředku.  
  
> [!IMPORTANT]
>  Stejně jako u všech mechanismů synchronizace, je nutné zajistit, že všechny cesty kódu čekání na popisovač odpovídající čekání před přístupem k chráněnému prostředku. Synchronizace vláken je spolupráci.  
  
 Pokud událost automatický reset signalizace při žádné vláken čekají, zůstane signalizovaného, dokud vlákno pokusí čekat na něm. Událost uvolní vlákno a okamžitě resetuje blokování následné vláken.  
  
## <a name="event-wait-handles-that-reset-manually"></a>Obslužné rutiny čekání událostí, které ručně obnovit  
 Vytvořte Ruční vynulování události zadáním <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> při vytváření <xref:System.Threading.EventWaitHandle> objektu. Jak již název napovídá, tato událost synchronizace, musí se obnovit ručně po jeho nesignalizuje. Dokud se resetuje voláním jeho <xref:System.Threading.EventWaitHandle.Reset%2A> metoda, vláken, která čekání na popisovač události prakticky hned pokračovat bez blokování.  
  
 Ruční obnovení úkony událostí jako pro bránu corral. Pokud není signál události, vláken, která čekat na něm blokovat jako koně v corral. Když signalizace události voláním jeho <xref:System.Threading.EventWaitHandle.Set%2A> metoda, všechna vlákna čekání jsou zdarma pokračovat. Událost zůstane signalizovaného dokud jeho <xref:System.Threading.EventWaitHandle.Reset%2A> metoda je volána. Díky tomu Ruční vynulování události nevhodnější způsob pojmout až vláken, které je potřeba čekat, až jedno vlákno dokončí úlohu.  
  
 Jako koně ponechat corral jak dlouho trvá dobu vydaná vláken naplánovat podle operačního systému a pokračovat v provádění. Pokud <xref:System.Threading.EventWaitHandle.Reset%2A> metoda je volána před všechna vlákna mít obnovil provádění, zbývající vláken znovu blokovat. Které obnovení vláken a které blokování vláken závisí na náhodných faktorech, jako je zatížení systému, počet vláken čekání pro Plánovač a tak dále. To není problém, pokud vlákno, které signály události končí po signalizace, což je nejběžnější vzor používání. Pokud chcete, aby vlákno, které signalizace událostí zahájíte nové úlohy po všech čekání, které se mají obnovit vláken, musíte zablokovat až do mají obnovit všechna vlákna čekání. Jinak máte časování a nepředvídatelné chování kódu.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Běžné funkce automatického nebo ručního události  
 Obvykle jeden nebo více podprocesů blokovat na <xref:System.Threading.EventWaitHandle> dokud odblokuje vlákno volá <xref:System.Threading.EventWaitHandle.Set%2A> metodu, která uvolní jeden vláken čekání (v případě událostí automatický reset) nebo všechny z nich (v případě ručního resetovat událostí). Vlákno můžete signál <xref:System.Threading.EventWaitHandle> a pak blokovat, jako atomickou operaci, voláním statické <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType> metoda.  
  
 <xref:System.Threading.EventWaitHandle>objekty lze použít s statických <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> a <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> metody. Protože <xref:System.Threading.EventWaitHandle> a <xref:System.Threading.Mutex> třídy obě jsou odvozeny od <xref:System.Threading.WaitHandle>, můžete použít obě třídy pomocí těchto metod.  
  
### <a name="named-events"></a>Pojmenované události  
 Operační systém Windows umožňuje obslužné rutiny čekání na událost názvy. Pojmenované událost je celého systému. To znamená že po vytvoření pojmenovaného událostí je viditelná pro všechny vláken ve všech procesů. Proto s názvem události slouží k synchronizaci aktivity procesy a také vláken.  
  
 Můžete vytvořit <xref:System.Threading.EventWaitHandle> objekt, který reprezentuje událostí s názvem systému pomocí jedné z konstruktorů, které určuje název události.  
  
> [!NOTE]
>  Vzhledem k pojmenované události jsou celého systému, je možné, že více <xref:System.Threading.EventWaitHandle> objekty, které představují stejné s názvem událostí. Při každém volání konstruktoru, nebo <xref:System.Threading.EventWaitHandle.OpenExisting%2A> metoda, nový <xref:System.Threading.EventWaitHandle> je vytvořen objekt. Zadat stejný název opakovaně vytvoří více objektů, které představují stejnou událost s názvem.  
  
 Upozornění se doporučuje při použití s názvem události. Protože jsou celého systému, může jiný proces, který používá stejný název neočekávaně blokovat vaší vláken. Škodlivý kód provádění na stejném počítači může použít jako základ útoku denial of service.  
  
 Použít zabezpečení řízení přístupu k ochraně <xref:System.Threading.EventWaitHandle> objekt, který představuje pojmenovanou událostí, pokud možno s využitím konstruktor, který určuje <xref:System.Security.AccessControl.EventWaitHandleSecurity> objektu. Můžete taky použít přístupu k řízení zabezpečení pomocí <xref:System.Threading.EventWaitHandle.SetAccessControl%2A> metoda, ale ponechá okno ohrožení zabezpečení mezi časem popisovač čekání událostí je vytvořen a čas, který je chráněn. Ochrana události pomocí řízení přístupu zabezpečení pomáhá zabránit útoky se zlými úmysly, ale nebyl vyřešen problém kolize neúmyslnému názvů.  
  
> [!NOTE]
>  Na rozdíl od <xref:System.Threading.EventWaitHandle> třídu, odvozené třídy <xref:System.Threading.AutoResetEvent> a <xref:System.Threading.ManualResetEvent> můžete představují pouze místní obslužné rutiny čekání. Nelze představují pojmenované systémové události.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
