---
title: "Parametr návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7d49c4263517830f46b1416684c7d9b874cda4db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-design"></a><span data-ttu-id="63148-102">Parametr návrhu</span><span class="sxs-lookup"><span data-stu-id="63148-102">Parameter Design</span></span>
<span data-ttu-id="63148-103">Tato část obsahuje obecné Rady ohledně návrhu parametr, včetně oddíly s pokyny pro kontrolu argumenty.</span><span class="sxs-lookup"><span data-stu-id="63148-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="63148-104">Kromě toho se seznamte s podle pokynů popsaných v [pojmenování parametry](../../../docs/standard/design-guidelines/naming-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="63148-104">In addition, you should refer to the guidelines described in [Naming Parameters](../../../docs/standard/design-guidelines/naming-parameters.md).</span></span>  
  
 <span data-ttu-id="63148-105">**PROVEĎTE ✓** používat alespoň odvozený typ parametru, který poskytuje funkci vyžadovanou člena.</span><span class="sxs-lookup"><span data-stu-id="63148-105">**✓ DO** use the least derived parameter type that provides the functionality required by the member.</span></span>  
  
 <span data-ttu-id="63148-106">Předpokládejme například, že můžete navrhnout metodu, která vytvoří výčet kolekce a vytiskne každou položku do konzoly.</span><span class="sxs-lookup"><span data-stu-id="63148-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="63148-107">Tato metoda by měla trvat <xref:System.Collections.IEnumerable> jako parametr, není <xref:System.Collections.ArrayList> nebo <xref:System.Collections.IList>, např.</span><span class="sxs-lookup"><span data-stu-id="63148-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>  
  
 <span data-ttu-id="63148-108">**X nesmí** používat vyhrazené parametry.</span><span class="sxs-lookup"><span data-stu-id="63148-108">**X DO NOT** use reserved parameters.</span></span>  
  
 <span data-ttu-id="63148-109">Další vstup na člena, je potřeba v některých budoucí verze, mohou být přidány nové přetížení.</span><span class="sxs-lookup"><span data-stu-id="63148-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>  
  
 <span data-ttu-id="63148-110">**X nesmí** mít veřejně vystaven metod, které berou ukazatele, pole ukazatele nebo vícerozměrná pole jako parametry.</span><span class="sxs-lookup"><span data-stu-id="63148-110">**X DO NOT** have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>  
  
 <span data-ttu-id="63148-111">Multidimenzionální pole a ukazatelé jsou relativně obtížně použitelný správně.</span><span class="sxs-lookup"><span data-stu-id="63148-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="63148-112">Ve většině případů může být rozhraní API upravený tak, aby Neberte tyto typy jako parametry.</span><span class="sxs-lookup"><span data-stu-id="63148-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>  
  
 <span data-ttu-id="63148-113">**PROVEĎTE ✓** umístit všechny `out` všechny hodnoty ve-následující parametry a `ref` parametry (s výjimkou pole parametrů), i když je výsledkem nekonzistence v parametru řazení mezi přetížení (najdete v části [člena Přetížení](../../../docs/standard/design-guidelines/member-overloading.md)).</span><span class="sxs-lookup"><span data-stu-id="63148-113">**✓ DO** place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](../../../docs/standard/design-guidelines/member-overloading.md)).</span></span>  
  
 <span data-ttu-id="63148-114">`out` Parametry se dají považovat za velmi návratové hodnoty, a jejich seskupování usnadňuje podpis metody pochopit.</span><span class="sxs-lookup"><span data-stu-id="63148-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>  
  
 <span data-ttu-id="63148-115">**PROVEĎTE ✓** být konzistentní názvy parametrů při přepisování členy nebo implementace členů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="63148-115">**✓ DO** be consistent in naming parameters when overriding members or implementing interface members.</span></span>  
  
 <span data-ttu-id="63148-116">To lépe komunikuje vztah mezi metody.</span><span class="sxs-lookup"><span data-stu-id="63148-116">This better communicates the relationship between the methods.</span></span>  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="63148-117">Volba mezi logickou parametry a výčtu</span><span class="sxs-lookup"><span data-stu-id="63148-117">Choosing Between Enum and Boolean Parameters</span></span>  
 <span data-ttu-id="63148-118">**PROVEĎTE ✓** použijte výčty, pokud člen byste jinak museli dvě nebo více parametrů logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="63148-118">**✓ DO** use enums if a member would otherwise have two or more Boolean parameters.</span></span>  
  
 <span data-ttu-id="63148-119">**X nesmí** používat logické hodnoty, pokud jste si naprosto jisti, nikdy bude potřeba více než dvě hodnoty.</span><span class="sxs-lookup"><span data-stu-id="63148-119">**X DO NOT** use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>  
  
 <span data-ttu-id="63148-120">Výčty získáte určitý prostor pro budoucí přidání hodnot, ale byste měli vědět všechny dopadů přidání hodnot do výčty, které jsou popsané v [návrhu výčtu](../../../docs/standard/design-guidelines/enum.md).</span><span class="sxs-lookup"><span data-stu-id="63148-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](../../../docs/standard/design-guidelines/enum.md).</span></span>  
  
 <span data-ttu-id="63148-121">**✓ ZVAŽTE** pomocí logických výrazů pro konstruktor parametry, které jsou hodnoty skutečně dvou stavů a jednoduše slouží k inicializaci logická hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="63148-121">**✓ CONSIDER** using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>  
  
