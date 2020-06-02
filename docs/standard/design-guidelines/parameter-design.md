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
ms.openlocfilehash: 46c1b8f03d054a63ea837a73fd30eeed163ab0a4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290094"
---
# <a name="parameter-design"></a><span data-ttu-id="6531b-102">Návrh parametru</span><span class="sxs-lookup"><span data-stu-id="6531b-102">Parameter design</span></span>

<span data-ttu-id="6531b-103">Tato část obsahuje obecné pokyny pro návrh parametrů, včetně oddílů s pokyny pro kontrolu argumentů.</span><span class="sxs-lookup"><span data-stu-id="6531b-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="6531b-104">Kromě toho byste měli postupovat podle pokynů popsaných v tématu [parametry pojmenování](naming-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6531b-104">In addition, you should refer to the guidelines described in [Naming Parameters](naming-parameters.md).</span></span>

 <span data-ttu-id="6531b-105">✔️ použít nejmenší odvozený typ parametru, který poskytuje funkce vyžadované členem.</span><span class="sxs-lookup"><span data-stu-id="6531b-105">✔️ DO use the least derived parameter type that provides the functionality required by the member.</span></span>

 <span data-ttu-id="6531b-106">Předpokládejme například, že chcete navrhnout metodu, která vytvoří výčet kolekce a vytiskne každou položku do konzoly.</span><span class="sxs-lookup"><span data-stu-id="6531b-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="6531b-107">Taková metoda by měla být provedena <xref:System.Collections.IEnumerable> jako parametr, nikoli <xref:System.Collections.ArrayList> nebo <xref:System.Collections.IList> , například.</span><span class="sxs-lookup"><span data-stu-id="6531b-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>

 <span data-ttu-id="6531b-108">❌Nepoužívejte rezervované parametry.</span><span class="sxs-lookup"><span data-stu-id="6531b-108">❌ DO NOT use reserved parameters.</span></span>

 <span data-ttu-id="6531b-109">Pokud je v některé budoucí verzi potřeba více vstupů ke členu, může být přidáno nové přetížení.</span><span class="sxs-lookup"><span data-stu-id="6531b-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>

 <span data-ttu-id="6531b-110">❌Nemají veřejně vystavené metody, které přebírají ukazatele, pole ukazatelů nebo multidimenzionální pole jako parametry.</span><span class="sxs-lookup"><span data-stu-id="6531b-110">❌ DO NOT have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>

 <span data-ttu-id="6531b-111">Ukazatele a multidimenzionální pole jsou poměrně obtížné použít.</span><span class="sxs-lookup"><span data-stu-id="6531b-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="6531b-112">Ve většině případů je možné rozhraní API přenavrhovat, aby se předešlo přebírání těchto typů jako parametrů.</span><span class="sxs-lookup"><span data-stu-id="6531b-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>

 <span data-ttu-id="6531b-113">✔️ umístit všechny `out` parametry za všechny parametry podle hodnoty a `ref` parametrů (kromě polí parametrů), a to i v případě, že výsledkem je nekonzistence v pořadí parametrů mezi přetíženími (viz téma [přetížení člena](member-overloading.md)).</span><span class="sxs-lookup"><span data-stu-id="6531b-113">✔️ DO place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](member-overloading.md)).</span></span>

 <span data-ttu-id="6531b-114">`out`Parametry lze zobrazit jako nadbytečné návratové hodnoty a jejich seskupení usnadňuje pochopení signatury metody.</span><span class="sxs-lookup"><span data-stu-id="6531b-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>

 <span data-ttu-id="6531b-115">✔️ být v parametrech pojmenování konzistentní při přepisování členů nebo implementaci členů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6531b-115">✔️ DO be consistent in naming parameters when overriding members or implementing interface members.</span></span>

 <span data-ttu-id="6531b-116">Tím se lépe komunikuje vztah mezi metodami.</span><span class="sxs-lookup"><span data-stu-id="6531b-116">This better communicates the relationship between the methods.</span></span>

