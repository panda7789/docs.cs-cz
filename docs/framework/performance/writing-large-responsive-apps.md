---
title: Psaní velkých a pohotově reagujících aplikací .NET Framework
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03c2620913aff2ef2934e7c07574c130923c7139
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540660"
---
# <a name="writing-large-responsive-net-framework-apps"></a><span data-ttu-id="e9b41-102">Psaní velkých a pohotově reagujících aplikací .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e9b41-102">Writing Large, Responsive .NET Framework Apps</span></span>
<span data-ttu-id="e9b41-103">Tento článek poskytuje tipy pro zvýšení výkonu velkých aplikací rozhraní .NET Framework nebo aplikace, které zpracovávají velké množství dat, jako jsou soubory nebo databáze.</span><span class="sxs-lookup"><span data-stu-id="e9b41-103">This article provides tips for improving the performance of large .NET Framework apps, or apps that process a large amount of data such as files or databases.</span></span> <span data-ttu-id="e9b41-104">Tyto tipy pocházejí z přepsání kompilátory C# i Visual Basic ve spravovaném kódu a tento článek obsahuje několik skutečné příklady z kompilátoru jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e9b41-104">These tips come from rewriting the C# and Visual Basic compilers in managed code, and this article includes several real examples from the C# compiler.</span></span> 
  
 <span data-ttu-id="e9b41-105">Rozhraní .NET Framework je vysoce produktivní pro vytváření aplikací.</span><span class="sxs-lookup"><span data-stu-id="e9b41-105">The .NET Framework is highly productive for building apps.</span></span> <span data-ttu-id="e9b41-106">Jazyky výkonný a bezpečný a bohaté kolekci knihoven je vytváření aplikací s vysokou plodný.</span><span class="sxs-lookup"><span data-stu-id="e9b41-106">Powerful and safe languages and a rich collection of libraries make app building highly fruitful.</span></span> <span data-ttu-id="e9b41-107">S skvělé kancelářské dodává odpovědnost.</span><span class="sxs-lookup"><span data-stu-id="e9b41-107">However, with great productivity comes responsibility.</span></span> <span data-ttu-id="e9b41-108">By měl používat všechny funkce rozhraní .NET Framework, ale buďte připraveni vyladit výkon vašeho kódu v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="e9b41-108">You should use all the power of the .NET Framework, but be prepared to tune your code’s performance when needed.</span></span> 
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a><span data-ttu-id="e9b41-109">Proč nový kompilátor výkonu platí pro vaši aplikaci</span><span class="sxs-lookup"><span data-stu-id="e9b41-109">Why the new compiler performance applies to your app</span></span>  
 <span data-ttu-id="e9b41-110">Tým .NET Compiler Platform ("Roslyn") rewrote jazyka C# a kompilátory jazyka Visual Basic v spravovaného kódu k poskytnutí nových rozhraní API pro modelování a analýza kódu, nástroje pro sestavování a umožňuje provoz mnohem širší, s ohledem na kód v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e9b41-110">The .NET Compiler Platform ("Roslyn") team rewrote the C# and Visual Basic compilers in managed code to provide new APIs for modeling and analyzing code, building tools, and enabling much richer, code-aware experiences in Visual Studio.</span></span> <span data-ttu-id="e9b41-111">Přepisování kompilátory a sestavování sady Visual Studio prostředí na nových kompilátory zjistí informace o užitečné výkonu, které se vztahují na všechny velké aplikace rozhraní .NET Framework nebo jakékoli aplikaci, která zpracovává velké množství dat.</span><span class="sxs-lookup"><span data-stu-id="e9b41-111">Rewriting the compilers and building Visual Studio experiences on the new compilers revealed useful performance insights that are applicable to any large .NET Framework app or any app that processes a lot of data.</span></span> <span data-ttu-id="e9b41-112">Nemusíte vědět o kompilátory využijte postřehů a příklady z kompilátoru jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e9b41-112">You don't need to know about compilers to take advantage of the insights and examples from the C# compiler.</span></span> 
  
 <span data-ttu-id="e9b41-113">Visual Studio používá kompilátor rozhraní API k vytvoření všechny funkce technologie IntelliSense, které máte rádi uživatele, například podtržení vlnovkou zabarvení identifikátory a klíčová slova, seznamy dokončení syntaxe, pro chyby, parametr tipy, potíží s kódem a akce kódu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-113">Visual Studio uses the compiler APIs to build all the IntelliSense features that users love, such as colorization of identifiers and keywords, syntax completion lists, squiggles for errors, parameter tips, code issues, and code actions.</span></span> <span data-ttu-id="e9b41-114">Visual Studio poskytuje tuto nápovědu, zatímco jsou vývojáři psát a měnit jejich kód a sady Visual Studio musí stále reagovat, zatímco kompilátor průběžně modely kód, který vývojářům upravit.</span><span class="sxs-lookup"><span data-stu-id="e9b41-114">Visual Studio provides this help while developers are typing and changing their code, and Visual Studio must remain responsive while the compiler continually models the code developers edit.</span></span> 
  
 <span data-ttu-id="e9b41-115">Když koncoví uživatelé pracovat s vaší aplikací, očekávané bude reagovat.</span><span class="sxs-lookup"><span data-stu-id="e9b41-115">When your end users interact with your app, they expect it to be responsive.</span></span> <span data-ttu-id="e9b41-116">Nikdy by se zablokovat zadáním nebo zpracování příkazu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-116">Typing or command handling should never be blocked.</span></span> <span data-ttu-id="e9b41-117">Nápovědu by měl automaticky otevře, rychle nebo vzdát-li i nadále uživatele při psaní.</span><span class="sxs-lookup"><span data-stu-id="e9b41-117">Help should pop up quickly or give up if the user continues typing.</span></span> <span data-ttu-id="e9b41-118">Vaše aplikace by měl předcházet zablokování vlákna uživatelského rozhraní s dlouhou výpočty, které aplikace může.</span><span class="sxs-lookup"><span data-stu-id="e9b41-118">Your app should avoid blocking the UI thread with long computations that make the app feel sluggish.</span></span> 
  
 <span data-ttu-id="e9b41-119">Další informace o kompilátory Roslyn najdete v tématu [sada SDK platformy kompilátoru .NET](../../csharp/roslyn-sdk/index.md).</span><span class="sxs-lookup"><span data-stu-id="e9b41-119">For more information about Roslyn compilers, see [The .NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md).</span></span>
  
## <a name="just-the-facts"></a><span data-ttu-id="e9b41-120">Pouze fakty</span><span class="sxs-lookup"><span data-stu-id="e9b41-120">Just the Facts</span></span>  
 <span data-ttu-id="e9b41-121">Vezměte v úvahu následující skutečnosti při ladění výkonu a vytváření přizpůsobivých aplikací rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e9b41-121">Consider these facts when tuning performance and creating responsive .NET Framework apps.</span></span> 
  
### <a name="fact-1-dont-prematurely-optimize"></a><span data-ttu-id="e9b41-122">Fakt 1: Neoptimalizovat předčasně ukončen.</span><span class="sxs-lookup"><span data-stu-id="e9b41-122">Fact 1: Don’t prematurely optimize</span></span>  
 <span data-ttu-id="e9b41-123">Psaní kódu, který je složitější, než se musí se jednat o vznikají náklady na údržbu, ladění a leštění náklady.</span><span class="sxs-lookup"><span data-stu-id="e9b41-123">Writing code that is more complex than it needs to be incurs maintenance, debugging, and polishing costs.</span></span> <span data-ttu-id="e9b41-124">Zkušení programátoři mít intuitivní pochopit, jak vyřešit problémy psaní kódu a psaní kódu efektivnější.</span><span class="sxs-lookup"><span data-stu-id="e9b41-124">Experienced programmers have an intuitive grasp of how to solve coding problems and write more efficient code.</span></span> <span data-ttu-id="e9b41-125">Ale jsou někdy předčasně optimalizovat svůj kód.</span><span class="sxs-lookup"><span data-stu-id="e9b41-125">However, they sometimes prematurely optimize their code.</span></span> <span data-ttu-id="e9b41-126">Například používají tabulku hash při jednoduchém poli by stačit, nebo použijte složité ukládání do mezipaměti, který může nastat únik paměti namísto jednoduše recomputing hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e9b41-126">For example, they use a hash table when a simple array would suffice, or use complicated caching that may leak memory instead of simply recomputing values.</span></span> <span data-ttu-id="e9b41-127">I v případě, že jste programátor prostředí, by měl test výkonu a analýzu kódu při vyhledání potíží.</span><span class="sxs-lookup"><span data-stu-id="e9b41-127">Even if you’re an experience programmer, you should test for performance and analyze your code when you find issues.</span></span> 
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a><span data-ttu-id="e9b41-128">Fakt 2: Pokud nejsou měření, že uhodnutí</span><span class="sxs-lookup"><span data-stu-id="e9b41-128">Fact 2: If you’re not measuring, you’re guessing</span></span>  
 <span data-ttu-id="e9b41-129">Nemusíte být profily a měření.</span><span class="sxs-lookup"><span data-stu-id="e9b41-129">Profiles and measurements don’t lie.</span></span> <span data-ttu-id="e9b41-130">Profily ukazují, jestli CPU je plně načten nebo určuje, zda jste blokováno při vstupně-výstupních operací disku.</span><span class="sxs-lookup"><span data-stu-id="e9b41-130">Profiles show you whether the CPU is fully loaded or whether you’re blocked on disk I/O.</span></span> <span data-ttu-id="e9b41-131">Profily můžete zjistit, jaký typ a kolik paměti máte přidělení a zda procesoru tráví spoustu času v [uvolňování](../../../docs/standard/garbage-collection/index.md) (GC).</span><span class="sxs-lookup"><span data-stu-id="e9b41-131">Profiles tell you what kind and how much memory you’re allocating and whether your CPU is spending a lot of time in [garbage collection](../../../docs/standard/garbage-collection/index.md) (GC).</span></span> 
  
 <span data-ttu-id="e9b41-132">By měl nastavit prostředí nebo scénáře výkonnostních cílů pro zákazníků ve vaší aplikaci a psaní testů k měření výkonu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-132">You should set performance goals for key customer experiences or scenarios in your app and write tests to measure performance.</span></span> <span data-ttu-id="e9b41-133">Prozkoumat selhání testů s použitím vědecké metody: použití profilů na vás, co může být problém, vyslovují hypotézy o jejich a testovat vaše hypotézu s experiment nebo změny kódu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-133">Investigate failing tests by applying the scientific method: use profiles to guide you, hypothesize what the issue might be, and test your hypothesis with an experiment or code change.</span></span> <span data-ttu-id="e9b41-134">Vytvořte standardní hodnoty měření výkonu v čase s pravidelné testování tak může izolovat změny, které způsobují regrese výkonu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-134">Establish baseline performance measurements over time with regular testing, so you can isolate changes that cause regressions in performance.</span></span> <span data-ttu-id="e9b41-135">Výkon pracovních blíží přísné způsobem, budete vyhnete plýtvání časem se aktualizace kódu, které nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="e9b41-135">By approaching performance work in a rigorous way, you’ll avoid wasting time with code updates you don’t need.</span></span> 
  
