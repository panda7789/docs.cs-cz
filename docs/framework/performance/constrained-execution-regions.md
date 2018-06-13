---
title: Oblasti omezeného provádění
ms.date: 03/30/2017
helpviewer_keywords:
- constrained execution regions
- CERs
ms.assetid: 99354547-39c1-4b0b-8553-938e8f8d1808
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e7e653101faf9e0664f41e031c7bad05523825f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394680"
---
# <a name="constrained-execution-regions"></a>Oblasti omezeného provádění
Oblasti omezeného provádění (CER) je součástí mechanismus pro vytváření spolehlivé spravovaného kódu. CER definuje oblast, ve kterém je omezené common language runtime (CLR) z vyvolání out-of-band výjimek, které by bránily provádění v celé jeho šíři kód v oblasti. V rámci oblasti je ve spouštění kódu, který by mělo za následek vyvolání výjimky out-of-band omezené uživatelského kódu. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Metoda musí předcházet okamžitě `try` bloku a označí `catch`, `finally`, a `fault` bloky jako omezené oblasti provádění. Jakmile označeno v omezené oblasti, kód musí volat pouze s kontrakty spolehlivosti silné jiný kód a kód by neměl přidělit nebo provádět virtuální volání metod neupravený nebo nespolehlivé, pokud kód je připravený pro zpracování chyby. Vlákno zpoždění CLR zruší pro kód, který spouští v CER.  
  
 Omezené oblasti provádění se používají v různých formulářů v modulu CLR kromě poznámkami `try` blokovat, zejména kritické finalizační provádění v třídy odvozené z metody <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> třídy a kódu spouštěných pomocí <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> metoda.  
  
## <a name="cer-advance-preparation"></a>Předběžná příprava CER  
 Modul CLR připraví CERs předem, aby se zabránilo podmínky z důvodu nedostatku paměti. Předběžná příprava je vyžadován, takže modulu CLR nezpůsobí nedostatku paměti při načítání kompilace nebo typu za běhu.  
  
 Vývojář je potřeba znamenat, že kód oblasti CER:  
  
-   Nejvyšší úrovni oblasti CER a metody v tomto grafu úplné volání, které mají <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> atribut použitý předem připravené. <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> Můžete pouze stav záruky <xref:System.Runtime.ConstrainedExecution.Cer.Success> nebo <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>.  
  
-   Předběžná příprava nelze provést pro volání, které nelze staticky určit, jako je například virtuální odesílání. Použití <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> metoda v těchto případech. Při použití <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> metody <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> atribut má být použita na čištění kódu.  
  
## <a name="constraints"></a>Omezení  
 Uživatelé jsou omezené v typu kód, který může zapisovat v CER. Kód nelze způsobit výjimku out-of-band, jako například může být výsledkem následující operace:  
  
-   Explicitní přidělení.  
  
-   Zabalení.  
  
-   Získávání zámku.  
  
-   Volání metody neupravený prakticky.  
  
-   Volání metody s kontraktu spolehlivost slabé, nebo neexistuje.  
  
 V rozhraní .NET Framework verze 2.0 jsou tato omezení pokyny. Diagnostika je zajišťována prostřednictvím nástrojů pro analýzu kódu.  
  
## <a name="reliability-contracts"></a>Kontrakty spolehlivosti  
 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> Je vlastní atribut, který dokumenty záruky spolehlivost a stav poškození dané metody.  
  
### <a name="reliability-guarantees"></a>Spolehlivost záruky  
 Spolehlivost záruky, reprezentována <xref:System.Runtime.ConstrainedExecution.Cer> hodnoty výčtu, znamenat stupeň spolehlivost dané metody:  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>. Za výjimečných podmínek se nemusí podařit metodu. V takovém případě metodu sestavy zpět do volání metody jestli ho byla úspěšná nebo neúspěšná. Metoda musí být obsažena v CER zajistit, že se může hlásit návratovou hodnotu.  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer.None>. Metoda, typ nebo sestavení neobsahuje žádná koncepce CER a pravděpodobně není bezpečné volat v rámci CER bez významné zmírnění poškozené stavu. Tato možnost nevyžaduje výhod CER záruky. To znamená následující:  
  
    1.  Za výjimečných podmínek může selhat metodu.  
  
    2.  Metoda může nebo nemusí informovat, že se nezdařilo.  
  
    3.  Metoda zapisuje na použití CER, nejpravděpodobnější scénář.  
  
    4.  Pokud metoda, typ nebo sestavení není explicitně identifikovaná proběhla úspěšně, je implicitně identifikován jako <xref:System.Runtime.ConstrainedExecution.Cer.None>.  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer.Success>. Za výjimečných podmínek metoda záruku, že proběhla úspěšně. K dosažení tato úroveň spolehlivosti vytvoříte vždy CER kolem metodu, která je volána, i když se označuje jako z v rámci oblasti bez CER. Metoda je úspěšné, pokud to je možné díky co je určený, i když lze zobrazit subjektivně rozlišitelná úspěch. Například označení počet se `ReliabilityContractAttribute(Cer.Success)` znamená, že při spuštění v rámci CER, vždy vrátí počet prvků v <xref:System.Collections.ArrayList> a nikdy ho můžete nechat interní pole v neurčeném stavu.  Ale <xref:System.Threading.Interlocked.CompareExchange%2A> metoda je označena jako úspěšné i, s tím, že úspěch může to znamenat hodnotu nelze nahradit, s novou hodnotou z důvodu časování.  Klíče bod je, že metoda chová způsobem, jakým je popsána chovat a kód CER nepotřebuje k zapsání očekávat jakékoli neobvyklé chování nad rámec jaké správné ale nespolehlivé kód bude vypadat.  
  
