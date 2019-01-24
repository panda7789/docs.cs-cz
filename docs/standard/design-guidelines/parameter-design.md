---
title: Návrh parametru
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
author: KrzysztofCwalina
ms.openlocfilehash: 5a0f6e0fab5d0f2fe8574e348fc6b8ae726eeb99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617210"
---
# <a name="parameter-design"></a><span data-ttu-id="366c3-102">Návrh parametru</span><span class="sxs-lookup"><span data-stu-id="366c3-102">Parameter Design</span></span>
<span data-ttu-id="366c3-103">Tato část obsahuje pokyny pro široké parametr návrh, včetně oddíly s pokyny pro kontrolu argumenty.</span><span class="sxs-lookup"><span data-stu-id="366c3-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="366c3-104">Kromě toho by měla odkazovat na pokynů popsaných v [Naming Parameters](../../../docs/standard/design-guidelines/naming-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="366c3-104">In addition, you should refer to the guidelines described in [Naming Parameters](../../../docs/standard/design-guidelines/naming-parameters.md).</span></span>  
  
 <span data-ttu-id="366c3-105">**✓ DO** používat alespoň odvozený typ parametru, který poskytuje funkci vyžadovanou člena.</span><span class="sxs-lookup"><span data-stu-id="366c3-105">**✓ DO** use the least derived parameter type that provides the functionality required by the member.</span></span>  
  
 <span data-ttu-id="366c3-106">Předpokládejme například, že chcete navrhnout metodu, která vytvoří výčet kolekce a vypíše do konzoly pro každou položku.</span><span class="sxs-lookup"><span data-stu-id="366c3-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="366c3-107">Tato metoda by měla přijímat <xref:System.Collections.IEnumerable> jako parametr, ne <xref:System.Collections.ArrayList> nebo <xref:System.Collections.IList>, např.</span><span class="sxs-lookup"><span data-stu-id="366c3-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>  
  
 <span data-ttu-id="366c3-108">**X DO NOT** používat vyhrazené parametry.</span><span class="sxs-lookup"><span data-stu-id="366c3-108">**X DO NOT** use reserved parameters.</span></span>  
  
 <span data-ttu-id="366c3-109">Pokud v některé budoucí verzi je potřeba další vstup pro člena, je možné přidat nové přetížení.</span><span class="sxs-lookup"><span data-stu-id="366c3-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>  
  
 <span data-ttu-id="366c3-110">**X DO NOT** mít veřejně vystaven metod, které berou ukazatele, pole ukazatele nebo vícerozměrná pole jako parametry.</span><span class="sxs-lookup"><span data-stu-id="366c3-110">**X DO NOT** have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>  
  
 <span data-ttu-id="366c3-111">Ukazatele a vícerozměrná pole jsou poměrně obtížné správně použít.</span><span class="sxs-lookup"><span data-stu-id="366c3-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="366c3-112">V téměř všech případech může být rozhraní API přepracovali tak, vyhnete se tak tyto typy jako parametry.</span><span class="sxs-lookup"><span data-stu-id="366c3-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>  
  
 <span data-ttu-id="366c3-113">**✓ DO** umístit všechny `out` všechny hodnoty ve-následující parametry a `ref` parametry (s výjimkou pole parametrů), i když je výsledkem nekonzistence v parametru řazení mezi přetížení (najdete v části [člena Přetížení](../../../docs/standard/design-guidelines/member-overloading.md)).</span><span class="sxs-lookup"><span data-stu-id="366c3-113">**✓ DO** place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](../../../docs/standard/design-guidelines/member-overloading.md)).</span></span>  
  
 <span data-ttu-id="366c3-114">`out` Parametrů se dají považovat za velmi návratové hodnoty, a jejich seskupováním usnadňuje podpis metody pochopit.</span><span class="sxs-lookup"><span data-stu-id="366c3-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>  
  
 <span data-ttu-id="366c3-115">**✓ DO** být konzistentní názvy parametrů při přepisování členy nebo implementace členů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="366c3-115">**✓ DO** be consistent in naming parameters when overriding members or implementing interface members.</span></span>  
  
 <span data-ttu-id="366c3-116">Komunikuje se to lépe vztah mezi metodami.</span><span class="sxs-lookup"><span data-stu-id="366c3-116">This better communicates the relationship between the methods.</span></span>  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="366c3-117">Volba mezi výčtu a logické parametry</span><span class="sxs-lookup"><span data-stu-id="366c3-117">Choosing Between Enum and Boolean Parameters</span></span>  
 <span data-ttu-id="366c3-118">**✓ DO** použijte výčty, pokud člen byste jinak museli dvě nebo více parametrů logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="366c3-118">**✓ DO** use enums if a member would otherwise have two or more Boolean parameters.</span></span>  
  
 <span data-ttu-id="366c3-119">**X DO NOT** používat logické hodnoty, pokud jste si naprosto jisti, nikdy bude potřeba více než dvě hodnoty.</span><span class="sxs-lookup"><span data-stu-id="366c3-119">**X DO NOT** use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>  
  
 <span data-ttu-id="366c3-120">Výčty získáte některé prostor pro budoucí součet hodnot, ale je třeba si uvědomit všechny rozbor aspektů přidání hodnot do výčty, které jsou popsány v [návrh výčtu](../../../docs/standard/design-guidelines/enum.md).</span><span class="sxs-lookup"><span data-stu-id="366c3-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](../../../docs/standard/design-guidelines/enum.md).</span></span>  
  
 <span data-ttu-id="366c3-121">**✓ CONSIDER** pomocí logických výrazů pro konstruktor parametry, které jsou hodnoty skutečně dvou stavů a jednoduše slouží k inicializaci logická hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="366c3-121">**✓ CONSIDER** using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>  
  
