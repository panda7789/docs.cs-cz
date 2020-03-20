---
title: Psaní velkých a pohotově reagujících aplikací .NET Framework
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 57f65feff5260cb83df5354f5d7ee1bad0babb3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180585"
---
# <a name="writing-large-responsive-net-framework-apps"></a><span data-ttu-id="3c12d-102">Psaní velkých a pohotově reagujících aplikací .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3c12d-102">Writing Large, Responsive .NET Framework Apps</span></span>

<span data-ttu-id="3c12d-103">Tento článek obsahuje tipy pro zlepšení výkonu velkých aplikací rozhraní .NET Framework nebo aplikací, které zpracovávají velké množství dat, jako jsou soubory nebo databáze.</span><span class="sxs-lookup"><span data-stu-id="3c12d-103">This article provides tips for improving the performance of large .NET Framework apps, or apps that process a large amount of data such as files or databases.</span></span> <span data-ttu-id="3c12d-104">Tyto tipy pocházejí z přepisování kompilátorů jazyka C# a Visual Basic ve spravovaném kódu a tento článek obsahuje několik reálných příkladů z kompilátoru Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="3c12d-104">These tips come from rewriting the C# and Visual Basic compilers in managed code, and this article includes several real examples from the C# compiler.</span></span>
  
<span data-ttu-id="3c12d-105">Rozhraní .NET Framework je vysoce produktivní pro vytváření aplikací.</span><span class="sxs-lookup"><span data-stu-id="3c12d-105">The .NET Framework is highly productive for building apps.</span></span> <span data-ttu-id="3c12d-106">Díky výkonným a bezpečným jazykům a bohaté sbírce knihoven je vytváření aplikací velmi plodné.</span><span class="sxs-lookup"><span data-stu-id="3c12d-106">Powerful and safe languages and a rich collection of libraries make app building highly fruitful.</span></span> <span data-ttu-id="3c12d-107">Nicméně, s velkou produktivitou přichází odpovědnost.</span><span class="sxs-lookup"><span data-stu-id="3c12d-107">However, with great productivity comes responsibility.</span></span> <span data-ttu-id="3c12d-108">Měli byste použít všechny výkon rozhraní .NET Framework, ale být připraveni vyladit výkon kódu v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="3c12d-108">You should use all the power of the .NET Framework, but be prepared to tune your code’s performance when needed.</span></span>
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a><span data-ttu-id="3c12d-109">Proč se nový výkon kompilátoru vztahuje na vaši aplikaci</span><span class="sxs-lookup"><span data-stu-id="3c12d-109">Why the new compiler performance applies to your app</span></span>  
 <span data-ttu-id="3c12d-110">Tým .NET Compiler Platform ("Roslyn") přepsal kompilátory jazyka C# a Visual Basic ve spravovaném kódu, aby poskytoval nová rozhraní API pro modelování a analýzu kódu, vytváření nástrojů a povolení mnohem bohatších prostředí podporujících kód v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3c12d-110">The .NET Compiler Platform ("Roslyn") team rewrote the C# and Visual Basic compilers in managed code to provide new APIs for modeling and analyzing code, building tools, and enabling much richer, code-aware experiences in Visual Studio.</span></span> <span data-ttu-id="3c12d-111">Přepsání kompilátorů a vytváření prostředí sady Visual Studio na nových kompilátorech odhalilo užitečné přehledy výkonu, které jsou použitelné pro všechny velké aplikace rozhraní .NET Framework nebo pro jakoukoli aplikaci, která zpracovává velké množství dat.</span><span class="sxs-lookup"><span data-stu-id="3c12d-111">Rewriting the compilers and building Visual Studio experiences on the new compilers revealed useful performance insights that are applicable to any large .NET Framework app or any app that processes a lot of data.</span></span> <span data-ttu-id="3c12d-112">Nemusíte vědět o kompilátory využít přehledy a příklady z kompilátoru Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="3c12d-112">You don't need to know about compilers to take advantage of the insights and examples from the C# compiler.</span></span>
  
 <span data-ttu-id="3c12d-113">Visual Studio používá rozhraní API kompilátoru k vytvoření všech funkcí Technologie IntelliSense, které uživatelé milují, jako je vybarvení identifikátorů a klíčových slov, seznamy dokončení syntaxe, klikyháky pro chyby, tipy parametrů, problémy s kódem a akce kódu.</span><span class="sxs-lookup"><span data-stu-id="3c12d-113">Visual Studio uses the compiler APIs to build all the IntelliSense features that users love, such as colorization of identifiers and keywords, syntax completion lists, squiggles for errors, parameter tips, code issues, and code actions.</span></span> <span data-ttu-id="3c12d-114">Visual Studio poskytuje tuto nápovědu, zatímco vývojáři přidávají a mění svůj kód a Visual Studio musí zůstat responzivní, zatímco kompilátor neustále modeluje kód, který vývojáři upravují.</span><span class="sxs-lookup"><span data-stu-id="3c12d-114">Visual Studio provides this help while developers are typing and changing their code, and Visual Studio must remain responsive while the compiler continually models the code developers edit.</span></span>
  
 <span data-ttu-id="3c12d-115">Když vaši koncoví uživatelé interagují s vaší aplikací, očekávají, že bude reagovat.</span><span class="sxs-lookup"><span data-stu-id="3c12d-115">When your end users interact with your app, they expect it to be responsive.</span></span> <span data-ttu-id="3c12d-116">Psaní nebo zpracování příkazů by nikdy nemělo být blokováno.</span><span class="sxs-lookup"><span data-stu-id="3c12d-116">Typing or command handling should never be blocked.</span></span> <span data-ttu-id="3c12d-117">Nápověda by se měla rychle objevit nebo se vzdát, pokud uživatel pokračuje v psaní.</span><span class="sxs-lookup"><span data-stu-id="3c12d-117">Help should pop up quickly or give up if the user continues typing.</span></span> <span data-ttu-id="3c12d-118">Vaše aplikace by se měla vyhnout blokování vlákna uživatelského rozhraní s dlouhými výpočty, které dělají aplikaci pomalu.</span><span class="sxs-lookup"><span data-stu-id="3c12d-118">Your app should avoid blocking the UI thread with long computations that make the app feel sluggish.</span></span>
  
 <span data-ttu-id="3c12d-119">Další informace o kompilátorech Roslyn naleznete [v tématu .NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md).</span><span class="sxs-lookup"><span data-stu-id="3c12d-119">For more information about Roslyn compilers, see [The .NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md).</span></span>
  
## <a name="just-the-facts"></a><span data-ttu-id="3c12d-120">Jen fakta</span><span class="sxs-lookup"><span data-stu-id="3c12d-120">Just the Facts</span></span>  
 <span data-ttu-id="3c12d-121">Zvažte tato fakta při ladění výkonu a vytváření responzivních aplikací rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3c12d-121">Consider these facts when tuning performance and creating responsive .NET Framework apps.</span></span>
  
### <a name="fact-1-dont-prematurely-optimize"></a><span data-ttu-id="3c12d-122">Fakt 1: Neoptimalizujte předčasně</span><span class="sxs-lookup"><span data-stu-id="3c12d-122">Fact 1: Don’t prematurely optimize</span></span>  
 <span data-ttu-id="3c12d-123">Psaní kódu, který je složitější, než je třeba, které mají být vzniknou náklady na údržbu, ladění a leštění.</span><span class="sxs-lookup"><span data-stu-id="3c12d-123">Writing code that is more complex than it needs to be incurs maintenance, debugging, and polishing costs.</span></span> <span data-ttu-id="3c12d-124">Zkušení programátoři mají intuitivní přehled o tom, jak řešit problémy s kódováním a psát efektivnější kód.</span><span class="sxs-lookup"><span data-stu-id="3c12d-124">Experienced programmers have an intuitive grasp of how to solve coding problems and write more efficient code.</span></span> <span data-ttu-id="3c12d-125">Někdy však předčasně optimalizují svůj kód.</span><span class="sxs-lookup"><span data-stu-id="3c12d-125">However, they sometimes prematurely optimize their code.</span></span> <span data-ttu-id="3c12d-126">Používají například tabulku hash, když by stačilo jednoduché pole, nebo používají složité ukládání do mezipaměti, které může unikat paměť namísto pouhého opětovného výpočtu hodnot.</span><span class="sxs-lookup"><span data-stu-id="3c12d-126">For example, they use a hash table when a simple array would suffice, or use complicated caching that may leak memory instead of simply recomputing values.</span></span> <span data-ttu-id="3c12d-127">I když jste programátor zkušeností, měli byste otestovat výkon a analyzovat kód, když zjistíte problémy.</span><span class="sxs-lookup"><span data-stu-id="3c12d-127">Even if you’re an experience programmer, you should test for performance and analyze your code when you find issues.</span></span>
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a><span data-ttu-id="3c12d-128">Fakt 2: Pokud neměříte, hádáte</span><span class="sxs-lookup"><span data-stu-id="3c12d-128">Fact 2: If you’re not measuring, you’re guessing</span></span>  
 <span data-ttu-id="3c12d-129">Profily a měření nelžou.</span><span class="sxs-lookup"><span data-stu-id="3c12d-129">Profiles and measurements don’t lie.</span></span> <span data-ttu-id="3c12d-130">Profily ukazují, zda je procesor plně načten nebo zda jste blokováni vstupně-diskem.</span><span class="sxs-lookup"><span data-stu-id="3c12d-130">Profiles show you whether the CPU is fully loaded or whether you’re blocked on disk I/O.</span></span> <span data-ttu-id="3c12d-131">Profily vám řeknou, jaký druh a kolik paměti přidělujete a zda procesor tráví spoustu času v [uvolňování paměti](../../standard/garbage-collection/index.md) (GC).</span><span class="sxs-lookup"><span data-stu-id="3c12d-131">Profiles tell you what kind and how much memory you’re allocating and whether your CPU is spending a lot of time in [garbage collection](../../standard/garbage-collection/index.md) (GC).</span></span>
  
 <span data-ttu-id="3c12d-132">Měli byste nastavit cíle výkonu pro klíčové zkušenosti zákazníků nebo scénáře ve vaší aplikaci a psát testy pro měření výkonu.</span><span class="sxs-lookup"><span data-stu-id="3c12d-132">You should set performance goals for key customer experiences or scenarios in your app and write tests to measure performance.</span></span> <span data-ttu-id="3c12d-133">Prozkoumejte neúspěšné testy pomocí vědecké metody: použijte profily, které vás provedou, předpokládají, jaký problém by mohl být, a otestujte hypotézu pomocí experimentu nebo změny kódu.</span><span class="sxs-lookup"><span data-stu-id="3c12d-133">Investigate failing tests by applying the scientific method: use profiles to guide you, hypothesize what the issue might be, and test your hypothesis with an experiment or code change.</span></span> <span data-ttu-id="3c12d-134">Stanovit základní měření výkonu v průběhu času s pravidelným testováním, takže můžete izolovat změny, které způsobují regrese ve výkonu.</span><span class="sxs-lookup"><span data-stu-id="3c12d-134">Establish baseline performance measurements over time with regular testing, so you can isolate changes that cause regressions in performance.</span></span> <span data-ttu-id="3c12d-135">Tím, že se přiblížíte k práci s výkonem přísným způsobem, vyhnete se plýtvání časem s aktualizacemi kódu, které nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="3c12d-135">By approaching performance work in a rigorous way, you’ll avoid wasting time with code updates you don’t need.</span></span>
  
