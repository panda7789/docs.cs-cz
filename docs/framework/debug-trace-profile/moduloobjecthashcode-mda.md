---
title: moduloObjectHashcode – pomocník spravovaného ladění (MDA)
description: Projděte si pomocníka spravovaného ladění moduloObjectHashcode (MDA), který změní třídu objektu tak, aby získala zbývající hodnotu ve výsledku metody GetHashCode.
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
ms.openlocfilehash: a929ec2b9196f1f6cad0528fdf7323839a86fa55
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052062"
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="bbe15-103">moduloObjectHashcode – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="bbe15-103">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="bbe15-104">`moduloObjectHashcode`Pomocník spravovaného ladění (MDA) změní chování <xref:System.Object> třídy a provede operaci modulo u kódu hash vráceného <xref:System.Object.GetHashCode%2A> metodou.</span><span class="sxs-lookup"><span data-stu-id="bbe15-104">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="bbe15-105">Výchozí modul pro tento MDA je 1, což způsobí, že <xref:System.Object.GetHashCode%2A> vrátí 0 pro všechny objekty.</span><span class="sxs-lookup"><span data-stu-id="bbe15-105">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="bbe15-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="bbe15-106">Symptoms</span></span>  
 <span data-ttu-id="bbe15-107">Po přesunu na novou verzi modulu CLR (Common Language Runtime) se program již neprovádí správně:</span><span class="sxs-lookup"><span data-stu-id="bbe15-107">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
- <span data-ttu-id="bbe15-108">Program získává špatný objekt z <xref:System.Collections.Hashtable> .</span><span class="sxs-lookup"><span data-stu-id="bbe15-108">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
- <span data-ttu-id="bbe15-109">Pořadí výčtu z a <xref:System.Collections.Hashtable> má změnu, která program přerušuje.</span><span class="sxs-lookup"><span data-stu-id="bbe15-109">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
- <span data-ttu-id="bbe15-110">Dva objekty, které mají být rovny, se již neshodují.</span><span class="sxs-lookup"><span data-stu-id="bbe15-110">Two objects that used to be equal are no longer equal.</span></span>  
  
- <span data-ttu-id="bbe15-111">Jsou nyní stejné dva objekty, které se neshodují.</span><span class="sxs-lookup"><span data-stu-id="bbe15-111">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="bbe15-112">Příčina</span><span class="sxs-lookup"><span data-stu-id="bbe15-112">Cause</span></span>  
 <span data-ttu-id="bbe15-113">Váš program může získat špatný objekt z objektu, <xref:System.Collections.Hashtable> protože implementace <xref:System.Object.Equals%2A> metody třídy pro klíč do <xref:System.Collections.Hashtable> testů pro rovnost objektů porovnáním výsledků volání <xref:System.Object.GetHashCode%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bbe15-113">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="bbe15-114">Kódy hash by se neměly používat k testování rovnosti objektů, protože dva objekty mohou mít stejný kód hash, a to i v případě, že jejich příslušná pole mají jiné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bbe15-114">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="bbe15-115">Tyto kolizí kódů hash, i když jsou v praxi zřídka, proběhnou.</span><span class="sxs-lookup"><span data-stu-id="bbe15-115">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="bbe15-116">Efekt, který je výsledkem <xref:System.Collections.Hashtable> vyhledávání, je, že dva klíče, které nejsou stejné, se zdají být stejné a chybný objekt je vrácen z <xref:System.Collections.Hashtable> .</span><span class="sxs-lookup"><span data-stu-id="bbe15-116">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="bbe15-117">Z důvodů výkonu může implementace nástroje <xref:System.Object.GetHashCode%2A> změnit mezi verzemi modulu runtime, takže kolize, ke kterým může dojít v jedné verzi, se mohou vyskytnout v následujících verzích.</span><span class="sxs-lookup"><span data-stu-id="bbe15-117">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="bbe15-118">Povolte Tento MDA k otestování, jestli váš kód obsahuje chyby, když dojde ke kolizi kódů hash.</span><span class="sxs-lookup"><span data-stu-id="bbe15-118">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="bbe15-119">Je-li tato možnost povolena, způsobí to, že <xref:System.Object.GetHashCode%2A> Metoda vrátí hodnotu 0, což vede ke konfliktu všech kódů hash.</span><span class="sxs-lookup"><span data-stu-id="bbe15-119">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="bbe15-120">Jediným účinkem, který umožňuje této službě MDA, by měl mít program v programu, že váš program běží pomaleji.</span><span class="sxs-lookup"><span data-stu-id="bbe15-120">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="bbe15-121">Pořadí výčtu ze se <xref:System.Collections.Hashtable> může změnit z jedné verze modulu runtime na jiný, pokud algoritmus používaný k výpočtu kódů hash pro změnu klíče.</span><span class="sxs-lookup"><span data-stu-id="bbe15-121">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="bbe15-122">Chcete-li otestovat, zda program provedl závislost na pořadí výčtu klíčů nebo hodnot z zatřiďovací tabulky, můžete povolit Tento MDA.</span><span class="sxs-lookup"><span data-stu-id="bbe15-122">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="bbe15-123">Řešení</span><span class="sxs-lookup"><span data-stu-id="bbe15-123">Resolution</span></span>  
 <span data-ttu-id="bbe15-124">Nikdy nepoužívejte kódy hash jako náhradu identity objektu.</span><span class="sxs-lookup"><span data-stu-id="bbe15-124">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="bbe15-125">Implementujte přepsání <xref:System.Object.Equals%2A?displayProperty=nameWithType> metody pro neporovnání kódů hash.</span><span class="sxs-lookup"><span data-stu-id="bbe15-125">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="bbe15-126">Nevytvářejte závislosti na pořadí výčtů klíčů nebo hodnot v zatřiďovacích tabulkách.</span><span class="sxs-lookup"><span data-stu-id="bbe15-126">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="bbe15-127">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="bbe15-127">Effect on the Runtime</span></span>  
 <span data-ttu-id="bbe15-128">Pokud je tento MDA povolený, aplikace běží pomaleji.</span><span class="sxs-lookup"><span data-stu-id="bbe15-128">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="bbe15-129">Tento MDA jednoduše převezme kód hash, který by byl vrácen, a místo toho vrátí zbytek, pokud je dělen modulem.</span><span class="sxs-lookup"><span data-stu-id="bbe15-129">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="bbe15-130">Výstup</span><span class="sxs-lookup"><span data-stu-id="bbe15-130">Output</span></span>  
 <span data-ttu-id="bbe15-131">Pro tento MDA není k dispozici žádný výstup.</span><span class="sxs-lookup"><span data-stu-id="bbe15-131">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="bbe15-132">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="bbe15-132">Configuration</span></span>  
 <span data-ttu-id="bbe15-133">`modulus`Atribut určuje zbytky používané v kódu hash.</span><span class="sxs-lookup"><span data-stu-id="bbe15-133">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="bbe15-134">Výchozí hodnota je 1.</span><span class="sxs-lookup"><span data-stu-id="bbe15-134">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bbe15-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="bbe15-135">See also</span></span>

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bbe15-136">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="bbe15-136">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