### <a name="validating-arguments"></a><span data-ttu-id="366c3-122">Validaci argumentů</span><span class="sxs-lookup"><span data-stu-id="366c3-122">Validating Arguments</span></span>  
 <span data-ttu-id="366c3-123">**✓ DO** ověřte argumenty předaný veřejný, chráněný nebo – explicitně implementovaná členy.</span><span class="sxs-lookup"><span data-stu-id="366c3-123">**✓ DO** validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="366c3-124">Vyvolat <xref:System.ArgumentException?displayProperty=nameWithType>, nebo jeden z jejích podtříd, pokud se ověření nezdaří.</span><span class="sxs-lookup"><span data-stu-id="366c3-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>  
  
 <span data-ttu-id="366c3-125">Všimněte si, že skutečné ověřování nemusí nutně dojde v veřejný nebo chráněný člen samotný.</span><span class="sxs-lookup"><span data-stu-id="366c3-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="366c3-126">K tomu mohlo dojít na nižší úrovni v rutině některé soukromé nebo interní.</span><span class="sxs-lookup"><span data-stu-id="366c3-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="366c3-127">Nejdůležitější je, že celý plochy, která je vystavena koncovým uživatelům kontroluje argumenty.</span><span class="sxs-lookup"><span data-stu-id="366c3-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>  
  
 <span data-ttu-id="366c3-128">**✓ DO** throw <xref:System.ArgumentNullException> Pokud je předán prázdný argument a člen nepodporuje argumenty null.</span><span class="sxs-lookup"><span data-stu-id="366c3-128">**✓ DO** throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>  
  
 <span data-ttu-id="366c3-129">**✓ DO** ověření výčtu parametry.</span><span class="sxs-lookup"><span data-stu-id="366c3-129">**✓ DO** validate enum parameters.</span></span>  
  
 <span data-ttu-id="366c3-130">Nepředpokládejte, že argumenty výčtu bude v rozsahu definovaném touto výčtového typu.</span><span class="sxs-lookup"><span data-stu-id="366c3-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="366c3-131">Modul CLR umožňuje i v případě, že hodnota není definována ve výčtovém typu přetypování hodnotu celého čísla na hodnoty výčtu.</span><span class="sxs-lookup"><span data-stu-id="366c3-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>  
  
 <span data-ttu-id="366c3-132">**X DO NOT** použít <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> rozsahu výčtu kontrol.</span><span class="sxs-lookup"><span data-stu-id="366c3-132">**X DO NOT** use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>  
  
 <span data-ttu-id="366c3-133">**✓ DO** mějte na paměti, že měnitelný argumenty byl změněn. po jejich byly ověřeny.</span><span class="sxs-lookup"><span data-stu-id="366c3-133">**✓ DO** be aware that mutable arguments might have changed after they were validated.</span></span>  
  
 <span data-ttu-id="366c3-134">Pokud je člen citlivé z hlediska zabezpečení, jsou ukončena. doporučujeme vytvořit kopii a pak ověření a zpracování argument.</span><span class="sxs-lookup"><span data-stu-id="366c3-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>  
  