### <a name="validating-arguments"></a><span data-ttu-id="63148-122">Ověřování argumenty</span><span class="sxs-lookup"><span data-stu-id="63148-122">Validating Arguments</span></span>  
 <span data-ttu-id="63148-123">**PROVEĎTE ✓** ověřte argumenty předaný veřejný, chráněný nebo – explicitně implementovaná členy.</span><span class="sxs-lookup"><span data-stu-id="63148-123">**✓ DO** validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="63148-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, nebo jeden z jejích podtříd, pokud se ověření nezdaří.</span><span class="sxs-lookup"><span data-stu-id="63148-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>  
  
 <span data-ttu-id="63148-125">Všimněte si, že samotné ověření nemusí nutně dojít ve veřejných nebo chráněného člena samotného.</span><span class="sxs-lookup"><span data-stu-id="63148-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="63148-126">K tomu mohlo dojít na nižší úrovni v některé rutiny soukromý nebo interní.</span><span class="sxs-lookup"><span data-stu-id="63148-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="63148-127">Hlavní bod je, že celém povrchu, který je zveřejněný koncovým uživatelům kontroluje argumenty.</span><span class="sxs-lookup"><span data-stu-id="63148-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>  
  
 <span data-ttu-id="63148-128">**PROVEĎTE ✓** throw <xref:System.ArgumentNullException> Pokud je předán prázdný argument a člen nepodporuje argumenty null.</span><span class="sxs-lookup"><span data-stu-id="63148-128">**✓ DO** throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>  
  
 <span data-ttu-id="63148-129">**PROVEĎTE ✓** ověření výčtu parametry.</span><span class="sxs-lookup"><span data-stu-id="63148-129">**✓ DO** validate enum parameters.</span></span>  
  
 <span data-ttu-id="63148-130">Nepředpokládejte výčtu argumenty bude v rozsah definovaný hodnotami výčtu.</span><span class="sxs-lookup"><span data-stu-id="63148-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="63148-131">Modul CLR umožňuje přetypování žádné celočíselnou hodnotu na hodnotu výčtu, i v případě, že hodnota není definována ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="63148-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>  
  
 <span data-ttu-id="63148-132">**X nesmí** použít <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> rozsahu výčtu kontrol.</span><span class="sxs-lookup"><span data-stu-id="63148-132">**X DO NOT** use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>  
  
 <span data-ttu-id="63148-133">**PROVEĎTE ✓** mějte na paměti, že měnitelný argumenty byl změněn. po jejich byly ověřeny.</span><span class="sxs-lookup"><span data-stu-id="63148-133">**✓ DO** be aware that mutable arguments might have changed after they were validated.</span></span>  
  
 <span data-ttu-id="63148-134">Pokud je člen citlivé na zabezpečení, můžete se doporučuje vytvoření kopie a poté ověření a zpracování argument.</span><span class="sxs-lookup"><span data-stu-id="63148-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>  
  
