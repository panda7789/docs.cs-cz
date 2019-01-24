---
title: Oblasti omezeného provádění
ms.date: 03/30/2017
helpviewer_keywords:
- constrained execution regions
- CERs
ms.assetid: 99354547-39c1-4b0b-8553-938e8f8d1808
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5854abd97c05cf0d57bfdd9a19826fea2fd7502
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566941"
---
# <a name="constrained-execution-regions"></a>Oblasti omezeného provádění
Oblasti omezeného provádění (CER) je mechanismus pro vytváření spolehlivých spravovaného kódu. CER vymezuje oblast, ve kterém je omezená common language runtime (CLR) z vyvolávání výjimek out-of-band, které by jinak znemožňovaly kód v oblasti spuštění v celém rozsahu. V rámci oblasti je omezen uživatelský kód z provádění kódu, který způsobí vyvolání výjimky out-of-band. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Metoda musí bezprostředně předcházet `try` bloku a značky `catch`, `finally`, a `fault` bloky jako oblasti omezeného provádění. Jakmile označen jako omezené oblasti kódu musí volat pouze jiný kód s kontrakty spolehlivosti a kód by neměl přidělit nebo volání virtuální metody neupravený nebo nespolehlivé Pokud kód je připravena ke zpracování chyb. Zpoždění vlákna CLR zruší pro kód, který je spouštěn v CER.  
  
 Oblasti omezeného provádění se používají v různých formulářích v modulu CLR kromě s poznámkami `try` blokovat, zejména kritické finalizační provádění v třídy odvozené z metody <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> třídy a proveden pomocí kódu <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> metody.  
  
## <a name="cer-advance-preparation"></a>Předběžná příprava CER  
 Modul CLR připraví CERs předem, aby se zabránilo podmínek na více instancí z důvodu nedostatku paměti. Předběžná příprava se vyžaduje, aby modul CLR nezpůsobí nedostatku paměti během kompilace nebo typ načítání just-in-time.  
  
 Vývojář se vyžaduje k označení, že je kód oblasti CER:  
  
-   Nejvyšší úrovni oblasti CER a metody v grafu úplné volání, které mají <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> atribut jsou předem připravené. <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> Lze pouze stav záruky <xref:System.Runtime.ConstrainedExecution.Cer.Success> nebo <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>.  
  
-   Předběžná příprava nelze provést pro volání, která nemůže staticky určena, jako je například virtuální odeslání. Použití <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> metoda v těchto případech. Při použití <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> metody <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> atribut by měl použít pro vyčištění kódu.  
  
## <a name="constraints"></a>Omezení  
 Uživatelé jsou omezeny v typu kódu, který můžete napsat v CER. Kód nemůže způsobit výjimku out-of-band, jako například může být výsledkem následující operace:  
  
-   Explicitní přidělování.  
  
-   Zabalení.  
  
-   Získání zámku.  
  
-   Volání metod neupravený virtuálně.  
  
-   Volání metody s kontraktem slabé nebo neexistující spolehlivost.  
  
 V rozhraní .NET Framework verze 2.0 tato omezení jsou pokyny. Diagnostické nástroje jsou k dispozici prostřednictvím nástrojů pro analýzu kódu.  
  
## <a name="reliability-contracts"></a>Kontrakty spolehlivosti  
 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> Je vlastní atribut dokumentující záruky spolehlivost a poškození stavu dané metody.  
  
### <a name="reliability-guarantees"></a>Záruky spolehlivosti  
 Spolehlivost záruky, reprezentovaný <xref:System.Runtime.ConstrainedExecution.Cer> hodnot výčtu, označují úroveň spolehlivosti dané metody:  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>. Za výjimečných podmínek metoda může selhat. V tomto případě metodu oznamuje ho zpátky k volání metody, zda bylo úspěšné nebo neúspěšné. Metoda musí být součástí CER zajistit, že může hlásit návratovou hodnotu.  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer.None>. Metoda, typ nebo sestavení nemá žádný koncept CER a je s největší pravděpodobností není bezpečné volat v rámci CER bez značné omezení rizik poškození stavu. To nevyužívá záruk CER. Z toho vyplývá následující:  
  
    1.  Za výjimečných podmínek se nemusí podařit metodu.  
  
    2.  Metoda může nebo nemusí hlásit, že se nezdařilo.  
  
    3.  Metoda není zapsána do použít CER, nejpravděpodobnější situací.  
  
    4.  Pokud metoda, typ nebo sestavení není identifikován explicitně proběhla úspěšně, je implicitně identifikován jako <xref:System.Runtime.ConstrainedExecution.Cer.None>.  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer.Success>. Za výjimečných podmínek metoda je zaručeno úspěšné. K dosažení této úrovně spolehlivosti by měla vždy vytvořit CER kolem metodu, která je volána, i když je volána z v rámci oblasti mimo CER. Metoda je úspěšná, pokud se provádí co se má, i když lze zobrazit subjektivně rozlišitelná úspěch. Například počet s označením `ReliabilityContractAttribute(Cer.Success)` znamená, že při spuštění v části CER, vždy vrátí počet prvků v <xref:System.Collections.ArrayList> a nikdy ho můžete nechat interní pole v neurčeném stavu.  Ale <xref:System.Threading.Interlocked.CompareExchange%2A> metoda je označena jako úspěch, s vědomím, že úspěch může to znamenat hodnotu nelze nahradit novou hodnotu z důvodu konfliktu časování.  Klíčovým bodem tedy je, že metoda chová způsobem, jakým jsou uvedené chování a CER kód nemusí k zapsání očekávat jakékoli neobvyklé chování rámec toho, jaký kód správný, ale nespolehlivé vypadat nějak takto.  
  
