---
title: Oblasti omezeného provádění
ms.date: 03/30/2017
helpviewer_keywords:
- constrained execution regions
- CERs
ms.assetid: 99354547-39c1-4b0b-8553-938e8f8d1808
ms.openlocfilehash: fde2bab99f156ddffec678022a58e7b14e0af01e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716161"
---
# <a name="constrained-execution-regions"></a>Oblasti omezeného provádění
Omezená oblast provádění (CER) je součástí mechanismu pro vytváření spolehlivého spravovaného kódu. CER definuje oblast, ve které je modul CLR (Common Language Runtime) omezený od vyvolání výjimek mimo pásmo, které by bránily v celém spuštění kódu v oblasti. V této oblasti je uživatelský kód omezen spouštěním kódu, který by způsobil vyvolání výjimek mimo pásmo. Metoda <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> musí bezprostředně předcházet bloku `try` a označit `catch`, `finally`a `fault` bloky jako omezené oblasti provádění. Po označení jako omezené oblasti musí kód volat pouze jiný kód se silnými kontrakty spolehlivosti a kód by neměl přidělit nebo vytvořit virtuální volání nepřipravených nebo nespolehlivých metod, pokud není kód připraven pro zpracování selhání. Rozhraní CLR zpoždění vlákna je přerušeno pro kód, který je spuštěn v CER.  
  
 Omezené oblasti provádění jsou používány v různých formulářích v modulu CLR kromě `try` blok s poznámkou, zejména kritické finalizační metody prováděné ve třídách odvozených z <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> třídy a kódu spouštěného pomocí metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A>.  
  
## <a name="cer-advance-preparation"></a>Předběžná příprava CER  
 Modul CLR připraví CERs předem, aby se předešlo podmínkám mimo paměť. Příprava předem je nutná, takže CLR nezpůsobí nedostatek paměti při kompilaci nebo načítání typu za běhu.  
  
 Vývojář je nutný k označení, že oblast kódu je CER:  
  
- Oblast a metody CER nejvyšší úrovně v plném grafu volání, které mají použit atribut <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute>, jsou připraveny předem. <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> může pouze státní záruky <xref:System.Runtime.ConstrainedExecution.Cer.Success> nebo <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>.  
  
- Přípravu předem nelze provést pro volání, která nelze staticky určit, jako je například virtuální odeslání. V těchto případech použijte metodu <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>. Při použití metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> by měl být atribut <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> použit pro vyčištění kódu.  
  
## <a name="constraints"></a>Omezení  
 Uživatelé jsou omezeni v typu kódu, který může psát v CER. Kód nemůže způsobit výjimku mimo pásmo, například, může být výsledkem následujících operací:  
  
- Explicitní přidělení.  
  
- Zabalení.  
  
- Získává se zámek.  
  
- Volání nepřipravených metod prakticky.  
  
- Volání metod se slabou nebo neexistující smlouvou o spolehlivosti.  
  
 V .NET Framework verze 2,0 jsou tato omezení pokyny. Diagnostika se poskytuje prostřednictvím nástrojů pro analýzu kódu.  
  
## <a name="reliability-contracts"></a>Smlouvy o spolehlivosti  
 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> je vlastní atribut, který dokumentuje záruky spolehlivosti a stav poškození dané metody.  
  
### <a name="reliability-guarantees"></a>Záruky spolehlivosti  
 Záruky spolehlivosti, reprezentované hodnotami <xref:System.Runtime.ConstrainedExecution.Cer> výčtu, označují stupeň spolehlivosti dané metody:  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>. Ve výjimečných podmínkách může být metoda neúspěšná. V tomto případě metoda hlásí zpět do volající metody bez ohledu na to, zda byla úspěšná nebo neúspěšná. Metoda musí být obsažena ve CER, aby bylo zajištěno, že může nahlásit vrácenou hodnotu.  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.None>. Metoda, typ nebo sestavení nemá žádný koncept typu CER a pravděpodobně není bezpečná pro volání v rámci CER, aniž by došlo k výraznému zmírnění rizik od poškození stavu. Nevyužívá záruky CER. To zahrnuje následující:  
  
    1. Při mimořádných podmínkách může být metoda neúspěšná.  
  
    2. Metoda může nebo nemusí hlásit, že se nezdařila.  
  
    3. Metoda není určena k použití CER, nejpravděpodobnějšího scénáře.  
  
    4. Pokud metoda, typ nebo sestavení nejsou explicitně identifikovány jako úspěšné, je implicitně identifikována jako <xref:System.Runtime.ConstrainedExecution.Cer.None>.  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.Success>. Za výjimečných podmínek je zaručeno, že metoda bude úspěšná. K dosažení této úrovně spolehlivosti byste měli vždy vytvořit CER kolem volané metody, a to i v případě, že jsou volány z oblasti, která není typu CER. Metoda je úspěšná, pokud dosahuje toho, co je určeno, i když úspěch může být zobrazen v předmětně. Například označení počet s `ReliabilityContractAttribute(Cer.Success)` znamená, že když je spuštěný pomocí CER, vrátí vždycky počet prvků v <xref:System.Collections.ArrayList> a nikdy nemůže ponechat interní pole v neurčeném stavu.  Nicméně metoda <xref:System.Threading.Interlocked.CompareExchange%2A> je označena jako úspěšná a při porozumění, která by mohla znamenat úspěch, by nebylo možné hodnotu nahradit novou hodnotou z důvodu konfliktu časování.  Klíčovým bodem je, že se Metoda chová způsobem, který je zdokumentována, a kód CER není nutné zapisovat, aby bylo možné očekávat jakékoli neobvyklé chování, než je to správné, ale nespolehlivý kód by vypadal jako.  
  
