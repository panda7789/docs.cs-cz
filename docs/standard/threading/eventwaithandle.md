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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138079"
---
# <a name="eventwaithandle"></a>EventWaitHandle
Třída <xref:System.Threading.EventWaitHandle> umožňuje vláknům vzájemně komunikovat pomocí signalizace a čekáním na signály. Obslužné rutiny čekání na události (také označované jako události) jsou obslužné rutiny čekání, které mohou být vydány k uvolnění jednoho nebo více čekajících vláken. Po signalizaci je obslužná rutina čekání na událost resetována ručně nebo automaticky. Třída <xref:System.Threading.EventWaitHandle> může představovat buď obslužná rutina čekání na místní událost (místní událost), nebo pojmenovaný popisovač čekání systémové události (událost nebo systémová událost, která je viditelná pro všechny procesy).  
  
> [!NOTE]
> Obslužné rutiny čekání událostí nejsou [událostmi](../events/index.md).NET. Nejsou zapojeni žádní Delegáti nebo obslužné rutiny událostí. Slovo "Event" se používá k popsání, protože byly tradičně označovány jako události operačního systému a vzhledem k tomu, že poznámení popisovače čekání čeká na čekající vlákna, ke kterým došlo událost.  
  
 Místní i pojmenované události čekají na používání objektů synchronizace systému, které jsou chráněny <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> obálky, aby bylo zajištěno, že se prostředky uvolní. Můžete použít metodu <xref:System.Threading.WaitHandle.Dispose%2A> k uvolnění prostředků hned po dokončení používání objektu.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Obslužné rutiny čekání na události, které se automaticky resetují  
 Událost automatického resetování vytvoříte zadáním <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> při vytváření objektu <xref:System.Threading.EventWaitHandle>. Jak je uvedeno, tato událost synchronizace se automaticky obnoví po vyřízení signálu po uvolnění jediného čekajícího vlákna. Vysignálit událost voláním metody <xref:System.Threading.EventWaitHandle.Set%2A>.  
  
 Události automatického resetování se obvykle používají k poskytování výhradního přístupu k prostředku pro jedno vlákno v jednom okamžiku. Vlákno požaduje prostředek voláním metody <xref:System.Threading.WaitHandle.WaitOne%2A>. Pokud žádné jiné vlákno nedrží popisovač čekání, metoda vrátí `true` a volající vlákno má kontrolu nad prostředkem.  
  
> [!IMPORTANT]
> Stejně jako u všech synchronizačních mechanismů je nutné zajistit, aby všechny cesty kódu čekaly příslušnému popisovači čekání před přístupem k chráněnému prostředku. Synchronizace vláken je kooperativní.  
  
 Pokud dojde k signalizaci události automatického resetování, když nečekají žádná vlákna, zůstane signál, dokud se vlákno nepokusí o čekání. Událost uvolní vlákno a okamžitě obnoví a blokuje následná vlákna.  
  