### <a name="fact-3-good-tools-make-all-the-difference"></a><span data-ttu-id="3c12d-136">Fakt 3: Dobré nástroje, aby celý rozdíl</span><span class="sxs-lookup"><span data-stu-id="3c12d-136">Fact 3: Good tools make all the difference</span></span>  
 <span data-ttu-id="3c12d-137">Dobré nástroje umožňují rychle přejít k podrobnostem o největších problémech s výkonem (procesor, paměť nebo disk) a pomoci vám najít kód, který způsobuje tato kritická místa.</span><span class="sxs-lookup"><span data-stu-id="3c12d-137">Good tools let you drill quickly into the biggest performance issues (CPU, memory, or disk) and help you locate the code that causes those bottlenecks.</span></span> <span data-ttu-id="3c12d-138">Společnost Microsoft dodává různé nástroje pro výkon, například [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) a [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span><span class="sxs-lookup"><span data-stu-id="3c12d-138">Microsoft ships a variety of performance tools such as [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) and [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span></span>
  
 <span data-ttu-id="3c12d-139">PerfView je bezplatný a úžasně výkonný nástroj, který vám pomůže zaměřit se na hluboké problémy, jako je disk V/O, GC události a paměť.</span><span class="sxs-lookup"><span data-stu-id="3c12d-139">PerfView is a free and amazingly powerful tool that helps you focus on deep issues such as disk I/O, GC events, and memory.</span></span> <span data-ttu-id="3c12d-140">Můžete zachytit události sledování událostí související s [výkonem pro Windows](../wcf/samples/etw-tracing.md) (ETW) a snadno zobrazit na aplikaci, na proces, na zásobník a informace o vlákně.</span><span class="sxs-lookup"><span data-stu-id="3c12d-140">You can capture performance-related [Event Tracing for Windows](../wcf/samples/etw-tracing.md) (ETW) events and view easily per app, per process, per stack, and per thread information.</span></span> <span data-ttu-id="3c12d-141">PerfView ukazuje, kolik a jaký druh paměti vaše aplikace přiděluje a které funkce nebo zásobníky volání přispívají, kolik přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="3c12d-141">PerfView shows you how much and what kind of memory your app allocates, and which functions or call stacks contribute how much to the memory allocations.</span></span> <span data-ttu-id="3c12d-142">Podrobnosti najdete v tématech s bohatou nápovědou, ukázkách a videích, které jsou součástí nástroje (například [kurzy PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) na kanálu 9).</span><span class="sxs-lookup"><span data-stu-id="3c12d-142">For details, see the rich help topics, demos, and videos included with the tool (such as the [PerfView tutorials](https://channel9.msdn.com/Series/PerfView-Tutorial) on Channel 9).</span></span>
  
### <a name="fact-4-its-all-about-allocations"></a><span data-ttu-id="3c12d-143">Fakt 4: Je to všechno o přidělení</span><span class="sxs-lookup"><span data-stu-id="3c12d-143">Fact 4: It’s all about allocations</span></span>  
 <span data-ttu-id="3c12d-144">Můžete si myslet, že vytváření responzivní aplikace rozhraní .NET Framework je o algoritmech, jako je například použití rychlého řazení namísto řazení bublin, ale to není tento případ.</span><span class="sxs-lookup"><span data-stu-id="3c12d-144">You might think that building a responsive .NET Framework app is all about algorithms, such as using quick sort instead of bubble sort, but that's not the case.</span></span> <span data-ttu-id="3c12d-145">Největším faktorem při vytváření responzivní aplikace je přidělování paměti, zejména když je vaše aplikace velmi velká nebo zpracovává velké množství dat.</span><span class="sxs-lookup"><span data-stu-id="3c12d-145">The biggest factor in building a responsive app is allocating memory, especially when your app is very large or processes large amounts of data.</span></span>
  
 <span data-ttu-id="3c12d-146">Téměř všechny práce na vytváření responzivních prostředí IDE s novými rozhraními API kompilátoru zahrnovaly předcházení přidělení a správu strategií ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="3c12d-146">Almost all the work to build responsive IDE experiences with the new compiler APIs involved avoiding allocations and managing caching strategies.</span></span> <span data-ttu-id="3c12d-147">PerfView trasování ukazují, že výkon nové c# a visual basic kompilátory je zřídka vázaný na procesor.</span><span class="sxs-lookup"><span data-stu-id="3c12d-147">PerfView traces show that the performance of the new C# and Visual Basic compilers is rarely CPU bound.</span></span> <span data-ttu-id="3c12d-148">Kompilátory mohou být vázány vstupně-výstupními moduly při čtení stovek tisíc nebo milionů řádků kódu, čtení metadat nebo vyzařování generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="3c12d-148">The compilers can be I/O bound when reading hundreds of thousands or millions of lines of code, reading metadata, or emitting generated code.</span></span> <span data-ttu-id="3c12d-149">Zpoždění vlákna uživatelského rozhraní jsou téměř všechny z důvodu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="3c12d-149">The UI thread delays are nearly all due to garbage collection.</span></span> <span data-ttu-id="3c12d-150">.NET Framework GC je vysoce naladěn na výkon a provádí velkou část své práce souběžně při spuštění kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="3c12d-150">The .NET Framework GC is highly tuned for performance and does much of its work concurrently while app code executes.</span></span> <span data-ttu-id="3c12d-151">Jediné přidělení však může aktivovat kolekci nákladné [gen2,](../../standard/garbage-collection/fundamentals.md) zastavení všech vláken.</span><span class="sxs-lookup"><span data-stu-id="3c12d-151">However, a single allocation can trigger an expensive [gen2](../../standard/garbage-collection/fundamentals.md) collection, stopping all threads.</span></span>
  
## <a name="common-allocations-and-examples"></a><span data-ttu-id="3c12d-152">Společné příděly a příklady</span><span class="sxs-lookup"><span data-stu-id="3c12d-152">Common allocations and examples</span></span>  
 <span data-ttu-id="3c12d-153">Ukázkové výrazy v této části mají skryté přidělení, které se zobrazují malé.</span><span class="sxs-lookup"><span data-stu-id="3c12d-153">The example expressions in this section have hidden allocations that appear small.</span></span> <span data-ttu-id="3c12d-154">Pokud však velká aplikace spustí výrazy dostatečně krát, mohou způsobit stovky megabajtů, dokonce i gigabajtů přidělení.</span><span class="sxs-lookup"><span data-stu-id="3c12d-154">However, if a large app executes the expressions enough times, they can causes hundreds of megabytes, even gigabytes, of allocations.</span></span> <span data-ttu-id="3c12d-155">Například jednominutové testy, které simulovaly psaní vývojáře v editoru, přidělily gigabajty paměti a vedly tým výkonu k zaměření na scénáře psaní.</span><span class="sxs-lookup"><span data-stu-id="3c12d-155">For example, one-minute tests that simulated a developer’s typing in the editor allocated gigabytes of memory and led the performance team to focus on typing scenarios.</span></span>
  
### <a name="boxing"></a><span data-ttu-id="3c12d-156">Zabalení</span><span class="sxs-lookup"><span data-stu-id="3c12d-156">Boxing</span></span>  
 <span data-ttu-id="3c12d-157">[K zabalení](../../csharp/programming-guide/types/boxing-and-unboxing.md) dochází, když typy hodnot, které normálně žijí v zásobníku nebo v datových strukturách, jsou zabaleny do objektu.</span><span class="sxs-lookup"><span data-stu-id="3c12d-157">[Boxing](../../csharp/programming-guide/types/boxing-and-unboxing.md) occurs when value types that normally live on the stack or in data structures are wrapped in an object.</span></span> <span data-ttu-id="3c12d-158">To znamená, že přidělíte objekt k uložení dat a potom vrátíte ukazatel na objekt.</span><span class="sxs-lookup"><span data-stu-id="3c12d-158">That is, you allocate an object to hold the data, and then return a pointer to the object.</span></span> <span data-ttu-id="3c12d-159">Rozhraní .NET Framework někdy krabice hodnoty z důvodu podpisu metody nebo typ umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="3c12d-159">The .NET Framework sometimes boxes values due to the signature of a method or the type of a storage location.</span></span> <span data-ttu-id="3c12d-160">Obtékání typu hodnoty v objektu způsobí přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="3c12d-160">Wrapping a value type in an object causes memory allocation.</span></span> <span data-ttu-id="3c12d-161">Mnoho operací zabalení může do vaší aplikace přispívat megabajty nebo gigabajty přidělení, což znamená, že vaše aplikace způsobí více řadičů domény.</span><span class="sxs-lookup"><span data-stu-id="3c12d-161">Many boxing operations can contribute megabytes or gigabytes of allocations to your app, which means that your app will cause more GCs.</span></span> <span data-ttu-id="3c12d-162">Rozhraní .NET Framework a kompilátory jazyka vyhnout zabalení, pokud je to možné, ale někdy se to stane, když nejméně očekávat.</span><span class="sxs-lookup"><span data-stu-id="3c12d-162">The .NET Framework and the language compilers avoid boxing when possible, but sometimes it happens when you least expect it.</span></span>
  
 <span data-ttu-id="3c12d-163">Chcete-li zobrazit zabalení v PerfView, otevřete trasování a podívejte se na GC Haldy Alloc zásobníky pod název procesu vaší aplikace (pamatujte, PerfView sestavy na všechny procesy).</span><span class="sxs-lookup"><span data-stu-id="3c12d-163">To see boxing in PerfView, open a trace and look at GC Heap Alloc Stacks under your app’s process name (remember, PerfView reports on all processes).</span></span> <span data-ttu-id="3c12d-164">Pokud se zobrazí <xref:System.Int32?displayProperty=nameWithType> <xref:System.Char?displayProperty=nameWithType> typy jako a pod přidělení, jsou zabalení typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="3c12d-164">If you see types like <xref:System.Int32?displayProperty=nameWithType> and <xref:System.Char?displayProperty=nameWithType> under allocations, you are boxing value types.</span></span> <span data-ttu-id="3c12d-165">Výběr jednoho z těchto typů se zobrazí zásobníky a funkce, ve kterých jsou zabaleny.</span><span class="sxs-lookup"><span data-stu-id="3c12d-165">Choosing one of these types will show the stacks and functions in which they are boxed.</span></span>
  
 <span data-ttu-id="3c12d-166">**Příklad 1: metody řetězce a argumenty typu hodnoty**</span><span class="sxs-lookup"><span data-stu-id="3c12d-166">**Example 1: string methods and value type arguments**</span></span>  
  
 <span data-ttu-id="3c12d-167">Tento ukázkový kód ilustruje potenciálně zbytečné a nadměrné zabalení:</span><span class="sxs-lookup"><span data-stu-id="3c12d-167">This sample code illustrates potentially unnecessary and excessive boxing:</span></span>  
  
```csharp  
public class Logger  
{  
    public static void WriteLine(string s) { /*...*/ }  
}  
  
public class BoxingExample  
{  
    public void Log(int id, int size)  
    {  
        var s = string.Format("{0}:{1}", id, size);  
        Logger.WriteLine(s);  
    }  
}  
```  
  
 <span data-ttu-id="3c12d-168">Tento kód poskytuje funkce protokolování, takže `Log` aplikace může volat funkci často, možná milionkrát.</span><span class="sxs-lookup"><span data-stu-id="3c12d-168">This code provides logging functionality, so an app may call the `Log` function frequently, maybe millions of times.</span></span> <span data-ttu-id="3c12d-169">Problém je, že `string.Format` volání řeší <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> přetížení.</span><span class="sxs-lookup"><span data-stu-id="3c12d-169">The problem is that the call to `string.Format` resolves to the <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> overload.</span></span>
  
 <span data-ttu-id="3c12d-170">Toto přetížení vyžaduje rozhraní .NET Framework zaokříznout `int` hodnoty do objektů předat volání této metody.</span><span class="sxs-lookup"><span data-stu-id="3c12d-170">This overload requires the .NET Framework to box the `int` values into objects to pass them to this method call.</span></span> <span data-ttu-id="3c12d-171">Částečná oprava je `id.ToString()` `size.ToString()` volání a předání všech řetězců (které `string.Format` jsou objekty) volání.</span><span class="sxs-lookup"><span data-stu-id="3c12d-171">A partial fix is to call `id.ToString()` and `size.ToString()` and pass all strings (which are objects) to the `string.Format` call.</span></span> <span data-ttu-id="3c12d-172">Volání `ToString()` přiděluje řetězec, ale toto přidělení se stane stejně uvnitř `string.Format`.</span><span class="sxs-lookup"><span data-stu-id="3c12d-172">Calling `ToString()` does allocate a string, but that allocation will happen anyway inside `string.Format`.</span></span>
  
 <span data-ttu-id="3c12d-173">Můžete zvážit, že toto základní volání `string.Format` je pouze zřetězení řetězce, takže místo toho můžete napsat tento kód:</span><span class="sxs-lookup"><span data-stu-id="3c12d-173">You might consider that this basic call to `string.Format` is just string concatenation, so you might write this code instead:</span></span>  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 <span data-ttu-id="3c12d-174">Tento řádek kódu však zavádí přidělení zabalení, <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>protože zkompiluje do .</span><span class="sxs-lookup"><span data-stu-id="3c12d-174">However, that line of code introduces a boxing allocation because it compiles to <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span></span> <span data-ttu-id="3c12d-175">Rozhraní .NET Framework musí zaokřovat literál znaku, který vyvolá`Concat`</span><span class="sxs-lookup"><span data-stu-id="3c12d-175">The .NET Framework must box the character literal to invoke `Concat`</span></span>  
  
 <span data-ttu-id="3c12d-176">**Opravit například 1**</span><span class="sxs-lookup"><span data-stu-id="3c12d-176">**Fix for example 1**</span></span>  
  
 <span data-ttu-id="3c12d-177">Kompletní oprava je jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="3c12d-177">The complete fix is simple.</span></span> <span data-ttu-id="3c12d-178">Stačí nahradit literál znaku literál řetězcem, který nevzniká žádné zabalení, protože řetězce jsou již objekty:</span><span class="sxs-lookup"><span data-stu-id="3c12d-178">Just replace the character literal with a string literal, which incurs no boxing because strings are already objects:</span></span>  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 <span data-ttu-id="3c12d-179">**Příklad 2: enum boxing**</span><span class="sxs-lookup"><span data-stu-id="3c12d-179">**Example 2: enum boxing**</span></span>  
  
 <span data-ttu-id="3c12d-180">Tento příklad byl zodpovědný za obrovské množství přidělení v nové kompilátory jazyka C# a Visual Basic z důvodu časté hojné použití typů výčtu, zejména ve slovníku vyhledávací operace.</span><span class="sxs-lookup"><span data-stu-id="3c12d-180">This example was responsible for a huge amount of allocation in the new C# and Visual Basic compilers due to frequent use of enumeration types, especially in dictionary lookup operations.</span></span>
  
```csharp  
public enum Color  
{  
    Red, Green, Blue  
}  
  
public class BoxingExample  
{  
    private string name;  
    private Color color;  
    public override int GetHashCode()  
    {  
        return name.GetHashCode() ^ color.GetHashCode();  
    }  
}  
```  
  
 <span data-ttu-id="3c12d-181">Tento problém je velmi jemný.</span><span class="sxs-lookup"><span data-stu-id="3c12d-181">This problem is very subtle.</span></span> <span data-ttu-id="3c12d-182">PerfView by to <xref:System.Enum.GetHashCode> hlásit jako zabalení, protože metoda boxy základní reprezentace typu výčtu, z důvodů implementace.</span><span class="sxs-lookup"><span data-stu-id="3c12d-182">PerfView would report this as <xref:System.Enum.GetHashCode> boxing because the method boxes the underlying representation of the enumeration type, for implementation reasons.</span></span> <span data-ttu-id="3c12d-183">Pokud se podíváte pozorně v PerfView, může se <xref:System.Enum.GetHashCode>zobrazit dvě přidělení zabalení pro každé volání .</span><span class="sxs-lookup"><span data-stu-id="3c12d-183">If you look closely in PerfView, you may see two boxing allocations for each call to <xref:System.Enum.GetHashCode>.</span></span> <span data-ttu-id="3c12d-184">Kompilátor vloží jeden a rozhraní .NET Framework vloží druhou.</span><span class="sxs-lookup"><span data-stu-id="3c12d-184">The compiler inserts one, and the .NET Framework inserts the other.</span></span>
  
 <span data-ttu-id="3c12d-185">**Oprava například 2**</span><span class="sxs-lookup"><span data-stu-id="3c12d-185">**Fix for example 2**</span></span>  
  
 <span data-ttu-id="3c12d-186">Můžete snadno vyhnout obě přidělení obsazení majestátu před voláním <xref:System.Enum.GetHashCode>:</span><span class="sxs-lookup"><span data-stu-id="3c12d-186">You can easily avoid both allocations by casting to the underlying representation before calling <xref:System.Enum.GetHashCode>:</span></span>  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 <span data-ttu-id="3c12d-187">Dalším běžným zdrojem zabalení na <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> typy výčtu je metoda.</span><span class="sxs-lookup"><span data-stu-id="3c12d-187">Another common source of boxing on enumeration types is the <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3c12d-188">Argument předaný <xref:System.Enum.HasFlag%28System.Enum%29> musí být zabalen.</span><span class="sxs-lookup"><span data-stu-id="3c12d-188">The argument passed to <xref:System.Enum.HasFlag%28System.Enum%29> has to be boxed.</span></span> <span data-ttu-id="3c12d-189">Ve většině případů nahrazení <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> volání bitovým testem je jednodušší a bez přidělení.</span><span class="sxs-lookup"><span data-stu-id="3c12d-189">In most cases, replacing calls to <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> with a bitwise test is simpler and allocation-free.</span></span>
  
 <span data-ttu-id="3c12d-190">Mějte na paměti první fakt výkonu (to znamená, nepředčasně optimalizovat) a nezačínejte přepisovat veškerý kód tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="3c12d-190">Keep the first performance fact in mind (that is, don’t prematurely optimize) and don’t start rewriting all your code in this way.</span></span> <span data-ttu-id="3c12d-191">Uvědomte si tyto náklady na box, ale změnit kód pouze po profilování aplikace a hledání horkých míst.</span><span class="sxs-lookup"><span data-stu-id="3c12d-191">Be aware of these boxing costs, but change your code only after profiling your app and finding the hot spots.</span></span>
  
### <a name="strings"></a><span data-ttu-id="3c12d-192">Řetězce</span><span class="sxs-lookup"><span data-stu-id="3c12d-192">Strings</span></span>  
 <span data-ttu-id="3c12d-193">Řetězec manipulace jsou některé z největších viníků pro přidělení a často se zobrazí v PerfView v prvních pěti přidělení.</span><span class="sxs-lookup"><span data-stu-id="3c12d-193">String manipulations are some of the biggest culprits for allocations, and they often show up in PerfView in the top five allocations.</span></span> <span data-ttu-id="3c12d-194">Programy používají řetězce pro serializaci, JSON a REST API.</span><span class="sxs-lookup"><span data-stu-id="3c12d-194">Programs use strings for serialization, JSON, and REST APIs.</span></span> <span data-ttu-id="3c12d-195">Řetězce můžete použít jako programové konstanty pro spolupráci se systémy, když nelze použít typy výčtu.</span><span class="sxs-lookup"><span data-stu-id="3c12d-195">You can use strings as programmatic constants for interoperating with systems when you can’t use enumeration types.</span></span> <span data-ttu-id="3c12d-196">Pokud profilování ukazuje, že řetězce mají velký vliv <xref:System.String> na <xref:System.String.Format%2A>výkon, <xref:System.String.Split%2A> <xref:System.String.Join%2A>vyhledejte volání metod, jako jsou například , <xref:System.String.Substring%2A> <xref:System.String.Concat%2A>, , a tak dále.</span><span class="sxs-lookup"><span data-stu-id="3c12d-196">When your profiling shows that strings are highly affecting performance, look for calls to <xref:System.String> methods such as <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, and so on.</span></span> <span data-ttu-id="3c12d-197">Použití, <xref:System.Text.StringBuilder> aby se zabránilo náklady na vytvoření jednoho řetězce z <xref:System.Text.StringBuilder> mnoha kusů pomáhá, ale i přidělení objektu se může stát kritickým bodem, který je třeba spravovat.</span><span class="sxs-lookup"><span data-stu-id="3c12d-197">Using <xref:System.Text.StringBuilder> to avoid the cost of creating one string from many pieces helps, but even allocating the <xref:System.Text.StringBuilder> object might become a bottleneck that you need to manage.</span></span>
  
 <span data-ttu-id="3c12d-198">**Příklad 3: operace řetězce**</span><span class="sxs-lookup"><span data-stu-id="3c12d-198">**Example 3: string operations**</span></span>  
  
 <span data-ttu-id="3c12d-199">Kompilátor Jazyka C# měl tento kód, který zapisuje text formátovaného komentáře dokumentu XML:</span><span class="sxs-lookup"><span data-stu-id="3c12d-199">The C# compiler had this code that writes the text of a formatted XML doc comment:</span></span>  
  
```csharp  
public void WriteFormattedDocComment(string text)  
{  
    string[] lines = text.Split(new[] { "\r\n", "\r", "\n" },  
                                StringSplitOptions.None);  
    int numLines = lines.Length;  
    bool skipSpace = true;  
    if (lines[0].TrimStart().StartsWith("///"))  
    {  
        for (int i = 0; i < numLines; i++)  
        {  
            string trimmed = lines[i].TrimStart();  
            if (trimmed.Length < 4 || !char.IsWhiteSpace(trimmed[3]))  
            {  
                skipSpace = false;  
                break;  
            }  
        }  
        int substringStart = skipSpace ? 4 : 3;  
        for (int i = 0; i < numLines; i++)  
            WriteLine(lines[i].TrimStart().Substring(substringStart));  
    }  
    else { /* ... */ }  
```  
  
 <span data-ttu-id="3c12d-200">Můžete vidět, že tento kód provádí mnoho manipulace s řetězci.</span><span class="sxs-lookup"><span data-stu-id="3c12d-200">You can see that this code does a lot of string manipulation.</span></span> <span data-ttu-id="3c12d-201">Kód používá metody knihovny k rozdělení řádků do samostatných řetězců, `text` k oříznutí prázdného místa, ke kontrole, zda je argument emblém dokumentace XML, a k extrahování podřetězců z řádků.</span><span class="sxs-lookup"><span data-stu-id="3c12d-201">The code uses library methods to split lines into separate strings, to trim white space, to check whether the argument `text` is an XML documentation comment, and to extract substrings from lines.</span></span>
  
 <span data-ttu-id="3c12d-202">Na prvním řádku `WriteFormattedDocComment`uvnitř `text.Split` volání přiděluje nové pole tří prvků jako argument pokaždé, když je volána.</span><span class="sxs-lookup"><span data-stu-id="3c12d-202">On the first line inside `WriteFormattedDocComment`, the `text.Split` call allocates a new three-element array as the argument every time it’s called.</span></span> <span data-ttu-id="3c12d-203">Kompilátor musí vyzařovat kód pro přidělení tohoto pole pokaždé.</span><span class="sxs-lookup"><span data-stu-id="3c12d-203">The compiler has to emit code to allocate this array each time.</span></span> <span data-ttu-id="3c12d-204">Důvodem je, že kompilátor <xref:System.String.Split%2A> neví, pokud ukládá pole někde, kde pole může být `WriteFormattedDocComment`změněn jiným kódem, což by ovlivnilo pozdější volání .</span><span class="sxs-lookup"><span data-stu-id="3c12d-204">That’s because the compiler doesn’t know if <xref:System.String.Split%2A> stores the array somewhere where the array might be modified by other code, which would affect later calls to `WriteFormattedDocComment`.</span></span> <span data-ttu-id="3c12d-205">Volání <xref:System.String.Split%2A> také přiděluje řetězec pro `text` každý řádek v a přiděluje další paměti k provedení operace.</span><span class="sxs-lookup"><span data-stu-id="3c12d-205">The call to <xref:System.String.Split%2A> also allocates a string for every line in `text` and allocates other memory to perform the operation.</span></span>
  
 <span data-ttu-id="3c12d-206">`WriteFormattedDocComment`má tři volání <xref:System.String.TrimStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3c12d-206">`WriteFormattedDocComment` has three calls to the <xref:System.String.TrimStart%2A> method.</span></span> <span data-ttu-id="3c12d-207">Dva jsou ve vnitřních smyčkách, které duplikují práci a přidělení.</span><span class="sxs-lookup"><span data-stu-id="3c12d-207">Two are in inner loops that duplicate work and allocations.</span></span> <span data-ttu-id="3c12d-208">Aby toho nebylo málo, volání <xref:System.String.TrimStart%2A> metody bez argumentů přiděluje prázdné pole (pro `params` parametr) kromě výsledku řetězce.</span><span class="sxs-lookup"><span data-stu-id="3c12d-208">To make matters worse, calling the <xref:System.String.TrimStart%2A> method with no arguments allocates an empty array (for the `params` parameter) in addition to the string result.</span></span>
  
 <span data-ttu-id="3c12d-209">Nakonec je volání <xref:System.String.Substring%2A> metody, která obvykle přiděluje nový řetězec.</span><span class="sxs-lookup"><span data-stu-id="3c12d-209">Lastly, there is a call to the <xref:System.String.Substring%2A> method, which usually allocates a new string.</span></span>
  
 <span data-ttu-id="3c12d-210">**Opravit například 3**</span><span class="sxs-lookup"><span data-stu-id="3c12d-210">**Fix for example 3**</span></span>  
  
 <span data-ttu-id="3c12d-211">Na rozdíl od předchozích příkladů malé úpravy nelze opravit tyto přidělení.</span><span class="sxs-lookup"><span data-stu-id="3c12d-211">Unlike the earlier examples, small edits cannot fix these allocations.</span></span> <span data-ttu-id="3c12d-212">Musíte ustoupit, podívat se na problém a přistupovat k němu jinak.</span><span class="sxs-lookup"><span data-stu-id="3c12d-212">You need to step back, look at the problem, and approach it differently.</span></span> <span data-ttu-id="3c12d-213">Například si všimnete, že `WriteFormattedDocComment()` argument je řetězec, který má všechny informace, které metoda potřebuje, takže kód může provést více indexování namísto přidělení mnoho dílčích řetězců.</span><span class="sxs-lookup"><span data-stu-id="3c12d-213">For example, you'll notice that the argument to `WriteFormattedDocComment()` is a string that has all the information that the method needs, so the code could do more indexing instead of allocating many partial strings.</span></span>
  
 <span data-ttu-id="3c12d-214">Výkonnostní tým kompilátoru řešil všechny tyto přidělení s kódem, jako je tento:</span><span class="sxs-lookup"><span data-stu-id="3c12d-214">The compiler’s performance team tackled all these allocations with code like this:</span></span>  
  
```csharp  
private int IndexOfFirstNonWhiteSpaceChar(string text, int start) {  
    while (start < text.Length && char.IsWhiteSpace(text[start])) start++;  
    return start;  
}  
  
private bool TrimmedStringStartsWith(string text, int start, string prefix) {  
    start = IndexOfFirstNonWhiteSpaceChar(text, start);  
    int len = text.Length - start;  
    if (len < prefix.Length) return false;  
    for (int i = 0; i < len; i++)  
    {  
        if (prefix[i] != text[start + i]) return false;  
    }  
    return true;  
}  
  
// etc...
```  
  
 <span data-ttu-id="3c12d-215">První verze `WriteFormattedDocComment()` přidělené pole, několik podřetězců a oříznuté podřetězec spolu `params` s prázdným polem.</span><span class="sxs-lookup"><span data-stu-id="3c12d-215">The first version of `WriteFormattedDocComment()` allocated an array, several substrings, and a trimmed substring along with an empty `params` array.</span></span> <span data-ttu-id="3c12d-216">Také zkontroloval "///".</span><span class="sxs-lookup"><span data-stu-id="3c12d-216">It also checked for "///".</span></span> <span data-ttu-id="3c12d-217">Revidovaný kód používá pouze indexování a nepřiděluje nic.</span><span class="sxs-lookup"><span data-stu-id="3c12d-217">The revised code uses only indexing and allocates nothing.</span></span> <span data-ttu-id="3c12d-218">Najde první znak, který není prázdné místo a potom zkontroluje znak po znaku, aby zjistil, zda řetězec začíná "///".</span><span class="sxs-lookup"><span data-stu-id="3c12d-218">It finds the first character that is not white space, and then checks character by character to see if the string starts with "///".</span></span> <span data-ttu-id="3c12d-219">Nový kód `IndexOfFirstNonWhiteSpaceChar` používá <xref:System.String.TrimStart%2A> místo vrátit první index (po zadaném indexu start), kde dojde k neprázdné místo znaku.</span><span class="sxs-lookup"><span data-stu-id="3c12d-219">The new code uses `IndexOfFirstNonWhiteSpaceChar` instead of <xref:System.String.TrimStart%2A> to return the first index (after a specified start index) where a non-white-space character occurs.</span></span> <span data-ttu-id="3c12d-220">Oprava není dokončena, ale můžete vidět, jak použít podobné opravy pro úplné řešení.</span><span class="sxs-lookup"><span data-stu-id="3c12d-220">The fix is not complete, but you can see how to apply similar fixes for a complete solution.</span></span> <span data-ttu-id="3c12d-221">Použitím tohoto přístupu v celém kódu můžete `WriteFormattedDocComment()`odebrat všechna přidělení v aplikaci .</span><span class="sxs-lookup"><span data-stu-id="3c12d-221">By applying this approach throughout the code, you can remove all allocations in `WriteFormattedDocComment()`.</span></span>
  
 <span data-ttu-id="3c12d-222">**Příklad 4: StringBuilder**</span><span class="sxs-lookup"><span data-stu-id="3c12d-222">**Example 4: StringBuilder**</span></span>  
  
 <span data-ttu-id="3c12d-223">Tento příklad <xref:System.Text.StringBuilder> používá objekt.</span><span class="sxs-lookup"><span data-stu-id="3c12d-223">This example uses a <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="3c12d-224">Následující funkce generuje úplný název typu pro obecné typy:</span><span class="sxs-lookup"><span data-stu-id="3c12d-224">The following function generates a full type name for generic types:</span></span>  
  
```csharp  
public class Example  
{  
    // Constructs a name like "SomeType<T1, T2, T3>"  
    public string GenerateFullTypeName(string name, int arity)  
    {  
        StringBuilder sb = new StringBuilder();  
  
        sb.Append(name);  
        if (arity != 0)  
        {  
            sb.Append("<");  
            for (int i = 1; i < arity; i++)  
            {  
                sb.Append("T"); sb.Append(i.ToString()); sb.Append(", ");  
            }  
            sb.Append("T"); sb.Append(i.ToString()); sb.Append(">");  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
 <span data-ttu-id="3c12d-225">Fokus je na řádku, <xref:System.Text.StringBuilder> který vytvoří novou instanci.</span><span class="sxs-lookup"><span data-stu-id="3c12d-225">The focus is on the line that creates a new <xref:System.Text.StringBuilder> instance.</span></span> <span data-ttu-id="3c12d-226">Kód způsobí přidělení `sb.ToString()` a vnitřní přidělení <xref:System.Text.StringBuilder> v rámci implementace, ale nelze řídit tato přidělení, pokud chcete výsledek řetězce.</span><span class="sxs-lookup"><span data-stu-id="3c12d-226">The code causes an allocation for `sb.ToString()` and internal allocations within the <xref:System.Text.StringBuilder> implementation, but you cannot control those allocations if you want the string result.</span></span>
  
 <span data-ttu-id="3c12d-227">**Oprava například 4**</span><span class="sxs-lookup"><span data-stu-id="3c12d-227">**Fix for example 4**</span></span>  
  
 <span data-ttu-id="3c12d-228">Chcete-li `StringBuilder` opravit přidělení objektu, uvěnujte objekt do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="3c12d-228">To fix the `StringBuilder` object allocation, cache the  object.</span></span> <span data-ttu-id="3c12d-229">Dokonce i ukládání do mezipaměti jedné instance, která by mohla dostat vyhodit může výrazně zlepšit výkon.</span><span class="sxs-lookup"><span data-stu-id="3c12d-229">Even caching a single instance that might get thrown away can improve performance significantly.</span></span> <span data-ttu-id="3c12d-230">Toto je nová implementace funkce, vynechání veškerý kód s výjimkou nové první a poslední řádky:</span><span class="sxs-lookup"><span data-stu-id="3c12d-230">This is the function’s new implementation, omitting all the code except for the new first and last lines:</span></span>  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 <span data-ttu-id="3c12d-231">Klíčovými částmi `AcquireBuilder()` jsou `GetStringAndReleaseBuilder()` nové a funkce:</span><span class="sxs-lookup"><span data-stu-id="3c12d-231">The key parts are the new `AcquireBuilder()` and `GetStringAndReleaseBuilder()` functions:</span></span>  
  
```csharp  
[ThreadStatic]  
private static StringBuilder cachedStringBuilder;  
  
private static StringBuilder AcquireBuilder()  
{  
    StringBuilder result = cachedStringBuilder;  
    if (result == null)  
    {  
        return new StringBuilder();  
    }  
    result.Clear();  
    cachedStringBuilder = null;  
    return result;  
}  
  
private static string GetStringAndReleaseBuilder(StringBuilder sb)  
{  
    string result = sb.ToString();  
    cachedStringBuilder = sb;  
    return result;  
}  
```  
  
 <span data-ttu-id="3c12d-232">Vzhledem k tomu, že nové kompilátory používají<xref:System.ThreadStaticAttribute> podproces, tyto <xref:System.Text.StringBuilder>implementace používají statické pole `ThreadStatic` podprocesu (atribut) k ukládání do mezipaměti a pravděpodobně můžete zprostit deklarace.</span><span class="sxs-lookup"><span data-stu-id="3c12d-232">Because the new compilers use threading, these implementations use a thread-static field (<xref:System.ThreadStaticAttribute> attribute) to cache the <xref:System.Text.StringBuilder>, and you likely can forgo the `ThreadStatic` declaration.</span></span> <span data-ttu-id="3c12d-233">Pole statické vlákno obsahuje jedinečnou hodnotu pro každé vlákno, které spustí tento kód.</span><span class="sxs-lookup"><span data-stu-id="3c12d-233">The thread-static field holds a unique value for each thread that executes this code.</span></span>
  
 <span data-ttu-id="3c12d-234">`AcquireBuilder()`vrátí instanci uloženou v mezipaměti, <xref:System.Text.StringBuilder> pokud existuje, po vymazání a nastavení pole nebo mezipaměti na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3c12d-234">`AcquireBuilder()` returns the cached <xref:System.Text.StringBuilder> instance if there is one, after clearing it and setting the field or cache to null.</span></span> <span data-ttu-id="3c12d-235">V `AcquireBuilder()` opačném případě vytvoří novou instanci a vrátí ji, přičemž pole nebo mezipaměti nastavena na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3c12d-235">Otherwise, `AcquireBuilder()` creates a new instance and returns it, leaving the field or cache set to null.</span></span>
  
 <span data-ttu-id="3c12d-236">Po dokončení s <xref:System.Text.StringBuilder> , volání `GetStringAndReleaseBuilder()` získat výsledek řetězce, <xref:System.Text.StringBuilder> uložte instanci v poli nebo mezipaměti a potom vrátit výsledek.</span><span class="sxs-lookup"><span data-stu-id="3c12d-236">When you’re done with <xref:System.Text.StringBuilder> , you call `GetStringAndReleaseBuilder()` to get the string result, save the <xref:System.Text.StringBuilder> instance in the field or cache, and then return the result.</span></span> <span data-ttu-id="3c12d-237">Je možné pro spuštění znovu zadat tento kód <xref:System.Text.StringBuilder> a vytvořit více objektů (i když to zřídka se stane).</span><span class="sxs-lookup"><span data-stu-id="3c12d-237">It is possible for execution to re-enter this code and to create multiple <xref:System.Text.StringBuilder> objects (although that rarely happens).</span></span> <span data-ttu-id="3c12d-238">Kód uloží pouze poslední <xref:System.Text.StringBuilder> vydané instance pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="3c12d-238">The code saves only the last released <xref:System.Text.StringBuilder> instance for later use.</span></span> <span data-ttu-id="3c12d-239">Tato jednoduchá strategie ukládání do mezipaměti výrazně snížila přidělení v nových kompilátorech.</span><span class="sxs-lookup"><span data-stu-id="3c12d-239">This simple caching strategy significantly reduced allocations in the new compilers.</span></span> <span data-ttu-id="3c12d-240">Části rozhraní .NET Framework a MSBuild ("MSBuild") používají podobnou techniku ke zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="3c12d-240">Parts of the .NET Framework and MSBuild ("MSBuild") use a similar technique to improve performance.</span></span>
  
 <span data-ttu-id="3c12d-241">Tato jednoduchá strategie ukládání do mezipaměti dodržuje dobrý design mezipaměti, protože má velikostní čepici.</span><span class="sxs-lookup"><span data-stu-id="3c12d-241">This simple caching strategy adheres to good cache design because it has a size cap.</span></span> <span data-ttu-id="3c12d-242">Existuje však více kódu nyní než v originále, což znamená více nákladů na údržbu.</span><span class="sxs-lookup"><span data-stu-id="3c12d-242">However, there is more code now than in the original, which means more maintenance costs.</span></span> <span data-ttu-id="3c12d-243">Strategii ukládání do mezipaměti byste měli přijmout pouze v případě, že jste <xref:System.Text.StringBuilder> našli problém s výkonem a PerfView ukázalo, že přidělení jsou významným přispěvatelem.</span><span class="sxs-lookup"><span data-stu-id="3c12d-243">You should adopt the caching strategy only if you’ve found a performance problem, and PerfView has shown that <xref:System.Text.StringBuilder> allocations are a significant contributor.</span></span>
  
### <a name="linq-and-lambdas"></a><span data-ttu-id="3c12d-244">LINQ a lambdas</span><span class="sxs-lookup"><span data-stu-id="3c12d-244">LINQ and lambdas</span></span>  
<span data-ttu-id="3c12d-245">Jazykově integrovaný dotaz (LINQ), ve spojení s výrazy lambda, je příkladem funkce produktivity.</span><span class="sxs-lookup"><span data-stu-id="3c12d-245">Language-Integrated Query (LINQ), in conjunction with lambda expressions, is an example of a productivity feature.</span></span> <span data-ttu-id="3c12d-246">Jeho použití však může mít významný vliv na výkon v průběhu času a může být nutné přepsat kód.</span><span class="sxs-lookup"><span data-stu-id="3c12d-246">However, its use may have a significant impact on performance over time, and you might find you need to rewrite your code.</span></span>
  
 <span data-ttu-id="3c12d-247">**Příklad 5: Lambdas, Seznam\<T>\<a IEnumerable T>**</span><span class="sxs-lookup"><span data-stu-id="3c12d-247">**Example 5: Lambdas, List\<T>, and IEnumerable\<T>**</span></span>  
  
 <span data-ttu-id="3c12d-248">Tento příklad používá [linq a kód funkčního stylu](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) k nalezení symbolu v modelu kompilátoru, který je uveden v řetězci názvu:</span><span class="sxs-lookup"><span data-stu-id="3c12d-248">This example uses [LINQ and functional style code](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) to find a symbol in the compiler’s model, given a name string:</span></span>  
  
```csharp  
class Symbol {  
    public string Name { get; private set; }  
    /*...*/  
}  
  
class Compiler {  
    private List<Symbol> symbols;  
    public Symbol FindMatchingSymbol(string name)  
    {  
        return symbols.FirstOrDefault(s => s.Name == name);  
    }  
}  
```  
  
 <span data-ttu-id="3c12d-249">Nový kompilátor a prostředí IDE `FindMatchingSymbol()` postavené na něm volání velmi často a existuje několik skrytých přidělení v této funkce jeden řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="3c12d-249">The new compiler and the IDE experiences built on it call `FindMatchingSymbol()` very frequently, and there are several hidden allocations in this function’s single line of code.</span></span> <span data-ttu-id="3c12d-250">Chcete-li zkontrolovat tyto přidělení, nejprve rozdělit funkci jeden řádek kódu do dvou řádků:</span><span class="sxs-lookup"><span data-stu-id="3c12d-250">To examine those allocations, first split the function’s single line of code into two lines:</span></span>  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 <span data-ttu-id="3c12d-251">V prvním řádku [lambda výraz](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [zavře přes](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) `name`místní proměnné .</span><span class="sxs-lookup"><span data-stu-id="3c12d-251">In the first line, the [lambda expression](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [closes over](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) the local variable `name`.</span></span> <span data-ttu-id="3c12d-252">To znamená, že kromě přidělení objektu pro [delegáta,](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) který `predicate` drží, kód přiděluje statickou `name`třídu pro uložení prostředí, které zachycuje hodnotu .</span><span class="sxs-lookup"><span data-stu-id="3c12d-252">This means that in addition to allocating an object for the [delegate](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) that `predicate` holds, the code allocates a static class to hold the environment that captures the value of `name`.</span></span> <span data-ttu-id="3c12d-253">Kompilátor generuje kód takto:</span><span class="sxs-lookup"><span data-stu-id="3c12d-253">The compiler generates code like the following:</span></span>  
  
```csharp  
// Compiler-generated class to hold environment state for lambda  
private class Lambda1Environment  
{  
    public string capturedName;  
    public bool Evaluate(Symbol s)  
    {  
        return s.Name == this.capturedName;  
    }  
}  
  
// Expanded Func<Symbol, bool> predicate = s => s.Name == name;  
Lambda1Environment l = new Lambda1Environment() { capturedName = name };  
var predicate = new Func<Symbol, bool>(l.Evaluate);  
```  
  
 <span data-ttu-id="3c12d-254">Dvě `new` přidělení (jeden pro třídu prostředí a jeden pro delegáta) jsou nyní explicitní.</span><span class="sxs-lookup"><span data-stu-id="3c12d-254">The two `new` allocations (one for the environment class and one for the delegate) are explicit now.</span></span>
  
 <span data-ttu-id="3c12d-255">Nyní se podívejte `FirstOrDefault`na volání do .</span><span class="sxs-lookup"><span data-stu-id="3c12d-255">Now look at the call to `FirstOrDefault`.</span></span> <span data-ttu-id="3c12d-256">Tato metoda rozšíření <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> na typu vznikne přidělení příliš.</span><span class="sxs-lookup"><span data-stu-id="3c12d-256">This extension method on the <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> type incurs an allocation too.</span></span> <span data-ttu-id="3c12d-257">Protože `FirstOrDefault` má <xref:System.Collections.Generic.IEnumerable%601> objekt jako svůj první argument, můžete rozšířit volání na následující kód (zjednodušený bit pro diskusi):</span><span class="sxs-lookup"><span data-stu-id="3c12d-257">Because `FirstOrDefault` takes an <xref:System.Collections.Generic.IEnumerable%601> object as its first argument, you can expand the call to the following code (simplified a bit for discussion):</span></span>  
  
```csharp  
// Expanded return symbols.FirstOrDefault(predicate) ...
     IEnumerable<Symbol> enumerable = symbols;  
     IEnumerator<Symbol> enumerator = enumerable.GetEnumerator();  
     while(enumerator.MoveNext())  
     {  
         if (predicate(enumerator.Current))  
             return enumerator.Current;  
     }  
     return default(Symbol);  
```  
  
 <span data-ttu-id="3c12d-258">Proměnná `symbols` má <xref:System.Collections.Generic.List%601>typ .</span><span class="sxs-lookup"><span data-stu-id="3c12d-258">The `symbols` variable has type <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="3c12d-259">Typ <xref:System.Collections.Generic.List%601> kolekce <xref:System.Collections.Generic.IEnumerable%601> implementuje a chytře definuje čítač (rozhraní),<xref:System.Collections.Generic.IEnumerator%601> který <xref:System.Collections.Generic.List%601> implementuje `struct`s .</span><span class="sxs-lookup"><span data-stu-id="3c12d-259">The <xref:System.Collections.Generic.List%601> collection type implements <xref:System.Collections.Generic.IEnumerable%601> and cleverly defines an enumerator (<xref:System.Collections.Generic.IEnumerator%601> interface) that <xref:System.Collections.Generic.List%601> implements with a `struct`.</span></span> <span data-ttu-id="3c12d-260">Použití struktury namísto třídy znamená, že se obvykle vyhnete přidělení haldy, což může ovlivnit výkon uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="3c12d-260">Using a structure instead of a class means that you usually avoid any heap allocations, which, in turn, can affect garbage collection performance.</span></span> <span data-ttu-id="3c12d-261">Čítače výčtu se obvykle používají `foreach` s smyčkou jazyka, který používá strukturu čítače výčtu, jak je vrácena v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="3c12d-261">Enumerators are typically used with the language’s `foreach` loop, which uses the enumerator structure as it is returned on the call stack.</span></span> <span data-ttu-id="3c12d-262">Zvýšení ukazatele zásobníku volání, aby se uvolnilo místo pro objekt, nemá vliv na gc tak, jak přidělení haldy nemá.</span><span class="sxs-lookup"><span data-stu-id="3c12d-262">Incrementing the call stack pointer to make room for an object does not affect GC the way a heap allocation does.</span></span>
  
 <span data-ttu-id="3c12d-263">V případě rozšířenévolání `FirstOrDefault` kód musí volat `GetEnumerator()` na <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="3c12d-263">In the case of the expanded `FirstOrDefault` call, the code needs to call `GetEnumerator()` on an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="3c12d-264">Přiřazení `symbols` `enumerable` proměnné typu `IEnumerable<Symbol>` ztratí informace o tom, že <xref:System.Collections.Generic.List%601>skutečný objekt je .</span><span class="sxs-lookup"><span data-stu-id="3c12d-264">Assigning `symbols` to the `enumerable` variable of type `IEnumerable<Symbol>` loses the information that the actual object is a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="3c12d-265">To znamená, že když kód načte `enumerable.GetEnumerator()`čítač s , rozhraní .NET Framework `enumerator` musí zaokřovat vrácenou strukturu a přiřadit ji proměnné.</span><span class="sxs-lookup"><span data-stu-id="3c12d-265">This means that when the code fetches the enumerator with `enumerable.GetEnumerator()`, the .NET Framework has to box the returned structure to assign it to the `enumerator` variable.</span></span>
  
 <span data-ttu-id="3c12d-266">**Oprava například 5**</span><span class="sxs-lookup"><span data-stu-id="3c12d-266">**Fix for example 5**</span></span>  
  
 <span data-ttu-id="3c12d-267">Oprava je přepsat `FindMatchingSymbol` takto, nahrazení jeho jeden řádek kódu se šesti řádky kódu, které jsou stále stručné, snadno čitelné a srozumitelné a snadno udržovatelné:</span><span class="sxs-lookup"><span data-stu-id="3c12d-267">The fix is to rewrite `FindMatchingSymbol` as follows, replacing its single line of code with six lines of code that are still concise, easy to read and understand, and easy to maintain:</span></span>  
  
```csharp  
public Symbol FindMatchingSymbol(string name)  
    {  
        foreach (Symbol s in symbols)  
        {  
            if (s.Name == name)  
                return s;  
        }  
        return null;  
    }  
```  
  
 <span data-ttu-id="3c12d-268">Tento kód nepoužívá linq rozšíření metody, lambdas nebo čítače výčtu a vznikne žádné přidělení.</span><span class="sxs-lookup"><span data-stu-id="3c12d-268">This code doesn’t use LINQ extension methods, lambdas, or enumerators, and it incurs no allocations.</span></span> <span data-ttu-id="3c12d-269">Neexistují žádné přidělení, protože kompilátor `symbols` může vidět, že kolekce je <xref:System.Collections.Generic.List%601> a může vázat výsledný čítač výčtu (struktura) na místní proměnnou se správným typem, aby se zabránilo zabalení.</span><span class="sxs-lookup"><span data-stu-id="3c12d-269">There are no allocations because the compiler can see that the `symbols` collection is a <xref:System.Collections.Generic.List%601> and can bind the resulting enumerator (a structure) to a local variable with the right type to avoid boxing.</span></span> <span data-ttu-id="3c12d-270">Původní verze této funkce byla skvělým příkladem expresivní výkon Jazyka C# a produktivitu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3c12d-270">The original version of this function was a great example of the expressive power of C# and the productivity of the .NET Framework.</span></span> <span data-ttu-id="3c12d-271">Tato nová a efektivnější verze zachovává tyto vlastnosti bez přidání jakéhokoli složitého kódu pro údržbu.</span><span class="sxs-lookup"><span data-stu-id="3c12d-271">This new and more efficient version preserves those qualities without adding any complex code to maintain.</span></span>
  
### <a name="async-method-caching"></a><span data-ttu-id="3c12d-272">Ukládání do mezipaměti asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="3c12d-272">Async method caching</span></span>  

<span data-ttu-id="3c12d-273">Následující příklad ukazuje běžný problém při pokusu o použití výsledků v mezipaměti v [asynchronní](../../csharp/programming-guide/concepts/async/index.md) metodě.</span><span class="sxs-lookup"><span data-stu-id="3c12d-273">The next example shows a common problem when you try to use cached results in an [async](../../csharp/programming-guide/concepts/async/index.md) method.</span></span>
  
 <span data-ttu-id="3c12d-274">**Příklad 6: ukládání do mezipaměti v asynchronních metodách**</span><span class="sxs-lookup"><span data-stu-id="3c12d-274">**Example 6: caching in async methods**</span></span>  
  
 <span data-ttu-id="3c12d-275">Visual Studio IDE funkce postavené na nové kompilátory Jazyka C# a Visual Basic často načítat stromy syntaxe a kompilátory použít asynchronní při tom, aby Visual Studio reagovat.</span><span class="sxs-lookup"><span data-stu-id="3c12d-275">The Visual Studio IDE features built on the new C# and Visual Basic compilers frequently fetch syntax trees, and the compilers use async when doing so to keep Visual Studio responsive.</span></span> <span data-ttu-id="3c12d-276">Zde je první verze kódu, který můžete napsat, abyste získali strom syntaxe:</span><span class="sxs-lookup"><span data-stu-id="3c12d-276">Here’s the first version of the code you might write to get a syntax tree:</span></span>  
  
```csharp  
class SyntaxTree { /*...*/ }  
  
class Parser { /*...*/  
    public SyntaxTree Syntax { get; }  
    public Task ParseSourceCode() { /*...*/ }  
}  
  
class Compilation { /*...*/  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 <span data-ttu-id="3c12d-277">Můžete vidět, `GetSyntaxTreeAsync()` že volání konkretizuje `Parser`, analyzuje kód <xref:System.Threading.Tasks.Task> a `Task<SyntaxTree>`pak vrátí objekt, .</span><span class="sxs-lookup"><span data-stu-id="3c12d-277">You can see that calling `GetSyntaxTreeAsync()` instantiates a `Parser`, parses the code, and then returns a <xref:System.Threading.Tasks.Task> object, `Task<SyntaxTree>`.</span></span> <span data-ttu-id="3c12d-278">Nákladné část je přidělení `Parser` instance a analýzy kódu.</span><span class="sxs-lookup"><span data-stu-id="3c12d-278">The expensive part is allocating the `Parser` instance and parsing the code.</span></span> <span data-ttu-id="3c12d-279">Funkce vrátí <xref:System.Threading.Tasks.Task> tak, aby volající můžete čekat na práci analýzy a uvolnit vlákno uživatelského rozhraní, které mají být citlivé na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="3c12d-279">The function returns a <xref:System.Threading.Tasks.Task> so that callers can await the parsing work and free the UI thread to be responsive to user input.</span></span>
  
 <span data-ttu-id="3c12d-280">Několik funkcí sady Visual Studio se může pokusit získat stejný strom syntaxe, takže můžete napsat následující kód pro uložení výsledku analýzy do mezipaměti, abyste ušetřili čas a přidělení.</span><span class="sxs-lookup"><span data-stu-id="3c12d-280">Several Visual Studio features might try to get the same syntax tree, so you might write the following code to cache the parsing result to save time and allocations.</span></span> <span data-ttu-id="3c12d-281">Tento kód však vzniká přidělení:</span><span class="sxs-lookup"><span data-stu-id="3c12d-281">However, this code incurs an allocation:</span></span>  
  
```csharp  
class Compilation { /*...*/  
  
    private SyntaxTree cachedResult;  
  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        if (this.cachedResult == null)  
        {  
            var parser = new Parser(); // allocation  
            await parser.ParseSourceCode(); // expensive  
            this.cachedResult = parser.Syntax;  
        }  
        return this.cachedResult;  
    }  
}  
```  
  
 <span data-ttu-id="3c12d-282">Uvidíte, že nový kód s `SyntaxTree` ukládáním `cachedResult`do mezipaměti má pole s názvem .</span><span class="sxs-lookup"><span data-stu-id="3c12d-282">You see that the new code with caching has a `SyntaxTree` field named `cachedResult`.</span></span> <span data-ttu-id="3c12d-283">Pokud je toto `GetSyntaxTreeAsync()` pole null, provádí práci a ukládá výsledek do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="3c12d-283">When this field is null, `GetSyntaxTreeAsync()` does the work and saves the result in the cache.</span></span> <span data-ttu-id="3c12d-284">`GetSyntaxTreeAsync()`vrátí `SyntaxTree` objekt.</span><span class="sxs-lookup"><span data-stu-id="3c12d-284">`GetSyntaxTreeAsync()` returns the `SyntaxTree` object.</span></span> <span data-ttu-id="3c12d-285">Problém je, že pokud `async` máte `Task<SyntaxTree>`funkci typu a vrátíte `SyntaxTree`hodnotu typu , kompilátor vydává kód pro `Task<SyntaxTree>.FromResult()`přidělení Task uchovávat výsledek (pomocí ).</span><span class="sxs-lookup"><span data-stu-id="3c12d-285">The problem is that when you have an `async` function of type `Task<SyntaxTree>`, and you return a value of type `SyntaxTree`, the compiler emits code to allocate a Task to hold the result (by using `Task<SyntaxTree>.FromResult()`).</span></span> <span data-ttu-id="3c12d-286">Úkol je označen jako dokončený a výsledek je okamžitě k dispozici.</span><span class="sxs-lookup"><span data-stu-id="3c12d-286">The Task is marked as completed, and the result is immediately available.</span></span> <span data-ttu-id="3c12d-287">V kódu pro nové kompilátory objekty, <xref:System.Threading.Tasks.Task> které již byly dokončeny došlo tak často, že oprava těchto přidělení výrazně zlepšila odezvu.</span><span class="sxs-lookup"><span data-stu-id="3c12d-287">In the code for the new compilers, <xref:System.Threading.Tasks.Task> objects that were already completed occurred so often that fixing these allocations improved responsiveness noticeably.</span></span>
  
 <span data-ttu-id="3c12d-288">**Oprava například 6**</span><span class="sxs-lookup"><span data-stu-id="3c12d-288">**Fix for example 6**</span></span>  
  
 <span data-ttu-id="3c12d-289">Chcete-li <xref:System.Threading.Tasks.Task> odebrat dokončené přidělení, můžete uložit objekt Task do mezipaměti s dokončeným výsledkem:</span><span class="sxs-lookup"><span data-stu-id="3c12d-289">To remove the completed <xref:System.Threading.Tasks.Task> allocation, you can cache the Task object with the completed result:</span></span>  
  
```csharp  
class Compilation { /*...*/  
  
    private Task<SyntaxTree> cachedResult;  
  
    public Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        return this.cachedResult ??
               (this.cachedResult = GetSyntaxTreeUncachedAsync());  
    }  
  
    private async Task<SyntaxTree> GetSyntaxTreeUncachedAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 <span data-ttu-id="3c12d-290">Tento kód změní `cachedResult` typ `Task<SyntaxTree>` do a `async` používá pomocnou funkci, `GetSyntaxTreeAsync()`která obsahuje původní kód z aplikace .</span><span class="sxs-lookup"><span data-stu-id="3c12d-290">This code changes the type of `cachedResult` to `Task<SyntaxTree>` and employs an `async` helper function that holds the original code from `GetSyntaxTreeAsync()`.</span></span> <span data-ttu-id="3c12d-291">`GetSyntaxTreeAsync()`Nyní používá [null coalescing](../../csharp/language-reference/operators/null-coalescing-operator.md) `cachedResult` operátor vrátit, pokud není null.</span><span class="sxs-lookup"><span data-stu-id="3c12d-291">`GetSyntaxTreeAsync()` now uses the [null coalescing operator](../../csharp/language-reference/operators/null-coalescing-operator.md) to return `cachedResult` if it isn't null.</span></span> <span data-ttu-id="3c12d-292">Pokud `cachedResult` je null, pak `GetSyntaxTreeAsync()` volá `GetSyntaxTreeUncachedAsync()` a ukládá výsledek.</span><span class="sxs-lookup"><span data-stu-id="3c12d-292">If `cachedResult` is null, then `GetSyntaxTreeAsync()` calls `GetSyntaxTreeUncachedAsync()` and caches the result.</span></span> <span data-ttu-id="3c12d-293">Všimněte `GetSyntaxTreeAsync()` si, že nečeká `GetSyntaxTreeUncachedAsync()` volání jako kód by normálně.</span><span class="sxs-lookup"><span data-stu-id="3c12d-293">Notice that `GetSyntaxTreeAsync()` doesn’t await the call to `GetSyntaxTreeUncachedAsync()` as the code would normally.</span></span> <span data-ttu-id="3c12d-294">Nepoužíváte await znamená, že když `GetSyntaxTreeUncachedAsync()` vrátí svůj <xref:System.Threading.Tasks.Task> objekt, `GetSyntaxTreeAsync()` okamžitě vrátí <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="3c12d-294">Not using await means that when `GetSyntaxTreeUncachedAsync()` returns its <xref:System.Threading.Tasks.Task> object, `GetSyntaxTreeAsync()` immediately returns the <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="3c12d-295">Nyní je výsledek uložený <xref:System.Threading.Tasks.Task>v mezipaměti , takže neexistují žádné přidělení vrátit výsledek mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="3c12d-295">Now, the cached result is a <xref:System.Threading.Tasks.Task>, so there are no allocations to return the cached result.</span></span>
  
### <a name="additional-considerations"></a><span data-ttu-id="3c12d-296">Další aspekty</span><span class="sxs-lookup"><span data-stu-id="3c12d-296">Additional considerations</span></span>  
 <span data-ttu-id="3c12d-297">Tady je několik dalších bodů o potenciálních problémech ve velkých aplikacích nebo aplikacích, které zpracovávají velké množství dat.</span><span class="sxs-lookup"><span data-stu-id="3c12d-297">Here are a few more points about potential problems in large apps or apps that process a lot of data.</span></span>
  
 <span data-ttu-id="3c12d-298">**Slovníky**</span><span class="sxs-lookup"><span data-stu-id="3c12d-298">**Dictionaries**</span></span>  
  
 <span data-ttu-id="3c12d-299">Slovníky se používají všudypřítomně v mnoha programech, a když slovníky jsou velmi pohodlné a ze své podstaty efektivní.</span><span class="sxs-lookup"><span data-stu-id="3c12d-299">Dictionaries are used ubiquitously in many programs, and though dictionaries are very convenient and inherently efficient.</span></span> <span data-ttu-id="3c12d-300">Často se však používají nevhodně.</span><span class="sxs-lookup"><span data-stu-id="3c12d-300">However, they’re often used inappropriately.</span></span> <span data-ttu-id="3c12d-301">V sadě Visual Studio a nové kompilátory analýza ukazuje, že mnoho slovníků obsahovaljeden prvek nebo byly prázdné.</span><span class="sxs-lookup"><span data-stu-id="3c12d-301">In Visual Studio and the new compilers, analysis shows that many of the dictionaries contained a single element or were empty.</span></span> <span data-ttu-id="3c12d-302">Prázdné <xref:System.Collections.Generic.Dictionary%602> má deset polí a zabírá 48 bajtů na haldě na x86 počítači.</span><span class="sxs-lookup"><span data-stu-id="3c12d-302">An empty <xref:System.Collections.Generic.Dictionary%602> has ten fields and occupies 48 bytes on the heap on an x86 machine.</span></span> <span data-ttu-id="3c12d-303">Slovníky jsou skvělé, když potřebujete mapování nebo asociativní strukturu dat s konstantní masovou vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="3c12d-303">Dictionaries are great when you need a mapping or associative data structure with constant-time lookup.</span></span> <span data-ttu-id="3c12d-304">Pokud však máte jen několik prvků, ztrácíte spoustu místa pomocí slovníku.</span><span class="sxs-lookup"><span data-stu-id="3c12d-304">However, when you have only a few elements, you waste a lot of space by using a dictionary.</span></span> <span data-ttu-id="3c12d-305">Místo toho, například, můžete iterativně `List<KeyValuePair\<K,V>>`podívat přes , stejně rychle.</span><span class="sxs-lookup"><span data-stu-id="3c12d-305">Instead, for example, you could iteratively look through a `List<KeyValuePair\<K,V>>`, just as fast.</span></span> <span data-ttu-id="3c12d-306">Pokud používáte slovník pouze k načtení dat a potom číst z něj (velmi běžný vzor), pomocí seřazené pole s N(log(N)) vyhledávání může být téměř stejně rychle, v závislosti na počtu prvků, které používáte.</span><span class="sxs-lookup"><span data-stu-id="3c12d-306">If you use a dictionary only to load it with data and then read from it (a very common pattern), using a sorted array with an N(log(N)) lookup might be nearly as fast, depending on the number of elements you're using.</span></span>
  
 <span data-ttu-id="3c12d-307">**Třídy vs. struktury**</span><span class="sxs-lookup"><span data-stu-id="3c12d-307">**Classes vs. structures**</span></span>  
  
 <span data-ttu-id="3c12d-308">Třídy a struktury svým způsobem poskytují klasický kompromis prostor/čas pro ladění aplikací.</span><span class="sxs-lookup"><span data-stu-id="3c12d-308">In a way, classes and structures provide a classic space/time tradeoff for tuning your apps.</span></span> <span data-ttu-id="3c12d-309">Třídy vynakládat 12 bajtů režie na x86 počítač i v případě, že nemají žádná pole, ale jsou levné předat, protože trvá pouze ukazatel odkazovat na instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="3c12d-309">Classes incur 12 bytes of overhead on an x86 machine even if they have no fields, but they are inexpensive to pass around because it only takes a pointer to refer to a class instance.</span></span> <span data-ttu-id="3c12d-310">Struktury nevznikají žádné přidělení haldy, pokud nejsou v rámečku, ale při předání velkých struktur jako argumenty funkce nebo vrácené hodnoty, trvá čas procesoru atomicky zkopírovat všechny datové členy struktur.</span><span class="sxs-lookup"><span data-stu-id="3c12d-310">Structures incur no heap allocations if they aren’t boxed, but when you pass large structures as function arguments or return values, it takes CPU time to atomically copy all the data members of the structures.</span></span> <span data-ttu-id="3c12d-311">Dávejte pozor na opakované volání vlastností, které vracejí struktury, a ukládat hodnotu vlastnosti do mezipaměti v místní proměnné, aby se zabránilo nadměrnému kopírování dat.</span><span class="sxs-lookup"><span data-stu-id="3c12d-311">Watch out for repeated calls to properties that return structures, and cache the property’s value in a local variable to avoid excessive data copying.</span></span>
  
 <span data-ttu-id="3c12d-312">**Caches**</span><span class="sxs-lookup"><span data-stu-id="3c12d-312">**Caches**</span></span>  
  
 <span data-ttu-id="3c12d-313">Běžným trikem s výkonem je ukládání výsledků do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="3c12d-313">A common performance trick is to cache results.</span></span> <span data-ttu-id="3c12d-314">Mezipaměť bez omezení velikosti nebo zásady vyřazení však může být nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="3c12d-314">However, a cache without a size cap or disposal policy can be a memory leak.</span></span> <span data-ttu-id="3c12d-315">Při zpracování velkého množství dat, pokud podržíte velké množství paměti v mezipaměti, můžete způsobit uvolňování paměti přepsat výhody vyhledávání v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="3c12d-315">When processing large amounts of data, if you hold on to a lot of memory in caches, you can cause garbage collection to override the benefits of your cached lookups.</span></span>
  
 <span data-ttu-id="3c12d-316">V tomto článku jsme diskutovali o tom, jak byste měli být vědomi příznaků kritického místa výkonu, které mohou ovlivnit odezvu vaší aplikace, zejména pro velké systémy nebo systémy, které zpracovávají velké množství dat.</span><span class="sxs-lookup"><span data-stu-id="3c12d-316">In this article, we discussed how you should be aware of performance bottleneck symptoms that can affect your app's responsiveness, especially for large systems or systems that process a large amount of data.</span></span> <span data-ttu-id="3c12d-317">Mezi běžné viníky patří boxování, manipulace s řetězci, LINQ a lambda, ukládání do mezipaměti v asynchronních metodách, ukládání do mezipaměti bez omezení velikosti nebo zásady vyřazení, nevhodné používání slovníků a předávání struktur.</span><span class="sxs-lookup"><span data-stu-id="3c12d-317">Common culprits include boxing, string manipulations, LINQ and lambda, caching in async methods, caching without a size limit or disposal policy, inappropriate use of dictionaries, and passing around structures.</span></span> <span data-ttu-id="3c12d-318">Mějte na paměti čtyři fakta pro ladění aplikací:</span><span class="sxs-lookup"><span data-stu-id="3c12d-318">Keep in mind the four facts for tuning your apps:</span></span>  
  
- <span data-ttu-id="3c12d-319">Neoptimalizujte předčasně – buďte produktivní a vylaďte aplikaci, když naprvní místo najdete problémy.</span><span class="sxs-lookup"><span data-stu-id="3c12d-319">Don’t prematurely optimize – be productive and tune your app when you spot problems.</span></span>
  
- <span data-ttu-id="3c12d-320">Profily nelžou - hádáte, pokud neměříte.</span><span class="sxs-lookup"><span data-stu-id="3c12d-320">Profiles don’t lie – you’re guessing if you’re not measuring.</span></span>
  
- <span data-ttu-id="3c12d-321">Dobré nástroje, aby celý rozdíl - download PerfView a vyzkoušet.</span><span class="sxs-lookup"><span data-stu-id="3c12d-321">Good tools make all the difference – download PerfView and try it out.</span></span>
  
- <span data-ttu-id="3c12d-322">Je to všechno o přidělení – to je místo, kde tým platformy kompilátoru strávil většinu svého času zlepšováním výkonu nových kompilátorů.</span><span class="sxs-lookup"><span data-stu-id="3c12d-322">It's all about allocations – that is where the compiler platform team spent most of their time improving the performance of the new compilers.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3c12d-323">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c12d-323">See also</span></span>

- [<span data-ttu-id="3c12d-324">Video z prezentace tohoto tématu</span><span class="sxs-lookup"><span data-stu-id="3c12d-324">Video of presentation of this topic</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [<span data-ttu-id="3c12d-325">Začátečníci Průvodce profilování výkonu</span><span class="sxs-lookup"><span data-stu-id="3c12d-325">Beginners Guide to Performance Profiling</span></span>](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [<span data-ttu-id="3c12d-326">Výkon</span><span class="sxs-lookup"><span data-stu-id="3c12d-326">Performance</span></span>](index.md)
- <span data-ttu-id="3c12d-327">[Tipy pro zvýšení výkonu rozhraní .NET](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))</span><span class="sxs-lookup"><span data-stu-id="3c12d-327">[.NET Performance Tips](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))</span></span>
- [<span data-ttu-id="3c12d-328">Kanál 9 PerfView výukové programy</span><span class="sxs-lookup"><span data-stu-id="3c12d-328">Channel 9 PerfView tutorials</span></span>](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [<span data-ttu-id="3c12d-329">Sada SDK platformy kompilátoru ROZHRANÍ .NET</span><span class="sxs-lookup"><span data-stu-id="3c12d-329">The .NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="3c12d-330">dotnet/roslyn repo na GitHubu</span><span class="sxs-lookup"><span data-stu-id="3c12d-330">dotnet/roslyn repo on GitHub</span></span>](https://github.com/dotnet/roslyn)