### <a name="choose-between-enum-and-boolean-parameters"></a><span data-ttu-id="6531b-117">Zvolit mezi výčtovým a logickým parametrem</span><span class="sxs-lookup"><span data-stu-id="6531b-117">Choose between enum and boolean parameters</span></span>
 <span data-ttu-id="6531b-118">✔️ použít výčty, pokud by měl člen jinak mít dva nebo více logických parametrů.</span><span class="sxs-lookup"><span data-stu-id="6531b-118">✔️ DO use enums if a member would otherwise have two or more Boolean parameters.</span></span>

 <span data-ttu-id="6531b-119">❌Nepoužívejte logické hodnoty, pokud nebudete naprosto jisti, že nikdy nebude potřeba více než dvě hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6531b-119">❌ DO NOT use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>

 <span data-ttu-id="6531b-120">Výčty umožňují určit místo pro budoucí sčítání hodnot, ale měli byste si uvědomit o všech důsledcích přidávání hodnot do výčtů, které jsou popsány v [návrhu výčtu](enum.md).</span><span class="sxs-lookup"><span data-stu-id="6531b-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](enum.md).</span></span>

 <span data-ttu-id="6531b-121">✔️ Zvažte použití logických hodnot pro parametry konstruktoru, které jsou skutečné hodnoty dvou stavů a slouží pouze k inicializaci logických vlastností.</span><span class="sxs-lookup"><span data-stu-id="6531b-121">✔️ CONSIDER using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>

### <a name="validate-arguments"></a><span data-ttu-id="6531b-122">Ověřit argumenty</span><span class="sxs-lookup"><span data-stu-id="6531b-122">Validate arguments</span></span>
 <span data-ttu-id="6531b-123">✔️ PROVÉST ověření argumentů předaných veřejným, chráněným nebo explicitně implementovaným členům.</span><span class="sxs-lookup"><span data-stu-id="6531b-123">✔️ DO validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="6531b-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType> nebo jedna z jejích podtříd, pokud se ověřování nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="6531b-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>

 <span data-ttu-id="6531b-125">Všimněte si, že skutečné ověření nemusí nutně probíhat ve veřejném nebo chráněném členu.</span><span class="sxs-lookup"><span data-stu-id="6531b-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="6531b-126">Může dojít na nižší úrovni v některé soukromé nebo interní rutině.</span><span class="sxs-lookup"><span data-stu-id="6531b-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="6531b-127">Hlavním bodem je, že celá oblast Surface, která je vystavena koncovým uživatelům, kontroluje argumenty.</span><span class="sxs-lookup"><span data-stu-id="6531b-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>

 <span data-ttu-id="6531b-128">✔️ Vyvolejte <xref:System.ArgumentNullException> , pokud je předán argument null a člen nepodporuje argumenty null.</span><span class="sxs-lookup"><span data-stu-id="6531b-128">✔️ DO throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>

 <span data-ttu-id="6531b-129">✔️ PROVÉST ověření parametrů výčtu.</span><span class="sxs-lookup"><span data-stu-id="6531b-129">✔️ DO validate enum parameters.</span></span>

 <span data-ttu-id="6531b-130">Nepředpokládat argumenty výčtu budou v rozsahu definovaném výčtem.</span><span class="sxs-lookup"><span data-stu-id="6531b-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="6531b-131">Modul CLR umožňuje přetypování libovolné celočíselné hodnoty do hodnoty Enum i v případě, že ve výčtu není definována hodnota.</span><span class="sxs-lookup"><span data-stu-id="6531b-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>

 <span data-ttu-id="6531b-132">❌Nepoužívejte <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> pro kontroly rozsahu výčtu.</span><span class="sxs-lookup"><span data-stu-id="6531b-132">❌ DO NOT use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>

 <span data-ttu-id="6531b-133">✔️ Upozorňujeme, že po ověření se mohly změnit proměnlivé argumenty.</span><span class="sxs-lookup"><span data-stu-id="6531b-133">✔️ DO be aware that mutable arguments might have changed after they were validated.</span></span>

 <span data-ttu-id="6531b-134">Pokud je člen citlivý na zabezpečení, doporučujeme vytvořit kopii a pak ověřit a zpracovat argument.</span><span class="sxs-lookup"><span data-stu-id="6531b-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>

