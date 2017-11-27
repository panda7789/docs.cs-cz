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
# <a name="invalidcercall-mda"></a><span data-ttu-id="d64f9-102">invalidCERCall – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="d64f9-102">invalidCERCall MDA</span></span>
<span data-ttu-id="d64f9-103">`invalidCERCall` Pomocník spravovaného ladění (MDA) se aktivuje při volání metody, která má žádné spolehlivost smlouvy nebo nadměrně slabé kontrakt v rámci omezeného provádění (CER) oblasti grafu.</span><span class="sxs-lookup"><span data-stu-id="d64f9-103">The `invalidCERCall` managed debugging assistant (MDA) is activated when there is a call within the constrained execution region (CER) graph to a method that has no reliability contract or an excessively weak contract.</span></span> <span data-ttu-id="d64f9-104">Slabé smlouva je kontrakt, který deklaruje, že nejhorší stav případu poškození je větší rozsah než instance předána volání, který je <xref:System.AppDomain> nebo stav procesu může dojít k poškození nebo že jeho výsledek není vždy nepodmíněně computable Při volání v rámci CER.</span><span class="sxs-lookup"><span data-stu-id="d64f9-104">A weak contract is a contract that declares that the worst case state corruption is of greater scope than the instance passed to the call, that is, the <xref:System.AppDomain> or process state may become corrupted or that its result is not always deterministically computable when called within a CER.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d64f9-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="d64f9-105">Symptoms</span></span>  
 <span data-ttu-id="d64f9-106">Neočekávané výsledky při provádění kódu v CER.</span><span class="sxs-lookup"><span data-stu-id="d64f9-106">Unexpected results when executing code in a CER.</span></span> <span data-ttu-id="d64f9-107">Příznaky nejsou specifické.</span><span class="sxs-lookup"><span data-stu-id="d64f9-107">The symptoms are not specific.</span></span> <span data-ttu-id="d64f9-108">Může být neočekávanou <xref:System.OutOfMemoryException>, <xref:System.Threading.ThreadAbortException>, nebo jiné výjimky při volání do metody nespolehlivé protože nepřešly připravit předem nebo chránit z modulu runtime <xref:System.Threading.ThreadAbortException> výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="d64f9-108">They could be an unexpected <xref:System.OutOfMemoryException>, a <xref:System.Threading.ThreadAbortException>, or other exceptions at the call into the unreliable method because the runtime did not prepare it ahead of time or protect it from <xref:System.Threading.ThreadAbortException> exceptions at run time.</span></span> <span data-ttu-id="d64f9-109">Větší hrozbu je, že všechny výjimky vyplývající z metody v době běhu může nechat <xref:System.AppDomain> nebo procesy v nestabilním stavu, které bylo v rozporu s cílem CER.</span><span class="sxs-lookup"><span data-stu-id="d64f9-109">A greater threat is that any exception resulting from the method at run time could leave the <xref:System.AppDomain> or process in an unstable state, which is contrary to the objective of a CER.</span></span> <span data-ttu-id="d64f9-110">Je vytvořena CER důvodem je, aby se zabránilo poškození stavu, jako je tato.</span><span class="sxs-lookup"><span data-stu-id="d64f9-110">The reason a CER is created is to avoid state corruptions such as this.</span></span> <span data-ttu-id="d64f9-111">Příznaky složky v porušeném stavu jsou specifické pro aplikaci, protože definice konzistentní stav se liší mezi aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="d64f9-111">The symptoms of corrupt state are application specific because the definition of consistent state is different between applications.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d64f9-112">příčina</span><span class="sxs-lookup"><span data-stu-id="d64f9-112">Cause</span></span>  
 <span data-ttu-id="d64f9-113">Kód v rámci CER volá funkci bez <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> nebo s weak <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> není kompatibilní s spuštěné v CER.</span><span class="sxs-lookup"><span data-stu-id="d64f9-113">Code within a CER is calling a function with no <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> or with a weak <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> that is not compatible with running in a CER.</span></span>  
  
 <span data-ttu-id="d64f9-114">Z hlediska spolehlivost kontrakt syntaxi, která je slabé kontrakt kontraktu, která neurčuje <xref:System.Runtime.ConstrainedExecution.Consistency> hodnota výčtu nebo určuje <xref:System.Runtime.ConstrainedExecution.Consistency> hodnotu <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>, nebo <xref:System.Runtime.ConstrainedExecution.Cer.None>.</span><span class="sxs-lookup"><span data-stu-id="d64f9-114">In terms of reliability contract syntax, a weak contract is a contract that does not specify a <xref:System.Runtime.ConstrainedExecution.Consistency> enumeration value or specifies a <xref:System.Runtime.ConstrainedExecution.Consistency> value of <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>, or <xref:System.Runtime.ConstrainedExecution.Cer.None>.</span></span> <span data-ttu-id="d64f9-115">Některé z těchto podmínek určuje, že kódu volaného může mít dopad na úsilí další kód CER pro zachování konzistentní stavu.</span><span class="sxs-lookup"><span data-stu-id="d64f9-115">Any of these conditions indicates that the code called may impede the efforts of the other code in the CER to maintain consistent state.</span></span>  <span data-ttu-id="d64f9-116">CERs umožnit kódu považovat chyb velmi deterministickou způsobem, údržbu interní výstupních podmínek, které jsou důležité pro aplikace a umožní tak jeho pokračovat v činnosti ve tučné přechodné chyby jako např. výjimky nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="d64f9-116">CERs allow code to treat errors in a very deterministic manner, maintaining internal invariants that are important to the application and allowing it to continue running in the face of transient errors such as out-of-memory exceptions.</span></span>  
  
 <span data-ttu-id="d64f9-117">Aktivace této MDA označuje možnost metoda volána v CER může selhat způsobem, který volající neočekávali, nebo která zůstane <xref:System.AppDomain> nebo zpracovat stavu poškozená nebo je nejde obnovit.</span><span class="sxs-lookup"><span data-stu-id="d64f9-117">The activation of this MDA indicates a possibility the method being called in the CER can fail in a way that the caller did not expect or that leaves the <xref:System.AppDomain> or process state corrupted or unrecoverable.</span></span> <span data-ttu-id="d64f9-118">Samozřejmě volané kód se může správně spustit a problému je jednoduše chybějící kontrakt.</span><span class="sxs-lookup"><span data-stu-id="d64f9-118">Of course, the called code might execute correctly and the problem is simply a missing contract.</span></span> <span data-ttu-id="d64f9-119">Ale problematiku zápis spolehlivého kódu jsou jemně a neexistence kontraktu je dobré indikátor, který kód se nemusí správně spustit.</span><span class="sxs-lookup"><span data-stu-id="d64f9-119">However, the issues involved in writing reliable code are subtle and the absence of a contract is a good indicator the code might not execute correctly.</span></span> <span data-ttu-id="d64f9-120">Kontrakty jsou indikátory, které programátorů má programového spolehlivě a také nabízí, že tyto záruky nedojde ke změně v budoucnosti revize kódu.</span><span class="sxs-lookup"><span data-stu-id="d64f9-120">The contracts are indicators that the programmer has coded reliably and also promises that these guarantees will not change in future revisions of the code.</span></span>  <span data-ttu-id="d64f9-121">To znamená že smluv jsou deklarace záměr a nikoli pouze podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="d64f9-121">That is, the contracts are declarations of intent and not just implementation details.</span></span>  
  
 <span data-ttu-id="d64f9-122">Protože libovolné metody s kontraktu slabé nebo neexistující mohou selhat nepředvídatelným způsobem, modul runtime nebude pokoušet o odeberte vlastní nepředvídatelným chyb z metody, které jsou zavedené službou opožděné JIT – kompilace, slovníku obecné typy naplnění nebo vlákno zruší, např.</span><span class="sxs-lookup"><span data-stu-id="d64f9-122">Because any method with a weak or nonexistent contract can potentially fail in many unpredictable ways, the runtime does not attempt to remove any of its own unpredictable failures from the method  that are introduced by lazy JIT-compiling, generics dictionary population, or thread aborts, for example.</span></span> <span data-ttu-id="d64f9-123">To znamená při aktivaci tento MDA označuje, že modul runtime neobsahuje zavolat metodu CER definovaný; Graf volání byl ukončen v tomto uzlu, protože nadále připravit tento podstrom pomohou maskování potenciální chyby.</span><span class="sxs-lookup"><span data-stu-id="d64f9-123">That is, when this MDA is activated, it indicates that the runtime did not include the called method in the CER being defined; the call graph was terminated at this node because continuing to prepare this subtree would help mask the potential error.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d64f9-124">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="d64f9-124">Resolution</span></span>  
 <span data-ttu-id="d64f9-125">Přidejte platný spolehlivost kontrakt funkce nebo nepoužívejte volání této funkce.</span><span class="sxs-lookup"><span data-stu-id="d64f9-125">Add a valid reliability contract to the function or avoid using that function call.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d64f9-126">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="d64f9-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="d64f9-127">Účinek volání kontraktu slabé z CER může být selhání CER k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="d64f9-127">The effect of calling a weak contract from a CER could be the CER failure to complete its operations.</span></span> <span data-ttu-id="d64f9-128">To může vést k poškození systému souborů <xref:System.AppDomain> zpracování stavu.</span><span class="sxs-lookup"><span data-stu-id="d64f9-128">This could lead to corruption of the <xref:System.AppDomain> process state.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d64f9-129">Výstup</span><span class="sxs-lookup"><span data-stu-id="d64f9-129">Output</span></span>  
 <span data-ttu-id="d64f9-130">Následuje příklad výstupu z této (mda).</span><span class="sxs-lookup"><span data-stu-id="d64f9-130">The following is sample output from this MDA.</span></span>  
  
 `Method 'MethodWithCer', while executing within a constrained execution region, makes a call at IL offset 0x000C to 'MethodWithWeakContract', which does not have a sufficiently strong reliability contract and might cause non-deterministic results.`  
  
## <a name="configuration"></a><span data-ttu-id="d64f9-131">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="d64f9-131">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d64f9-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="d64f9-132">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution>  
 [<span data-ttu-id="d64f9-133">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="d64f9-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
