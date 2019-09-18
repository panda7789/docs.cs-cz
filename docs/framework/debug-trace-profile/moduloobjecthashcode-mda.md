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
ms.openlocfilehash: 1679e283a801044ad5a0baed89f17e6acc74259c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052447"
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="98d9a-102">moduloObjectHashcode – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="98d9a-102">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="98d9a-103">Pomocník spravovaného ladění (MDA) změní chování <xref:System.Object> třídy a provede operaci modulo u kódu <xref:System.Object.GetHashCode%2A> hash vráceného metodou. `moduloObjectHashcode`</span><span class="sxs-lookup"><span data-stu-id="98d9a-103">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="98d9a-104">Výchozí modul pro tento MDA je 1, což způsobí <xref:System.Object.GetHashCode%2A> , že vrátí 0 pro všechny objekty.</span><span class="sxs-lookup"><span data-stu-id="98d9a-104">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="98d9a-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="98d9a-105">Symptoms</span></span>  
 <span data-ttu-id="98d9a-106">Po přesunu na novou verzi modulu CLR (Common Language Runtime) se program již neprovádí správně:</span><span class="sxs-lookup"><span data-stu-id="98d9a-106">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
- <span data-ttu-id="98d9a-107">Program získává špatný objekt z <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="98d9a-107">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
- <span data-ttu-id="98d9a-108">Pořadí výčtu z a <xref:System.Collections.Hashtable> má změnu, která program přerušuje.</span><span class="sxs-lookup"><span data-stu-id="98d9a-108">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
- <span data-ttu-id="98d9a-109">Dva objekty, které mají být rovny, se již neshodují.</span><span class="sxs-lookup"><span data-stu-id="98d9a-109">Two objects that used to be equal are no longer equal.</span></span>  
  
- <span data-ttu-id="98d9a-110">Jsou nyní stejné dva objekty, které se neshodují.</span><span class="sxs-lookup"><span data-stu-id="98d9a-110">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="98d9a-111">příčina</span><span class="sxs-lookup"><span data-stu-id="98d9a-111">Cause</span></span>  
 <span data-ttu-id="98d9a-112">Váš program může získat špatný <xref:System.Collections.Hashtable> objekt z, protože implementace <xref:System.Object.Equals%2A> metody ve třídě <xref:System.Collections.Hashtable> pro klíč do testů pro rovnost objektů <xref:System.Object.GetHashCode%2A> porovnáním výsledků volání metody .</span><span class="sxs-lookup"><span data-stu-id="98d9a-112">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="98d9a-113">Kódy hash by se neměly používat k testování rovnosti objektů, protože dva objekty mohou mít stejný kód hash, a to i v případě, že jejich příslušná pole mají jiné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="98d9a-113">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="98d9a-114">Tyto kolizí kódů hash, i když jsou v praxi zřídka, proběhnou.</span><span class="sxs-lookup"><span data-stu-id="98d9a-114">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="98d9a-115">Efekt, který je výsledkem <xref:System.Collections.Hashtable> vyhledávání, je, že dva klíče, které nejsou stejné, se zdají být stejné a chybný objekt je vrácen <xref:System.Collections.Hashtable>z.</span><span class="sxs-lookup"><span data-stu-id="98d9a-115">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="98d9a-116">Z důvodů výkonu <xref:System.Object.GetHashCode%2A> může implementace nástroje změnit mezi verzemi modulu runtime, takže kolize, ke kterým může dojít v jedné verzi, se mohou vyskytnout v následujících verzích.</span><span class="sxs-lookup"><span data-stu-id="98d9a-116">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="98d9a-117">Povolte Tento MDA k otestování, jestli váš kód obsahuje chyby, když dojde ke kolizi kódů hash.</span><span class="sxs-lookup"><span data-stu-id="98d9a-117">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="98d9a-118">Je-li tato možnost povolena, <xref:System.Object.GetHashCode%2A> způsobí to, že metoda vrátí hodnotu 0, což vede ke konfliktu všech kódů hash.</span><span class="sxs-lookup"><span data-stu-id="98d9a-118">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="98d9a-119">Jediným účinkem, který umožňuje této službě MDA, by měl mít program v programu, že váš program běží pomaleji.</span><span class="sxs-lookup"><span data-stu-id="98d9a-119">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="98d9a-120">Pořadí výčtu ze <xref:System.Collections.Hashtable> se může změnit z jedné verze modulu runtime na jiný, pokud algoritmus používaný k výpočtu kódů hash pro změnu klíče.</span><span class="sxs-lookup"><span data-stu-id="98d9a-120">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="98d9a-121">Chcete-li otestovat, zda program provedl závislost na pořadí výčtu klíčů nebo hodnot z zatřiďovací tabulky, můžete povolit Tento MDA.</span><span class="sxs-lookup"><span data-stu-id="98d9a-121">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="98d9a-122">Řešení</span><span class="sxs-lookup"><span data-stu-id="98d9a-122">Resolution</span></span>  
 <span data-ttu-id="98d9a-123">Nikdy nepoužívejte kódy hash jako náhradu identity objektu.</span><span class="sxs-lookup"><span data-stu-id="98d9a-123">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="98d9a-124">Implementujte přepsání <xref:System.Object.Equals%2A?displayProperty=nameWithType> metody pro neporovnání kódů hash.</span><span class="sxs-lookup"><span data-stu-id="98d9a-124">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="98d9a-125">Nevytvářejte závislosti na pořadí výčtů klíčů nebo hodnot v zatřiďovacích tabulkách.</span><span class="sxs-lookup"><span data-stu-id="98d9a-125">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="98d9a-126">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="98d9a-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="98d9a-127">Pokud je tento MDA povolený, aplikace běží pomaleji.</span><span class="sxs-lookup"><span data-stu-id="98d9a-127">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="98d9a-128">Tento MDA jednoduše převezme kód hash, který by byl vrácen, a místo toho vrátí zbytek, pokud je dělen modulem.</span><span class="sxs-lookup"><span data-stu-id="98d9a-128">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="98d9a-129">Výstup</span><span class="sxs-lookup"><span data-stu-id="98d9a-129">Output</span></span>  
 <span data-ttu-id="98d9a-130">Pro tento MDA není k dispozici žádný výstup.</span><span class="sxs-lookup"><span data-stu-id="98d9a-130">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="98d9a-131">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="98d9a-131">Configuration</span></span>  
 <span data-ttu-id="98d9a-132">`modulus` Atribut určuje zbytky používané v kódu hash.</span><span class="sxs-lookup"><span data-stu-id="98d9a-132">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="98d9a-133">Výchozí hodnota je 1.</span><span class="sxs-lookup"><span data-stu-id="98d9a-133">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="98d9a-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98d9a-134">See also</span></span>

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="98d9a-135">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="98d9a-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