### <a name="pass-parameters"></a><span data-ttu-id="6531b-135">Parametry předání</span><span class="sxs-lookup"><span data-stu-id="6531b-135">Pass parameters</span></span>
 <span data-ttu-id="6531b-136">Z perspektivy návrháře architektury existují tři hlavní skupiny parametrů: parametry podle hodnoty, `ref` parametry a `out` parametry.</span><span class="sxs-lookup"><span data-stu-id="6531b-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>

 <span data-ttu-id="6531b-137">Pokud je předán argument pomocí parametru podle hodnoty, člen obdrží kopii skutečného předaného argumentu.</span><span class="sxs-lookup"><span data-stu-id="6531b-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="6531b-138">Pokud je argumentem hodnotový typ, je kopie argumentu vložena do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6531b-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="6531b-139">Pokud je argumentem odkazový typ, kopie odkazu je vložena do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6531b-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="6531b-140">Nejoblíbenější jazyky CLR, jako je C#, Visual Basic a C++, jsou ve výchozím nastavení předány parametrům podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6531b-140">Most popular CLR languages, such as C#, Visual Basic, and C++, default to passing parameters by value.</span></span>

 <span data-ttu-id="6531b-141">Když je argument předán pomocí `ref` parametru, člen obdrží odkaz na vlastní předaný argument.</span><span class="sxs-lookup"><span data-stu-id="6531b-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="6531b-142">Pokud je argumentem hodnotový typ, odkaz na argument je vložen do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6531b-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="6531b-143">Pokud je argumentem odkazový typ, odkaz na odkaz je vložen do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6531b-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="6531b-144">`Ref`parametry lze použít k umožnění člena upravovat argumenty předané volajícím.</span><span class="sxs-lookup"><span data-stu-id="6531b-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>

 <span data-ttu-id="6531b-145">`Out`parametry jsou podobné `ref` parametrům s malým rozdílem.</span><span class="sxs-lookup"><span data-stu-id="6531b-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="6531b-146">Parametr je zpočátku považován za nepřiřazený a nemůže být načten v těle členu před tím, než se mu přiřadí nějaká hodnota.</span><span class="sxs-lookup"><span data-stu-id="6531b-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="6531b-147">Parametr musí být také přiřazen určitou hodnotu před tím, než se člen vrátí.</span><span class="sxs-lookup"><span data-stu-id="6531b-147">Also, the parameter has to be assigned some value before the member returns.</span></span>

 <span data-ttu-id="6531b-148">❌Vyhněte se použití `out` `ref` parametrů nebo.</span><span class="sxs-lookup"><span data-stu-id="6531b-148">❌ AVOID using `out` or `ref` parameters.</span></span>

 <span data-ttu-id="6531b-149">Použití `out` `ref` parametrů or vyžaduje zkušenosti s ukazateli, porozumění způsobu, jakým se liší typy hodnot a typy odkazů, a metody zpracování s více návratových hodnot.</span><span class="sxs-lookup"><span data-stu-id="6531b-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="6531b-150">Také rozdíl mezi `out` parametry a není `ref` široce srozumitelný.</span><span class="sxs-lookup"><span data-stu-id="6531b-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="6531b-151">Architektura architekt návrhu pro obecnou cílovou skupinu by neměla očekávat, že uživatelé budou hlavní pracovat s `out` `ref` parametry nebo.</span><span class="sxs-lookup"><span data-stu-id="6531b-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>

 <span data-ttu-id="6531b-152">❌Nepředávejte odkazový typ odkazem.</span><span class="sxs-lookup"><span data-stu-id="6531b-152">❌ DO NOT pass reference types by reference.</span></span>

 <span data-ttu-id="6531b-153">Na pravidlo existují omezené výjimky, jako je například metoda, kterou lze použít k prohození odkazů.</span><span class="sxs-lookup"><span data-stu-id="6531b-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>

### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="6531b-154">Členové s proměnným počtem parametrů</span><span class="sxs-lookup"><span data-stu-id="6531b-154">Members with variable number of parameters</span></span>
 <span data-ttu-id="6531b-155">Členy, kteří mohou převzít proměnný počet argumentů, jsou vyjádřeny zadáním parametru Array.</span><span class="sxs-lookup"><span data-stu-id="6531b-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="6531b-156">Například <xref:System.String> poskytuje následující metodu:</span><span class="sxs-lookup"><span data-stu-id="6531b-156">For example, <xref:System.String> provides the following method:</span></span>

