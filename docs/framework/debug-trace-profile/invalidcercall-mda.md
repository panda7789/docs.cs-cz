---
title: "invalidCERCall – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- invalid CER calls
- InvalidCERCall MDA
- MDAs (managed debugging assistants), CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: c4577410-602e-44e5-9dab-fea7c55bcdfe
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0c051e1513f8e8ad1735085cb93f106b4fb9b0d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="invalidcercall-mda"></a>invalidCERCall – pomocník spravovaného ladění (MDA)
`invalidCERCall` Pomocník spravovaného ladění (MDA) se aktivuje při volání metody, která má žádné spolehlivost smlouvy nebo nadměrně slabé kontrakt v rámci omezeného provádění (CER) oblasti grafu. Slabé smlouva je kontrakt, který deklaruje, že nejhorší stav případu poškození je větší rozsah než instance předána volání, který je <xref:System.AppDomain> nebo stav procesu může dojít k poškození nebo že jeho výsledek není vždy nepodmíněně computable Při volání v rámci CER.  
  
## <a name="symptoms"></a>Příznaky  
 Neočekávané výsledky při provádění kódu v CER. Příznaky nejsou specifické. Může být neočekávanou <xref:System.OutOfMemoryException>, <xref:System.Threading.ThreadAbortException>, nebo jiné výjimky při volání do metody nespolehlivé protože nepřešly připravit předem nebo chránit z modulu runtime <xref:System.Threading.ThreadAbortException> výjimky za běhu. Větší hrozbu je, že všechny výjimky vyplývající z metody v době běhu může nechat <xref:System.AppDomain> nebo procesy v nestabilním stavu, které bylo v rozporu s cílem CER. Je vytvořena CER důvodem je, aby se zabránilo poškození stavu, jako je tato. Příznaky složky v porušeném stavu jsou specifické pro aplikaci, protože definice konzistentní stav se liší mezi aplikacemi.  
  
## <a name="cause"></a>příčina  
 Kód v rámci CER volá funkci bez <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> nebo s weak <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> není kompatibilní s spuštěné v CER.  
  
 Z hlediska spolehlivost kontrakt syntaxi, která je slabé kontrakt kontraktu, která neurčuje <xref:System.Runtime.ConstrainedExecution.Consistency> hodnota výčtu nebo určuje <xref:System.Runtime.ConstrainedExecution.Consistency> hodnotu <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>, nebo <xref:System.Runtime.ConstrainedExecution.Cer.None>. Některé z těchto podmínek určuje, že kódu volaného může mít dopad na úsilí další kód CER pro zachování konzistentní stavu.  CERs umožnit kódu považovat chyb velmi deterministickou způsobem, údržbu interní výstupních podmínek, které jsou důležité pro aplikace a umožní tak jeho pokračovat v činnosti ve tučné přechodné chyby jako např. výjimky nedostatku paměti.  
  
 Aktivace této MDA označuje možnost metoda volána v CER může selhat způsobem, který volající neočekávali, nebo která zůstane <xref:System.AppDomain> nebo zpracovat stavu poškozená nebo je nejde obnovit. Samozřejmě volané kód se může správně spustit a problému je jednoduše chybějící kontrakt. Ale problematiku zápis spolehlivého kódu jsou jemně a neexistence kontraktu je dobré indikátor, který kód se nemusí správně spustit. Kontrakty jsou indikátory, které programátorů má programového spolehlivě a také nabízí, že tyto záruky nedojde ke změně v budoucnosti revize kódu.  To znamená že smluv jsou deklarace záměr a nikoli pouze podrobnosti implementace.  
  
 Protože libovolné metody s kontraktu slabé nebo neexistující mohou selhat nepředvídatelným způsobem, modul runtime nebude pokoušet o odeberte vlastní nepředvídatelným chyb z metody, které jsou zavedené službou opožděné JIT – kompilace, slovníku obecné typy naplnění nebo vlákno zruší, např. To znamená při aktivaci tento MDA označuje, že modul runtime neobsahuje zavolat metodu CER definovaný; Graf volání byl ukončen v tomto uzlu, protože nadále připravit tento podstrom pomohou maskování potenciální chyby.  
  
## <a name="resolution"></a>Rozlišení  
 Přidejte platný spolehlivost kontrakt funkce nebo nepoužívejte volání této funkce.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Účinek volání kontraktu slabé z CER může být selhání CER k dokončení operace. To může vést k poškození systému souborů <xref:System.AppDomain> zpracování stavu.  
  
## <a name="output"></a>Výstup  
 Následuje příklad výstupu z této (mda).  
  
 `Method 'MethodWithCer', while executing within a constrained execution region, makes a call at IL offset 0x000C to 'MethodWithWeakContract', which does not have a sufficiently strong reliability contract and might cause non-deterministic results.`  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