## <a name="event-wait-handles-that-reset-manually"></a>Obslužné rutiny čekání na události, které se resetují ručně  
 Událost ručního resetování vytvoříte zadáním <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> při vytváření objektu <xref:System.Threading.EventWaitHandle>. Vzhledem k tomu, že je tato událost synchronizace nutná, je nutné ji po signalizaci resetovat ručně. Dokud je obnoveno, voláním své <xref:System.Threading.EventWaitHandle.Reset%2A> metody, vlákna, která čekají na zpracování události, okamžitě bez blokování.  
  
 Událost ručního resetování funguje jako brána Corral. Pokud událost není signalizována, vlákny, které čekají na blok IT, jako jsou koně v Corral. Je-li událost signalizována voláním metody <xref:System.Threading.EventWaitHandle.Set%2A>, budou pokračovat všechny čekající podprocesy. Událost zůstává signalizována, dokud nebude volána jeho <xref:System.Threading.EventWaitHandle.Reset%2A> metoda. Tím se vytvoří událost ručního resetování ideální způsob, jak umístit vlákna, která musí čekat, až jeden podproces dokončí úlohu.  
  
 Stejně jako koně opouštějící Corral trvá čas vydaných vláken operačním systémem a k pokračování v provádění. Pokud je metoda <xref:System.Threading.EventWaitHandle.Reset%2A> volána před tím, než všechna vlákna obnovila spuštění, zbývající vlákna znovu zablokují. Které vlákna obnoví a které blok vlákna závisí na náhodných faktorech, jako je zatížení systému, počet vláken, která čekají na Plánovač, a tak dále. Nejedná se o problém, pokud vlákno signalizující událost končí po signalizaci, což je nejběžnější vzor použití. Pokud chcete, aby vlákno, které signalizuje událost, zahájilo novou úlohu po obnovení všech čekajících vláken, je nutné ji zablokovat, dokud nebudou obnovena všechna čekající vlákna. V opačném případě máte spor a chování vašeho kódu nepředvídatelné.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Funkce společné pro automatické a ruční události  
 Obvykle jedno nebo více vláken blokuje <xref:System.Threading.EventWaitHandle>, dokud neblokované vlákno zavolá metodu <xref:System.Threading.EventWaitHandle.Set%2A>, která uvolní jeden z čekajících vláken (v případě událostí automatického resetování) nebo všechny (v případě událostí ručního resetování). Vlákno může signalizovat <xref:System.Threading.EventWaitHandle> a pak ho zablokovat jako atomickou operaci voláním statické <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType> metody.  
  
 <xref:System.Threading.EventWaitHandle> objekty lze použít se statickými metodami <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> a <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType>. Vzhledem k tomu, že třídy <xref:System.Threading.EventWaitHandle> a <xref:System.Threading.Mutex> jsou odvozeny z <xref:System.Threading.WaitHandle>, můžete použít obě třídy s těmito metodami.  
  
### <a name="named-events"></a>Pojmenované události  
 Operační systém Windows umožňuje obslužným rutinám čekání na název mít názvy. Pojmenovaná událost je celá systémová. To znamená, že jakmile je vytvořena pojmenovaná událost, je viditelná pro všechna vlákna ve všech procesech. Proto lze pomocí pojmenovaných událostí synchronizovat aktivity procesů i vlákna.  
  
 Můžete vytvořit objekt <xref:System.Threading.EventWaitHandle>, který představuje pojmenovanou systémovou událost pomocí jednoho z konstruktorů, které určují název události.  
  
> [!NOTE]
> Vzhledem k tomu, že pojmenované události jsou napříč systémem, je možné mít více <xref:System.Threading.EventWaitHandle> objektů, které představují stejnou pojmenovanou událost. Pokaždé, když zavoláte konstruktor nebo metodu <xref:System.Threading.EventWaitHandle.OpenExisting%2A>, vytvoří se nový objekt <xref:System.Threading.EventWaitHandle>. Zadáním stejného názvu opakovaně vytvoříte více objektů, které reprezentují stejnou pojmenovanou událost.  
  
 Při používání pojmenovaných událostí se doporučuje opatrnost. Vzhledem k tomu, že se jedná o systém, může jiný proces, který používá stejný název, blokovat vlákna neočekávaně. Škodlivý kód spuštěný ve stejném počítači může použít tento způsob útoku DOS (Denial of Service).  
  
 Použijte zabezpečení řízení přístupu k ochraně objektu <xref:System.Threading.EventWaitHandle>, který představuje pojmenovanou událost, nejlépe pomocí konstruktoru, který určuje objekt <xref:System.Security.AccessControl.EventWaitHandleSecurity>. Můžete také použít zabezpečení řízení přístupu pomocí metody <xref:System.Threading.EventWaitHandle.SetAccessControl%2A>, ale to zachová okno ohrožení zabezpečení mezi časem vytvoření popisovače čekání na událost a časem, který je chráněn. Ochrana událostí pomocí zabezpečení řízení přístupu pomáhá zabránit škodlivým útokům, ale neřeší problém kolizí neúmyslného názvu.  
  
> [!NOTE]
> Na rozdíl od <xref:System.Threading.EventWaitHandle> třídy mohou odvozené třídy <xref:System.Threading.AutoResetEvent> a <xref:System.Threading.ManualResetEvent> představovat pouze místní čekací obslužné rutiny. Nemůžou představovat pojmenované systémové události.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.EventWaitHandle>
- <xref:System.Threading.WaitHandle>
- <xref:System.Threading.AutoResetEvent>
- <xref:System.Threading.ManualResetEvent>
