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
ms.openlocfilehash: 80c90254978495a58d228c4302eda84d6165c800
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138079"
---
# <a name="eventwaithandle"></a>EventWaitHandle
Třída <xref:System.Threading.EventWaitHandle> umožňuje vláknům vzájemnou komunikaci signalizací a čekáním na signály. Popisovače čekání událostí (označované také jednoduše jako události) jsou popisovače čekání, které mohou být signalizovány, aby se uvolnilo jedno nebo více čekajících vláken. Po signalizaci je popisovač čekání události resetován ručně nebo automaticky. Třída <xref:System.Threading.EventWaitHandle> může představovat buď místní popisovač čekání události (místní událost) nebo pojmenovaný popisovač čekání systémové události (pojmenovaná událost nebo systémová událost, viditelná pro všechny procesy).  
  
> [!NOTE]
> Popisovače čekání událostí nejsou [události](../events/index.md).NET . Nejsou zapojeni žádní delegáti nebo obslužné rutiny událostí. Slovo "událost" se používá k jejich popisu, protože byly tradičně označovány jako události operačního systému a protože akt signalizace popisovač čekání označuje čekající vlákna, ke kterým došlo k události.  
  
 Popisovače čekání místní i pojmenované události používají objekty <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> synchronizace systému, které jsou chráněny obálkami, aby bylo zajištěno, že prostředky jsou uvolněny. Tuto metodu <xref:System.Threading.WaitHandle.Dispose%2A> můžete použít k okamžitému uvolnění prostředků po dokončení použití objektu.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Popisovače čekání událostí, které se automaticky resetují  
 Událost automatického obnovení vytvoříte <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> zadáním <xref:System.Threading.EventWaitHandle> při vytváření objektu. Jak již název napovídá, tato událost synchronizace se automaticky resetuje, když je signalizována, po uvolnění jednoho čekajícího vlákna. Signalizační událost voláním její <xref:System.Threading.EventWaitHandle.Set%2A> metody.  
  
 Automatické obnovení události se obvykle používají k poskytování výhradní přístup k prostředku pro jedno vlákno najednou. Podproces požaduje prostředek voláním <xref:System.Threading.WaitHandle.WaitOne%2A> metody. Pokud žádné jiné vlákno drží popisovač `true` čekání, metoda vrátí a volající vlákno má kontrolu nad prostředek.  
  
> [!IMPORTANT]
> Stejně jako u všech synchronizačních mechanismů, musíte zajistit, že všechny cesty kódu čekat na příslušné čekání popisovač před přístupem k chráněnému prostředku. Synchronizace vláken je kooperativní.  
  
 Pokud je událost automatického resetování signalizována, když nečekají žádná vlákna, zůstane signalizována, dokud se na ni vlákno nepokusí čekat. Událost uvolní vlákno a okamžitě se resetuje a blokuje následující vlákna.  
  
