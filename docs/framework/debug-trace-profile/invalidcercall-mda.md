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
ms.openlocfilehash: d508beb697e07f7d3b960b6627b9a07ffe25adf4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052639"
---
# <a name="invalidcercall-mda"></a>invalidCERCall – pomocník spravovaného ladění (MDA)
Pomocník `invalidCERCall` spravovaného ladění (MDA) je aktivován, pokud je volání v grafu s omezeným prováděním (CER) k metodě, která nemá žádnou smlouvu o spolehlivosti nebo nadměrnému slabému kontraktu. Slabý kontrakt je kontrakt, který deklaruje, že poškození nejhoršího případu má větší rozsah než instance předaná volání, to znamená, <xref:System.AppDomain> že stav procesu nebo může být poškozený nebo že jeho výsledek není vždycky deterministický Compute. volá se v rámci CER.  
  
## <a name="symptoms"></a>Příznaky  
 Neočekávané výsledky při provádění kódu v CER Příznaky nejsou specifické. Mohou to být neočekávané <xref:System.OutOfMemoryException> <xref:System.Threading.ThreadAbortException>, nebo jiné výjimky při volání do nespolehlivé metody, protože modul runtime nepřipravil předem <xref:System.Threading.ThreadAbortException> čas nebo ho předá za běhu před výjimkami. Větší hrozba je, že jakákoli výjimka vyplývající z metody v době běhu může opustit <xref:System.AppDomain> proces nebo v nestabilním stavu, což je v rozporu s cílem CER. Důvodem, proč je vytvořený CER, je zabránit poškození stavu, jako je to. Příznaky poškozeného stavu jsou specifické pro aplikace, protože definice konzistentního stavu se mezi aplikacemi liší.  
  
## <a name="cause"></a>příčina  
 Kód v rámci CER volá funkci bez <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> nebo se slabým <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> , která není kompatibilní se spuštěným v CER.  
  
 V případě syntaxe kontraktu spolehlivosti je malý kontrakt kontraktem, který <xref:System.Runtime.ConstrainedExecution.Consistency> neurčuje hodnotu výčtu nebo <xref:System.Runtime.ConstrainedExecution.Consistency> Určuje hodnotu <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>nebo <xref:System.Runtime.ConstrainedExecution.Cer.None>. Kterákoli z těchto podmínek indikuje, že volaný kód může bránit v tom, aby bylo možné zabránit v konzistentním stavu úsilím druhého kódu ve službě CER.  CERs umožňuje kódu považovat chyby za velmi deterministické, zachovat interní invarianty, které jsou pro aplikaci důležité, a umožnit tak pokračování v běhu, jako je třeba výjimka z hlediska nedostatku paměti.  
  
 Aktivace této služby MDA indikuje možnost, že metoda, která je volána v CER, může selhat způsobem, který volající neočekával, nebo který opustí <xref:System.AppDomain> stav procesu nebo poškozený. Volaný kód samozřejmě může být spuštěn správně a problém je jednoduše chybějící kontrakt. Problémy spojené s psaním spolehlivého kódu jsou ale malé a absence kontraktu je dobrým indikátorem, že kód se nemusí správně spustit. Kontrakty jsou indikátory, které programátor má spolehlivé kódování a také příslibů, že se tyto záruky v budoucích revizích kódu nezmění.  To znamená, že kontrakty jsou deklarace záměru a ne pouze podrobnosti implementace.  
  
 Vzhledem k tomu, že jakákoli metoda se slabou nebo neexistující smlouvou může potenciálně selhat v mnoha nepředvídatelných způsobech, modul runtime se nepokusí odebrat žádné vlastní nepředvídatelné selhání z metody, která je zavedena opožděným kompilováním JIT, obecný slovník naplnění nebo přerušení vlákna, například. To znamená, že když je tento MDA aktivován, znamená to, že modul runtime nezahrnuje volanou metodu ve definovaném CER. graf volání byl ukončen v tomto uzlu, protože pokračováním v přípravě tohoto podstromu bude snazší maskovat potenciální chybu.  
  
## <a name="resolution"></a>Řešení  
 Přidejte k funkci platný kontrakt spolehlivosti nebo nepoužívejte volání této funkce.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Výsledkem volání slabé smlouvy ze CER může být chyba CER při provádění operací. To může vést k poškození <xref:System.AppDomain> stavu procesu.  
  
## <a name="output"></a>Výstup  
 Následuje ukázkový výstup z tohoto MDA.  
  
 `Method 'MethodWithCer', while executing within a constrained execution region, makes a call at IL offset 0x000C to 'MethodWithWeakContract', which does not have a sufficiently strong reliability contract and might cause non-deterministic results.`  
  
## <a name="configuration"></a>Konfiguraci  
  
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
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
