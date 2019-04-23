---
title: invalidCERCall – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- invalid CER calls
- InvalidCERCall MDA
- MDAs (managed debugging assistants), CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: c4577410-602e-44e5-9dab-fea7c55bcdfe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a68aac2a92a0569e288da858e4a4e4695fd5eaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193912"
---
# <a name="invalidcercall-mda"></a>invalidCERCall – pomocník spravovaného ladění (MDA)
`invalidCERCall` Pomocníka spravovaného ladění (MDA) se aktivuje při volání v grafu (CER) oblasti omezeného provádění metody, která nemá žádný kontrakt spolehlivosti nebo kontrakt příliš slabé. Slabé smlouvy je kontrakt, který deklaruje, že nejhorší případ stavu poškození mají větší rozsah než instance předává do volání, to znamená, <xref:System.AppDomain> stav procesu může dojít k poškození nebo, který není výsledek vždy nedeterministicky nelze vypočítat Při volání v rámci CER.  
  
## <a name="symptoms"></a>Příznaky  
 Neočekávané výsledky při spuštění kódu v CER. Příznaky se netýkají. By mohly být neočekávané <xref:System.OutOfMemoryException>, <xref:System.Threading.ThreadAbortException>, nebo další výjimky při volání do metody nespolehlivé vzhledem k tomu, že modul runtime nepřešly připravit předem nebo chránit z <xref:System.Threading.ThreadAbortException> výjimky za běhu. Větší hrozbu je, že všechny výjimky vyplývající z metody v době běhu může ponechte <xref:System.AppDomain> nebo zpracovat v nestabilním stavu, které bylo v rozporu s cílem CER. Z důvodů, proč se vytvoří CER je vyhnout poškození stavu takovou situaci. Příznaky poškozený stav jsou specifické pro aplikaci, protože definice konzistentně se liší mezi aplikacemi.  
  
## <a name="cause"></a>Příčina  
 Kód v rámci CER volá funkci bez <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> nebo s slabé <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> , který není kompatibilní s používané CER.  
  
 Z hlediska syntaxe kontrakt spolehlivosti, je slabé kontrakt kontrakt, který nemá <xref:System.Runtime.ConstrainedExecution.Consistency> hodnota výčtu nebo určuje <xref:System.Runtime.ConstrainedExecution.Consistency> hodnotu <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>, nebo <xref:System.Runtime.ConstrainedExecution.Cer.None>. Kterákoli z těchto podmínek označuje, že kód volá může bránit ve snaze jiný kód v CER udržovat konzistentní stav.  CERs povolit kód přistupovat ke všem chybám velmi deterministické způsobem, údržbu interní výstupních podmínek, které jsou důležité k aplikaci a umožňuje pracovat v obličej systému přechodné chyby, jako jsou například výjimky na více instancí z důvodu nedostatku paměti.  
  
 Aktivace toto MDA určuje možnost tak, aby volající nebyl očekáván nebo opustí, který může selhat v CER volané metody <xref:System.AppDomain> nebo zpracovat stav poškozený, nebo neopravitelným. Samozřejmě je volána kód se může správně spustit a problému je jednoduše chybějící kontrakt. Ale problematiku zápis spolehlivého kódu jsou drobné a absence kontraktu je vhodný indikátor, který nemusí být správně spuštěn kód. Kontrakty jsou indikátory, které spolehlivě kódovaný programátora a také slibuje, že tyto záruky nedojde ke změně v budoucnu revize kódu.  To znamená že smlouvách jsou deklarace záměr a nikoli pouze podrobnosti implementace.  
  
 Protože jakoukoli metodou s kontraktem slabé nebo neexistující mohou selhat nepředvídatelnými způsoby, modul runtime nebude pokoušet odstraňte přitom všechny své vlastní nepředvídatelných chyb z metody, která vznikají zavlečením opožděné kompilace JIT, slovník obecných typů naplnění nebo vlákna přeruší, např. To znamená když je toto MDA aktivováno, znamená to, že modul runtime nenabízela volané metody CER definovanému; v tomto uzlu byl ukončen grafu volání, vzhledem k tomu, že budete pokračovat k přípravě tento podstrom by pomohl maskování potenciální chyby.  
  
## <a name="resolution"></a>Řešení  
 Přidat smlouvu platný spolehlivost funkci nebo Vyhněte se použití volání dané funkce.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Efekt volání slabé smlouvy z CER může být selhání CER pro dokončení jeho operace. To může vést k poškození <xref:System.AppDomain> zpracování stavu.  
  
## <a name="output"></a>Výstup  
 Tady je ukázkový výstup z tohoto MDA.  
  
 `Method 'MethodWithCer', while executing within a constrained execution region, makes a call at IL offset 0x000C to 'MethodWithWeakContract', which does not have a sufficiently strong reliability contract and might cause non-deterministic results.`  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
