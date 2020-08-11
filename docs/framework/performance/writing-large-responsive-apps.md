---
title: Psaní velkých a pohotově reagujících aplikací .NET Framework
description: Vytvářejte velké, reagující aplikace .NET nebo aplikace, které zpracovávají velké objemy dat, jako jsou například soubory nebo databáze.
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a9f5d50ad78b2b0bef0ece3c4fce47d2925aca5
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063754"
---
# <a name="writing-large-responsive-net-framework-apps"></a><span data-ttu-id="98d6a-103">Psaní velkých a pohotově reagujících aplikací .NET Framework</span><span class="sxs-lookup"><span data-stu-id="98d6a-103">Writing Large, Responsive .NET Framework Apps</span></span>

<span data-ttu-id="98d6a-104">Tento článek poskytuje tipy pro zlepšení výkonu rozsáhlých aplikací .NET Framework, nebo aplikací, které zpracovávají velké objemy dat, jako jsou soubory nebo databáze.</span><span class="sxs-lookup"><span data-stu-id="98d6a-104">This article provides tips for improving the performance of large .NET Framework apps, or apps that process a large amount of data such as files or databases.</span></span> <span data-ttu-id="98d6a-105">Tyto tipy přicházejí z přepisu kompilátorů C# a Visual Basic ve spravovaném kódu a tento článek obsahuje několik reálných příkladů z kompilátoru C#.</span><span class="sxs-lookup"><span data-stu-id="98d6a-105">These tips come from rewriting the C# and Visual Basic compilers in managed code, and this article includes several real examples from the C# compiler.</span></span>
  
<span data-ttu-id="98d6a-106">.NET Framework je vysoce produktivní pro vytváření aplikací.</span><span class="sxs-lookup"><span data-stu-id="98d6a-106">The .NET Framework is highly productive for building apps.</span></span> <span data-ttu-id="98d6a-107">Výkonné a bezpečné jazyky a rozsáhlá kolekce knihoven usnadňují vytváření aplikací pro vysoce ovocné účely.</span><span class="sxs-lookup"><span data-stu-id="98d6a-107">Powerful and safe languages and a rich collection of libraries make app building highly fruitful.</span></span> <span data-ttu-id="98d6a-108">Přináší ale odpovědnost za skvělou produktivitu.</span><span class="sxs-lookup"><span data-stu-id="98d6a-108">However, with great productivity comes responsibility.</span></span> <span data-ttu-id="98d6a-109">Měli byste použít veškerou sílu .NET Framework, ale v případě potřeby připravujte výkon svého kódu.</span><span class="sxs-lookup"><span data-stu-id="98d6a-109">You should use all the power of the .NET Framework, but be prepared to tune your code’s performance when needed.</span></span>
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a><span data-ttu-id="98d6a-110">Proč se nový výkon kompilátoru vztahuje na vaši aplikaci</span><span class="sxs-lookup"><span data-stu-id="98d6a-110">Why the new compiler performance applies to your app</span></span>  
 <span data-ttu-id="98d6a-111">Tým .NET Compiler Platform ("Roslyn") přepsal kompilátory jazyka C# a Visual Basic ve spravovaném kódu, aby poskytoval nová rozhraní API pro modelování a analýzu kódu, vytváření nástrojů a povolení mnohem rozsáhlejšího prostředí s kódováním kódu v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="98d6a-111">The .NET Compiler Platform ("Roslyn") team rewrote the C# and Visual Basic compilers in managed code to provide new APIs for modeling and analyzing code, building tools, and enabling much richer, code-aware experiences in Visual Studio.</span></span> <span data-ttu-id="98d6a-112">Přepisování kompilátorů a sestavování prostředí sady Visual Studio na nových kompilátorech odhalilo užitečné přehledy výkonu, které platí pro všechny velké .NET Framework aplikace nebo aplikace, které zpracovávají velké množství dat.</span><span class="sxs-lookup"><span data-stu-id="98d6a-112">Rewriting the compilers and building Visual Studio experiences on the new compilers revealed useful performance insights that are applicable to any large .NET Framework app or any app that processes a lot of data.</span></span> <span data-ttu-id="98d6a-113">Nemusíte znát kompilátory, abyste mohli využívat přehledy a příklady z kompilátoru C#.</span><span class="sxs-lookup"><span data-stu-id="98d6a-113">You don't need to know about compilers to take advantage of the insights and examples from the C# compiler.</span></span>
  
 <span data-ttu-id="98d6a-114">Visual Studio používá rozhraní API kompilátoru k sestavení všech funkcí technologie IntelliSense, které uživatelé mají rádi, jako je například obarvení identifikátorů a klíčových slov, seznamy pro doplňování syntaxe, vlnovky pro chyby, tipy k parametrům, problémy s kódem a akce kódu.</span><span class="sxs-lookup"><span data-stu-id="98d6a-114">Visual Studio uses the compiler APIs to build all the IntelliSense features that users love, such as colorization of identifiers and keywords, syntax completion lists, squiggles for errors, parameter tips, code issues, and code actions.</span></span> <span data-ttu-id="98d6a-115">Visual Studio poskytuje tuto technickou podporu, zatímco vývojáři zadávají a mění kód a Visual Studio musí zůstat reagovat, zatímco kompilátor průběžně modeluje úpravy vývojářů kódu.</span><span class="sxs-lookup"><span data-stu-id="98d6a-115">Visual Studio provides this help while developers are typing and changing their code, and Visual Studio must remain responsive while the compiler continually models the code developers edit.</span></span>
  
 <span data-ttu-id="98d6a-116">Když koncoví uživatelé komunikují s vaší aplikací, očekávají, že budou reagovat.</span><span class="sxs-lookup"><span data-stu-id="98d6a-116">When your end users interact with your app, they expect it to be responsive.</span></span> <span data-ttu-id="98d6a-117">Psaní nebo zpracování příkazů by nikdy nemělo být blokované.</span><span class="sxs-lookup"><span data-stu-id="98d6a-117">Typing or command handling should never be blocked.</span></span> <span data-ttu-id="98d6a-118">V případě, že uživatel pokračuje v psaní, je nutné nápovědu rychle zobrazit nebo zadat.</span><span class="sxs-lookup"><span data-stu-id="98d6a-118">Help should pop up quickly or give up if the user continues typing.</span></span> <span data-ttu-id="98d6a-119">Vaše aplikace by se neměla blokovat vlákno uživatelského rozhraní s dlouhými výpočty, díky kterým se aplikace bude cítit pomalá.</span><span class="sxs-lookup"><span data-stu-id="98d6a-119">Your app should avoid blocking the UI thread with long computations that make the app feel sluggish.</span></span>
  
 <span data-ttu-id="98d6a-120">Další informace o kompilátorech Roslyn naleznete v sadě [SDK pro .NET Compiler Platform](../../csharp/roslyn-sdk/index.md).</span><span class="sxs-lookup"><span data-stu-id="98d6a-120">For more information about Roslyn compilers, see [The .NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md).</span></span>
  
## <a name="just-the-facts"></a><span data-ttu-id="98d6a-121">Jenom fakta</span><span class="sxs-lookup"><span data-stu-id="98d6a-121">Just the Facts</span></span>  
 <span data-ttu-id="98d6a-122">Při ladění výkonu a vytváření .NET Frameworkch aplikací s odezvou doporučujeme vzít v úvahu tato fakta.</span><span class="sxs-lookup"><span data-stu-id="98d6a-122">Consider these facts when tuning performance and creating responsive .NET Framework apps.</span></span>
  