### <a name="fact-3-good-tools-make-all-the-difference"></a><span data-ttu-id="e9b41-136">Fakt 3: Vhodné nástroje vytvářejí všechny rozdíl</span><span class="sxs-lookup"><span data-stu-id="e9b41-136">Fact 3: Good tools make all the difference</span></span>  
 <span data-ttu-id="e9b41-137">Vhodné nástroje umožňují rychle přejít k největší problémy s výkonem (procesor, paměť nebo disk) a pomohou vyhledat kód, který způsobí, že tyto kritické body.</span><span class="sxs-lookup"><span data-stu-id="e9b41-137">Good tools let you drill quickly into the biggest performance issues (CPU, memory, or disk) and help you locate the code that causes those bottlenecks.</span></span> <span data-ttu-id="e9b41-138">Microsoft se dodává s celou řadou nástrojů výkonu, jako [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling), [nástroj pro analýzu Windows Phone](https://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f), a [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span><span class="sxs-lookup"><span data-stu-id="e9b41-138">Microsoft ships a variety of performance tools such as [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling), [Windows Phone Analysis Tool](https://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f), and [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span></span> 
  
 <span data-ttu-id="e9b41-139">PerfView je zadarmo. je neuvěřitelně výkonné nástroj, který pomůže zaměřit se na podrobné problémy, jako je / v disku, GC – události a paměti.</span><span class="sxs-lookup"><span data-stu-id="e9b41-139">PerfView is a free and amazingly powerful tool that helps you focus on deep issues such as disk I/O, GC events, and memory.</span></span> <span data-ttu-id="e9b41-140">Můžete zaznamenat související s výkonem [události trasování pro Windows](../../../docs/framework/wcf/samples/etw-tracing.md) událostí (ETW) a zobrazení snadno na aplikaci, proces, na zásobníku a na informace o vlákně.</span><span class="sxs-lookup"><span data-stu-id="e9b41-140">You can capture performance-related [Event Tracing for Windows](../../../docs/framework/wcf/samples/etw-tracing.md) (ETW) events and view easily per app, per process, per stack, and per thread information.</span></span> <span data-ttu-id="e9b41-141">PerfView ukazuje, kolik a jaký druh paměti přidělí vaši aplikaci a které funkce nebo volání zásobníků přispívat množství služeb pro přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="e9b41-141">PerfView shows you how much and what kind of memory your app allocates, and which functions or call stacks contribute how much to the memory allocations.</span></span> <span data-ttu-id="e9b41-142">Podrobnosti najdete v tématu bohaté témata nápovědy, ukázky a videa, které jsou součástí nástroje (například [PerfView kurzy](https://channel9.msdn.com/Series/PerfView-Tutorial) na webu Channel 9).</span><span class="sxs-lookup"><span data-stu-id="e9b41-142">For details, see the rich help topics, demos, and videos included with the tool (such as the [PerfView tutorials](https://channel9.msdn.com/Series/PerfView-Tutorial) on Channel 9).</span></span> 
  
### <a name="fact-4-its-all-about-allocations"></a><span data-ttu-id="e9b41-143">Fakt 4: Všechno se točí kolem přidělení</span><span class="sxs-lookup"><span data-stu-id="e9b41-143">Fact 4: It’s all about allocations</span></span>  
 <span data-ttu-id="e9b41-144">Si možná myslíte, že vytváření rychlou odezvou aplikace rozhraní .NET Framework se točí kolem algoritmy, například pomocí rychlé řazení namísto bublinu řazení, ale to není případ.</span><span class="sxs-lookup"><span data-stu-id="e9b41-144">You might think that building a responsive .NET Framework app is all about algorithms, such as using quick sort instead of bubble sort, but that's not the case.</span></span> <span data-ttu-id="e9b41-145">Největší faktorem při vytváření responzivní aplikace je přidělování paměti, zejména v případě, že vaše aplikace je moc velká, nebo zpracovává velké objemy dat.</span><span class="sxs-lookup"><span data-stu-id="e9b41-145">The biggest factor in building a responsive app is allocating memory, especially when your app is very large or processes large amounts of data.</span></span> 
  
 <span data-ttu-id="e9b41-146">Téměř všechny pracovní vytvářet interaktivní IDE prostředí kompilátor nové rozhraní API podílejí vyhnout rozdělení a správu strategií ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e9b41-146">Almost all the work to build responsive IDE experiences with the new compiler APIs involved avoiding allocations and managing caching strategies.</span></span> <span data-ttu-id="e9b41-147">Trasování PerfView zobrazení výkonu nové kompilátory C# a Visual Basic je málokdy závislá na procesoru.</span><span class="sxs-lookup"><span data-stu-id="e9b41-147">PerfView traces show that the performance of the new C# and Visual Basic compilers is rarely CPU bound.</span></span> <span data-ttu-id="e9b41-148">Kompilátory mohou být vstupně-výstupní operace při čtení stovky, tisíce nebo miliony řádků kódu, vázaná čtení metadat, nebo výstupu generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-148">The compilers can be I/O bound when reading hundreds of thousands or millions of lines of code, reading metadata, or emitting generated code.</span></span> <span data-ttu-id="e9b41-149">Uživatelské rozhraní se zpozdí vlákna jsou téměř všechny kvůli uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e9b41-149">The UI thread delays are nearly all due to garbage collection.</span></span> <span data-ttu-id="e9b41-150">Uvolňování paměti rozhraní .NET Framework je vysoce optimalizovaných pro výkon a udělá velkou část práce současně, zatímco spustí kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9b41-150">The .NET Framework GC is highly tuned for performance and does much of its work concurrently while app code executes.</span></span> <span data-ttu-id="e9b41-151">Však můžete aktivovat jednu alokovanou nákladné [gen2](../../../docs/standard/garbage-collection/fundamentals.md) kolekce zastavení všech vláken.</span><span class="sxs-lookup"><span data-stu-id="e9b41-151">However, a single allocation can trigger an expensive [gen2](../../../docs/standard/garbage-collection/fundamentals.md) collection, stopping all threads.</span></span> 
  
## <a name="common-allocations-and-examples"></a><span data-ttu-id="e9b41-152">Běžné přidělení a příklady</span><span class="sxs-lookup"><span data-stu-id="e9b41-152">Common allocations and examples</span></span>  
 <span data-ttu-id="e9b41-153">Příklady výrazů v této části jsou skryté přidělení, které se zobrazí malá.</span><span class="sxs-lookup"><span data-stu-id="e9b41-153">The example expressions in this section have hidden allocations that appear small.</span></span> <span data-ttu-id="e9b41-154">Pokud velké aplikace provede výrazy dostatek vícekrát, ale mohou způsobí, že stovek megabajtů, dokonce i gigabajtů přidělení.</span><span class="sxs-lookup"><span data-stu-id="e9b41-154">However, if a large app executes the expressions enough times, they can causes hundreds of megabytes, even gigabytes, of allocations.</span></span> <span data-ttu-id="e9b41-155">Například minutu trvající testy, které simulované vývojáře psaní v editoru gigabajtů paměti přidělené a vedla tým výkonu a zaměřte se na psaní scénáře.</span><span class="sxs-lookup"><span data-stu-id="e9b41-155">For example, one-minute tests that simulated a developer’s typing in the editor allocated gigabytes of memory and led the performance team to focus on typing scenarios.</span></span> 
  
### <a name="boxing"></a><span data-ttu-id="e9b41-156">Zabalení</span><span class="sxs-lookup"><span data-stu-id="e9b41-156">Boxing</span></span>  
 <span data-ttu-id="e9b41-157">[Zabalení](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) nastane, pokud hodnota typy, které obvykle za provozu v zásobníku nebo v datové struktury jsou zabaleny v objektu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-157">[Boxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) occurs when value types that normally live on the stack or in data structures are wrapped in an object.</span></span> <span data-ttu-id="e9b41-158">To znamená přidělit objekt pro uložení dat a pak se vraťte ukazatel na objekt.</span><span class="sxs-lookup"><span data-stu-id="e9b41-158">That is, you allocate an object to hold the data, and then return a pointer to the object.</span></span> <span data-ttu-id="e9b41-159">Rozhraní .NET Framework někdy pole hodnot, protože signatura metody nebo typu umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="e9b41-159">The .NET Framework sometimes boxes values due to the signature of a method or the type of a storage location.</span></span> <span data-ttu-id="e9b41-160">Zabalení typu hodnoty během přidělování paměti způsobí, že objekt.</span><span class="sxs-lookup"><span data-stu-id="e9b41-160">Wrapping a value type in an object causes memory allocation.</span></span> <span data-ttu-id="e9b41-161">Mnoho operací zabalení může přispět, megabajtech nebo gigabajtech přidělení do vaší aplikace, což znamená, že vaše aplikace způsobí, že další GC.</span><span class="sxs-lookup"><span data-stu-id="e9b41-161">Many boxing operations can contribute megabytes or gigabytes of allocations to your app, which means that your app will cause more GCs.</span></span> <span data-ttu-id="e9b41-162">Rozhraní .NET Framework a kompilátory jazyka vyhnout zabalení, pokud je to možné, ale někdy to se stane, když očekáváte nejméně.</span><span class="sxs-lookup"><span data-stu-id="e9b41-162">The .NET Framework and the language compilers avoid boxing when possible, but sometimes it happens when you least expect it.</span></span> 
  
 <span data-ttu-id="e9b41-163">Zabalení v PerfView zobrazíte otevřít trasování a podívejte se na zásobníky alokační haldy GC v rámci vaší aplikace, název procesu (Nezapomeňte, že PerfView sestavy o všech procesů).</span><span class="sxs-lookup"><span data-stu-id="e9b41-163">To see boxing in PerfView, open a trace and look at GC Heap Alloc Stacks under your app’s process name (remember, PerfView reports on all processes).</span></span> <span data-ttu-id="e9b41-164">Pokud se zobrazí typy jako <xref:System.Int32?displayProperty=nameWithType> a <xref:System.Char?displayProperty=nameWithType> v rámci přidělených jsou zabalení typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="e9b41-164">If you see types like <xref:System.Int32?displayProperty=nameWithType> and <xref:System.Char?displayProperty=nameWithType> under allocations, you are boxing value types.</span></span> <span data-ttu-id="e9b41-165">Výběrem jedné z těchto typů zobrazí zásobníky a funkce, ve kterých jsou zabaleny.</span><span class="sxs-lookup"><span data-stu-id="e9b41-165">Choosing one of these types will show the stacks and functions in which they are boxed.</span></span> 
  
 <span data-ttu-id="e9b41-166">**Příklad 1: řetězcových metod a hodnotu argumentů**</span><span class="sxs-lookup"><span data-stu-id="e9b41-166">**Example 1: string methods and value type arguments**</span></span>  
  
 <span data-ttu-id="e9b41-167">Tento ukázkový kód ukazuje potenciálně zbytečné a rostly zabalení:</span><span class="sxs-lookup"><span data-stu-id="e9b41-167">This sample code illustrates potentially unnecessary and excessive boxing:</span></span>  
  
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
  
 <span data-ttu-id="e9b41-168">Tento kód poskytuje funkce protokolování, takže aplikace mohou volat `Log` funkce často, možná miliony časy.</span><span class="sxs-lookup"><span data-stu-id="e9b41-168">This code provides logging functionality, so an app may call the `Log` function frequently, maybe millions of times.</span></span> <span data-ttu-id="e9b41-169">Problém je, že volání `string.Format` překládá <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> přetížení.</span><span class="sxs-lookup"><span data-stu-id="e9b41-169">The problem is that the call to `string.Format` resolves to the <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> overload.</span></span> 
  
 <span data-ttu-id="e9b41-170">Toto přetížení vyžaduje rozhraní .NET Framework do pole `int` hodnoty do objektů předejte toto volání metody.</span><span class="sxs-lookup"><span data-stu-id="e9b41-170">This overload requires the .NET Framework to box the `int` values into objects to pass them to this method call.</span></span> <span data-ttu-id="e9b41-171">Částečné opravy je volání `id.ToString()` a `size.ToString()` a všechny řetězce (které jsou objekty) předat `string.Format` volání.</span><span class="sxs-lookup"><span data-stu-id="e9b41-171">A partial fix is to call `id.ToString()` and `size.ToString()` and pass all strings (which are objects) to the `string.Format` call.</span></span> <span data-ttu-id="e9b41-172">Volání `ToString()` přidělit řetězce, ale, že přidělování bude přesto došlo v `string.Format`.</span><span class="sxs-lookup"><span data-stu-id="e9b41-172">Calling `ToString()` does allocate a string, but that allocation will happen anyway inside `string.Format`.</span></span> 
  
 <span data-ttu-id="e9b41-173">Můžete zvážit, který tuto základní volání `string.Format` je právě zřetězení řetězců, takže místo toho můžete například napsat tento kód:</span><span class="sxs-lookup"><span data-stu-id="e9b41-173">You might consider that this basic call to `string.Format` is just string concatenation, so you might write this code instead:</span></span>  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 <span data-ttu-id="e9b41-174">Však tento řádek kódu zavádí zabalení přidělení, protože zkompiluje pro <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="e9b41-174">However, that line of code introduces a boxing allocation because it compiles to <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span></span> <span data-ttu-id="e9b41-175">Rozhraní .NET Framework musí pole znakový literál k vyvolání `Concat`</span><span class="sxs-lookup"><span data-stu-id="e9b41-175">The .NET Framework must box the character literal to invoke `Concat`</span></span>  
  
 <span data-ttu-id="e9b41-176">**Oprava Příklad 1**</span><span class="sxs-lookup"><span data-stu-id="e9b41-176">**Fix for example 1**</span></span>  
  
 <span data-ttu-id="e9b41-177">Dokončení opravy je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="e9b41-177">The complete fix is simple.</span></span> <span data-ttu-id="e9b41-178">Stačí nahradíte literálu s řetězcovým literálem, znak, který protože řetězce jsou již objekty s sebou nese náklady bez zabalení:</span><span class="sxs-lookup"><span data-stu-id="e9b41-178">Just replace the character literal with a string literal, which incurs no boxing because strings are already objects:</span></span>  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 <span data-ttu-id="e9b41-179">**Příklad 2: zabalení výčtu**</span><span class="sxs-lookup"><span data-stu-id="e9b41-179">**Example 2: enum boxing**</span></span>  
  
 <span data-ttu-id="e9b41-180">V tomto příkladu je odpovědná za obrovské množství přidělení v nové kompilátory C# a Visual Basic z důvodu často používají výčtové typy, zejména ve slovníku operace vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="e9b41-180">This example was responsible for a huge amount of allocation in the new C# and Visual Basic compilers due to frequent use of enumeration types, especially in dictionary lookup operations.</span></span> 
  
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
  
 <span data-ttu-id="e9b41-181">Tento problém je velmi malý.</span><span class="sxs-lookup"><span data-stu-id="e9b41-181">This problem is very subtle.</span></span> <span data-ttu-id="e9b41-182">PerfView zasílat zprávy jako <xref:System.Enum.GetHashCode> zabalení, protože metoda polích podkladové reprezentace typu výčtu důvodů implementace.</span><span class="sxs-lookup"><span data-stu-id="e9b41-182">PerfView would report this as <xref:System.Enum.GetHashCode> boxing because the method boxes the underlying representation of the enumeration type, for implementation reasons.</span></span> <span data-ttu-id="e9b41-183">Úzce podíváte v PerfView, může se zobrazit dvě zabalení přidělení pro každé volání <xref:System.Enum.GetHashCode>.</span><span class="sxs-lookup"><span data-stu-id="e9b41-183">If you look closely in PerfView, you may see two boxing allocations for each call to <xref:System.Enum.GetHashCode>.</span></span> <span data-ttu-id="e9b41-184">Kompilátor vloží jednu a rozhraní .NET Framework vloží druhé.</span><span class="sxs-lookup"><span data-stu-id="e9b41-184">The compiler inserts one, and the .NET Framework inserts the other.</span></span> 
  
 <span data-ttu-id="e9b41-185">**Oprava například 2**</span><span class="sxs-lookup"><span data-stu-id="e9b41-185">**Fix for example 2**</span></span>  
  
 <span data-ttu-id="e9b41-186">Můžete snadno vyhnout obou přidělení přetypování na podkladové reprezentace před voláním <xref:System.Enum.GetHashCode>:</span><span class="sxs-lookup"><span data-stu-id="e9b41-186">You can easily avoid both allocations by casting to the underlying representation before calling <xref:System.Enum.GetHashCode>:</span></span>  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 <span data-ttu-id="e9b41-187">Další běžné příčiny zabalení na typy výčtu je <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e9b41-187">Another common source of boxing on enumeration types is the <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e9b41-188">Argument předaný do <xref:System.Enum.HasFlag%28System.Enum%29> musí být pevně určený.</span><span class="sxs-lookup"><span data-stu-id="e9b41-188">The argument passed to <xref:System.Enum.HasFlag%28System.Enum%29> has to be boxed.</span></span> <span data-ttu-id="e9b41-189">Ve většině případů, nahraďte volání <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> bitový testu je jednodušší a bez přidělení.</span><span class="sxs-lookup"><span data-stu-id="e9b41-189">In most cases, replacing calls to <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> with a bitwise test is simpler and allocation-free.</span></span> 
  
 <span data-ttu-id="e9b41-190">První fakt výkonu mějte na paměti (to znamená, neoptimalizovat předčasně ukončen) a nespouštět přepisování váš kód tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="e9b41-190">Keep the first performance fact in mind (that is, don’t prematurely optimize) and don’t start rewriting all your code in this way.</span></span> <span data-ttu-id="e9b41-191">Mějte na náklady na tyto zabalení, ale změna kódu až po profilování vaší aplikace a vyhledání aktivní body.</span><span class="sxs-lookup"><span data-stu-id="e9b41-191">Be aware of these boxing costs, but change your code only after profiling your app and finding the hot spots.</span></span> 
  
### <a name="strings"></a><span data-ttu-id="e9b41-192">Řetězce</span><span class="sxs-lookup"><span data-stu-id="e9b41-192">Strings</span></span>  
 <span data-ttu-id="e9b41-193">Manipulace s řetězci jsou některé z největších culprits pro přidělení a často zobrazí v PerfView v pěti hlavních přidělení.</span><span class="sxs-lookup"><span data-stu-id="e9b41-193">String manipulations are some of the biggest culprits for allocations, and they often show up in PerfView in the top five allocations.</span></span> <span data-ttu-id="e9b41-194">Programy pomocí řetězce pro serializaci JSON a REST API.</span><span class="sxs-lookup"><span data-stu-id="e9b41-194">Programs use strings for serialization, JSON, and REST APIs.</span></span> <span data-ttu-id="e9b41-195">Řetězce můžete použít jako programový konstanty pro spolupráci s systémy, pokud nelze použít typy výčtu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-195">You can use strings as programmatic constants for interoperating with systems when you can’t use enumeration types.</span></span> <span data-ttu-id="e9b41-196">Pokud vaše profilování ukazuje řetězce vysoce ovlivňuje výkon, vyhledejte volání <xref:System.String> metody jako <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e9b41-196">When your profiling shows that strings are highly affecting performance, look for calls to <xref:System.String> methods such as <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, and so on.</span></span> <span data-ttu-id="e9b41-197">Pomocí <xref:System.Text.StringBuilder> náklady na vytvoření jednoho řetězce z mnoha pomáhá kusů, ale i přidělování, aby <xref:System.Text.StringBuilder> objekt může být kritickým bodem, který je potřeba spravovat.</span><span class="sxs-lookup"><span data-stu-id="e9b41-197">Using <xref:System.Text.StringBuilder> to avoid the cost of creating one string from many pieces helps, but even allocating the <xref:System.Text.StringBuilder> object might become a bottleneck that you need to manage.</span></span> 
  
 <span data-ttu-id="e9b41-198">**Příklad 3: operace s řetězci**</span><span class="sxs-lookup"><span data-stu-id="e9b41-198">**Example 3: string operations**</span></span>  
  
 <span data-ttu-id="e9b41-199">Kompilátor jazyka C# má tento kód, který zapíše text formátovaný komentář dokumentace XML:</span><span class="sxs-lookup"><span data-stu-id="e9b41-199">The C# compiler had this code that writes the text of a formatted XML doc comment:</span></span>  
  
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
  
 <span data-ttu-id="e9b41-200">Uvidíte, že tento kód provádí spoustu zacházení s řetězci.</span><span class="sxs-lookup"><span data-stu-id="e9b41-200">You can see that this code does a lot of string manipulation.</span></span> <span data-ttu-id="e9b41-201">Tento kód použije metody knihovny rozdělit řádky do samostatných řetězců, oříznout prázdný znak, chcete-li zkontrolovat, zda je argument `text` je komentáře dokumentace XML a k extrahování podřetězců z řádků.</span><span class="sxs-lookup"><span data-stu-id="e9b41-201">The code uses library methods to split lines into separate strings, to trim white space, to check whether the argument `text` is an XML documentation comment, and to extract substrings from lines.</span></span> 
  
 <span data-ttu-id="e9b41-202">Na prvním řádku uvnitř `WriteFormattedDocComment`, `text.Split` volání pokaždé, když je volána přidělí nové pole třech prvcích jako argument.</span><span class="sxs-lookup"><span data-stu-id="e9b41-202">On the first line inside `WriteFormattedDocComment`, the `text.Split` call allocates a new three-element array as the argument every time it’s called.</span></span> <span data-ttu-id="e9b41-203">Generovat kód pro přidělení pokaždé, když toto pole má kompilátor.</span><span class="sxs-lookup"><span data-stu-id="e9b41-203">The compiler has to emit code to allocate this array each time.</span></span> <span data-ttu-id="e9b41-204">Důvodem je, že kompilátor nebude vědět, pokud <xref:System.String.Split%2A> ukládá pole někde ve kterém může upravit pole jiným kódem, který bude mít vliv na pozdější volání `WriteFormattedDocComment`.</span><span class="sxs-lookup"><span data-stu-id="e9b41-204">That’s because the compiler doesn’t know if <xref:System.String.Split%2A> stores the array somewhere where the array might be modified by other code, which would affect later calls to `WriteFormattedDocComment`.</span></span> <span data-ttu-id="e9b41-205">Volání <xref:System.String.Split%2A> také přiděluje řetězec pro každý řádek v `text` a přiděluje další paměť k provedení této operace.</span><span class="sxs-lookup"><span data-stu-id="e9b41-205">The call to <xref:System.String.Split%2A> also allocates a string for every line in `text` and allocates other memory to perform the operation.</span></span> 
  
 <span data-ttu-id="e9b41-206">`WriteFormattedDocComment` má tři volání <xref:System.String.TrimStart%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e9b41-206">`WriteFormattedDocComment` has three calls to the <xref:System.String.TrimStart%2A> method.</span></span> <span data-ttu-id="e9b41-207">Jsou dva ve vnitřní smyčky, které duplikují práce a přidělení.</span><span class="sxs-lookup"><span data-stu-id="e9b41-207">Two are in inner loops that duplicate work and allocations.</span></span> <span data-ttu-id="e9b41-208">Aby věcech ještě hůř, volání <xref:System.String.TrimStart%2A> metoda bez argumentů přiděluje prázdné pole (pro `params` parametr) kromě výsledek řetězce.</span><span class="sxs-lookup"><span data-stu-id="e9b41-208">To make matters worse, calling the <xref:System.String.TrimStart%2A> method with no arguments allocates an empty array (for the `params` parameter) in addition to the string result.</span></span> 
  
 <span data-ttu-id="e9b41-209">Součástí je volání <xref:System.String.Substring%2A> metodu, která obvykle přiděluje nový řetězec.</span><span class="sxs-lookup"><span data-stu-id="e9b41-209">Lastly, there is a call to the <xref:System.String.Substring%2A> method, which usually allocates a new string.</span></span> 
  
 <span data-ttu-id="e9b41-210">**Oprava například 3**</span><span class="sxs-lookup"><span data-stu-id="e9b41-210">**Fix for example 3**</span></span>  
  
 <span data-ttu-id="e9b41-211">Na rozdíl od předchozích příkladech nelze opravit malými úpravami tyto přidělení.</span><span class="sxs-lookup"><span data-stu-id="e9b41-211">Unlike the earlier examples, small edits cannot fix these allocations.</span></span> <span data-ttu-id="e9b41-212">Potřebujete chcete zastav, podívejte se na problém a postupovat jinak.</span><span class="sxs-lookup"><span data-stu-id="e9b41-212">You need to step back, look at the problem, and approach it differently.</span></span> <span data-ttu-id="e9b41-213">Například, uvidíte, že argument `WriteFormattedDocComment()` je řetězec, který obsahuje všechny informace, které potřebuje metodě, takže kód by mohl provést další indexování namísto přidělení mnoho částečné řetězce.</span><span class="sxs-lookup"><span data-stu-id="e9b41-213">For example, you'll notice that the argument to `WriteFormattedDocComment()` is a string that has all the information that the method needs, so the code could do more indexing instead of allocating many partial strings.</span></span> 
  
 <span data-ttu-id="e9b41-214">Tým výkonu kompilátoru řešeny tyto přidělení kódem takto:</span><span class="sxs-lookup"><span data-stu-id="e9b41-214">The compiler’s performance team tackled all these allocations with code like this:</span></span>  
  
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
  
 <span data-ttu-id="e9b41-215">První verze `WriteFormattedDocComment()` přidělené pole, více dílčích podřetězců a zkrácená podřetězec spolu s prázdnou `params` pole.</span><span class="sxs-lookup"><span data-stu-id="e9b41-215">The first version of `WriteFormattedDocComment()` allocated an array, several substrings, and a trimmed substring along with an empty `params` array.</span></span> <span data-ttu-id="e9b41-216">Také kontroluje pro "/ / / / /".</span><span class="sxs-lookup"><span data-stu-id="e9b41-216">It also checked for "///".</span></span> <span data-ttu-id="e9b41-217">Upravený kód používá pouze indexování a přiděluje žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="e9b41-217">The revised code uses only indexing and allocates nothing.</span></span> <span data-ttu-id="e9b41-218">Vyhledá první znak, který není prázdným znakem a poté ověří znak po znaku zobrazíte, pokud řetězec začíná symbolem "/ / / / /".</span><span class="sxs-lookup"><span data-stu-id="e9b41-218">It finds the first character that is not white space, and then checks character by character to see if the string starts with "///".</span></span> <span data-ttu-id="e9b41-219">Nový kód používá `IndexOfFirstNonWhiteSpaceChar` místo <xref:System.String.TrimStart%2A> vrátit první index (za zadaný počáteční index), kde dochází k znaku prázdný znak.</span><span class="sxs-lookup"><span data-stu-id="e9b41-219">The new code uses `IndexOfFirstNonWhiteSpaceChar` instead of <xref:System.String.TrimStart%2A> to return the first index (after a specified start index) where a non-white-space character occurs.</span></span> <span data-ttu-id="e9b41-220">Oprava není úplný, ale můžete zjistit, jak použít podobné opravy pro kompletní řešení.</span><span class="sxs-lookup"><span data-stu-id="e9b41-220">The fix is not complete, but you can see how to apply similar fixes for a complete solution.</span></span> <span data-ttu-id="e9b41-221">Při použití tohoto přístupu napříč kódem můžete odebrat všechna přidělení v `WriteFormattedDocComment()`.</span><span class="sxs-lookup"><span data-stu-id="e9b41-221">By applying this approach throughout the code, you can remove all allocations in `WriteFormattedDocComment()`.</span></span> 
  
 <span data-ttu-id="e9b41-222">**Příklad 4: StringBuilder**</span><span class="sxs-lookup"><span data-stu-id="e9b41-222">**Example 4: StringBuilder**</span></span>  
  
 <span data-ttu-id="e9b41-223">Tento příklad používá <xref:System.Text.StringBuilder> objektu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-223">This example uses a <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="e9b41-224">Následující funkce generuje úplný název typu pro obecné typy:</span><span class="sxs-lookup"><span data-stu-id="e9b41-224">The following function generates a full type name for generic types:</span></span>  
  
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
  
 <span data-ttu-id="e9b41-225">Zaměřuje se na řádek, který vytvoří nový <xref:System.Text.StringBuilder> instance.</span><span class="sxs-lookup"><span data-stu-id="e9b41-225">The focus is on the line that creates a new <xref:System.Text.StringBuilder> instance.</span></span> <span data-ttu-id="e9b41-226">Kód způsobí, že přidělení pro `sb.ToString()` a interní přidělení v rámci <xref:System.Text.StringBuilder> implementaci, ale nemůžete ovládat těchto přidělení, pokud má řetězec výsledek.</span><span class="sxs-lookup"><span data-stu-id="e9b41-226">The code causes an allocation for `sb.ToString()` and internal allocations within the <xref:System.Text.StringBuilder> implementation, but you cannot control those allocations if you want the string result.</span></span> 
  
 <span data-ttu-id="e9b41-227">**Oprava například 4**</span><span class="sxs-lookup"><span data-stu-id="e9b41-227">**Fix for example 4**</span></span>  
  
 <span data-ttu-id="e9b41-228">Chcete-li vyřešit `StringBuilder` objekt přidělování, objekt do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e9b41-228">To fix the `StringBuilder` object allocation, cache the  object.</span></span> <span data-ttu-id="e9b41-229">I ukládání jediné instance, která může získat zahozeny může výrazně zvýšit výkon.</span><span class="sxs-lookup"><span data-stu-id="e9b41-229">Even caching a single instance that might get thrown away can improve performance significantly.</span></span> <span data-ttu-id="e9b41-230">Toto je novou implementaci funkce vynechání veškerý kód s výjimkou nové první a poslední řádky:</span><span class="sxs-lookup"><span data-stu-id="e9b41-230">This is the function’s new implementation, omitting all the code except for the new first and last lines:</span></span>  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 <span data-ttu-id="e9b41-231">Jsou klíčové části nové `AcquireBuilder()` a `GetStringAndReleaseBuilder()` funkce:</span><span class="sxs-lookup"><span data-stu-id="e9b41-231">The key parts are the new `AcquireBuilder()` and `GetStringAndReleaseBuilder()` functions:</span></span>  
  
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
  
 <span data-ttu-id="e9b41-232">Protože kompilátory nové použít dělení na vlákna, tyto implementace použít pole vlákna (<xref:System.ThreadStaticAttribute> atribut) do mezipaměti <xref:System.Text.StringBuilder>, a pravděpodobně můžete vynecháte `ThreadStatic` deklarace.</span><span class="sxs-lookup"><span data-stu-id="e9b41-232">Because the new compilers use threading, these implementations use a thread-static field (<xref:System.ThreadStaticAttribute> attribute) to cache the <xref:System.Text.StringBuilder>, and you likely can forgo the `ThreadStatic` declaration.</span></span> <span data-ttu-id="e9b41-233">Vlákno statické pole má jedinečnou hodnotu pro každý podproces, který se spustí tento kód.</span><span class="sxs-lookup"><span data-stu-id="e9b41-233">The thread-static field holds a unique value for each thread that executes this code.</span></span> 
  
 <span data-ttu-id="e9b41-234">`AcquireBuilder()` Vrátí v mezipaměti <xref:System.Text.StringBuilder> instance, pokud existuje, po zrušení a pole nebo mezipaměti nastavíte na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="e9b41-234">`AcquireBuilder()` returns the cached <xref:System.Text.StringBuilder> instance if there is one, after clearing it and setting the field or cache to null.</span></span> <span data-ttu-id="e9b41-235">V opačném případě `AcquireBuilder()` vytvoří novou instanci a vrací, opuštění sady polí nebo mezipaměti na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="e9b41-235">Otherwise, `AcquireBuilder()` creates a new instance and returns it, leaving the field or cache set to null.</span></span> 
  
 <span data-ttu-id="e9b41-236">Až budete mít s <xref:System.Text.StringBuilder> , volání `GetStringAndReleaseBuilder()` získat výsledek řetězce, uložte <xref:System.Text.StringBuilder> instanci v poli nebo mezipaměti a potom vrátí výsledky.</span><span class="sxs-lookup"><span data-stu-id="e9b41-236">When you’re done with <xref:System.Text.StringBuilder> , you call `GetStringAndReleaseBuilder()` to get the string result, save the <xref:System.Text.StringBuilder> instance in the field or cache, and then return the result.</span></span> <span data-ttu-id="e9b41-237">Je možné znovu zadat Tento kód a vytvořit několik <xref:System.Text.StringBuilder> objekty (i když tomu zřídka dojde).</span><span class="sxs-lookup"><span data-stu-id="e9b41-237">It is possible for execution to re-enter this code and to create multiple <xref:System.Text.StringBuilder> objects (although that rarely happens).</span></span> <span data-ttu-id="e9b41-238">Kód uloží jenom poslední vydání <xref:System.Text.StringBuilder> instance pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="e9b41-238">The code saves only the last released <xref:System.Text.StringBuilder> instance for later use.</span></span> <span data-ttu-id="e9b41-239">Tento jednoduchý strategií ukládání do mezipaměti výrazně snížit přidělení v kompilátorech, které nový.</span><span class="sxs-lookup"><span data-stu-id="e9b41-239">This simple caching strategy significantly reduced allocations in the new compilers.</span></span> <span data-ttu-id="e9b41-240">Součásti rozhraní .NET Framework a MSBuild ("MSBuild") podobný postup použít ke zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-240">Parts of the .NET Framework and MSBuild ("MSBuild") use a similar technique to improve performance.</span></span> 
  
 <span data-ttu-id="e9b41-241">Tento jednoduchý strategií ukládání do mezipaměti dodržuje návrh dobrý mezipaměti vzhledem k tomu, že má limit velikosti.</span><span class="sxs-lookup"><span data-stu-id="e9b41-241">This simple caching strategy adheres to good cache design because it has a size cap.</span></span> <span data-ttu-id="e9b41-242">Existuje ale více kódu nyní než v původním, což znamená další náklady na údržbu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-242">However, there is more code now than in the original, which means more maintenance costs.</span></span> <span data-ttu-id="e9b41-243">Můžete přijmout strategií ukládání do mezipaměti pouze v případě, že jste nalezen problém s výkonem a PerfView ukázala, že <xref:System.Text.StringBuilder> přidělení je významným přispěvatelem.</span><span class="sxs-lookup"><span data-stu-id="e9b41-243">You should adopt the caching strategy only if you’ve found a performance problem, and PerfView has shown that <xref:System.Text.StringBuilder> allocations are a significant contributor.</span></span> 
  
### <a name="linq-and-lambdas"></a><span data-ttu-id="e9b41-244">LINQ a výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="e9b41-244">LINQ and lambdas</span></span>  
<span data-ttu-id="e9b41-245">Language-Integrated Query (LINQ), ve spojení s lambda výrazy, je příkladem funkcí produktivitu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-245">Language-Integrated Query (LINQ), in conjunction with lambda expressions, is an example of a productivity feature.</span></span> <span data-ttu-id="e9b41-246">Ale jeho použití může mít významný dopad na výkon v čase a je možné, že budete muset revize kódu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-246">However, its use may have a significant impact on performance over time, and you might find you need to rewrite your code.</span></span>
  
 <span data-ttu-id="e9b41-247">**Příklad 5: Výrazy lambda, seznam\<T >, IEnumerable a\<T >**</span><span class="sxs-lookup"><span data-stu-id="e9b41-247">**Example 5: Lambdas, List\<T>, and IEnumerable\<T>**</span></span>  
  
 <span data-ttu-id="e9b41-248">Tento příklad používá [LINQ a funkční stylu kódu](https://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) najít symbol v modelu kompilátoru dle názvu řetězce:</span><span class="sxs-lookup"><span data-stu-id="e9b41-248">This example uses [LINQ and functional style code](https://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) to find a symbol in the compiler’s model, given a name string:</span></span>  
  
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
  
 <span data-ttu-id="e9b41-249">Nový kompilátor a prostředí IDE založená na něm volání `FindMatchingSymbol()` velmi často a že jsou několik skrytých přidělení v této funkce jediný řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-249">The new compiler and the IDE experiences built on it call `FindMatchingSymbol()` very frequently, and there are several hidden allocations in this function’s single line of code.</span></span> <span data-ttu-id="e9b41-250">Prozkoumat tyto přidělení, nejprve jediný řádek kódu funkce rozdělení na dva řádky:</span><span class="sxs-lookup"><span data-stu-id="e9b41-250">To examine those allocations, first split the function’s single line of code into two lines:</span></span>  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 <span data-ttu-id="e9b41-251">V prvním řádku [výraz lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [zavře přes](https://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) lokální proměnná `name`.</span><span class="sxs-lookup"><span data-stu-id="e9b41-251">In the first line, the [lambda expression](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [closes over](https://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) the local variable `name`.</span></span> <span data-ttu-id="e9b41-252">To znamená, že kromě objekt pro přidělování [delegovat](~/docs/csharp/language-reference/keywords/delegate.md) , který `predicate` obsahuje kód přiděluje statická třída pro uložení prostředí, který zachycuje hodnoty `name`.</span><span class="sxs-lookup"><span data-stu-id="e9b41-252">This means that in addition to allocating an object for the [delegate](~/docs/csharp/language-reference/keywords/delegate.md) that `predicate` holds, the code allocates a static class to hold the environment that captures the value of `name`.</span></span> <span data-ttu-id="e9b41-253">Kompilátor generuje kód podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="e9b41-253">The compiler generates code like the following:</span></span>  
  
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
  
 <span data-ttu-id="e9b41-254">Dva `new` přidělení (jeden pro třídu prostředí) a jeden pro delegáta jsou nyní explicitní.</span><span class="sxs-lookup"><span data-stu-id="e9b41-254">The two `new` allocations (one for the environment class and one for the delegate) are explicit now.</span></span> 
  
 <span data-ttu-id="e9b41-255">Nyní se podívejte na volání `FirstOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="e9b41-255">Now look at the call to `FirstOrDefault`.</span></span> <span data-ttu-id="e9b41-256">Tato metoda rozšíření na <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typ s sebou nese náklady přidělení příliš.</span><span class="sxs-lookup"><span data-stu-id="e9b41-256">This extension method on the <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> type incurs an allocation too.</span></span> <span data-ttu-id="e9b41-257">Protože `FirstOrDefault` přebírá <xref:System.Collections.Generic.IEnumerable%601> objektu jako svůj první argument, můžete rozbalit volání následující kód (zjednodušené trochu pro diskuse):</span><span class="sxs-lookup"><span data-stu-id="e9b41-257">Because `FirstOrDefault` takes an <xref:System.Collections.Generic.IEnumerable%601> object as its first argument, you can expand the call to the following code (simplified a bit for discussion):</span></span>  
  
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
  
 <span data-ttu-id="e9b41-258">`symbols` Proměnná má typ <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="e9b41-258">The `symbols` variable has type <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="e9b41-259"><xref:System.Collections.Generic.List%601> Implementuje typ kolekce <xref:System.Collections.Generic.IEnumerable%601> a cleverly definuje enumerátor (<xref:System.Collections.Generic.IEnumerator%601> rozhraní), který <xref:System.Collections.Generic.List%601> implementuje s `struct`.</span><span class="sxs-lookup"><span data-stu-id="e9b41-259">The <xref:System.Collections.Generic.List%601> collection type implements <xref:System.Collections.Generic.IEnumerable%601> and cleverly defines an enumerator (<xref:System.Collections.Generic.IEnumerator%601> interface) that <xref:System.Collections.Generic.List%601> implements with a `struct`.</span></span> <span data-ttu-id="e9b41-260">Používání struktury namísto třídy znamená, že je obvykle velmi riskantní libovolná přidělení haldy, které pak může ovlivnit výkon kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="e9b41-260">Using a structure instead of a class means that you usually avoid any heap allocations, which, in turn, can affect garbage collection performance.</span></span> <span data-ttu-id="e9b41-261">Enumerátory se obvykle používají pro jazyk `foreach` smyčku, která používá strukturu enumerátor je vrácená v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="e9b41-261">Enumerators are typically used with the language’s `foreach` loop, which uses the enumerator structure as it is returned on the call stack.</span></span> <span data-ttu-id="e9b41-262">Zvyšování ukazatel zásobníku volání, aby uvolnil prostor pro objekt nemá vliv na způsob přidělení haldy provádí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e9b41-262">Incrementing the call stack pointer to make room for an object does not affect GC the way a heap allocation does.</span></span> 
  
 <span data-ttu-id="e9b41-263">V případě rozbalených `FirstOrDefault` volání, kód je nutné volat `GetEnumerator()` na <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="e9b41-263">In the case of the expanded `FirstOrDefault` call, the code needs to call `GetEnumerator()` on an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="e9b41-264">Přiřazení `symbols` k `enumerable` proměnné typu `IEnumerable<Symbol>` nedochází ke ztrátě informací, které je objekt, který vede <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="e9b41-264">Assigning `symbols` to the `enumerable` variable of type `IEnumerable<Symbol>` loses the information that the actual object is a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="e9b41-265">To znamená, že když kód načte čítač s `enumerable.GetEnumerator()`, musíme pole vrácené struktury a přiřaďte k rozhraní .NET Framework `enumerator` proměnné.</span><span class="sxs-lookup"><span data-stu-id="e9b41-265">This means that when the code fetches the enumerator with `enumerable.GetEnumerator()`, the .NET Framework has to box the returned structure to assign it to the `enumerator` variable.</span></span> 
  
 <span data-ttu-id="e9b41-266">**Oprava například 5**</span><span class="sxs-lookup"><span data-stu-id="e9b41-266">**Fix for example 5**</span></span>  
  
 <span data-ttu-id="e9b41-267">Je nutné přepsat `FindMatchingSymbol` následujícím způsobem nahraďte šest řádků kódu, které jsou stále stručné, snadno čitelný a pochopit a snadnou údržbou jeho jediný řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="e9b41-267">The fix is to rewrite `FindMatchingSymbol` as follows, replacing its single line of code with six lines of code that are still concise, easy to read and understand, and easy to maintain:</span></span>  
  
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
  
 <span data-ttu-id="e9b41-268">Tento kód nepoužívá rozšiřující metody, lambda výrazy nebo enumerátory LINQ, a to s sebou nese náklady bez přidělení.</span><span class="sxs-lookup"><span data-stu-id="e9b41-268">This code doesn’t use LINQ extension methods, lambdas, or enumerators, and it incurs no allocations.</span></span> <span data-ttu-id="e9b41-269">Nejsou žádné přidělení, protože kompilátor může vidět, že `symbols` je kolekce <xref:System.Collections.Generic.List%601> a může svázat výsledné enumerátor (struktury) na místní proměnnou s správný typ, aby se zabránilo zabalení.</span><span class="sxs-lookup"><span data-stu-id="e9b41-269">There are no allocations because the compiler can see that the `symbols` collection is a <xref:System.Collections.Generic.List%601> and can bind the resulting enumerator (a structure) to a local variable with the right type to avoid boxing.</span></span> <span data-ttu-id="e9b41-270">Původní verze této funkce bylo skvělé příklad a výrazové Možnosti C# a produktivity rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e9b41-270">The original version of this function was a great example of the expressive power of C# and the productivity of the .NET Framework.</span></span> <span data-ttu-id="e9b41-271">Tato verze nové a efektivnější zachová tyto kvality bez přidání jakékoli složitý kód pro údržbu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-271">This new and more efficient version preserves those qualities without adding any complex code to maintain.</span></span> 
  
### <a name="async-method-caching"></a><span data-ttu-id="e9b41-272">Asynchronní metoda ukládání do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="e9b41-272">Async method caching</span></span>  

<span data-ttu-id="e9b41-273">Následující příklad znázorňuje běžný problém při pokusu o použití výsledky uložené v mezipaměti v [asynchronní](../../csharp/programming-guide/concepts/async/index.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e9b41-273">The next example shows a common problem when you try to use cached results in an [async](../../csharp/programming-guide/concepts/async/index.md) method.</span></span>
  
 <span data-ttu-id="e9b41-274">**Příklad 6: ukládání do mezipaměti v asynchronních metodách**</span><span class="sxs-lookup"><span data-stu-id="e9b41-274">**Example 6: caching in async methods**</span></span>  
  
 <span data-ttu-id="e9b41-275">Funkce Visual Studio IDE založená na nové kompilátory C# a Visual Basic často načíst syntaxe stromy a kompilátory použít operátory async přitom zajistit rychlou odezvou sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e9b41-275">The Visual Studio IDE features built on the new C# and Visual Basic compilers frequently fetch syntax trees, and the compilers use async when doing so to keep Visual Studio responsive.</span></span> <span data-ttu-id="e9b41-276">Zde je první verze kódu, který můžete například napsat získat strom syntaxe:</span><span class="sxs-lookup"><span data-stu-id="e9b41-276">Here’s the first version of the code you might write to get a syntax tree:</span></span>  
  
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
  
 <span data-ttu-id="e9b41-277">Uvidíte, že volání `GetSyntaxTreeAsync()` vytvoří instanci `Parser`, analyzuje kód a potom vrátí <xref:System.Threading.Tasks.Task> objektu, `Task<SyntaxTree>`.</span><span class="sxs-lookup"><span data-stu-id="e9b41-277">You can see that calling `GetSyntaxTreeAsync()` instantiates a `Parser`, parses the code, and then returns a <xref:System.Threading.Tasks.Task> object, `Task<SyntaxTree>`.</span></span> <span data-ttu-id="e9b41-278">Přidělení části nákladné `Parser` instance a analýzu kódu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-278">The expensive part is allocating the `Parser` instance and parsing the code.</span></span> <span data-ttu-id="e9b41-279">Funkce vrátí <xref:System.Threading.Tasks.Task> tak, aby volající může await analýzy práce a uvolnit vlákno uživatelského rozhraní bude reagovat na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="e9b41-279">The function returns a <xref:System.Threading.Tasks.Task> so that callers can await the parsing work and free the UI thread to be responsive to user input.</span></span> 
  
 <span data-ttu-id="e9b41-280">Několik funkcí sady Visual Studio může pokusit získat stejné stromu syntaxe, tak můžete například napsat následující kód pro ukládání do mezipaměti výsledek analýzy jak šetřit čas i přidělení.</span><span class="sxs-lookup"><span data-stu-id="e9b41-280">Several Visual Studio features might try to get the same syntax tree, so you might write the following code to cache the parsing result to save time and allocations.</span></span> <span data-ttu-id="e9b41-281">Tento kód však způsobuje přidělení:</span><span class="sxs-lookup"><span data-stu-id="e9b41-281">However, this code incurs an allocation:</span></span>  
  
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
  
 <span data-ttu-id="e9b41-282">Uvidíte, že má nový kód s ukládáním do mezipaměti `SyntaxTree` pole s názvem `cachedResult`.</span><span class="sxs-lookup"><span data-stu-id="e9b41-282">You see that the new code with caching has a `SyntaxTree` field named `cachedResult`.</span></span> <span data-ttu-id="e9b41-283">Když toto pole má hodnotu null, `GetSyntaxTreeAsync()` provádí a uloží výsledek v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e9b41-283">When this field is null, `GetSyntaxTreeAsync()` does the work and saves the result in the cache.</span></span> <span data-ttu-id="e9b41-284">`GetSyntaxTreeAsync()` Vrátí `SyntaxTree` objektu.</span><span class="sxs-lookup"><span data-stu-id="e9b41-284">`GetSyntaxTreeAsync()` returns the `SyntaxTree` object.</span></span> <span data-ttu-id="e9b41-285">Problém je, že až budete mít `async` – funkce typu `Task<SyntaxTree>`, a vrátí hodnotu typu `SyntaxTree`, kompilátor generuje kód pro přidělení úlohu pro uchování výsledku (s použitím `Task<SyntaxTree>.FromResult()`).</span><span class="sxs-lookup"><span data-stu-id="e9b41-285">The problem is that when you have an `async` function of type `Task<SyntaxTree>`, and you return a value of type `SyntaxTree`, the compiler emits code to allocate a Task to hold the result (by using `Task<SyntaxTree>.FromResult()`).</span></span> <span data-ttu-id="e9b41-286">Úkolu označena jako dokončená a výsledek je ihned k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e9b41-286">The Task is marked as completed, and the result is immediately available.</span></span> <span data-ttu-id="e9b41-287">V kódu pro nové kompilátory <xref:System.Threading.Tasks.Task> objekty, které již byly dokončeny tak často, který oprava těchto přidělení lepší odezvy výrazně došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="e9b41-287">In the code for the new compilers, <xref:System.Threading.Tasks.Task> objects that were already completed occurred so often that fixing these allocations improved responsiveness noticeably.</span></span> 
  
 <span data-ttu-id="e9b41-288">**Oprava například 6**</span><span class="sxs-lookup"><span data-stu-id="e9b41-288">**Fix for example 6**</span></span>  
  
 <span data-ttu-id="e9b41-289">Chcete-li odebrat dokončenou <xref:System.Threading.Tasks.Task> přidělení, můžete ukládat do mezipaměti objekt úlohy s výsledkem dokončené:</span><span class="sxs-lookup"><span data-stu-id="e9b41-289">To remove the completed <xref:System.Threading.Tasks.Task> allocation, you can cache the Task object with the completed result:</span></span>  
  
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
  
 <span data-ttu-id="e9b41-290">Tento kód změní typ `cachedResult` k `Task<SyntaxTree>` a využívá `async` pomocná funkce, která obsahuje původní kód `GetSyntaxTreeAsync()`.</span><span class="sxs-lookup"><span data-stu-id="e9b41-290">This code changes the type of `cachedResult` to `Task<SyntaxTree>` and employs an `async` helper function that holds the original code from `GetSyntaxTreeAsync()`.</span></span> <span data-ttu-id="e9b41-291">`GetSyntaxTreeAsync()` nyní používá [null operátor sloučení](../../csharp/language-reference/operators/null-coalescing-operator.md) vrátit `cachedResult` Pokud není null.</span><span class="sxs-lookup"><span data-stu-id="e9b41-291">`GetSyntaxTreeAsync()` now uses the [null coalescing operator](../../csharp/language-reference/operators/null-coalescing-operator.md) to return `cachedResult` if it isn't null.</span></span> <span data-ttu-id="e9b41-292">Pokud `cachedResult` má hodnotu null, pak `GetSyntaxTreeAsync()` volání `GetSyntaxTreeUncachedAsync()` a ukládá do mezipaměti výsledek.</span><span class="sxs-lookup"><span data-stu-id="e9b41-292">If `cachedResult` is null, then `GetSyntaxTreeAsync()` calls `GetSyntaxTreeUncachedAsync()` and caches the result.</span></span> <span data-ttu-id="e9b41-293">Všimněte si, že `GetSyntaxTreeAsync()` nebude očekávat volání `GetSyntaxTreeUncachedAsync()` jako kód obvykle.</span><span class="sxs-lookup"><span data-stu-id="e9b41-293">Notice that `GetSyntaxTreeAsync()` doesn’t await the call to `GetSyntaxTreeUncachedAsync()` as the code would normally.</span></span> <span data-ttu-id="e9b41-294">Bez použití operátoru await znamená, že `GetSyntaxTreeUncachedAsync()` vrátí jeho <xref:System.Threading.Tasks.Task> objektu, `GetSyntaxTreeAsync()` okamžitě vrátí <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="e9b41-294">Not using await means that when `GetSyntaxTreeUncachedAsync()` returns its <xref:System.Threading.Tasks.Task> object, `GetSyntaxTreeAsync()` immediately returns the <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="e9b41-295">Nyní je výsledky uložené v mezipaměti <xref:System.Threading.Tasks.Task>, aby vás nečekala žádná přidělení vrátit výsledky uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e9b41-295">Now, the cached result is a <xref:System.Threading.Tasks.Task>, so there are no allocations to return the cached result.</span></span> 
  
### <a name="additional-considerations"></a><span data-ttu-id="e9b41-296">Další informace</span><span class="sxs-lookup"><span data-stu-id="e9b41-296">Additional considerations</span></span>  
 <span data-ttu-id="e9b41-297">Tady je několik dalších bodů o potenciálních problémů v aplikacích pro velké nebo aplikace, které zpracovávají velké množství dat.</span><span class="sxs-lookup"><span data-stu-id="e9b41-297">Here are a few more points about potential problems in large apps or apps that process a lot of data.</span></span> 
  
 <span data-ttu-id="e9b41-298">**slovníky**</span><span class="sxs-lookup"><span data-stu-id="e9b41-298">**Dictionaries**</span></span>  
  
 <span data-ttu-id="e9b41-299">Slovníky se ubiquitously používají v mnoha aplikacích a i když jsou slovníky příliš pohodlné a ze své podstaty efektivní.</span><span class="sxs-lookup"><span data-stu-id="e9b41-299">Dictionaries are used ubiquitously in many programs, and though dictionaries are very convenient and inherently efficient.</span></span> <span data-ttu-id="e9b41-300">Však často slouží nesprávně.</span><span class="sxs-lookup"><span data-stu-id="e9b41-300">However, they’re often used inappropriately.</span></span> <span data-ttu-id="e9b41-301">V sadě Visual Studio a nové kompilátory analýza ukazuje mnoho slovníků obsahovala jeden element nebo byla prázdná.</span><span class="sxs-lookup"><span data-stu-id="e9b41-301">In Visual Studio and the new compilers, analysis shows that many of the dictionaries contained a single element or were empty.</span></span> <span data-ttu-id="e9b41-302">Prázdná <xref:System.Collections.Generic.Dictionary%602> deset pole a zabírá aspoň 48 bajtů v haldě na x x86 počítače.</span><span class="sxs-lookup"><span data-stu-id="e9b41-302">An empty <xref:System.Collections.Generic.Dictionary%602> has ten fields and occupies 48 bytes on the heap on an x86 machine.</span></span> <span data-ttu-id="e9b41-303">Slovníky se skvěle hodí, když potřebujete mapování nebo asociativní datová struktura s vyhledávaní v konstantním čase.</span><span class="sxs-lookup"><span data-stu-id="e9b41-303">Dictionaries are great when you need a mapping or associative data structure with constant-time lookup.</span></span> <span data-ttu-id="e9b41-304">Ale pokud máte pouze několik elementů, můžete odpadu velké množství místa pomocí slovníku.</span><span class="sxs-lookup"><span data-stu-id="e9b41-304">However, when you have only a few elements, you waste a lot of space by using a dictionary.</span></span> <span data-ttu-id="e9b41-305">Místo toho, například je iterativní vyhledat `List<KeyValuePair\<K,V>>`, stejně tak rychle.</span><span class="sxs-lookup"><span data-stu-id="e9b41-305">Instead, for example, you could iteratively look through a `List<KeyValuePair\<K,V>>`, just as fast.</span></span> <span data-ttu-id="e9b41-306">Pokud používáte jenom pro zatížení s daty a pak si můžete přečíst z něj (velmi běžný vzor) slovník, pomocí vyhledávání N(log(N)) seřazené pole může být skoro tak rychle, v závislosti na počtu prvků, které používáte.</span><span class="sxs-lookup"><span data-stu-id="e9b41-306">If you use a dictionary only to load it with data and then read from it (a very common pattern), using a sorted array with an N(log(N)) lookup might be nearly as fast, depending on the number of elements you're using.</span></span> 
  
 <span data-ttu-id="e9b41-307">**Třídy a struktury**</span><span class="sxs-lookup"><span data-stu-id="e9b41-307">**Classes vs. structures**</span></span>  
  
 <span data-ttu-id="e9b41-308">V režimu třídy a struktury poskytují kompromis classic místa a času pro ladění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9b41-308">In a way, classes and structures provide a classic space/time tradeoff for tuning your apps.</span></span> <span data-ttu-id="e9b41-309">Třídy se vám účtovat 12 bajtů režijní náklady na x x86 počítače i v případě, že nemají žádná pole, ale jsou cenově předávat, protože pouze bere ukazatel pro odkazování na instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="e9b41-309">Classes incur 12 bytes of overhead on an x86 machine even if they have no fields, but they are inexpensive to pass around because it only takes a pointer to refer to a class instance.</span></span> <span data-ttu-id="e9b41-310">Pokud nejsou zabaleny, ale když předat velké struktury jako argumenty funkce nebo návratové hodnoty, může zabrat určitý čas procesoru atomicky zkopírovat všechny datové členy struktury se vám účtovat struktury bez přidělení haldy.</span><span class="sxs-lookup"><span data-stu-id="e9b41-310">Structures incur no heap allocations if they aren’t boxed, but when you pass large structures as function arguments or return values, it takes CPU time to atomically copy all the data members of the structures.</span></span> <span data-ttu-id="e9b41-311">Dávejte pozor na opakovaná volání vlastnosti, které vrátí struktury a hodnotu vlastnosti v místní proměnné, aby se zabránilo nadměrnému kopírování dat do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e9b41-311">Watch out for repeated calls to properties that return structures, and cache the property’s value in a local variable to avoid excessive data copying.</span></span> 
  
 <span data-ttu-id="e9b41-312">**Caches**</span><span class="sxs-lookup"><span data-stu-id="e9b41-312">**Caches**</span></span>  
  
 <span data-ttu-id="e9b41-313">Běžné zdvih výkonu se výsledky do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e9b41-313">A common performance trick is to cache results.</span></span> <span data-ttu-id="e9b41-314">Bez zásady cap nebo vyřazení velikost mezipaměti však může být nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="e9b41-314">However, a cache without a size cap or disposal policy can be a memory leak.</span></span> <span data-ttu-id="e9b41-315">Při zpracování velkých objemů dat, pokud můžete blokovat velké množství paměti v mezipaměti, může způsobit uvolňování paměti pro přepsání výhody v mezipaměti vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="e9b41-315">When processing large amounts of data, if you hold on to a lot of memory in caches, you can cause garbage collection to override the benefits of your cached lookups.</span></span> 
  
 <span data-ttu-id="e9b41-316">V tomto článku jsme zmínili, jak byste měli vědět příznaky problémové místo výkonu, které může mít vliv na rychlost reakce vaší aplikace, zejména u velkých systémy nebo systémy, které zpracovávají velké množství dat.</span><span class="sxs-lookup"><span data-stu-id="e9b41-316">In this article, we discussed how you should be aware of performance bottleneck symptoms that can affect your app's responsiveness, especially for large systems or systems that process a large amount of data.</span></span> <span data-ttu-id="e9b41-317">Běžné culprits zahrnují zabalení, manipulace s řetězci, LINQ a lambda, ukládání do mezipaměti v asynchronních metodách, ukládání do mezipaměti bez zásad omezení nebo vyřazení velikost, nesprávné použití slovníky a předávání kolem struktury.</span><span class="sxs-lookup"><span data-stu-id="e9b41-317">Common culprits include boxing, string manipulations, LINQ and lambda, caching in async methods, caching without a size limit or disposal policy, inappropriate use of dictionaries, and passing around structures.</span></span> <span data-ttu-id="e9b41-318">Mějte na paměti čtyři faktů pro ladění vaší aplikace:</span><span class="sxs-lookup"><span data-stu-id="e9b41-318">Keep in mind the four facts for tuning your apps:</span></span>  
  
-   <span data-ttu-id="e9b41-319">Nemáte předčasně optimalizovat – produktivitu a ladit vaši aplikaci při odhalit problémy.</span><span class="sxs-lookup"><span data-stu-id="e9b41-319">Don’t prematurely optimize – be productive and tune your app when you spot problems.</span></span> 
  
-   <span data-ttu-id="e9b41-320">Profily nejsou leží – při odhadování, pokud nejsou měření.</span><span class="sxs-lookup"><span data-stu-id="e9b41-320">Profiles don’t lie – you’re guessing if you’re not measuring.</span></span> 
  
-   <span data-ttu-id="e9b41-321">Vhodné nástroje všechny záleží na tom – stáhnout PerfView a vyzkoušejte si to.</span><span class="sxs-lookup"><span data-stu-id="e9b41-321">Good tools make all the difference – download PerfView and try it out.</span></span> 
  
-   <span data-ttu-id="e9b41-322">To všechno je o přidělení – to znamená ve kterém tým platformy kompilátoru trvání většinu svého času zlepšení výkonu nové kompilátory.</span><span class="sxs-lookup"><span data-stu-id="e9b41-322">It's all about allocations – that is where the compiler platform team spent most of their time improving the performance of the new compilers.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="e9b41-323">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9b41-323">See also</span></span>

- [<span data-ttu-id="e9b41-324">Video prezentace v tomto tématu</span><span class="sxs-lookup"><span data-stu-id="e9b41-324">Video of presentation of this topic</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [<span data-ttu-id="e9b41-325">Průvodce začátečníka profilací výkonu</span><span class="sxs-lookup"><span data-stu-id="e9b41-325">Beginners Guide to Performance Profiling</span></span>](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [<span data-ttu-id="e9b41-326">Výkon</span><span class="sxs-lookup"><span data-stu-id="e9b41-326">Performance</span></span>](../../../docs/framework/performance/index.md)
- [<span data-ttu-id="e9b41-327">Tipy ke zvýšení výkonu rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="e9b41-327">.NET Performance Tips</span></span>](https://msdn.microsoft.com/library/ms973839.aspx)
- [<span data-ttu-id="e9b41-328">Nástroj pro analýzu výkonu Windows Phone</span><span class="sxs-lookup"><span data-stu-id="e9b41-328">Windows Phone Performance Analysis Tool</span></span>](https://msdn.microsoft.com/magazine/hh781024.aspx)
- [<span data-ttu-id="e9b41-329">Vyhledat problémová místa aplikace pomocí sady Visual Studio Profiler</span><span class="sxs-lookup"><span data-stu-id="e9b41-329">Find Application Bottlenecks with Visual Studio Profiler</span></span>](https://msdn.microsoft.com/magazine/cc337887.aspx)
- [<span data-ttu-id="e9b41-330">Na webu Channel 9 kurzů PerfView</span><span class="sxs-lookup"><span data-stu-id="e9b41-330">Channel 9 PerfView tutorials</span></span>](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [<span data-ttu-id="e9b41-331">The .NET Compiler Platform SDK</span><span class="sxs-lookup"><span data-stu-id="e9b41-331">The .NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="e9b41-332">DotNet/roslyn úložišti na Githubu</span><span class="sxs-lookup"><span data-stu-id="e9b41-332">dotnet/roslyn repo on GitHub</span></span>](https://github.com/dotnet/roslyn)