### <a name="corruption-levels"></a>Poškození úrovně  
 Poškození úrovně reprezentována <xref:System.Runtime.ConstrainedExecution.Consistency> hodnot výčtu, označuje, kolik stavu může být poškozený v daném prostředí:  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>. Modul CLR (CLR) za výjimečných podmínek, neposkytuje žádnou záruku týkající se stavu konzistence v aktuální doméně aplikace.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance>. Za výjimečných podmínek metoda je zaručeno, omezit poškození stavu na aktuální instanci.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, Za výjimečných podmínek, modul CLR neposkytuje žádnou záruku týkající se stavu konzistence; To znamená, že podmínka může dojít k poškození procesu.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState>. Za výjimečných podmínek metoda je zaručeno, že poškozený stav.  
  
## <a name="reliability-trycatchfinally"></a>Spolehlivost try/catch/finally  
 Spolehlivost `try/catch/finally` je mechanismus se stejnou úrovní předvídatelnost záruky jako nespravovaná verze zpracování výjimek. `catch/finally` Blok je CER. Metody v bloku vyžadují přípravou a musí být noninterruptible.  
  
 V rozhraní .NET Framework verze 2.0 kód informuje modul runtime, zkuste je spolehlivé voláním <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> bezprostředně před blok try. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> je členem skupiny <xref:System.Runtime.CompilerServices.RuntimeHelpers>, třídy podpory kompilátoru. Volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> přímo čekající její dostupnost prostřednictvím kompilátory.  
  
## <a name="noninterruptible-regions"></a>Noninterruptible oblastí  
 Oblast noninterruptible seskupit sadu pokynů do CER.  
  
 V rozhraní .NET Framework verze 2.0, čekající dostupnosti díky podpoře kompilátoru uživatelský kód vytvoří – paralelní oblasti s reliable try/catch/finally, která obsahuje blok try/catch – prázdný předcházet párový příkaz <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> volání metody.  
  
## <a name="critical-finalizer-object"></a>Důležitou finalizační metodu objektu  
 A <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> záruky, že uvolňování paměti spustí finalizační metodu. Po přidělení finalizační metody a jeho grafu volání jsou předem připravit. Finalizační metoda spustí CER a musí dodržovat všechna omezení na CERs a finalizační metody.  
  
 Typy, které dědí z <xref:System.Runtime.InteropServices.SafeHandle> a <xref:System.Runtime.InteropServices.CriticalHandle> je zaručeno, že mají jejich finalizační metodu spustit v rámci CER. Implementace <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> v <xref:System.Runtime.InteropServices.SafeHandle> odvozené třídy provést všechny kódu, který je potřeba uvolnit popisovač.  
  
## <a name="code-not-permitted-in-cers"></a>Kód není povolena v CERs  
 V CERs nejsou povolené následující operace:  
  
-   Explicitní přidělení.  
  
-   Získání zámku.  
  
-   Zabalení.  
  
-   Přístup multidimenzionálního pole.  
  
-   Volání metody prostřednictvím reflexe.  
  
-   <xref:System.Threading.Monitor.Enter%2A> nebo <xref:System.IO.FileStream.Lock%2A>.  
  
-   Kontroly zabezpečení. Není provádět požadavky, pouze požadavky na propojení.  
  
-   <xref:System.Reflection.Emit.OpCodes.Isinst> a <xref:System.Reflection.Emit.OpCodes.Castclass> pro objekty COM a proxy servery  
  
-   Získání nebo nastavení pole na transparentní proxy server.  
  
-   Serializace.  
  
-   Ukazatele na funkce a delegáti.  
  
## <a name="see-also"></a>Viz také:
- [Spolehlivost – doporučené postupy](../../../docs/framework/performance/reliability-best-practices.md)