## <a name="event-wait-handles-that-reset-manually"></a>Popisovače čekání událostí, které se resetují ručně  
 Událost ručního obnovení vytvoříte <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> zadáním <xref:System.Threading.EventWaitHandle> při vytváření objektu. Jak již název napovídá, tato událost synchronizace musí být resetována ručně poté, co byla signalizována. Dokud je resetován, <xref:System.Threading.EventWaitHandle.Reset%2A> voláním jeho metody, vlákna, která čekají na popisovač události pokračovat okamžitě bez blokování.  
  
 Událost ručního resetu se chová jako brána ohrady. Když událost není signalizována, vlákna, která na ní čekají, blokují, jako koně v ohradě. Když je událost signalizována <xref:System.Threading.EventWaitHandle.Set%2A> voláním její metody, všechna čekající vlákna mohou pokračovat. Událost zůstává signalizována, dokud není volána její <xref:System.Threading.EventWaitHandle.Reset%2A> metoda. Díky ručnímu resetování události ideální způsob, jak zdržet podprocesy, které je třeba počkat, dokud jeden podproces dokončí úlohu.  
  
 Stejně jako koně opouštějící ohrady, to vyžaduje čas pro uvolněné podprocesů, které mají být naplánovány operačním systémem a obnovit provádění. Pokud <xref:System.Threading.EventWaitHandle.Reset%2A> je metoda volána před všechna vlákna obnovily provádění, zbývající vlákna opět blokovat. Která vlákna pokračovat a které podprocesy bloku závisí na náhodné faktory, jako je zatížení systému, počet podprocesů čekání na plánovače a tak dále. To není problém, pokud podproces, který signalizuje událost končí po signalizaci, což je nejběžnější vzor použití. Pokud chcete, aby vlákno, které signalizovalo událost, zahájilo nový úkol poté, co byla obnovena všechna čekající vlákna, musíte ji zablokovat, dokud nebudou obnovena všechna čekající vlákna. V opačném případě máte spor a chování kódu je nepředvídatelné.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Funkce společné pro automatické a manuální události  
 Obvykle jeden nebo více vláken blokovat <xref:System.Threading.EventWaitHandle> na dokud odblokované vlákno volá metodu, <xref:System.Threading.EventWaitHandle.Set%2A> která uvolní jeden z čekajících vláken (v případě automatického resetovat události) nebo všechny z nich (v případě ručního resetování událostí). Podproces může <xref:System.Threading.EventWaitHandle> signalizovat a pak blokovat na něm, jako <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType> atomické operace voláním statické metody.  
  
 <xref:System.Threading.EventWaitHandle>objekty lze použít <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> se <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> statickými a metodami. Vzhledem <xref:System.Threading.EventWaitHandle> <xref:System.Threading.Mutex> k tomu, <xref:System.Threading.WaitHandle>že a třídy odvozují z , můžete použít obě třídy s těmito metodami.  
  
### <a name="named-events"></a>Pojmenované události  
 Operační systém Windows umožňuje popisovače čekání událostí mít názvy. Pojmenovaná událost je celosystémová. To znamená, že po vytvoření pojmenované události je viditelná pro všechna vlákna ve všech procesech. Pojmenované události lze tedy použít k synchronizaci aktivit procesů i vláken.  
  
 Můžete vytvořit <xref:System.Threading.EventWaitHandle> objekt, který představuje pojmenovanou systémovou událost pomocí jednoho z konstruktorů, který určuje název události.  
  
> [!NOTE]
> Vzhledem k tomu, že pojmenované události <xref:System.Threading.EventWaitHandle> jsou celého systému, je možné mít více objektů, které představují stejnou pojmenovanou událost. Pokaždé, když voláte konstruktor <xref:System.Threading.EventWaitHandle.OpenExisting%2A> nebo metodu, je vytvořen nový <xref:System.Threading.EventWaitHandle> objekt. Zadání stejného názvu opakovaně vytvoří více objektů, které představují stejnou pojmenovanou událost.  
  
 Při používání pojmenovaných událostí se doporučuje opatrnost. Vzhledem k tomu, že jsou celého systému, jiný proces, který používá stejný název může neočekávaně blokovat podprocesy. Škodlivý kód spuštěný ve stejném počítači by jej mohl použít jako základ útoku typu denial of service.  
  
 Zabezpečení řízení přístupu <xref:System.Threading.EventWaitHandle> slouží k ochraně objektu, který představuje pojmenovanou <xref:System.Security.AccessControl.EventWaitHandleSecurity> událost, nejlépe pomocí konstruktoru, který určuje objekt. Můžete také použít zabezpečení řízení <xref:System.Threading.EventWaitHandle.SetAccessControl%2A> přístupu pomocí metody, ale to ponechává okno zranitelnosti mezi čas čekání popisovač události je vytvořen a čas je chráněn. Ochrana událostí pomocí zabezpečení řízení přístupu pomáhá zabránit škodlivým útokům, ale neřeší problém neúmyslných kolizí názvů.  
  
> [!NOTE]
> Na <xref:System.Threading.EventWaitHandle> rozdíl od třídy <xref:System.Threading.AutoResetEvent> <xref:System.Threading.ManualResetEvent> odvozené třídy a může představovat pouze místní popisovače čekání. Nemohou představovat pojmenované systémové události.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.EventWaitHandle>
- <xref:System.Threading.WaitHandle>
- <xref:System.Threading.AutoResetEvent>
- <xref:System.Threading.ManualResetEvent>
