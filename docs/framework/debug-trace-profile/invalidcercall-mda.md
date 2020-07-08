---
title: invalidCERCall – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění invalidCERCall – (MDA), který se aktivuje v případě neplatného volání v grafu v oblasti omezeného spuštění (CER).
ms.date: 03/30/2017
helpviewer_keywords:
- invalid CER calls
- InvalidCERCall MDA
- MDAs (managed debugging assistants), CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: c4577410-602e-44e5-9dab-fea7c55bcdfe
ms.openlocfilehash: dec32a81929d72274757b75cb03d6615d9fa948b
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051789"
---
# <a name="invalidcercall-mda"></a>invalidCERCall – pomocník spravovaného ladění (MDA)
`invalidCERCall`Pomocník spravovaného ladění (MDA) je aktivován, pokud je volání v grafu s omezeným prováděním (CER) k metodě, která nemá žádnou smlouvu o spolehlivosti nebo nadměrnému slabému kontraktu. Slabý kontrakt je kontrakt, který deklaruje, že poškození nejhoršího případu má větší rozsah než instance předaná volání, to znamená, že <xref:System.AppDomain> stav procesu nebo může být poškozený nebo že jeho výsledek není vždy deterministické, pokud je volán v rámci CER.  
  
## <a name="symptoms"></a>Příznaky  
 Neočekávané výsledky při provádění kódu v CER Příznaky nejsou specifické. Mohou to být neočekávané <xref:System.OutOfMemoryException> , <xref:System.Threading.ThreadAbortException> nebo jiné výjimky při volání do nespolehlivé metody, protože modul runtime nepřipravil předem čas nebo ho předá <xref:System.Threading.ThreadAbortException> za běhu před výjimkami. Větší hrozba je, že jakákoli výjimka vyplývající z metody v době běhu může opustit <xref:System.AppDomain> proces nebo v nestabilním stavu, což je v rozporu s cílem CER. Důvodem, proč je vytvořený CER, je zabránit poškození stavu, jako je to. Příznaky poškozeného stavu jsou specifické pro aplikace, protože definice konzistentního stavu se mezi aplikacemi liší.  
  
## <a name="cause"></a>Příčina  
 Kód v rámci CER volá funkci bez <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> nebo se slabým <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> , která není kompatibilní se spuštěným v CER.  
  
 V případě syntaxe kontraktu spolehlivosti je malý kontrakt kontraktem, který neurčuje <xref:System.Runtime.ConstrainedExecution.Consistency> hodnotu výčtu nebo určuje <xref:System.Runtime.ConstrainedExecution.Consistency> hodnotu <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess> , <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain> nebo <xref:System.Runtime.ConstrainedExecution.Cer.None> . Kterákoli z těchto podmínek indikuje, že volaný kód může bránit v tom, aby bylo možné zabránit v konzistentním stavu úsilím druhého kódu ve službě CER.  CERs umožňuje kódu považovat chyby za velmi deterministické, zachovat interní invarianty, které jsou pro aplikaci důležité, a umožnit tak pokračování v běhu, jako je třeba výjimka z hlediska nedostatku paměti.  
  
 Aktivace této služby MDA indikuje možnost, že metoda, která je volána v CER, může selhat způsobem, který volající neočekával, nebo který opustí <xref:System.AppDomain> stav procesu nebo poškozený. Volaný kód samozřejmě může být spuštěn správně a problém je jednoduše chybějící kontrakt. Problémy spojené s psaním spolehlivého kódu jsou ale malé a absence kontraktu je dobrým indikátorem, že kód se nemusí správně spustit. Kontrakty jsou indikátory, které programátor má spolehlivé kódování a také příslibů, že se tyto záruky v budoucích revizích kódu nezmění.  To znamená, že kontrakty jsou deklarace záměru a ne pouze podrobnosti implementace.  
  
 Vzhledem k tomu, že jakákoli metoda se slabou nebo neexistující smlouvou může selhat v mnoha nepředvídatelných způsobech, modul runtime se nepokusí odebrat žádné vlastní nepředvídatelné selhání z metody, která je zavedena opožděným kompilováním JIT, obecnými slovníky slovníku nebo přerušením vlákna, například. To znamená, že když je tento MDA aktivován, znamená to, že modul runtime nezahrnuje volanou metodu ve definovaném CER. graf volání byl ukončen v tomto uzlu, protože pokračováním v přípravě tohoto podstromu bude snazší maskovat potenciální chybu.  
  
## <a name="resolution"></a>Řešení  
 Přidejte k funkci platný kontrakt spolehlivosti nebo nepoužívejte volání této funkce.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Výsledkem volání slabé smlouvy ze CER může být chyba CER při provádění operací. To může vést k poškození <xref:System.AppDomain> stavu procesu.  
  
## <a name="output"></a>Výstup  
 Následuje ukázkový výstup z tohoto MDA.  
  
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

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
