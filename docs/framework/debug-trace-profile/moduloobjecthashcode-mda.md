---
title: moduloObjectHashcode – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d8f6975d117d9920d2199c3996246822d1fdb6c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170765"
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="5d884-102">moduloObjectHashcode – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="5d884-102">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="5d884-103">`moduloObjectHashcode` Pomocníka spravovaného ladění (MDA) změní chování <xref:System.Object> pro provádění modulo operace na vrátil kód hash <xref:System.Object.GetHashCode%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="5d884-103">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="5d884-104">Výchozí modul pro toto MDA je 1, což způsobí, že <xref:System.Object.GetHashCode%2A> vrátit 0 pro všechny objekty.</span><span class="sxs-lookup"><span data-stu-id="5d884-104">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5d884-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="5d884-105">Symptoms</span></span>  
 <span data-ttu-id="5d884-106">Po přesunutí na novou verzi modulu common language runtime (CLR), program už správně provede:</span><span class="sxs-lookup"><span data-stu-id="5d884-106">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
-   <span data-ttu-id="5d884-107">Program je stále nesprávný objekt z <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="5d884-107">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
-   <span data-ttu-id="5d884-108">Pořadí výčtu ze <xref:System.Collections.Hashtable> má změnu, která program přestane fungovat.</span><span class="sxs-lookup"><span data-stu-id="5d884-108">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
-   <span data-ttu-id="5d884-109">Dva objekty, které používají musí rovnat už nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="5d884-109">Two objects that used to be equal are no longer equal.</span></span>  
  
-   <span data-ttu-id="5d884-110">Nyní jsou objekty, které používají nebude stejný jako rovnocenné.</span><span class="sxs-lookup"><span data-stu-id="5d884-110">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5d884-111">Příčina</span><span class="sxs-lookup"><span data-stu-id="5d884-111">Cause</span></span>  
 <span data-ttu-id="5d884-112">Váš program může zobrazovat v objektu nesprávného z <xref:System.Collections.Hashtable> protože provádění <xref:System.Object.Equals%2A> metody ve třídě pro klíč do <xref:System.Collections.Hashtable> testy pro rovnost objektů porovnáním výsledky volání <xref:System.Object.GetHashCode%2A> – metoda .</span><span class="sxs-lookup"><span data-stu-id="5d884-112">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="5d884-113">Kódů hash by neměl použije k testování rovnosti objektu, protože dva objekty mohou mít stejnou hodnotu hash, i když jejich příslušných polí mají různé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5d884-113">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="5d884-114">Tyto kolize hodnot hash kód, i když je vzácné v praxi, dojde k.</span><span class="sxs-lookup"><span data-stu-id="5d884-114">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="5d884-115">To má vliv <xref:System.Collections.Hashtable> vyhledávání je, že dva klíče, které nejsou shodné se zdají být stejné, a špatný objekt je vrácen z <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="5d884-115">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="5d884-116">Z důvodů výkonu provádění <xref:System.Object.GetHashCode%2A> verze modulu runtime, takže kolize, které nemusí být na jednu verzi můžou probíhat v budoucích verzích se může změnit.</span><span class="sxs-lookup"><span data-stu-id="5d884-116">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="5d884-117">Povolte toto MDA k otestování, jestli váš kód obsahuje chyby, když dojde ke kolizi těchto kódů hash.</span><span class="sxs-lookup"><span data-stu-id="5d884-117">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="5d884-118">Když je povoleno, toto MDA způsobí, že <xref:System.Object.GetHashCode%2A> metoda vrátí 0, výsledkem všech kódů hash kolize.</span><span class="sxs-lookup"><span data-stu-id="5d884-118">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="5d884-119">Pouze účinku povolení, které toto MDA by měl mít v programu je, že váš program spouští pomaleji.</span><span class="sxs-lookup"><span data-stu-id="5d884-119">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="5d884-120">Pořadí výčtu ze <xref:System.Collections.Hashtable> může změnit z jedné verze modulu runtime, pokud jiný algoritmus používaný k výpočtu hodnoty hash kódy pro změnu klíče.</span><span class="sxs-lookup"><span data-stu-id="5d884-120">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="5d884-121">K otestování, jestli váš program přijal závislost na pořadí výčtu klíče nebo hodnoty z tabulky hash, můžete povolit toto MDA.</span><span class="sxs-lookup"><span data-stu-id="5d884-121">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5d884-122">Řešení</span><span class="sxs-lookup"><span data-stu-id="5d884-122">Resolution</span></span>  
 <span data-ttu-id="5d884-123">Nikdy nepoužívejte kódů hash jako náhradu identity objektu.</span><span class="sxs-lookup"><span data-stu-id="5d884-123">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="5d884-124">Implementace přepsané <xref:System.Object.Equals%2A?displayProperty=nameWithType> metoda není výsledkem porovnání kódů hash.</span><span class="sxs-lookup"><span data-stu-id="5d884-124">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="5d884-125">Nevytvářejte závislosti v řádu výčty klíče nebo hodnoty ve zatřiďovacích tabulek.</span><span class="sxs-lookup"><span data-stu-id="5d884-125">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5d884-126">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="5d884-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="5d884-127">Aplikace poběží pomaleji, pokud je povolené toto MDA.</span><span class="sxs-lookup"><span data-stu-id="5d884-127">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="5d884-128">Toto MDA jednoduše převezme, která by byla vrácena hodnota hash a místo toho vrátí zbytek po vydělení zbytku.</span><span class="sxs-lookup"><span data-stu-id="5d884-128">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5d884-129">Výstup</span><span class="sxs-lookup"><span data-stu-id="5d884-129">Output</span></span>  
 <span data-ttu-id="5d884-130">Neexistuje žádný výstup pro toto MDA.</span><span class="sxs-lookup"><span data-stu-id="5d884-130">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5d884-131">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5d884-131">Configuration</span></span>  
 <span data-ttu-id="5d884-132">`modulus` Atribut určuje modul používá na hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="5d884-132">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="5d884-133">Výchozí hodnota je 1.</span><span class="sxs-lookup"><span data-stu-id="5d884-133">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d884-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d884-134">See also</span></span>

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5d884-135">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="5d884-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