### <a name="corruption-levels"></a>Úrovně poškození  
 Úrovně poškození reprezentované hodnotami <xref:System.Runtime.ConstrainedExecution.Consistency> výčtu určují, kolik stavů může být v daném prostředí poškozeno:  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>. Za výjimečných podmínek neprovede modul CLR (Common Language Runtime) žádné záruky týkající se konzistence stavu v aktuální doméně aplikace.  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance>. Za výjimečných podmínek je zaručeno, že metoda omezuje poškození stavu na aktuální instanci.  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>za výjimečných podmínek neposkytuje CLR žádné záruky týkající se konzistence stavu; To znamená, že podmínka může poškodit proces.  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState>. Ve výjimečných podmínkách je zaručeno, že metoda neškodí stav.  
  
## <a name="reliability-trycatchfinally"></a>Spolehlivost try/catch/finally  
 Spolehlivost `try/catch/finally` je mechanismus zpracování výjimek se stejnou úrovní předvídatelnosti garantujeme jako nespravovaná verze. Blok `catch/finally` je CER. Metody v bloku vyžadují pokročilou přípravu a musí být noninterruptible.  
  
 V .NET Framework verze 2,0 kód informuje modul runtime, že pokus je spolehlivý voláním <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> bezprostředně před blokem try. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> je členem <xref:System.Runtime.CompilerServices.RuntimeHelpers>, třídy podpory kompilátoru. Volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> přímo čeká na jeho dostupnost prostřednictvím kompilátorů.  
  
## <a name="noninterruptible-regions"></a>Noninterruptible oblasti  
 Noninterruptible region seskupuje sadu instrukcí do CER.  
  
 V .NET Framework verze 2,0, který čeká na dostupnost prostřednictvím podpory kompilátoru, vytvoří uživatelský kód oblasti bez přerušitelné s spolehlivým try/catch/finally, který obsahuje prázdný blok try/catch předchází voláním metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>.  
  
## <a name="critical-finalizer-object"></a>Kritický objekt finalizační metody  
 <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> garantuje, že uvolňování paměti spustí finalizační metodu. Po přidělení jsou finalizační metoda a její graf volání připravené předem. Metoda finalizační metody se spouští v CER a musí dodržovat všechna omezení pro CERs a finalizační metody.  
  
 Všechny typy děděné z <xref:System.Runtime.InteropServices.SafeHandle> a <xref:System.Runtime.InteropServices.CriticalHandle> jsou zaručeny, aby vykonávání finalizační metody v rámci CER. Implementujte <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> v <xref:System.Runtime.InteropServices.SafeHandle> odvozené třídy pro spuštění libovolného kódu, který je požadován pro uvolnění popisovače.  
  
## <a name="code-not-permitted-in-cers"></a>Kód není v CERs povolený.  
 V CERs nejsou povoleny následující operace:  
  
- Explicitní přidělení.  
  
- Získává se zámek.  
  
- Zabalení.  
  
- Přístup k multidimenzionálnímu poli  
  
- Volání metody prostřednictvím reflexe.  
  
- <xref:System.Threading.Monitor.Enter%2A> nebo <xref:System.IO.FileStream.Lock%2A>.  
  
- Kontroly zabezpečení. Neprovádějte požadavky, pouze propojení požadavků.  
  
- <xref:System.Reflection.Emit.OpCodes.Isinst> a <xref:System.Reflection.Emit.OpCodes.Castclass> pro objekty COM a proxy servery  
  
- Získávání nebo nastavování polí na transparentním proxy serveru.  
  
- Serializace.  
  
- Ukazatele na funkce a Delegáti.  
  
## <a name="see-also"></a>Viz také:

- [Spolehlivost – doporučené postupy](reliability-best-practices.md)