### <a name="parameter-passing"></a><span data-ttu-id="366c3-135">Předávání parametrů</span><span class="sxs-lookup"><span data-stu-id="366c3-135">Parameter Passing</span></span>  
 <span data-ttu-id="366c3-136">Z perspektivy návrháře rozhraní framework, jsou tři hlavní skupiny parametry: parametry, podle hodnoty `ref` parametry, a `out` parametry.</span><span class="sxs-lookup"><span data-stu-id="366c3-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>  
  
 <span data-ttu-id="366c3-137">Pokud argument je předat prostřednictvím parametru-hodnota, člen obdrží kopii je skutečný argument předaný v.</span><span class="sxs-lookup"><span data-stu-id="366c3-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="366c3-138">Pokud je argumentem Typ hodnoty, kopie argumentu je vložen do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="366c3-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="366c3-139">Pokud je argumentem Typ odkazu, zkopírovat odkaz přejde do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="366c3-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="366c3-140">Nejoblíbenější jazyky CLR, jako je C#, VB.NET a C++, výchozí k předání parametrů podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="366c3-140">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>  
  
 <span data-ttu-id="366c3-141">Pokud argument se předává `ref` parametru, členu přijímá odkaz na skutečný argument předaný.</span><span class="sxs-lookup"><span data-stu-id="366c3-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="366c3-142">Pokud je argumentem Typ hodnoty, odkaz na argument je vložen do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="366c3-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="366c3-143">Pokud je argumentem Typ odkazu, odkaz na odkaz je vložen do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="366c3-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="366c3-144">`Ref` Parametry lze povolit členu, který chcete upravit argumenty předaná volající funkcí.</span><span class="sxs-lookup"><span data-stu-id="366c3-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>  
  
 <span data-ttu-id="366c3-145">`Out` parametry jsou podobné `ref` parametry s několik malých rozdílů.</span><span class="sxs-lookup"><span data-stu-id="366c3-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="366c3-146">Parametr je zpočátku považován za nepřiřazené a nelze jej načíst v těle členské předtím, než je přiřazen některá z hodnot.</span><span class="sxs-lookup"><span data-stu-id="366c3-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="366c3-147">Parametr má také přiřadit některá z hodnot před vrácením člena.</span><span class="sxs-lookup"><span data-stu-id="366c3-147">Also, the parameter has to be assigned some value before the member returns.</span></span>  
  
 <span data-ttu-id="366c3-148">**X AVOID** pomocí `out` nebo `ref` parametry.</span><span class="sxs-lookup"><span data-stu-id="366c3-148">**X AVOID** using `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="366c3-149">Pomocí `out` nebo `ref` parametry vyžaduje zkušenosti s ukazateli, pochopení, jak se liší typy hodnot a odkazové typy a metody s více návratových zpracování.</span><span class="sxs-lookup"><span data-stu-id="366c3-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="366c3-150">Také rozdíl mezi `out` a `ref` parametrů není běžně chápán.</span><span class="sxs-lookup"><span data-stu-id="366c3-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="366c3-151">Architekti Framework návrhu pro širokou veřejnost, by neměli očekávat uživatelům pracovat s `out` nebo `ref` parametry.</span><span class="sxs-lookup"><span data-stu-id="366c3-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="366c3-152">**X DO NOT** předat odkazové typy odkazem.</span><span class="sxs-lookup"><span data-stu-id="366c3-152">**X DO NOT** pass reference types by reference.</span></span>  
  
 <span data-ttu-id="366c3-153">Existují některé mohou nastat výjimky z pravidla, jako je například metodu, která je možné přepínat odkazy.</span><span class="sxs-lookup"><span data-stu-id="366c3-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>  
  
### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="366c3-154">Členy s proměnný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="366c3-154">Members with Variable Number of Parameters</span></span>  
 <span data-ttu-id="366c3-155">Tím, že poskytuje jako parametr pole jsou vyjádřeny členy, které můžete provést proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="366c3-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="366c3-156">Například <xref:System.String> poskytuje následující metody:</span><span class="sxs-lookup"><span data-stu-id="366c3-156">For example, <xref:System.String> provides the following method:</span></span>  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 <span data-ttu-id="366c3-157">Uživatel potom může volat <xref:System.String.Format%2A?displayProperty=nameWithType> metodu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="366c3-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 <span data-ttu-id="366c3-158">Přidání C# klíčového slova params na parametr pole parametru se změní na pole parametr params takzvané a poskytuje zástupce vytvořit dočasné pole.</span><span class="sxs-lookup"><span data-stu-id="366c3-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 <span data-ttu-id="366c3-159">To umožňuje uživateli volat metodu předáním prvky pole přímo v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="366c3-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 <span data-ttu-id="366c3-160">Všimněte si, že klíčové slovo params lze přidat pouze pro poslední parametr v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="366c3-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="366c3-161">**✓ CONSIDER** přidávání params – klíčové slovo do pole parametry, pokud očekáváte, koncovým uživatelům předat pole s malý počet elementů.</span><span class="sxs-lookup"><span data-stu-id="366c3-161">**✓ CONSIDER** adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="366c3-162">Pokud se očekává, že velký počet prvků se předají v běžných scénářů, uživatelé budou pravděpodobně není předejte tyto prvky vložené přesto a tak klíčové slovo params není nutné.</span><span class="sxs-lookup"><span data-stu-id="366c3-162">If it’s expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>  
  
 <span data-ttu-id="366c3-163">**X AVOID** pomocí parametry pole, pokud má volající by téměř vždy již vstupu v matici.</span><span class="sxs-lookup"><span data-stu-id="366c3-163">**X AVOID** using params arrays if the caller would almost always have the input already in an array.</span></span>  
  
 <span data-ttu-id="366c3-164">Například členové s parametry pole bajtů by téměř nikdy volat předáním jednotlivých bajtech.</span><span class="sxs-lookup"><span data-stu-id="366c3-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="366c3-165">Z tohoto důvodu nepoužívejte parametry pole bajtů v rozhraní .NET Framework – klíčové slovo params.</span><span class="sxs-lookup"><span data-stu-id="366c3-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>  
  
 <span data-ttu-id="366c3-166">**X DO NOT** použijte parametry pole, pokud je pole upraveném člen trvá parametr pole parametry.</span><span class="sxs-lookup"><span data-stu-id="366c3-166">**X DO NOT** use params arrays if the array is modified by the member taking the params array parameter.</span></span>  
  
 <span data-ttu-id="366c3-167">Z důvodu skutečnost, že mnoho kompilátorů zapnout argumenty, které mají člena do přechodného pole na lokalitu volání pole může být dočasný objekt, a proto budou ztraceny všechny změny do pole.</span><span class="sxs-lookup"><span data-stu-id="366c3-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>  
  
 <span data-ttu-id="366c3-168">**✓ CONSIDER** pomocí klíčového slova parametry v jednoduchých přetížení, i když ho nelze použít na složitější přetížení.</span><span class="sxs-lookup"><span data-stu-id="366c3-168">**✓ CONSIDER** using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>  
  
 <span data-ttu-id="366c3-169">Položte si otázku: Pokud uživatelé by hodnota pole parametry s jedním přetížením i v případě, že nebyl ve všech přetížení.</span><span class="sxs-lookup"><span data-stu-id="366c3-169">Ask yourself if users would value having the params array in one overload even if it wasn’t in all overloads.</span></span>  
  
 <span data-ttu-id="366c3-170">**✓ DO** zkuste pořadí parametrů, aby bylo možné použít params – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="366c3-170">**✓ DO** try to order parameters to make it possible to use the params keyword.</span></span>  
  
 <span data-ttu-id="366c3-171">**✓ CONSIDER** poskytnutí speciální přetížení a cesty kódu pro volání s malým počtem argumentů rozhraní API velmi náročné na výkon.</span><span class="sxs-lookup"><span data-stu-id="366c3-171">**✓ CONSIDER** providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="366c3-172">Díky tomu je možné se vyhnout, vytvářet objekty array, při volání rozhraní API s malý počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="366c3-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="366c3-173">Názvy parametrů formuláře singulární podobě parametr pole a přidáním číselnou příponou.</span><span class="sxs-lookup"><span data-stu-id="366c3-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>  
  
 <span data-ttu-id="366c3-174">Byste měli jenom udělat Pokud budete pro zvláštní případy cesta celý kód, ne jenom vytvořit pole a volání obecné metody.</span><span class="sxs-lookup"><span data-stu-id="366c3-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>  
  
 <span data-ttu-id="366c3-175">**✓ DO** Uvědomte si, že null by prošel jako argument parametry pole.</span><span class="sxs-lookup"><span data-stu-id="366c3-175">**✓ DO** be aware that null could be passed as a params array argument.</span></span>  
  
 <span data-ttu-id="366c3-176">Měli byste ověřit, že pole není null před zpracováním.</span><span class="sxs-lookup"><span data-stu-id="366c3-176">You should validate that the array is not null before processing.</span></span>  
  
 <span data-ttu-id="366c3-177">**X DO NOT** použít `varargs` metody, které jsou známé jako se třemi tečkami.</span><span class="sxs-lookup"><span data-stu-id="366c3-177">**X DO NOT** use the `varargs` methods, otherwise known as the ellipsis.</span></span>  
  
 <span data-ttu-id="366c3-178">Některé jazyky CLR, například C++, podporují alternativní konvence pro předávání seznamy parametrů proměnných volá `varargs` metody.</span><span class="sxs-lookup"><span data-stu-id="366c3-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="366c3-179">Tato konvence by neměl v rozhraní, použít, protože není kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="366c3-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>  
  
### <a name="pointer-parameters"></a><span data-ttu-id="366c3-180">Parametry ukazatele</span><span class="sxs-lookup"><span data-stu-id="366c3-180">Pointer Parameters</span></span>  
 <span data-ttu-id="366c3-181">Obecně platí ukazatele by se neměl zobrazit ve veřejnou oblast Framework dobře navržené spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="366c3-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="366c3-182">Ve většině případů, by měl být zapouzdřen ukazatele.</span><span class="sxs-lookup"><span data-stu-id="366c3-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="366c3-183">Ale v některých případech jsou požadovány pro interoperabilitu důvodů ukazatele a pomocí ukazatelů v takových případech je vhodné.</span><span class="sxs-lookup"><span data-stu-id="366c3-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>  
  
 <span data-ttu-id="366c3-184">**✓ DO** alternativu přinášejí kteréhokoli člena, který se použije argument ukazatele, protože ukazatele nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="366c3-184">**✓ DO** provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>  
  
 <span data-ttu-id="366c3-185">**X AVOID** provádění nákladné argument kontrola ukazatel argumentů.</span><span class="sxs-lookup"><span data-stu-id="366c3-185">**X AVOID** doing expensive argument checking of pointer arguments.</span></span>  
  
 <span data-ttu-id="366c3-186">**✓ DO** použijte běžné konvence související ukazatele při návrhu členy s ukazatele.</span><span class="sxs-lookup"><span data-stu-id="366c3-186">**✓ DO** follow common pointer-related conventions when designing members with pointers.</span></span>  
  
 <span data-ttu-id="366c3-187">Například není nutné předat počáteční index, protože jednoduché aritmetika ukazatele lze použít k dosažení stejného výsledku.</span><span class="sxs-lookup"><span data-stu-id="366c3-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>  
  
 <span data-ttu-id="366c3-188">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="366c3-188">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="366c3-189">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="366c3-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="366c3-190">Viz také:</span><span class="sxs-lookup"><span data-stu-id="366c3-190">See also</span></span>

- [<span data-ttu-id="366c3-191">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="366c3-191">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="366c3-192">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="366c3-192">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
