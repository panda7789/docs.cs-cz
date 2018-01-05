---
title: "moduloObjectHashcode – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 618196473e8e947e84b0506771bce84ee71a1c2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="a5f91-102">moduloObjectHashcode – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="a5f91-102">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="a5f91-103">`moduloObjectHashcode` Pomocník spravovaného ladění (MDA) změní chování <xref:System.Object> třída k provedení modulo operace na vrátil kód hash <xref:System.Object.GetHashCode%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="a5f91-103">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="a5f91-104">Modulus výchozí pro tento MDA je 1, což způsobí, že <xref:System.Object.GetHashCode%2A> vrátit 0 pro všechny objekty.</span><span class="sxs-lookup"><span data-stu-id="a5f91-104">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a5f91-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="a5f91-105">Symptoms</span></span>  
 <span data-ttu-id="a5f91-106">Po přesunutí na novou verzi common language runtime (CLR), program již provede správně:</span><span class="sxs-lookup"><span data-stu-id="a5f91-106">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
-   <span data-ttu-id="a5f91-107">Tento program je získávání nesprávný objektu z <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="a5f91-107">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
-   <span data-ttu-id="a5f91-108">Pořadí výčtu z <xref:System.Collections.Hashtable> obsahuje změny, která dělí program.</span><span class="sxs-lookup"><span data-stu-id="a5f91-108">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
-   <span data-ttu-id="a5f91-109">Dva objekty, které používá k rovná již nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="a5f91-109">Two objects that used to be equal are no longer equal.</span></span>  
  
-   <span data-ttu-id="a5f91-110">Nyní jsou stejné dva objekty, které používají k nesmí být stejné.</span><span class="sxs-lookup"><span data-stu-id="a5f91-110">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a5f91-111">příčina</span><span class="sxs-lookup"><span data-stu-id="a5f91-111">Cause</span></span>  
 <span data-ttu-id="a5f91-112">Váš program může být získávání nesprávný objektu z <xref:System.Collections.Hashtable> protože provádění <xref:System.Object.Equals%2A> metody pro třídu pro klíč do <xref:System.Collections.Hashtable> testy rovnosti objektů srovnáním výsledků volání <xref:System.Object.GetHashCode%2A> – metoda .</span><span class="sxs-lookup"><span data-stu-id="a5f91-112">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="a5f91-113">Hash – kódy nepoužívejte k testování rovnosti objekt, protože dva objekty může mít stejnou hodnotu hash, i když je jejich odpovídající pole mají různé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a5f91-113">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="a5f91-114">Tyto kód kolize hodnot hash, i když je taková situace vzácná, v praxi, dojít.</span><span class="sxs-lookup"><span data-stu-id="a5f91-114">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="a5f91-115">To má na účinek <xref:System.Collections.Hashtable> vyhledávání je, že dva klíče, které se neshodují se zdají být rovna a nesprávný objekt je vrácen z <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="a5f91-115">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="a5f91-116">Z důvodů výkonu implementace <xref:System.Object.GetHashCode%2A> runtime verze, takže kolize, které nemusí být na jednu verzi může dojít v budoucích verzích se může změnit.</span><span class="sxs-lookup"><span data-stu-id="a5f91-116">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="a5f91-117">Povolte tento MDA k ověření, zda má váš kód chyby při konfliktu kódů hash.</span><span class="sxs-lookup"><span data-stu-id="a5f91-117">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="a5f91-118">Pokud povolena, budou tato MDA <xref:System.Object.GetHashCode%2A> metoda vrátí 0, což vede k všech kódů hash kolize.</span><span class="sxs-lookup"><span data-stu-id="a5f91-118">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="a5f91-119">Pouze účinku povolení, které na váš program by měl mít tato MDA je váš program probíhá pomaleji.</span><span class="sxs-lookup"><span data-stu-id="a5f91-119">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="a5f91-120">Pořadí výčtu z <xref:System.Collections.Hashtable> může změnit z jedné verze modulu runtime, když se jiný algoritmus používaný k výpočtu kódů hash pro změny klíče.</span><span class="sxs-lookup"><span data-stu-id="a5f91-120">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="a5f91-121">K ověření, zda váš program trvá závislostí v řádu výčet klíče nebo hodnoty mimo zatřiďovací tabulku, můžete povolit tuto (mda).</span><span class="sxs-lookup"><span data-stu-id="a5f91-121">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a5f91-122">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="a5f91-122">Resolution</span></span>  
 <span data-ttu-id="a5f91-123">Hash – kódy nikdy nepoužívejte jako náhrada za identity objektu.</span><span class="sxs-lookup"><span data-stu-id="a5f91-123">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="a5f91-124">Implementace přepis metody <xref:System.Object.Equals%2A?displayProperty=nameWithType> metoda není porovnat kódů hash.</span><span class="sxs-lookup"><span data-stu-id="a5f91-124">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="a5f91-125">Nevytvářejte závislosti v řádu výčty klíče nebo hodnoty hash – tabulky.</span><span class="sxs-lookup"><span data-stu-id="a5f91-125">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a5f91-126">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="a5f91-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="a5f91-127">Aplikace pracovat pomaleji, pokud je povolena tato (mda).</span><span class="sxs-lookup"><span data-stu-id="a5f91-127">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="a5f91-128">Tato MDA jednoduše trvá hash, která by byly vráceny a místo toho vrátí zbytek po dělený numerického zbytku.</span><span class="sxs-lookup"><span data-stu-id="a5f91-128">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a5f91-129">Výstup</span><span class="sxs-lookup"><span data-stu-id="a5f91-129">Output</span></span>  
 <span data-ttu-id="a5f91-130">Neexistuje žádný výstup pro tento (mda).</span><span class="sxs-lookup"><span data-stu-id="a5f91-130">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a5f91-131">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="a5f91-131">Configuration</span></span>  
 <span data-ttu-id="a5f91-132">`modulus` Atribut určuje numerického zbytku použít na hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="a5f91-132">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="a5f91-133">Výchozí hodnota je 1.</span><span class="sxs-lookup"><span data-stu-id="a5f91-133">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5f91-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5f91-134">See Also</span></span>  
 <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.Object.Equals%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="a5f91-135">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="a5f91-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