### <a name="fact-1-dont-prematurely-optimize"></a><span data-ttu-id="98d6a-123">Fakt 1: nezralá optimalizace</span><span class="sxs-lookup"><span data-stu-id="98d6a-123">Fact 1: Don’t prematurely optimize</span></span>  
 <span data-ttu-id="98d6a-124">Psaní kódu, který je složitější než IT oddělení musí mít za následek údržbu, ladění a proleštění nákladů.</span><span class="sxs-lookup"><span data-stu-id="98d6a-124">Writing code that is more complex than it needs to be incurs maintenance, debugging, and polishing costs.</span></span> <span data-ttu-id="98d6a-125">Zkušení programátoři mají intuitivní podrobnější informace o řešení problémů s kódováním a psaní efektivnějšího kódu.</span><span class="sxs-lookup"><span data-stu-id="98d6a-125">Experienced programmers have an intuitive grasp of how to solve coding problems and write more efficient code.</span></span> <span data-ttu-id="98d6a-126">Někdy ale předčasně optimalizují svůj kód.</span><span class="sxs-lookup"><span data-stu-id="98d6a-126">However, they sometimes prematurely optimize their code.</span></span> <span data-ttu-id="98d6a-127">Například používají zatřiďovací tabulku, když by bylo stačit jednoduché pole, nebo použití složitého ukládání do mezipaměti, které by mohlo způsobit nevracení paměti místo pouhého přepočítání hodnot.</span><span class="sxs-lookup"><span data-stu-id="98d6a-127">For example, they use a hash table when a simple array would suffice, or use complicated caching that may leak memory instead of simply recomputing values.</span></span> <span data-ttu-id="98d6a-128">I v případě, že jste programátorem zkušeností, měli byste otestovat výkon a analyzovat kód při hledání problémů.</span><span class="sxs-lookup"><span data-stu-id="98d6a-128">Even if you’re an experience programmer, you should test for performance and analyze your code when you find issues.</span></span>
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a><span data-ttu-id="98d6a-129">Fakt 2: Pokud se neměříte, odhaduje se</span><span class="sxs-lookup"><span data-stu-id="98d6a-129">Fact 2: If you’re not measuring, you’re guessing</span></span>  
 <span data-ttu-id="98d6a-130">Profily a měření neleží.</span><span class="sxs-lookup"><span data-stu-id="98d6a-130">Profiles and measurements don’t lie.</span></span> <span data-ttu-id="98d6a-131">V části profily se dozvíte, jestli je procesor plně načtený nebo jestli jste zablokovali v/v disku.</span><span class="sxs-lookup"><span data-stu-id="98d6a-131">Profiles show you whether the CPU is fully loaded or whether you’re blocked on disk I/O.</span></span> <span data-ttu-id="98d6a-132">V části profily se dozvíte, jaký typ a kolik paměti přidělujete a jestli váš procesor stráví spoustu času v [uvolňování paměti](../../standard/garbage-collection/index.md) (GC).</span><span class="sxs-lookup"><span data-stu-id="98d6a-132">Profiles tell you what kind and how much memory you’re allocating and whether your CPU is spending a lot of time in [garbage collection](../../standard/garbage-collection/index.md) (GC).</span></span>
  
 <span data-ttu-id="98d6a-133">Měli byste nastavit cíle výkonu pro klíčové zkušenosti zákazníků a scénáře v aplikaci a zapsat testy pro měření výkonu.</span><span class="sxs-lookup"><span data-stu-id="98d6a-133">You should set performance goals for key customer experiences or scenarios in your app and write tests to measure performance.</span></span> <span data-ttu-id="98d6a-134">Prozkoumat neúspěšné testy pomocí vědecké metody: pomocí profilů vás povedete, vyslovují, co problém může být, a otestování své hypotézy pomocí experimentu nebo změny kódu.</span><span class="sxs-lookup"><span data-stu-id="98d6a-134">Investigate failing tests by applying the scientific method: use profiles to guide you, hypothesize what the issue might be, and test your hypothesis with an experiment or code change.</span></span> <span data-ttu-id="98d6a-135">Pomocí pravidelného testování můžete stanovit základní měření výkonu směrného plánu, abyste mohli izolovat změny, které způsobují regrese ve výkonu.</span><span class="sxs-lookup"><span data-stu-id="98d6a-135">Establish baseline performance measurements over time with regular testing, so you can isolate changes that cause regressions in performance.</span></span> <span data-ttu-id="98d6a-136">Tím, že se přiblížíte k výkonu v rámci striktního způsobu, se vyhnete plýtvání časem s aktualizacemi kódu, které nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="98d6a-136">By approaching performance work in a rigorous way, you’ll avoid wasting time with code updates you don’t need.</span></span>
  