### <a name="parameter-passing"></a><span data-ttu-id="63148-135">Předávání parametrů</span><span class="sxs-lookup"><span data-stu-id="63148-135">Parameter Passing</span></span>  
 <span data-ttu-id="63148-136">Z pohledu návrháře framework, jsou tři hlavní skupiny parametrů: parametry, pomocí hodnoty `ref` parametrů, a `out` parametry.</span><span class="sxs-lookup"><span data-stu-id="63148-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>  
  
 <span data-ttu-id="63148-137">Když argument je předána prostřednictvím parametru-hodnota, člen obdrží kopii skutečného argument předaný v.</span><span class="sxs-lookup"><span data-stu-id="63148-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="63148-138">Pokud má argument hodnotu typu hodnoty, je kopie argumentu uložena v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="63148-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="63148-139">Pokud je argument typu odkazu, kopie odkaz na zprovozněn v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="63148-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="63148-140">Nejoblíbenější jazyky CLR, jako je C#, VB.NET a C++, výchozí nastavení předávání parametrů hodnotou.</span><span class="sxs-lookup"><span data-stu-id="63148-140">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>  
  
 <span data-ttu-id="63148-141">Když je argument předaný prostřednictvím `ref` parametr člen obdrží odkaz na skutečné argument předaný v.</span><span class="sxs-lookup"><span data-stu-id="63148-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="63148-142">Pokud má argument hodnotu typu hodnoty, je v zásobníku uvést odkaz na argument.</span><span class="sxs-lookup"><span data-stu-id="63148-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="63148-143">Pokud je argument typu odkazu, odkaz na odkaz na zprovozněn v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="63148-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="63148-144">`Ref`Parametry lze povolit člena pro úpravu argumenty předaná volající funkcí.</span><span class="sxs-lookup"><span data-stu-id="63148-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>  
  
 <span data-ttu-id="63148-145">`Out`parametry jsou podobné `ref` parametry se některé malé rozdíly.</span><span class="sxs-lookup"><span data-stu-id="63148-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="63148-146">Parametr je zpočátku považovat za nepřiřazené a nelze ho přečíst v těle člen před přiřazením některá z hodnot.</span><span class="sxs-lookup"><span data-stu-id="63148-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="63148-147">Parametr navíc má být přiděleny určitou hodnotu, než vrátí člena.</span><span class="sxs-lookup"><span data-stu-id="63148-147">Also, the parameter has to be assigned some value before the member returns.</span></span>  
  
 <span data-ttu-id="63148-148">**X nepoužívejte** pomocí `out` nebo `ref` parametry.</span><span class="sxs-lookup"><span data-stu-id="63148-148">**X AVOID** using `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="63148-149">Pomocí `out` nebo `ref` parametry vyžaduje zkušenosti s ukazatele, pochopení, jak se liší typy hodnot a typy odkazu a zpracování metod s více vrácených hodnot.</span><span class="sxs-lookup"><span data-stu-id="63148-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="63148-150">Navíc rozdíl mezi `out` a `ref` parametry nebyl pochopen široce.</span><span class="sxs-lookup"><span data-stu-id="63148-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="63148-151">Architekti Framework navrhování všem uživatelům by neměl očekávat uživatelům hlavní práci s `out` nebo `ref` parametry.</span><span class="sxs-lookup"><span data-stu-id="63148-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="63148-152">**X nesmí** předat odkazové typy odkazem.</span><span class="sxs-lookup"><span data-stu-id="63148-152">**X DO NOT** pass reference types by reference.</span></span>  
  
 <span data-ttu-id="63148-153">Existují některé omezené výjimky pravidla, jako je například metoda, která slouží k Prohodit odkazy.</span><span class="sxs-lookup"><span data-stu-id="63148-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>  
  
### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="63148-154">Členy s proměnný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="63148-154">Members with Variable Number of Parameters</span></span>  
 <span data-ttu-id="63148-155">Poskytnutím parametru pole jsou vyjádřeny členy, které může provádět proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="63148-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="63148-156">Například <xref:System.String> poskytuje následující metody:</span><span class="sxs-lookup"><span data-stu-id="63148-156">For example, <xref:System.String> provides the following method:</span></span>  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 <span data-ttu-id="63148-157">Uživatel potom může volat <xref:System.String.Format%2A?displayProperty=nameWithType> metoda následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="63148-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 <span data-ttu-id="63148-158">Přidávání do parametr pole jazyce C# params – klíčové slovo změny parametr parametr pole takzvané parametry a poskytuje zástupce k vytvoření dočasného pole.</span><span class="sxs-lookup"><span data-stu-id="63148-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 <span data-ttu-id="63148-159">To umožňuje uživateli volat metodu předáním elementy pole přímo v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="63148-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 <span data-ttu-id="63148-160">Všimněte si, že params – klíčové slovo lze přidat pouze poslední parametr v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="63148-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="63148-161">**✓ ZVAŽTE** přidávání params – klíčové slovo do pole parametry, pokud očekáváte, koncovým uživatelům předat pole s malý počet elementů.</span><span class="sxs-lookup"><span data-stu-id="63148-161">**✓ CONSIDER** adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="63148-162">Pokud je očekáváno, že velký počet elementů předány společné scénáře, uživatelé budou pravděpodobně není předejte tyto elementy vložené přesto a proto není nutné params – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="63148-162">If it’s expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>  
  
 <span data-ttu-id="63148-163">**X nepoužívejte** pomocí parametry pole, pokud má volající by téměř vždy již vstupu v matici.</span><span class="sxs-lookup"><span data-stu-id="63148-163">**X AVOID** using params arrays if the caller would almost always have the input already in an array.</span></span>  
  
 <span data-ttu-id="63148-164">Například by členy s parametry pole bajtů názvem téměř žádné předáním jednotlivých bajtů.</span><span class="sxs-lookup"><span data-stu-id="63148-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="63148-165">Z tohoto důvodu nepoužívejte parametry pole bajtů v rozhraní .NET Framework – klíčové slovo parametry.</span><span class="sxs-lookup"><span data-stu-id="63148-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>  
  
 <span data-ttu-id="63148-166">**X nesmí** použijte parametry pole, pokud je pole upraveném člen trvá parametr pole parametry.</span><span class="sxs-lookup"><span data-stu-id="63148-166">**X DO NOT** use params arrays if the array is modified by the member taking the params array parameter.</span></span>  
  
 <span data-ttu-id="63148-167">Z důvodu fakt, že mnoho kompilátory zapnout argumenty, které mají člena do dočasné pole v lokalitě volání pole může být dočasný objekt, a proto budou ztraceny všechny změny do pole.</span><span class="sxs-lookup"><span data-stu-id="63148-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>  
  
 <span data-ttu-id="63148-168">**✓ ZVAŽTE** pomocí klíčového slova parametry v jednoduchých přetížení, i když ho nelze použít na složitější přetížení.</span><span class="sxs-lookup"><span data-stu-id="63148-168">**✓ CONSIDER** using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>  
  
 <span data-ttu-id="63148-169">Položte otázku, pokud by uživatelé hodnotu s poli parametry ve jedním přetížením i v případě, že ho nebyl v všechny přetížení.</span><span class="sxs-lookup"><span data-stu-id="63148-169">Ask yourself if users would value having the params array in one overload even if it wasn’t in all overloads.</span></span>  
  
 <span data-ttu-id="63148-170">**PROVEĎTE ✓** zkuste pořadí parametrů, aby bylo možné použít params – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="63148-170">**✓ DO** try to order parameters to make it possible to use the params keyword.</span></span>  
  
 <span data-ttu-id="63148-171">**✓ ZVAŽTE** poskytnutí speciální přetížení a cesty kódu pro volání s malým počtem argumentů rozhraní API velmi náročné na výkon.</span><span class="sxs-lookup"><span data-stu-id="63148-171">**✓ CONSIDER** providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="63148-172">Díky tomu je možné, vyhněte se vytváření pole objektů při volání rozhraní API s malým počtem argumentů.</span><span class="sxs-lookup"><span data-stu-id="63148-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="63148-173">Názvy parametrů formuláři převzetím jednotném čísle parametru pole a přidáním číselnou příponou.</span><span class="sxs-lookup"><span data-stu-id="63148-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>  
  
 <span data-ttu-id="63148-174">Měli byste jenom to provést Pokud budete pro zvláštní případ celý kódová cesta, nejen vytvořte pole a volejte metodu obecnější.</span><span class="sxs-lookup"><span data-stu-id="63148-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>  
  
 <span data-ttu-id="63148-175">**PROVEĎTE ✓** Uvědomte si, že null by prošel jako argument parametry pole.</span><span class="sxs-lookup"><span data-stu-id="63148-175">**✓ DO** be aware that null could be passed as a params array argument.</span></span>  
  
 <span data-ttu-id="63148-176">Měli byste ověřit, že pole není null před zpracováním.</span><span class="sxs-lookup"><span data-stu-id="63148-176">You should validate that the array is not null before processing.</span></span>  
  
 <span data-ttu-id="63148-177">**X nesmí** použít `varargs` metody, které jsou známé jako se třemi tečkami.</span><span class="sxs-lookup"><span data-stu-id="63148-177">**X DO NOT** use the `varargs` methods, otherwise known as the ellipsis.</span></span>  
  
 <span data-ttu-id="63148-178">Některé jazyky CLR, jako je C++, podpora alternativní konvence pro předávání seznamy proměnné parametrů názvem `varargs` metody.</span><span class="sxs-lookup"><span data-stu-id="63148-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="63148-179">Konvence nepoužívejte v rozhraní, protože není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="63148-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>  
  
### <a name="pointer-parameters"></a><span data-ttu-id="63148-180">Parametry ukazatele</span><span class="sxs-lookup"><span data-stu-id="63148-180">Pointer Parameters</span></span>  
 <span data-ttu-id="63148-181">Obecně platí ukazatele neměla v veřejnou oblast Framework dobře navrženou spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="63148-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="63148-182">Ve většině případů, by měl být zapouzdřené ukazatele.</span><span class="sxs-lookup"><span data-stu-id="63148-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="63148-183">Ale v některých případech jsou požadovány důvodů interoperabilita ukazatele a použití ukazatele v takových případech je vhodné.</span><span class="sxs-lookup"><span data-stu-id="63148-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>  
  
 <span data-ttu-id="63148-184">**PROVEĎTE ✓** alternativu přinášejí kteréhokoli člena, který se použije argument ukazatele, protože ukazatele nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="63148-184">**✓ DO** provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>  
  
 <span data-ttu-id="63148-185">**X nepoužívejte** provádění nákladné argument kontrola ukazatel argumentů.</span><span class="sxs-lookup"><span data-stu-id="63148-185">**X AVOID** doing expensive argument checking of pointer arguments.</span></span>  
  
 <span data-ttu-id="63148-186">**PROVEĎTE ✓** použijte běžné konvence související ukazatele při návrhu členy s ukazatele.</span><span class="sxs-lookup"><span data-stu-id="63148-186">**✓ DO** follow common pointer-related conventions when designing members with pointers.</span></span>  
  
 <span data-ttu-id="63148-187">Například není třeba předat počáteční index, protože jednoduché aritmetika ukazatele je možné použít k dosažení stejného výsledku.</span><span class="sxs-lookup"><span data-stu-id="63148-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>  
  
 <span data-ttu-id="63148-188">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="63148-188">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="63148-189">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="63148-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63148-190">Viz také</span><span class="sxs-lookup"><span data-stu-id="63148-190">See Also</span></span>  
 [<span data-ttu-id="63148-191">Člen pokynů pro návrh</span><span class="sxs-lookup"><span data-stu-id="63148-191">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="63148-192">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="63148-192">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