### <a name="corruption-levels"></a>Poškození úrovně  
 Poškození úrovně reprezentována <xref:System.Runtime.ConstrainedExecution.Consistency> hodnoty výčtu, určit, kolik stavu může být poškozený v daném prostředí:  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>. Za výjimečných podmínek modul CLR (CLR) umožňuje žádné záruky týkající se stavu konzistence v aktuální doméně aplikace.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance>. Za výjimečných podmínek metoda záruku, že se k omezení stavu poškození na aktuální instanci.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, Za výjimečných podmínek modulu CLR Díky žádné záruky týkající se stavu konzistence; To znamená stavu může dojít k poškození proces.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState>. Za výjimečných podmínek metoda záruku, že nejsou poškozené stavu.  
  
## <a name="reliability-trycatchfinally"></a>Spolehlivost try/catch/finally  
 Spolehlivost `try/catch/finally` je mechanismus se stejnou úroveň záruky předvídatelnost jako nespravované verze zpracování výjimek. `catch/finally` Blok je CER. Metody v bloku vyžadují předběžná příprava a musí být noninterruptible.  
  
 V rozhraní .NET Framework verze 2.0, kód informuje o tom modul runtime, zkuste je spolehlivá voláním <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> bezprostředně před bloku try. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> je členem skupiny <xref:System.Runtime.CompilerServices.RuntimeHelpers>, třídy podpory kompilátoru. Volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> přímo čeká na jeho dostupnost prostřednictvím kompilátory.  
  
## <a name="noninterruptible-regions"></a>Noninterruptible oblastí  
 V oblasti noninterruptible skupiny sada pokynů do CER.  
  
 V rozhraní .NET Framework verze 2.0, čeká na dostupnost prostřednictvím podpory kompilátoru uživatelský kód vytvoří-přerušitelné oblasti s spolehlivé try/catch/finally obsahující bloku try/catch – prázdný před sebou <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> volání metody.  
  
## <a name="critical-finalizer-object"></a>Kritické finalizační metodu objektu  
 A <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> zaručuje, že uvolňování paměti spustí finalizační metodu. Při přidělení finalizační metodu a jeho volání grafu jsou předem připravit. Metoda finalizační metodu spustí CER a musí orientují všechna omezení na CERs a finalizační metody.  
  
 Všechny typy, která dědí z <xref:System.Runtime.InteropServices.SafeHandle> a <xref:System.Runtime.InteropServices.CriticalHandle> kombinace obsahuje jejich finalizační metodu provést v rámci CER. Implementace <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> v <xref:System.Runtime.InteropServices.SafeHandle> odvozených třídách k provedení kód, který je potřeba uvolnit popisovač.  
  
## <a name="code-not-permitted-in-cers"></a>Kód není povolený v CERs  
 V CERs nejsou povoleny následující operace:  
  
-   Explicitní přidělení.  
  
-   Získávání zámku.  
  
-   Zabalení.  
  
-   Multidimenzionální pole přístup.  
  
-   Volání metody prostřednictvím reflexe.  
  
-   <xref:System.Threading.Monitor.Enter%2A> nebo <xref:System.IO.FileStream.Lock%2A>.  
  
-   Kontroly zabezpečení. Není provádět požadavky, pouze požadavky na propojení.  
  
-   <xref:System.Reflection.Emit.OpCodes.Isinst> a <xref:System.Reflection.Emit.OpCodes.Castclass> pro objekty modelu COM a proxy servery  
  
-   Získání nebo nastavení polí na transparentní proxy server.  
  
-   Serializace.  
  
-   Ukazatele na funkce a delegáti.  
  
## <a name="see-also"></a>Viz také  
 [Spolehlivost – doporučené postupy](../../../docs/framework/performance/reliability-best-practices.md)