### <a name="fact-3-good-tools-make-all-the-difference"></a><span data-ttu-id="98d6a-137">Fakt 3: dobré nástroje vedou ke všem rozdílům</span><span class="sxs-lookup"><span data-stu-id="98d6a-137">Fact 3: Good tools make all the difference</span></span>  
 <span data-ttu-id="98d6a-138">Kvalitní nástroje umožňují rychle přejít k největším problémům s výkonem (procesor, paměť nebo disk) a pomůžou vám najít kód, který způsobuje Tato kritická místa.</span><span class="sxs-lookup"><span data-stu-id="98d6a-138">Good tools let you drill quickly into the biggest performance issues (CPU, memory, or disk) and help you locate the code that causes those bottlenecks.</span></span> <span data-ttu-id="98d6a-139">Společnost Microsoft dodává řadu nástrojů pro výkon, jako je například [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) a [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span><span class="sxs-lookup"><span data-stu-id="98d6a-139">Microsoft ships a variety of performance tools such as [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) and [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span></span>
  
 <span data-ttu-id="98d6a-140">PerfView je bezplatný a úžasné výkonný nástroj, který vám pomůže soustředit se na hloubkové problémy, jako jsou vstupně-výstupní operace disku, události GC a paměť.</span><span class="sxs-lookup"><span data-stu-id="98d6a-140">PerfView is a free and amazingly powerful tool that helps you focus on deep issues such as disk I/O, GC events, and memory.</span></span> <span data-ttu-id="98d6a-141">Můžete zachytit události trasování událostí souvisejících s výkonem [pro Windows](../wcf/samples/etw-tracing.md) (ETW) a snadno zobrazit jednotlivé aplikace, jednotlivé procesy, balíčky a informace o vláknech.</span><span class="sxs-lookup"><span data-stu-id="98d6a-141">You can capture performance-related [Event Tracing for Windows](../wcf/samples/etw-tracing.md) (ETW) events and view easily per app, per process, per stack, and per thread information.</span></span> <span data-ttu-id="98d6a-142">PerfView ukazuje, kolik paměti a jaký typ paměti vaše aplikace přiděluje a které funkce nebo zásobníky volání přispívají k tomu, kolik je přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="98d6a-142">PerfView shows you how much and what kind of memory your app allocates, and which functions or call stacks contribute how much to the memory allocations.</span></span> <span data-ttu-id="98d6a-143">Podrobnosti najdete v tématech s bohatou nápovědu, ukázky a videa, která jsou součástí tohoto nástroje (například [kurzy PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) na Channel 9).</span><span class="sxs-lookup"><span data-stu-id="98d6a-143">For details, see the rich help topics, demos, and videos included with the tool (such as the [PerfView tutorials](https://channel9.msdn.com/Series/PerfView-Tutorial) on Channel 9).</span></span>
  
### <a name="fact-4-its-all-about-allocations"></a><span data-ttu-id="98d6a-144">Fakt 4: vše o přiděleních</span><span class="sxs-lookup"><span data-stu-id="98d6a-144">Fact 4: It’s all about allocations</span></span>  
 <span data-ttu-id="98d6a-145">Možná si myslíte, že sestavování reakce .NET Framework aplikace je vše o algoritmech, jako je například použití rychlého řazení místo řazení bublin, ale to není případ.</span><span class="sxs-lookup"><span data-stu-id="98d6a-145">You might think that building a responsive .NET Framework app is all about algorithms, such as using quick sort instead of bubble sort, but that's not the case.</span></span> <span data-ttu-id="98d6a-146">Největší faktor v sestavování reakce aplikace přiděluje paměť, zejména v případě, že je vaše aplikace velmi rozsáhlá nebo zpracovává velké objemy dat.</span><span class="sxs-lookup"><span data-stu-id="98d6a-146">The biggest factor in building a responsive app is allocating memory, especially when your app is very large or processes large amounts of data.</span></span>
  
 <span data-ttu-id="98d6a-147">Skoro veškerá práce, která se má sestavit, reaguje prostředí IDE s novými rozhraními API kompilátoru, která se týkají zamezení přidělení a správě strategií ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="98d6a-147">Almost all the work to build responsive IDE experiences with the new compiler APIs involved avoiding allocations and managing caching strategies.</span></span> <span data-ttu-id="98d6a-148">Trasování PerfView ukazují, že výkon nových kompilátorů jazyka C# a Visual Basic je málo vázaný na procesor.</span><span class="sxs-lookup"><span data-stu-id="98d6a-148">PerfView traces show that the performance of the new C# and Visual Basic compilers is rarely CPU bound.</span></span> <span data-ttu-id="98d6a-149">Kompilátory můžou být vázané na vstupně-výstupní operace při čtení stovek tisíců nebo milionů řádků kódu, čtení metadat nebo generování generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="98d6a-149">The compilers can be I/O bound when reading hundreds of thousands or millions of lines of code, reading metadata, or emitting generated code.</span></span> <span data-ttu-id="98d6a-150">Zpoždění vlákna uživatelského rozhraní jsou skoro všechny z důvodu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="98d6a-150">The UI thread delays are nearly all due to garbage collection.</span></span> <span data-ttu-id="98d6a-151">Uvolňování .NET Framework GC je vysoce vyladěné pro výkon a provádí většinu jeho práce současně, zatímco se spouští kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="98d6a-151">The .NET Framework GC is highly tuned for performance and does much of its work concurrently while app code executes.</span></span> <span data-ttu-id="98d6a-152">Jedno přidělení ale může aktivovat nákladný [Gen2](../../standard/garbage-collection/fundamentals.md) kolekci, takže se zastaví všechna vlákna.</span><span class="sxs-lookup"><span data-stu-id="98d6a-152">However, a single allocation can trigger an expensive [gen2](../../standard/garbage-collection/fundamentals.md) collection, stopping all threads.</span></span>
  
## <a name="common-allocations-and-examples"></a><span data-ttu-id="98d6a-153">Běžné alokace a příklady</span><span class="sxs-lookup"><span data-stu-id="98d6a-153">Common allocations and examples</span></span>  
 <span data-ttu-id="98d6a-154">Ukázkové výrazy v této části mají skryté alokace, které se jeví jako malé.</span><span class="sxs-lookup"><span data-stu-id="98d6a-154">The example expressions in this section have hidden allocations that appear small.</span></span> <span data-ttu-id="98d6a-155">Pokud ale velké aplikace vykoná výrazy dostatečně dlouho, může to způsobit stovky megabajtů, dokonce i gigabajtů.</span><span class="sxs-lookup"><span data-stu-id="98d6a-155">However, if a large app executes the expressions enough times, they can causes hundreds of megabytes, even gigabytes, of allocations.</span></span> <span data-ttu-id="98d6a-156">Například jednorázové testy, které simulují psaní vývojářů v editoru, přidělené gigabajty paměti a vedli výkonnostnímu týmu, aby se zaměřili na psaní scénářů.</span><span class="sxs-lookup"><span data-stu-id="98d6a-156">For example, one-minute tests that simulated a developer’s typing in the editor allocated gigabytes of memory and led the performance team to focus on typing scenarios.</span></span>
  
### <a name="boxing"></a><span data-ttu-id="98d6a-157">Zabalení</span><span class="sxs-lookup"><span data-stu-id="98d6a-157">Boxing</span></span>  
 <span data-ttu-id="98d6a-158">[Zabalení](../../csharp/programming-guide/types/boxing-and-unboxing.md) nastane, pokud jsou typy hodnot, které jsou normálně živé v zásobníku nebo v datových strukturách zabaleny do objektu.</span><span class="sxs-lookup"><span data-stu-id="98d6a-158">[Boxing](../../csharp/programming-guide/types/boxing-and-unboxing.md) occurs when value types that normally live on the stack or in data structures are wrapped in an object.</span></span> <span data-ttu-id="98d6a-159">To znamená, že přidělíte objektu pro uchovávání dat a potom vrátíte ukazatel na objekt.</span><span class="sxs-lookup"><span data-stu-id="98d6a-159">That is, you allocate an object to hold the data, and then return a pointer to the object.</span></span> <span data-ttu-id="98d6a-160">.NET Framework jsou někdy hodnoty polí z důvodu signatury metody nebo typu umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="98d6a-160">The .NET Framework sometimes boxes values due to the signature of a method or the type of a storage location.</span></span> <span data-ttu-id="98d6a-161">Zabalením typu hodnoty v objektu dojde k přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="98d6a-161">Wrapping a value type in an object causes memory allocation.</span></span> <span data-ttu-id="98d6a-162">Mnohé operace zabalení můžou do vaší aplikace přispívat megabajtů a gigabajty přidělení, což znamená, že vaše aplikace bude způsobit větší GC.</span><span class="sxs-lookup"><span data-stu-id="98d6a-162">Many boxing operations can contribute megabytes or gigabytes of allocations to your app, which means that your app will cause more GCs.</span></span> <span data-ttu-id="98d6a-163">.NET Framework a kompilátory jazyka zabraňují zabalení, je-li to možné, ale někdy k tomu dojde, pokud je k dispozici alespoň po očekávání.</span><span class="sxs-lookup"><span data-stu-id="98d6a-163">The .NET Framework and the language compilers avoid boxing when possible, but sometimes it happens when you least expect it.</span></span>
  
 <span data-ttu-id="98d6a-164">Chcete-li zobrazit zabalení v PerfView, otevřete trasování a podívejte se na alokační zásobníky haldy GC v názvu procesu vaší aplikace (Nezapomeňte, PerfView sestavy pro všechny procesy).</span><span class="sxs-lookup"><span data-stu-id="98d6a-164">To see boxing in PerfView, open a trace and look at GC Heap Alloc Stacks under your app’s process name (remember, PerfView reports on all processes).</span></span> <span data-ttu-id="98d6a-165">Pokud se zobrazí typy jako <xref:System.Int32?displayProperty=nameWithType> a <xref:System.Char?displayProperty=nameWithType> v části přidělení, jsou typy hodnot zabalení.</span><span class="sxs-lookup"><span data-stu-id="98d6a-165">If you see types like <xref:System.Int32?displayProperty=nameWithType> and <xref:System.Char?displayProperty=nameWithType> under allocations, you are boxing value types.</span></span> <span data-ttu-id="98d6a-166">Když vyberete jeden z těchto typů, zobrazí se zásobníky a funkce, ve kterých jsou zabalené.</span><span class="sxs-lookup"><span data-stu-id="98d6a-166">Choosing one of these types will show the stacks and functions in which they are boxed.</span></span>
  
 <span data-ttu-id="98d6a-167">**Příklad 1: metody řetězce a argumenty typu hodnoty**</span><span class="sxs-lookup"><span data-stu-id="98d6a-167">**Example 1: string methods and value type arguments**</span></span>  
  
 <span data-ttu-id="98d6a-168">Tento vzorový kód ilustruje potenciálně zbytečný a nadměrný zabalení:</span><span class="sxs-lookup"><span data-stu-id="98d6a-168">This sample code illustrates potentially unnecessary and excessive boxing:</span></span>  
  
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
  
 <span data-ttu-id="98d6a-169">Tento kód poskytuje funkce protokolování, takže aplikace může `Log` často zavolat funkci, možná miliony časů.</span><span class="sxs-lookup"><span data-stu-id="98d6a-169">This code provides logging functionality, so an app may call the `Log` function frequently, maybe millions of times.</span></span> <span data-ttu-id="98d6a-170">Problém je, že volání `string.Format` překládá na <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> přetížení.</span><span class="sxs-lookup"><span data-stu-id="98d6a-170">The problem is that the call to `string.Format` resolves to the <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> overload.</span></span>
  
 <span data-ttu-id="98d6a-171">Toto přetížení vyžaduje, aby pole .NET Framework k zadání `int` hodnot do objektů, aby je bylo možné předat tomuto volání metody.</span><span class="sxs-lookup"><span data-stu-id="98d6a-171">This overload requires the .NET Framework to box the `int` values into objects to pass them to this method call.</span></span> <span data-ttu-id="98d6a-172">Částečnou opravu je zavolat `id.ToString()` a `size.ToString()` předat všechny řetězce (které jsou objekty) `string.Format` volání.</span><span class="sxs-lookup"><span data-stu-id="98d6a-172">A partial fix is to call `id.ToString()` and `size.ToString()` and pass all strings (which are objects) to the `string.Format` call.</span></span> <span data-ttu-id="98d6a-173">Volání `ToString()` přidělí řetězec, ale toto přidělení bude provedeno i v rámci `string.Format` .</span><span class="sxs-lookup"><span data-stu-id="98d6a-173">Calling `ToString()` does allocate a string, but that allocation will happen anyway inside `string.Format`.</span></span>
  
 <span data-ttu-id="98d6a-174">Můžete zvážit, že toto základní volání `string.Format` je pouze zřetězení řetězců, takže můžete místo toho napsat tento kód:</span><span class="sxs-lookup"><span data-stu-id="98d6a-174">You might consider that this basic call to `string.Format` is just string concatenation, so you might write this code instead:</span></span>  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 <span data-ttu-id="98d6a-175">Nicméně tento řádek kódu zavádí přidělení zabalení, protože se kompiluje do <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29> .</span><span class="sxs-lookup"><span data-stu-id="98d6a-175">However, that line of code introduces a boxing allocation because it compiles to <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span></span> <span data-ttu-id="98d6a-176">.NET Framework musí být vyvolán znakový literál.`Concat`</span><span class="sxs-lookup"><span data-stu-id="98d6a-176">The .NET Framework must box the character literal to invoke `Concat`</span></span>  
  
 <span data-ttu-id="98d6a-177">**Opravit příklad 1**</span><span class="sxs-lookup"><span data-stu-id="98d6a-177">**Fix for example 1**</span></span>  
  
 <span data-ttu-id="98d6a-178">Kompletní oprava je jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="98d6a-178">The complete fix is simple.</span></span> <span data-ttu-id="98d6a-179">Pouze nahraďte znakový literál řetězcovým literálem, který nevyvolává zabalení, protože řetězce jsou již objekty:</span><span class="sxs-lookup"><span data-stu-id="98d6a-179">Just replace the character literal with a string literal, which incurs no boxing because strings are already objects:</span></span>  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 <span data-ttu-id="98d6a-180">**Příklad 2: zabalení výčtu**</span><span class="sxs-lookup"><span data-stu-id="98d6a-180">**Example 2: enum boxing**</span></span>  
  
 <span data-ttu-id="98d6a-181">Tento příklad zodpovídá za obrovské množství přidělení v nových kompilátorech C# a Visual Basic z důvodu častého použití typů výčtu, zejména při operacích vyhledávání ve slovníku.</span><span class="sxs-lookup"><span data-stu-id="98d6a-181">This example was responsible for a huge amount of allocation in the new C# and Visual Basic compilers due to frequent use of enumeration types, especially in dictionary lookup operations.</span></span>
  
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
  
 <span data-ttu-id="98d6a-182">Tento problém je velice jemný.</span><span class="sxs-lookup"><span data-stu-id="98d6a-182">This problem is very subtle.</span></span> <span data-ttu-id="98d6a-183">PerfView by tuto zprávu nahlásil jako <xref:System.Enum.GetHashCode> zabalení, protože v případě důvodů implementace jsou v polích metoda základní reprezentace typu výčtu.</span><span class="sxs-lookup"><span data-stu-id="98d6a-183">PerfView would report this as <xref:System.Enum.GetHashCode> boxing because the method boxes the underlying representation of the enumeration type, for implementation reasons.</span></span> <span data-ttu-id="98d6a-184">Pokud se podrobněji podíváte v PerfView, může se pro každé volání na. zobrazit dvě přidělení zabalení <xref:System.Enum.GetHashCode> .</span><span class="sxs-lookup"><span data-stu-id="98d6a-184">If you look closely in PerfView, you may see two boxing allocations for each call to <xref:System.Enum.GetHashCode>.</span></span> <span data-ttu-id="98d6a-185">Kompilátor vloží jeden a .NET Framework vloží druhý.</span><span class="sxs-lookup"><span data-stu-id="98d6a-185">The compiler inserts one, and the .NET Framework inserts the other.</span></span>
  
 <span data-ttu-id="98d6a-186">**Oprava pro příklad 2**</span><span class="sxs-lookup"><span data-stu-id="98d6a-186">**Fix for example 2**</span></span>  
  
 <span data-ttu-id="98d6a-187">Můžete snadno zabránit tomu, aby se obě přidělení přetypování do základní reprezentace před voláním <xref:System.Enum.GetHashCode> :</span><span class="sxs-lookup"><span data-stu-id="98d6a-187">You can easily avoid both allocations by casting to the underlying representation before calling <xref:System.Enum.GetHashCode>:</span></span>  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 <span data-ttu-id="98d6a-188">Dalším běžným zdrojem zabalení pro výčtové typy je <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="98d6a-188">Another common source of boxing on enumeration types is the <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="98d6a-189">Argument předaný do <xref:System.Enum.HasFlag%28System.Enum%29> musí být zabalen.</span><span class="sxs-lookup"><span data-stu-id="98d6a-189">The argument passed to <xref:System.Enum.HasFlag%28System.Enum%29> has to be boxed.</span></span> <span data-ttu-id="98d6a-190">Ve většině případů je nahrazení volání <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> s bitovým testem jednodušší a bez přidělení.</span><span class="sxs-lookup"><span data-stu-id="98d6a-190">In most cases, replacing calls to <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> with a bitwise test is simpler and allocation-free.</span></span>
  
 <span data-ttu-id="98d6a-191">Zajistěte si první fakt o výkonu (to znamená, že se předčasně neoptimalizují) a nespustí se tímto způsobem přepis veškerého kódu.</span><span class="sxs-lookup"><span data-stu-id="98d6a-191">Keep the first performance fact in mind (that is, don’t prematurely optimize) and don’t start rewriting all your code in this way.</span></span> <span data-ttu-id="98d6a-192">Pamatujte na tyto náklady na zabalení, ale změňte kód pouze po profilaci aplikace a nalezení aktivních bodů.</span><span class="sxs-lookup"><span data-stu-id="98d6a-192">Be aware of these boxing costs, but change your code only after profiling your app and finding the hot spots.</span></span>
  
### <a name="strings"></a><span data-ttu-id="98d6a-193">Řetězce</span><span class="sxs-lookup"><span data-stu-id="98d6a-193">Strings</span></span>  
 <span data-ttu-id="98d6a-194">Manipulace s řetězci jsou některé z největších culprits pro přidělení a často se zobrazují v PerfView v horních pěti přiděleních.</span><span class="sxs-lookup"><span data-stu-id="98d6a-194">String manipulations are some of the biggest culprits for allocations, and they often show up in PerfView in the top five allocations.</span></span> <span data-ttu-id="98d6a-195">Programy používají řetězce pro serializaci, JSON a rozhraní REST API.</span><span class="sxs-lookup"><span data-stu-id="98d6a-195">Programs use strings for serialization, JSON, and REST APIs.</span></span> <span data-ttu-id="98d6a-196">Můžete použít řetězce jako programové konstanty pro spolupráci se systémy, když nemůžete použít typy výčtu.</span><span class="sxs-lookup"><span data-stu-id="98d6a-196">You can use strings as programmatic constants for interoperating with systems when you can’t use enumeration types.</span></span> <span data-ttu-id="98d6a-197">Když profilace znázorňuje, že řetězce mají vysoce ovlivněný výkon, hledejte volání metod, jako například,,, <xref:System.String> <xref:System.String.Format%2A> <xref:System.String.Concat%2A> <xref:System.String.Split%2A> <xref:System.String.Join%2A> , <xref:System.String.Substring%2A> a tak dále.</span><span class="sxs-lookup"><span data-stu-id="98d6a-197">When your profiling shows that strings are highly affecting performance, look for calls to <xref:System.String> methods such as <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, and so on.</span></span> <span data-ttu-id="98d6a-198">Použití <xref:System.Text.StringBuilder> , aby se předešlo nákladům na vytvoření jednoho řetězce z mnoha kusů, ale i přidělení <xref:System.Text.StringBuilder> objektu se může stát kritickým bodem, který potřebujete spravovat.</span><span class="sxs-lookup"><span data-stu-id="98d6a-198">Using <xref:System.Text.StringBuilder> to avoid the cost of creating one string from many pieces helps, but even allocating the <xref:System.Text.StringBuilder> object might become a bottleneck that you need to manage.</span></span>
  
 <span data-ttu-id="98d6a-199">**Příklad 3: operace s řetězci**</span><span class="sxs-lookup"><span data-stu-id="98d6a-199">**Example 3: string operations**</span></span>  
  
 <span data-ttu-id="98d6a-200">Kompilátor jazyka C# měl tento kód, který zapisuje text formátovaného komentáře XML dokumentu:</span><span class="sxs-lookup"><span data-stu-id="98d6a-200">The C# compiler had this code that writes the text of a formatted XML doc comment:</span></span>  
  
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
  
 <span data-ttu-id="98d6a-201">Můžete vidět, že tento kód provede mnoho manipulace s řetězci.</span><span class="sxs-lookup"><span data-stu-id="98d6a-201">You can see that this code does a lot of string manipulation.</span></span> <span data-ttu-id="98d6a-202">Kód používá metody knihovny pro rozdělení řádků do samostatných řetězců, pro oříznutí prázdných znaků, pro kontrolu, zda `text` je argument komentář k dokumentaci XML a extrahování podřetězců z řádků.</span><span class="sxs-lookup"><span data-stu-id="98d6a-202">The code uses library methods to split lines into separate strings, to trim white space, to check whether the argument `text` is an XML documentation comment, and to extract substrings from lines.</span></span>
  
 <span data-ttu-id="98d6a-203">Na prvním řádku uvnitř `WriteFormattedDocComment` , `text.Split` volání přidělí nové pole tří prvků jako argument pokaždé, když je volána.</span><span class="sxs-lookup"><span data-stu-id="98d6a-203">On the first line inside `WriteFormattedDocComment`, the `text.Split` call allocates a new three-element array as the argument every time it’s called.</span></span> <span data-ttu-id="98d6a-204">Kompilátor musí vygenerovat kód pro každé přidělení tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="98d6a-204">The compiler has to emit code to allocate this array each time.</span></span> <span data-ttu-id="98d6a-205">Důvodem je, že kompilátor neví, zda je pole <xref:System.String.Split%2A> uloženo, kde může být pole upraveno jiným kódem, což by ovlivnilo pozdější volání `WriteFormattedDocComment` .</span><span class="sxs-lookup"><span data-stu-id="98d6a-205">That’s because the compiler doesn’t know if <xref:System.String.Split%2A> stores the array somewhere where the array might be modified by other code, which would affect later calls to `WriteFormattedDocComment`.</span></span> <span data-ttu-id="98d6a-206">Volání pro <xref:System.String.Split%2A> také přiděluje řetězec pro každý řádek v `text` a přiděluje další paměť k provedení operace.</span><span class="sxs-lookup"><span data-stu-id="98d6a-206">The call to <xref:System.String.Split%2A> also allocates a string for every line in `text` and allocates other memory to perform the operation.</span></span>
  
 <span data-ttu-id="98d6a-207">`WriteFormattedDocComment`má tři volání <xref:System.String.TrimStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="98d6a-207">`WriteFormattedDocComment` has three calls to the <xref:System.String.TrimStart%2A> method.</span></span> <span data-ttu-id="98d6a-208">Dva jsou ve vnitřních smyčkách, které duplikují práci a přidělení.</span><span class="sxs-lookup"><span data-stu-id="98d6a-208">Two are in inner loops that duplicate work and allocations.</span></span> <span data-ttu-id="98d6a-209">Aby byly věci horší, volání <xref:System.String.TrimStart%2A> metody bez argumentů přidělí prázdné pole (pro `params` parametr) Kromě výsledku řetězce.</span><span class="sxs-lookup"><span data-stu-id="98d6a-209">To make matters worse, calling the <xref:System.String.TrimStart%2A> method with no arguments allocates an empty array (for the `params` parameter) in addition to the string result.</span></span>
  
 <span data-ttu-id="98d6a-210">Nakonec existuje volání <xref:System.String.Substring%2A> metody, která obvykle přiděluje nový řetězec.</span><span class="sxs-lookup"><span data-stu-id="98d6a-210">Lastly, there is a call to the <xref:System.String.Substring%2A> method, which usually allocates a new string.</span></span>
  
 <span data-ttu-id="98d6a-211">**Oprava pro příklad 3**</span><span class="sxs-lookup"><span data-stu-id="98d6a-211">**Fix for example 3**</span></span>  
  
 <span data-ttu-id="98d6a-212">Na rozdíl od předchozích příkladů malé úpravy nemůžou tyto alokace opravit.</span><span class="sxs-lookup"><span data-stu-id="98d6a-212">Unlike the earlier examples, small edits cannot fix these allocations.</span></span> <span data-ttu-id="98d6a-213">Budete se muset vrátit zpátky, podívat se na problém a přistupovat k němu jinak.</span><span class="sxs-lookup"><span data-stu-id="98d6a-213">You need to step back, look at the problem, and approach it differently.</span></span> <span data-ttu-id="98d6a-214">Například si všimnete, že argument `WriteFormattedDocComment()` je řetězec, který obsahuje všechny informace, které metoda potřebuje, takže kód by mohl provést větší indexování místo přidělení mnoha částečných řetězců.</span><span class="sxs-lookup"><span data-stu-id="98d6a-214">For example, you'll notice that the argument to `WriteFormattedDocComment()` is a string that has all the information that the method needs, so the code could do more indexing instead of allocating many partial strings.</span></span>
  
 <span data-ttu-id="98d6a-215">Tým výkonu kompilátoru projedná všechna tato přidělení s kódem podobným tomuto:</span><span class="sxs-lookup"><span data-stu-id="98d6a-215">The compiler’s performance team tackled all these allocations with code like this:</span></span>  
  
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
  
 <span data-ttu-id="98d6a-216">První verze `WriteFormattedDocComment()` přiděleného pole, několik podřetězců a oříznutý dílčí řetězec spolu s prázdným `params` polem.</span><span class="sxs-lookup"><span data-stu-id="98d6a-216">The first version of `WriteFormattedDocComment()` allocated an array, several substrings, and a trimmed substring along with an empty `params` array.</span></span> <span data-ttu-id="98d6a-217">Také je zaškrtnuté políčko///.</span><span class="sxs-lookup"><span data-stu-id="98d6a-217">It also checked for "///".</span></span> <span data-ttu-id="98d6a-218">Revidovaný kód používá pouze indexování a přiděluje nic.</span><span class="sxs-lookup"><span data-stu-id="98d6a-218">The revised code uses only indexing and allocates nothing.</span></span> <span data-ttu-id="98d6a-219">Vyhledá první znak, který není prázdný, a poté zkontroluje znak podle znaku, aby bylo možné zjistit, zda řetězec začíná řetězcem "///".</span><span class="sxs-lookup"><span data-stu-id="98d6a-219">It finds the first character that is not white space, and then checks character by character to see if the string starts with "///".</span></span> <span data-ttu-id="98d6a-220">Nový kód používá `IndexOfFirstNonWhiteSpaceChar` místo <xref:System.String.TrimStart%2A> k vrácení prvního indexu (po zadaném počátečním indexu), kde se vyskytuje neprázdný znak.</span><span class="sxs-lookup"><span data-stu-id="98d6a-220">The new code uses `IndexOfFirstNonWhiteSpaceChar` instead of <xref:System.String.TrimStart%2A> to return the first index (after a specified start index) where a non-white-space character occurs.</span></span> <span data-ttu-id="98d6a-221">Oprava není dokončena, ale můžete si prohlédnout, jak použít podobné opravy pro kompletní řešení.</span><span class="sxs-lookup"><span data-stu-id="98d6a-221">The fix is not complete, but you can see how to apply similar fixes for a complete solution.</span></span> <span data-ttu-id="98d6a-222">Použitím tohoto přístupu v rámci kódu můžete odebrat všechna přidělení v `WriteFormattedDocComment()` .</span><span class="sxs-lookup"><span data-stu-id="98d6a-222">By applying this approach throughout the code, you can remove all allocations in `WriteFormattedDocComment()`.</span></span>
  
 <span data-ttu-id="98d6a-223">**Příklad 4: StringBuilder**</span><span class="sxs-lookup"><span data-stu-id="98d6a-223">**Example 4: StringBuilder**</span></span>  
  
 <span data-ttu-id="98d6a-224">V tomto příkladu se používá <xref:System.Text.StringBuilder> objekt.</span><span class="sxs-lookup"><span data-stu-id="98d6a-224">This example uses a <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="98d6a-225">Následující funkce generuje úplný název typu pro obecné typy:</span><span class="sxs-lookup"><span data-stu-id="98d6a-225">The following function generates a full type name for generic types:</span></span>  
  
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
  
 <span data-ttu-id="98d6a-226">Fokus je na řádku, který vytvoří novou <xref:System.Text.StringBuilder> instanci.</span><span class="sxs-lookup"><span data-stu-id="98d6a-226">The focus is on the line that creates a new <xref:System.Text.StringBuilder> instance.</span></span> <span data-ttu-id="98d6a-227">Kód způsobí přidělení `sb.ToString()` a interní přidělení v rámci <xref:System.Text.StringBuilder> implementace, ale nemůžete řídit tato přidělení, pokud chcete výsledek řetězce.</span><span class="sxs-lookup"><span data-stu-id="98d6a-227">The code causes an allocation for `sb.ToString()` and internal allocations within the <xref:System.Text.StringBuilder> implementation, but you cannot control those allocations if you want the string result.</span></span>
  
 <span data-ttu-id="98d6a-228">**Oprava – příklad 4**</span><span class="sxs-lookup"><span data-stu-id="98d6a-228">**Fix for example 4**</span></span>  
  
 <span data-ttu-id="98d6a-229">Chcete-li opravit `StringBuilder` přidělení objektu, mezipaměť objektu.</span><span class="sxs-lookup"><span data-stu-id="98d6a-229">To fix the `StringBuilder` object allocation, cache the  object.</span></span> <span data-ttu-id="98d6a-230">I když mezipaměť jedné instance, která může být vyvolána, může výrazně zvýšit výkon.</span><span class="sxs-lookup"><span data-stu-id="98d6a-230">Even caching a single instance that might get thrown away can improve performance significantly.</span></span> <span data-ttu-id="98d6a-231">Jedná se o novou implementaci funkce a vynechání veškerého kódu s výjimkou nového prvního a posledního řádku:</span><span class="sxs-lookup"><span data-stu-id="98d6a-231">This is the function’s new implementation, omitting all the code except for the new first and last lines:</span></span>  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 <span data-ttu-id="98d6a-232">Hlavní části jsou nové `AcquireBuilder()` `GetStringAndReleaseBuilder()` funkce a:</span><span class="sxs-lookup"><span data-stu-id="98d6a-232">The key parts are the new `AcquireBuilder()` and `GetStringAndReleaseBuilder()` functions:</span></span>  
  
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
  
 <span data-ttu-id="98d6a-233">Vzhledem k tomu, že nové kompilátory používají dělení na vlákna, tyto implementace používají pole s statickým vláknem ( <xref:System.ThreadStaticAttribute> atribut) pro ukládání do mezipaměti <xref:System.Text.StringBuilder> a pravděpodobně si můžete vzdání `ThreadStatic` deklarace.</span><span class="sxs-lookup"><span data-stu-id="98d6a-233">Because the new compilers use threading, these implementations use a thread-static field (<xref:System.ThreadStaticAttribute> attribute) to cache the <xref:System.Text.StringBuilder>, and you likely can forgo the `ThreadStatic` declaration.</span></span> <span data-ttu-id="98d6a-234">Pole static vlákna obsahuje jedinečnou hodnotu pro každé vlákno, které provádí tento kód.</span><span class="sxs-lookup"><span data-stu-id="98d6a-234">The thread-static field holds a unique value for each thread that executes this code.</span></span>
  
 <span data-ttu-id="98d6a-235">`AcquireBuilder()`Vrátí instanci uloženou v mezipaměti <xref:System.Text.StringBuilder> , pokud ji vymažete a nastavíte pole nebo mezipaměť na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="98d6a-235">`AcquireBuilder()` returns the cached <xref:System.Text.StringBuilder> instance if there is one, after clearing it and setting the field or cache to null.</span></span> <span data-ttu-id="98d6a-236">V opačném případě `AcquireBuilder()` vytvoří novou instanci a vrátí ji, aby pole nebo mezipaměť bylo nastaveno na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="98d6a-236">Otherwise, `AcquireBuilder()` creates a new instance and returns it, leaving the field or cache set to null.</span></span>
  
 <span data-ttu-id="98d6a-237">Až budete hotovi <xref:System.Text.StringBuilder> , zavoláte, `GetStringAndReleaseBuilder()` abyste získali výsledek řetězce, uložili <xref:System.Text.StringBuilder> instanci v poli nebo mezipaměti a potom vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="98d6a-237">When you’re done with <xref:System.Text.StringBuilder> , you call `GetStringAndReleaseBuilder()` to get the string result, save the <xref:System.Text.StringBuilder> instance in the field or cache, and then return the result.</span></span> <span data-ttu-id="98d6a-238">Je možné, že spuštění tohoto kódu znovu zadáte a vytvoříte více <xref:System.Text.StringBuilder> objektů (i když se to zřídka stane).</span><span class="sxs-lookup"><span data-stu-id="98d6a-238">It is possible for execution to re-enter this code and to create multiple <xref:System.Text.StringBuilder> objects (although that rarely happens).</span></span> <span data-ttu-id="98d6a-239">Kód uloží pouze poslední vydanou <xref:System.Text.StringBuilder> instanci pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="98d6a-239">The code saves only the last released <xref:System.Text.StringBuilder> instance for later use.</span></span> <span data-ttu-id="98d6a-240">Tato jednoduchá strategie ukládání do mezipaměti významně snižuje přidělení v nových kompilátorech.</span><span class="sxs-lookup"><span data-stu-id="98d6a-240">This simple caching strategy significantly reduced allocations in the new compilers.</span></span> <span data-ttu-id="98d6a-241">Části .NET Framework a MSBuild ("MSBuild") používají podobnou techniku pro zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="98d6a-241">Parts of the .NET Framework and MSBuild ("MSBuild") use a similar technique to improve performance.</span></span>
  
 <span data-ttu-id="98d6a-242">Tato jednoduchá strategie ukládání do mezipaměti dodržuje dobrý návrh mezipaměti, protože má limit velikosti.</span><span class="sxs-lookup"><span data-stu-id="98d6a-242">This simple caching strategy adheres to good cache design because it has a size cap.</span></span> <span data-ttu-id="98d6a-243">Existuje však více kódů, než je původní, což znamená vyšší náklady na údržbu.</span><span class="sxs-lookup"><span data-stu-id="98d6a-243">However, there is more code now than in the original, which means more maintenance costs.</span></span> <span data-ttu-id="98d6a-244">Strategii ukládání do mezipaměti byste měli přijmout jenom v případě, že jste zjistili problém s výkonem a PerfView ukazuje, že <xref:System.Text.StringBuilder> přidělení jsou významným přispěvatelem.</span><span class="sxs-lookup"><span data-stu-id="98d6a-244">You should adopt the caching strategy only if you’ve found a performance problem, and PerfView has shown that <xref:System.Text.StringBuilder> allocations are a significant contributor.</span></span>
  
### <a name="linq-and-lambdas"></a><span data-ttu-id="98d6a-245">LINQ a výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="98d6a-245">LINQ and lambdas</span></span>  
<span data-ttu-id="98d6a-246">Jazykově integrovaný dotaz (LINQ), ve spojení s lambda výrazy, je příkladem funkce produktivita.</span><span class="sxs-lookup"><span data-stu-id="98d6a-246">Language-Integrated Query (LINQ), in conjunction with lambda expressions, is an example of a productivity feature.</span></span> <span data-ttu-id="98d6a-247">Jeho použití ale může mít významný dopad na výkon v průběhu času a může se stát, že budete muset přepsat kód.</span><span class="sxs-lookup"><span data-stu-id="98d6a-247">However, its use may have a significant impact on performance over time, and you might find you need to rewrite your code.</span></span>
  
 <span data-ttu-id="98d6a-248">**Příklad 5: výrazy lambda, seznamy \<T> a IEnumerable\<T>**</span><span class="sxs-lookup"><span data-stu-id="98d6a-248">**Example 5: Lambdas, List\<T>, and IEnumerable\<T>**</span></span>  
  
 <span data-ttu-id="98d6a-249">V tomto příkladu se používá [kód jazyka LINQ a funkčního stylu](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) k nalezení symbolu v modelu kompilátoru s daným názvem řetězec:</span><span class="sxs-lookup"><span data-stu-id="98d6a-249">This example uses [LINQ and functional style code](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) to find a symbol in the compiler’s model, given a name string:</span></span>  
  
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
  
 <span data-ttu-id="98d6a-250">Nový kompilátor a prostředí IDE, které jsou postaveny na `FindMatchingSymbol()` tomto volání, jsou velmi často a v jediném řádku kódu této funkce je několik skrytých přidělení.</span><span class="sxs-lookup"><span data-stu-id="98d6a-250">The new compiler and the IDE experiences built on it call `FindMatchingSymbol()` very frequently, and there are several hidden allocations in this function’s single line of code.</span></span> <span data-ttu-id="98d6a-251">Chcete-li tyto alokace prostudovat, nejprve jednotlivé řádky této funkce rozdělte na dva řádky:</span><span class="sxs-lookup"><span data-stu-id="98d6a-251">To examine those allocations, first split the function’s single line of code into two lines:</span></span>  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 <span data-ttu-id="98d6a-252">V prvním řádku se [výraz lambda](../../csharp/language-reference/operators/lambda-expressions.md) `s => s.Name == name` [zavře nad](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) místní proměnnou `name` .</span><span class="sxs-lookup"><span data-stu-id="98d6a-252">In the first line, the [lambda expression](../../csharp/language-reference/operators/lambda-expressions.md) `s => s.Name == name` [closes over](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) the local variable `name`.</span></span> <span data-ttu-id="98d6a-253">To znamená, že kromě přidělení objektu [delegáta](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) , který `predicate` obsahuje, kód přiděluje statickou třídu pro uchování prostředí, které zachycuje hodnotu `name` .</span><span class="sxs-lookup"><span data-stu-id="98d6a-253">This means that in addition to allocating an object for the [delegate](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) that `predicate` holds, the code allocates a static class to hold the environment that captures the value of `name`.</span></span> <span data-ttu-id="98d6a-254">Kompilátor generuje kód podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="98d6a-254">The compiler generates code like the following:</span></span>  
  
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
  
 <span data-ttu-id="98d6a-255">Dvě `new` alokace (jedna pro třídu prostředí a jeden pro delegáta) jsou nyní explicitní.</span><span class="sxs-lookup"><span data-stu-id="98d6a-255">The two `new` allocations (one for the environment class and one for the delegate) are explicit now.</span></span>
  
 <span data-ttu-id="98d6a-256">Nyní se podívejte na volání `FirstOrDefault` .</span><span class="sxs-lookup"><span data-stu-id="98d6a-256">Now look at the call to `FirstOrDefault`.</span></span> <span data-ttu-id="98d6a-257">Tato metoda rozšíření u typu vychází z <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> přidělení.</span><span class="sxs-lookup"><span data-stu-id="98d6a-257">This extension method on the <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> type incurs an allocation too.</span></span> <span data-ttu-id="98d6a-258">Vzhledem k tomu `FirstOrDefault` , že přebírá <xref:System.Collections.Generic.IEnumerable%601> objekt jako svůj první argument, můžete zavolat na následující kód (zjednodušený bit pro diskuzi):</span><span class="sxs-lookup"><span data-stu-id="98d6a-258">Because `FirstOrDefault` takes an <xref:System.Collections.Generic.IEnumerable%601> object as its first argument, you can expand the call to the following code (simplified a bit for discussion):</span></span>  
  
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
  
 <span data-ttu-id="98d6a-259">`symbols`Proměnná má typ <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="98d6a-259">The `symbols` variable has type <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="98d6a-260"><xref:System.Collections.Generic.List%601>Typ kolekce implementuje <xref:System.Collections.Generic.IEnumerable%601> a cleverly definuje enumerátor ( <xref:System.Collections.Generic.IEnumerator%601> rozhraní), který <xref:System.Collections.Generic.List%601> implementuje s `struct` .</span><span class="sxs-lookup"><span data-stu-id="98d6a-260">The <xref:System.Collections.Generic.List%601> collection type implements <xref:System.Collections.Generic.IEnumerable%601> and cleverly defines an enumerator (<xref:System.Collections.Generic.IEnumerator%601> interface) that <xref:System.Collections.Generic.List%601> implements with a `struct`.</span></span> <span data-ttu-id="98d6a-261">Použití struktury namísto třídy znamená, že se obvykle vyhnete jakémukoli přidělení haldy, což pak může ovlivnit výkon uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="98d6a-261">Using a structure instead of a class means that you usually avoid any heap allocations, which, in turn, can affect garbage collection performance.</span></span> <span data-ttu-id="98d6a-262">Enumerátory se obvykle používají se `foreach` smyčkou jazyka, která používá strukturu výčtu, jak je vrácena v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="98d6a-262">Enumerators are typically used with the language’s `foreach` loop, which uses the enumerator structure as it is returned on the call stack.</span></span> <span data-ttu-id="98d6a-263">Zvýšení ukazatele zásobníku volání, aby uvolnil prostor pro objekt, nemá vliv na uvolňování paměti způsobem, jakým provádí přidělení haldy.</span><span class="sxs-lookup"><span data-stu-id="98d6a-263">Incrementing the call stack pointer to make room for an object does not affect GC the way a heap allocation does.</span></span>
  
 <span data-ttu-id="98d6a-264">V případě rozšířeného `FirstOrDefault` volání musí kód volat `GetEnumerator()` na <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="98d6a-264">In the case of the expanded `FirstOrDefault` call, the code needs to call `GetEnumerator()` on an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="98d6a-265">Přiřazení `symbols` `enumerable` proměnné typu `IEnumerable<Symbol>` ztratí informace, které jsou aktuálním objektem <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="98d6a-265">Assigning `symbols` to the `enumerable` variable of type `IEnumerable<Symbol>` loses the information that the actual object is a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="98d6a-266">To znamená, že když kód načte enumerátor s `enumerable.GetEnumerator()` , .NET Framework musí zařadit vrácenou strukturu k `enumerator` proměnné.</span><span class="sxs-lookup"><span data-stu-id="98d6a-266">This means that when the code fetches the enumerator with `enumerable.GetEnumerator()`, the .NET Framework has to box the returned structure to assign it to the `enumerator` variable.</span></span>
  
 <span data-ttu-id="98d6a-267">**Oprava – příklad 5**</span><span class="sxs-lookup"><span data-stu-id="98d6a-267">**Fix for example 5**</span></span>  
  
 <span data-ttu-id="98d6a-268">Oprava má přepsat `FindMatchingSymbol` následujícím způsobem a nahradit tak jeden řádek kódu šestými řádky kódu, které jsou stále stručnější, snadno čitelné a srozumitelnější a snadno udržovatelnější:</span><span class="sxs-lookup"><span data-stu-id="98d6a-268">The fix is to rewrite `FindMatchingSymbol` as follows, replacing its single line of code with six lines of code that are still concise, easy to read and understand, and easy to maintain:</span></span>  
  
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
  
 <span data-ttu-id="98d6a-269">Tento kód nepoužívá metody rozšíření LINQ, výrazy lambda nebo enumerátory a nevyvolává žádné přidělení.</span><span class="sxs-lookup"><span data-stu-id="98d6a-269">This code doesn’t use LINQ extension methods, lambdas, or enumerators, and it incurs no allocations.</span></span> <span data-ttu-id="98d6a-270">Neexistují žádné přidělení, protože kompilátor uvidí, že `symbols` kolekce je <xref:System.Collections.Generic.List%601> a může vytvořit vazby výsledného enumerátoru (struktury) na místní proměnnou se správným typem, aby nedošlo k zabalení.</span><span class="sxs-lookup"><span data-stu-id="98d6a-270">There are no allocations because the compiler can see that the `symbols` collection is a <xref:System.Collections.Generic.List%601> and can bind the resulting enumerator (a structure) to a local variable with the right type to avoid boxing.</span></span> <span data-ttu-id="98d6a-271">Původní verze této funkce byla skvělým příkladem exprese jazyka C# a produktivity .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="98d6a-271">The original version of this function was a great example of the expressive power of C# and the productivity of the .NET Framework.</span></span> <span data-ttu-id="98d6a-272">Tato nová a efektivnější verze zachovává tyto kvality bez přidání jakéhokoliv komplexního kódu, který se má zachovat.</span><span class="sxs-lookup"><span data-stu-id="98d6a-272">This new and more efficient version preserves those qualities without adding any complex code to maintain.</span></span>
  
### <a name="async-method-caching"></a><span data-ttu-id="98d6a-273">Ukládání asynchronní metody do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="98d6a-273">Async method caching</span></span>  

<span data-ttu-id="98d6a-274">Následující příklad ukazuje běžný problém při pokusu o použití výsledků v mezipaměti v [asynchronní](../../csharp/programming-guide/concepts/async/index.md) metodě.</span><span class="sxs-lookup"><span data-stu-id="98d6a-274">The next example shows a common problem when you try to use cached results in an [async](../../csharp/programming-guide/concepts/async/index.md) method.</span></span>
  
 <span data-ttu-id="98d6a-275">**Příklad 6: ukládání do mezipaměti v asynchronních metodách**</span><span class="sxs-lookup"><span data-stu-id="98d6a-275">**Example 6: caching in async methods**</span></span>  
  
 <span data-ttu-id="98d6a-276">Funkce integrovaného vývojového prostředí sady Visual Studio, které jsou založené na nových kompilátorech C# a Visual Basic často načítají stromy syntaxe a kompilátory používají asynchronní použití při reakci sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="98d6a-276">The Visual Studio IDE features built on the new C# and Visual Basic compilers frequently fetch syntax trees, and the compilers use async when doing so to keep Visual Studio responsive.</span></span> <span data-ttu-id="98d6a-277">Zde je první verze kódu, který můžete napsat pro získání stromu syntaxe:</span><span class="sxs-lookup"><span data-stu-id="98d6a-277">Here’s the first version of the code you might write to get a syntax tree:</span></span>  
  
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
  
 <span data-ttu-id="98d6a-278">Můžete vidět, že volání `GetSyntaxTreeAsync()` instance a `Parser` , analyzuje kód a potom vrátí <xref:System.Threading.Tasks.Task> objekt, `Task<SyntaxTree>` .</span><span class="sxs-lookup"><span data-stu-id="98d6a-278">You can see that calling `GetSyntaxTreeAsync()` instantiates a `Parser`, parses the code, and then returns a <xref:System.Threading.Tasks.Task> object, `Task<SyntaxTree>`.</span></span> <span data-ttu-id="98d6a-279">Nákladná část přiděluje `Parser` instanci a analyzuje kód.</span><span class="sxs-lookup"><span data-stu-id="98d6a-279">The expensive part is allocating the `Parser` instance and parsing the code.</span></span> <span data-ttu-id="98d6a-280">Funkce vrátí <xref:System.Threading.Tasks.Task> , aby volající mohli očekávat, že analýza funguje, a uvolní vlákno uživatelského rozhraní, které bude reagovat na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="98d6a-280">The function returns a <xref:System.Threading.Tasks.Task> so that callers can await the parsing work and free the UI thread to be responsive to user input.</span></span>
  
 <span data-ttu-id="98d6a-281">Několik funkcí sady Visual Studio se může pokusit získat stejný strom syntaxe, takže můžete napsat následující kód pro uložení výsledků analýzy do mezipaměti a ušetřit tak čas a přidělení.</span><span class="sxs-lookup"><span data-stu-id="98d6a-281">Several Visual Studio features might try to get the same syntax tree, so you might write the following code to cache the parsing result to save time and allocations.</span></span> <span data-ttu-id="98d6a-282">Tento kód ale při přidělení:</span><span class="sxs-lookup"><span data-stu-id="98d6a-282">However, this code incurs an allocation:</span></span>  
  
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
  
 <span data-ttu-id="98d6a-283">Vidíte, že nový kód s ukládáním do mezipaměti má `SyntaxTree` pole s názvem `cachedResult` .</span><span class="sxs-lookup"><span data-stu-id="98d6a-283">You see that the new code with caching has a `SyntaxTree` field named `cachedResult`.</span></span> <span data-ttu-id="98d6a-284">Pokud je toto pole null, `GetSyntaxTreeAsync()` provede práci a uloží výsledek do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="98d6a-284">When this field is null, `GetSyntaxTreeAsync()` does the work and saves the result in the cache.</span></span> <span data-ttu-id="98d6a-285">`GetSyntaxTreeAsync()`Vrátí `SyntaxTree` objekt.</span><span class="sxs-lookup"><span data-stu-id="98d6a-285">`GetSyntaxTreeAsync()` returns the `SyntaxTree` object.</span></span> <span data-ttu-id="98d6a-286">Problém je, že pokud máte `async` funkci typu `Task<SyntaxTree>` a vrátíte hodnotu typu `SyntaxTree` , kompilátor vygeneruje kód pro přidělení úkolu pro uchování výsledku (pomocí `Task<SyntaxTree>.FromResult()` ).</span><span class="sxs-lookup"><span data-stu-id="98d6a-286">The problem is that when you have an `async` function of type `Task<SyntaxTree>`, and you return a value of type `SyntaxTree`, the compiler emits code to allocate a Task to hold the result (by using `Task<SyntaxTree>.FromResult()`).</span></span> <span data-ttu-id="98d6a-287">Úkol je označený jako dokončený a výsledek je hned dostupný.</span><span class="sxs-lookup"><span data-stu-id="98d6a-287">The Task is marked as completed, and the result is immediately available.</span></span> <span data-ttu-id="98d6a-288">V kódu pro nové kompilátory <xref:System.Threading.Tasks.Task> došlo k objektům, které již byly dokončeny, a to často, aby tato přidělení zvýšila odezvu na upozornění.</span><span class="sxs-lookup"><span data-stu-id="98d6a-288">In the code for the new compilers, <xref:System.Threading.Tasks.Task> objects that were already completed occurred so often that fixing these allocations improved responsiveness noticeably.</span></span>
  
 <span data-ttu-id="98d6a-289">**Oprava pro příklad 6**</span><span class="sxs-lookup"><span data-stu-id="98d6a-289">**Fix for example 6**</span></span>  
  
 <span data-ttu-id="98d6a-290">Chcete-li odebrat dokončené <xref:System.Threading.Tasks.Task> přidělení, můžete uložit objekt úlohy do mezipaměti s dokončeným výsledkem:</span><span class="sxs-lookup"><span data-stu-id="98d6a-290">To remove the completed <xref:System.Threading.Tasks.Task> allocation, you can cache the Task object with the completed result:</span></span>  
  
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
  
 <span data-ttu-id="98d6a-291">Tento kód změní typ `cachedResult` na `Task<SyntaxTree>` a využívá `async` pomocnou funkci, která obsahuje původní kód z `GetSyntaxTreeAsync()` .</span><span class="sxs-lookup"><span data-stu-id="98d6a-291">This code changes the type of `cachedResult` to `Task<SyntaxTree>` and employs an `async` helper function that holds the original code from `GetSyntaxTreeAsync()`.</span></span> <span data-ttu-id="98d6a-292">`GetSyntaxTreeAsync()`Nyní pomocí [operátoru slučování null](../../csharp/language-reference/operators/null-coalescing-operator.md) vrátí, `cachedResult` Pokud není null.</span><span class="sxs-lookup"><span data-stu-id="98d6a-292">`GetSyntaxTreeAsync()` now uses the [null coalescing operator](../../csharp/language-reference/operators/null-coalescing-operator.md) to return `cachedResult` if it isn't null.</span></span> <span data-ttu-id="98d6a-293">Pokud `cachedResult` je null, potom `GetSyntaxTreeAsync()` volání `GetSyntaxTreeUncachedAsync()` a uloží výsledek do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="98d6a-293">If `cachedResult` is null, then `GetSyntaxTreeAsync()` calls `GetSyntaxTreeUncachedAsync()` and caches the result.</span></span> <span data-ttu-id="98d6a-294">Všimněte si, že `GetSyntaxTreeAsync()` neočekává volání `GetSyntaxTreeUncachedAsync()` jako kód obvykle.</span><span class="sxs-lookup"><span data-stu-id="98d6a-294">Notice that `GetSyntaxTreeAsync()` doesn’t await the call to `GetSyntaxTreeUncachedAsync()` as the code would normally.</span></span> <span data-ttu-id="98d6a-295">Bez použití operátoru await znamená, že když `GetSyntaxTreeUncachedAsync()` vrátí svůj <xref:System.Threading.Tasks.Task> objekt, `GetSyntaxTreeAsync()` okamžitě vrátí <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="98d6a-295">Not using await means that when `GetSyntaxTreeUncachedAsync()` returns its <xref:System.Threading.Tasks.Task> object, `GetSyntaxTreeAsync()` immediately returns the <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="98d6a-296">Výsledkem je, že v mezipaměti je výsledek <xref:System.Threading.Tasks.Task> , takže neexistují žádné alokace k vrácení výsledku v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="98d6a-296">Now, the cached result is a <xref:System.Threading.Tasks.Task>, so there are no allocations to return the cached result.</span></span>
  
### <a name="additional-considerations"></a><span data-ttu-id="98d6a-297">Další aspekty</span><span class="sxs-lookup"><span data-stu-id="98d6a-297">Additional considerations</span></span>  
 <span data-ttu-id="98d6a-298">Tady je několik dalších bodů, které se týkají potenciálních problémů ve velkých aplikacích nebo aplikacích, které zpracovávají velké množství dat.</span><span class="sxs-lookup"><span data-stu-id="98d6a-298">Here are a few more points about potential problems in large apps or apps that process a lot of data.</span></span>
  
 <span data-ttu-id="98d6a-299">**Slovníky**</span><span class="sxs-lookup"><span data-stu-id="98d6a-299">**Dictionaries**</span></span>  
  
 <span data-ttu-id="98d6a-300">Slovníky se v mnoha programech používají ubiquitously a i když jsou slovníky velmi pohodlné a v podstatě efektivní.</span><span class="sxs-lookup"><span data-stu-id="98d6a-300">Dictionaries are used ubiquitously in many programs, and though dictionaries are very convenient and inherently efficient.</span></span> <span data-ttu-id="98d6a-301">Jsou ale často používány nevhodně.</span><span class="sxs-lookup"><span data-stu-id="98d6a-301">However, they’re often used inappropriately.</span></span> <span data-ttu-id="98d6a-302">V aplikaci Visual Studio a nových kompilátorech ukazuje analýza mnoho slovníků obsahuje jeden element nebo byl prázdný.</span><span class="sxs-lookup"><span data-stu-id="98d6a-302">In Visual Studio and the new compilers, analysis shows that many of the dictionaries contained a single element or were empty.</span></span> <span data-ttu-id="98d6a-303">Prázdné <xref:System.Collections.Generic.Dictionary%602> pole má deset polí a zabírá 48 bajtů v haldě na počítači x86.</span><span class="sxs-lookup"><span data-stu-id="98d6a-303">An empty <xref:System.Collections.Generic.Dictionary%602> has ten fields and occupies 48 bytes on the heap on an x86 machine.</span></span> <span data-ttu-id="98d6a-304">Slovníky jsou skvělé, pokud potřebujete mapování nebo asociativní datovou strukturu s vyhledáváním v čase.</span><span class="sxs-lookup"><span data-stu-id="98d6a-304">Dictionaries are great when you need a mapping or associative data structure with constant-time lookup.</span></span> <span data-ttu-id="98d6a-305">Pokud ale máte jenom několik prvků, zařadíte spoustu místa pomocí slovníku.</span><span class="sxs-lookup"><span data-stu-id="98d6a-305">However, when you have only a few elements, you waste a lot of space by using a dictionary.</span></span> <span data-ttu-id="98d6a-306">Místo toho můžete například iterativním způsobem prohledat `List<KeyValuePair\<K,V>>` , stejně jako rychle.</span><span class="sxs-lookup"><span data-stu-id="98d6a-306">Instead, for example, you could iteratively look through a `List<KeyValuePair\<K,V>>`, just as fast.</span></span> <span data-ttu-id="98d6a-307">Použijete-li slovník pouze k načtení s daty a pak ho z něj přečtete (velmi běžný vzor), může být v závislosti na počtu prvků, které používáte, možná skoro stejně rychlé.</span><span class="sxs-lookup"><span data-stu-id="98d6a-307">If you use a dictionary only to load it with data and then read from it (a very common pattern), using a sorted array with an N(log(N)) lookup might be nearly as fast, depending on the number of elements you're using.</span></span>
  
 <span data-ttu-id="98d6a-308">**Třídy vs. struktury**</span><span class="sxs-lookup"><span data-stu-id="98d6a-308">**Classes vs. structures**</span></span>  
  
 <span data-ttu-id="98d6a-309">V takovém případě třídy a struktury poskytují pro optimalizaci vašich aplikací klasický prostor a čas.</span><span class="sxs-lookup"><span data-stu-id="98d6a-309">In a way, classes and structures provide a classic space/time tradeoff for tuning your apps.</span></span> <span data-ttu-id="98d6a-310">Třídy účtují 12 bajtů režie na počítači x86 i v případě, že nemají žádná pole, ale mají nenákladné předávat, protože přebírají jenom ukazatel na odkazování na instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="98d6a-310">Classes incur 12 bytes of overhead on an x86 machine even if they have no fields, but they are inexpensive to pass around because it only takes a pointer to refer to a class instance.</span></span> <span data-ttu-id="98d6a-311">Struktury neúčtují žádné přidělení haldy, pokud nejsou zabalené, ale pokud předáte velké struktury jako argumenty funkce nebo návratové hodnoty, bere čas procesoru k atomické kopírování všech datových členů struktur.</span><span class="sxs-lookup"><span data-stu-id="98d6a-311">Structures incur no heap allocations if they aren’t boxed, but when you pass large structures as function arguments or return values, it takes CPU time to atomically copy all the data members of the structures.</span></span> <span data-ttu-id="98d6a-312">Podívejte se na opakující se volání vlastností, které vracejí struktury, a do mezipaměti hodnoty vlastnosti v místní proměnné, aby nedocházelo k nadměrnému kopírování dat.</span><span class="sxs-lookup"><span data-stu-id="98d6a-312">Watch out for repeated calls to properties that return structures, and cache the property’s value in a local variable to avoid excessive data copying.</span></span>
  
 <span data-ttu-id="98d6a-313">**Caches**</span><span class="sxs-lookup"><span data-stu-id="98d6a-313">**Caches**</span></span>  
  
 <span data-ttu-id="98d6a-314">Běžným zdvihem výkonu je ukládání výsledků do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="98d6a-314">A common performance trick is to cache results.</span></span> <span data-ttu-id="98d6a-315">Mezipaměť bez omezení velikosti nebo zásad odstraňování ale může být nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="98d6a-315">However, a cache without a size cap or disposal policy can be a memory leak.</span></span> <span data-ttu-id="98d6a-316">Při zpracování velkých objemů dat můžete v případě, že máte v mezipamětech na velké množství paměti, způsobit, že shromažďování paměti přepíše výhody hledání uložených v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="98d6a-316">When processing large amounts of data, if you hold on to a lot of memory in caches, you can cause garbage collection to override the benefits of your cached lookups.</span></span>
  
 <span data-ttu-id="98d6a-317">V tomto článku jsme probrali, jak byste měli být vědomi kritických příznaků výkonu, které mohou ovlivnit rychlost odezvy vaší aplikace, zejména pro velké systémy nebo systémy, které zpracovávají velké množství dat.</span><span class="sxs-lookup"><span data-stu-id="98d6a-317">In this article, we discussed how you should be aware of performance bottleneck symptoms that can affect your app's responsiveness, especially for large systems or systems that process a large amount of data.</span></span> <span data-ttu-id="98d6a-318">Mezi Běžné culprits patří zabalení, manipulace s řetězci, LINQ a lambda, ukládání do mezipaměti v asynchronních metodách, ukládání do mezipaměti bez omezení velikosti nebo zásad vyřazení, nevhodné použití slovníků a předávání okolo struktur.</span><span class="sxs-lookup"><span data-stu-id="98d6a-318">Common culprits include boxing, string manipulations, LINQ and lambda, caching in async methods, caching without a size limit or disposal policy, inappropriate use of dictionaries, and passing around structures.</span></span> <span data-ttu-id="98d6a-319">Mějte na paměti čtyři fakta pro optimalizaci vašich aplikací:</span><span class="sxs-lookup"><span data-stu-id="98d6a-319">Keep in mind the four facts for tuning your apps:</span></span>  
  
- <span data-ttu-id="98d6a-320">Nezralá optimalizace – Buďte produktivní a optimalizujte svou aplikaci při navýšení problémů.</span><span class="sxs-lookup"><span data-stu-id="98d6a-320">Don’t prematurely optimize – be productive and tune your app when you spot problems.</span></span>
  
- <span data-ttu-id="98d6a-321">Profily neleží – Pokud se neměříte, budete odhadem.</span><span class="sxs-lookup"><span data-stu-id="98d6a-321">Profiles don’t lie – you’re guessing if you’re not measuring.</span></span>
  
- <span data-ttu-id="98d6a-322">Dobré nástroje provedou všechny rozdíly – Stáhněte si PerfView a vyzkoušejte si to.</span><span class="sxs-lookup"><span data-stu-id="98d6a-322">Good tools make all the difference – download PerfView and try it out.</span></span>
  
- <span data-ttu-id="98d6a-323">Je to vše o přidělení – to znamená, že tým platformy pro kompilátor vytrvalo většinu času, který zlepšuje výkon nových kompilátorů.</span><span class="sxs-lookup"><span data-stu-id="98d6a-323">It's all about allocations – that is where the compiler platform team spent most of their time improving the performance of the new compilers.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="98d6a-324">Viz také</span><span class="sxs-lookup"><span data-stu-id="98d6a-324">See also</span></span>

- [<span data-ttu-id="98d6a-325">Video o prezentaci tohoto tématu</span><span class="sxs-lookup"><span data-stu-id="98d6a-325">Video of presentation of this topic</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [<span data-ttu-id="98d6a-326">Příručka pro začátečníky k profilaci výkonu</span><span class="sxs-lookup"><span data-stu-id="98d6a-326">Beginners Guide to Performance Profiling</span></span>](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [<span data-ttu-id="98d6a-327">Výkon</span><span class="sxs-lookup"><span data-stu-id="98d6a-327">Performance</span></span>](index.md)
- <span data-ttu-id="98d6a-328">[Tipy pro zvýšení výkonu rozhraní .NET](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))</span><span class="sxs-lookup"><span data-stu-id="98d6a-328">[.NET Performance Tips](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))</span></span>
- [<span data-ttu-id="98d6a-329">Kurzy PerfView pro Channel 9</span><span class="sxs-lookup"><span data-stu-id="98d6a-329">Channel 9 PerfView tutorials</span></span>](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [<span data-ttu-id="98d6a-330">Sada .NET Compiler Platform SDK</span><span class="sxs-lookup"><span data-stu-id="98d6a-330">The .NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="98d6a-331">dotnet/Roslyn úložiště na GitHubu</span><span class="sxs-lookup"><span data-stu-id="98d6a-331">dotnet/roslyn repo on GitHub</span></span>](https://github.com/dotnet/roslyn)