```csharp
public class String {
    public static string Format(string format, object[] parameters);
}
```

 <span data-ttu-id="6531b-157">Uživatel pak může zavolat <xref:System.String.Format%2A?displayProperty=nameWithType> metodu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="6531b-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>

 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`

 <span data-ttu-id="6531b-158">Přidáním klíčového slova param parametrů jazyka C# do parametru pole se změní parametr na parametr pole param, který se nazývá, a poskytuje zástupce pro vytvoření dočasného pole.</span><span class="sxs-lookup"><span data-stu-id="6531b-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>

```csharp
public class String {
    public static string Format(string format, params object[] parameters);
}
```

 <span data-ttu-id="6531b-159">Díky tomu může uživatel volat metodu předáním prvků pole přímo v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="6531b-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>

 `String.Format("File {0} not found in {1}",filename,directory);`

 <span data-ttu-id="6531b-160">Všimněte si, že klíčové slovo params lze přidat pouze k poslednímu parametru v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="6531b-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>

 <span data-ttu-id="6531b-161">✔️ Zvažte přidání klíčového slova params do parametrů pole, pokud očekáváte, že koncoví uživatelé budou předávat pole s malým počtem prvků.</span><span class="sxs-lookup"><span data-stu-id="6531b-161">✔️ CONSIDER adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="6531b-162">Pokud se očekává, že se v běžných scénářích budou předávat i celá řada prvků, uživatelé pravděpodobně nebudou tyto prvky vložit do seznamu, takže klíčové slovo params není nutné.</span><span class="sxs-lookup"><span data-stu-id="6531b-162">If it’s expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>

 <span data-ttu-id="6531b-163">❌Vyhněte se použití polí param, pokud by volající téměř vždy měl vstup v poli.</span><span class="sxs-lookup"><span data-stu-id="6531b-163">❌ AVOID using params arrays if the caller would almost always have the input already in an array.</span></span>

 <span data-ttu-id="6531b-164">Například členy s parametry bajtového pole by se téměř nikdy nevolaly předáním jednotlivých bajtů.</span><span class="sxs-lookup"><span data-stu-id="6531b-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="6531b-165">Z tohoto důvodu parametry bajtového pole v .NET Framework nepoužívají klíčové slovo params.</span><span class="sxs-lookup"><span data-stu-id="6531b-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>

 <span data-ttu-id="6531b-166">❌Nepoužívejte pole param, pokud je pole upraveno členem, který přebírá parametr pole params.</span><span class="sxs-lookup"><span data-stu-id="6531b-166">❌ DO NOT use params arrays if the array is modified by the member taking the params array parameter.</span></span>

 <span data-ttu-id="6531b-167">Vzhledem k tomu, že mnoho kompilátorů přepíná argumenty člena do dočasného pole na webu volání, pole může být dočasným objektem, a proto dojde ke ztrátě všech změn v poli.</span><span class="sxs-lookup"><span data-stu-id="6531b-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>

 <span data-ttu-id="6531b-168">✔️ Zvažte použití klíčového slova params v jednoduchém přetížení, a to i v případě, že se složitější přetížení nemůže použít.</span><span class="sxs-lookup"><span data-stu-id="6531b-168">✔️ CONSIDER using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>

 <span data-ttu-id="6531b-169">Zeptejte se sami, pokud by uživatelé měli hodnotu pole params v jednom přetížení, i když to nebylo ve všech přetíženích.</span><span class="sxs-lookup"><span data-stu-id="6531b-169">Ask yourself if users would value having the params array in one overload even if it wasn’t in all overloads.</span></span>

 <span data-ttu-id="6531b-170">✔️ se pokusíte seřadit parametry, aby bylo možné použít klíčové slovo params.</span><span class="sxs-lookup"><span data-stu-id="6531b-170">✔️ DO try to order parameters to make it possible to use the params keyword.</span></span>

 <span data-ttu-id="6531b-171">✔️ Zvažte poskytnutí speciálních přetížení a cest kódu pro volání s malým počtem argumentů v rozhraních API s extrémně citlivými na výkon.</span><span class="sxs-lookup"><span data-stu-id="6531b-171">✔️ CONSIDER providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>

 <span data-ttu-id="6531b-172">Díky tomu je možné vyhnout se vytváření objektů pole při volání rozhraní API s malým počtem argumentů.</span><span class="sxs-lookup"><span data-stu-id="6531b-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="6531b-173">Vytvořte názvy parametrů tak, že převezmete jednotný tvar parametru Array a přidáte číselnou příponu.</span><span class="sxs-lookup"><span data-stu-id="6531b-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>

 <span data-ttu-id="6531b-174">Tuto věc byste měli provést pouze v případě, že se chystáte o zvláštní cestu k celému kódu, ne pouze vytvořit pole a volat obecnější metodu.</span><span class="sxs-lookup"><span data-stu-id="6531b-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>

 <span data-ttu-id="6531b-175">✔️ Upozorňujeme, že hodnota null by mohla být předána jako argument pole param.</span><span class="sxs-lookup"><span data-stu-id="6531b-175">✔️ DO be aware that null could be passed as a params array argument.</span></span>

 <span data-ttu-id="6531b-176">Před zpracováním byste měli ověřit, že pole není null.</span><span class="sxs-lookup"><span data-stu-id="6531b-176">You should validate that the array is not null before processing.</span></span>

 <span data-ttu-id="6531b-177">❌Nepoužívejte `varargs` metody, jinak označované jako tři tečky.</span><span class="sxs-lookup"><span data-stu-id="6531b-177">❌ DO NOT use the `varargs` methods, otherwise known as the ellipsis.</span></span>

 <span data-ttu-id="6531b-178">Některé jazyky CLR, jako je například C++, podporují alternativní konvenci pro předávání seznamů parametrů proměnných nazývaných `varargs` metody.</span><span class="sxs-lookup"><span data-stu-id="6531b-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="6531b-179">Konvence by se neměla používat v rozhraních, protože není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="6531b-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>

### <a name="pointer-parameters"></a><span data-ttu-id="6531b-180">Parametry ukazatele</span><span class="sxs-lookup"><span data-stu-id="6531b-180">Pointer parameters</span></span>
 <span data-ttu-id="6531b-181">Obecně platí, že by ukazatelé neměl být uveden v oblasti veřejného povrchu dobře navržené architektury spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6531b-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="6531b-182">Ve většině případů by měly být ukazatele zapouzdřeny.</span><span class="sxs-lookup"><span data-stu-id="6531b-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="6531b-183">V některých případech se ale vyžaduje, aby se v případě interoperability a používání ukazatelů v takových případech používaly příslušné ukazatele.</span><span class="sxs-lookup"><span data-stu-id="6531b-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>

 <span data-ttu-id="6531b-184">✔️ poskytují alternativu pro každého člena, který přebírá argument ukazatele, protože ukazatelé nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="6531b-184">✔️ DO provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>

 <span data-ttu-id="6531b-185">❌Vyhněte se provádění náročných kontrol argumentů ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="6531b-185">❌ AVOID doing expensive argument checking of pointer arguments.</span></span>

 <span data-ttu-id="6531b-186">✔️ se při navrhování členů s ukazateli řídit běžnými konvencemi souvisejícími s ukazateli.</span><span class="sxs-lookup"><span data-stu-id="6531b-186">✔️ DO follow common pointer-related conventions when designing members with pointers.</span></span>

 <span data-ttu-id="6531b-187">Například není nutné předávat počáteční index, protože k dosažení stejného výsledku lze použít jednoduchou aritmetickou akci s ukazatelem.</span><span class="sxs-lookup"><span data-stu-id="6531b-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>

 <span data-ttu-id="6531b-188">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="6531b-188">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="6531b-189">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="6531b-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="6531b-190">Viz také</span><span class="sxs-lookup"><span data-stu-id="6531b-190">See also</span></span>

- [<span data-ttu-id="6531b-191">Pokyny pro návrh členů</span><span class="sxs-lookup"><span data-stu-id="6531b-191">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="6531b-192">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="6531b-192">Framework Design Guidelines</span></span>](index.md)
