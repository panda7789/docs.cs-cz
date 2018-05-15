---
title: Psaní velkých a pohotově reagujících aplikací .NET Framework
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 51b4758690257b999cce51f3e80fd263a6d5e275
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="writing-large-responsive-net-framework-apps"></a><span data-ttu-id="217ae-102">Psaní velkých a pohotově reagujících aplikací .NET Framework</span><span class="sxs-lookup"><span data-stu-id="217ae-102">Writing Large, Responsive .NET Framework Apps</span></span>
<span data-ttu-id="217ae-103">Tento článek obsahuje tipy pro zvýšení výkonu velkých aplikací rozhraní .NET Framework, nebo aplikace, které zpracovávají velké množství dat, jako jsou soubory nebo databáze.</span><span class="sxs-lookup"><span data-stu-id="217ae-103">This article provides tips for improving the performance of large .NET Framework apps, or apps that process a large amount of data such as files or databases.</span></span> <span data-ttu-id="217ae-104">Tyto tipy pocházet z přepisování C# a Visual Basic kompilátory ve spravovaném kódu a tento článek obsahuje několik příkladů skutečné z kompilátoru C#.</span><span class="sxs-lookup"><span data-stu-id="217ae-104">These tips come from rewriting the C# and Visual Basic compilers in managed code, and this article includes several real examples from the C# compiler.</span></span>  
  
 <span data-ttu-id="217ae-105">Rozhraní .NET Framework je vysoce výkonné pro vytváření aplikací.</span><span class="sxs-lookup"><span data-stu-id="217ae-105">The .NET Framework is highly productive for building apps.</span></span>  <span data-ttu-id="217ae-106">Výkonný a bezpečné jazyky a bohaté kolekce knihovny zkontrolujte aplikace vytváření vysoce plodnou.</span><span class="sxs-lookup"><span data-stu-id="217ae-106">Powerful and safe languages and a rich collection of libraries make app building highly fruitful.</span></span>  <span data-ttu-id="217ae-107">S skvělé produktivitu dodává zodpovědnost.</span><span class="sxs-lookup"><span data-stu-id="217ae-107">However, with great productivity comes responsibility.</span></span>  <span data-ttu-id="217ae-108">Musí používat všechny funkce rozhraní .NET Framework, ale mějte připravené informace o optimalizaci výkonu vašeho kódu v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="217ae-108">You should use all the power of the .NET Framework, but be prepared to tune your code’s performance when needed.</span></span>  
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a><span data-ttu-id="217ae-109">Proč nové výkonu kompilátoru platí pro vaši aplikaci</span><span class="sxs-lookup"><span data-stu-id="217ae-109">Why the new compiler performance applies to your app</span></span>  
 <span data-ttu-id="217ae-110">Týmem kompilátoru platformu .NET ("Roslyn") rewrote jazyka C# a kompilátory jazyka Visual Basic ve spravovaném kódu nabízí nová rozhraní API pro modelování a analýza kódu, nástroje pro vytváření a povolení prostředí mnohem širší, podporou kódu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="217ae-110">The .NET Compiler Platform ("Roslyn") team rewrote the C# and Visual Basic compilers in managed code to provide new APIs for modeling and analyzing code, building tools, and enabling much richer, code-aware experiences in Visual Studio.</span></span>  <span data-ttu-id="217ae-111">Přepisování kompilátory a sestavování sady Visual Studio narazí na nové kompilátory odhalilo užitečné performance Insight, které platí pro všechny velké rozhraní .NET Framework aplikace nebo jakékoli aplikaci, která zpracovává velké množství dat.</span><span class="sxs-lookup"><span data-stu-id="217ae-111">Rewriting the compilers and building Visual Studio experiences on the new compilers revealed useful performance insights that are applicable to any large .NET Framework app or any app that processes a lot of data.</span></span>  <span data-ttu-id="217ae-112">Nemusíte vědět o kompilátory využívat výhod přehledy a příklady z kompilátoru C#.</span><span class="sxs-lookup"><span data-stu-id="217ae-112">You don't need to know about compilers to take advantage of the insights and examples from the C# compiler.</span></span>  
  
 <span data-ttu-id="217ae-113">Visual Studio použije k vytvoření všech funkcí technologie IntelliSense, které uživatelé rádi, například podtržení vlnovkou zabarvení identifikátory a klíčová slova, seznamy dokončení syntaxe, chyb, parametr tipy, problémy kódu a kódu akce kompilátoru rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="217ae-113">Visual Studio uses the compiler APIs to build all the IntelliSense features that users love, such as colorization of identifiers and keywords, syntax completion lists, squiggles for errors, parameter tips, code issues, and code actions.</span></span>  <span data-ttu-id="217ae-114">Visual Studio poskytuje této nápovědy, zatímco vývojáři jsou zadáním a změna jejich kódu a sady Visual Studio musí zůstat přizpůsobivý při kompilátor průběžně modelů kód, který vývojářům upravit.</span><span class="sxs-lookup"><span data-stu-id="217ae-114">Visual Studio provides this help while developers are typing and changing their code, and Visual Studio must remain responsive while the compiler continually models the code developers edit.</span></span>  
  
 <span data-ttu-id="217ae-115">Pokud vaši koncoví uživatelé komunikovat s vaší aplikací, jejich očekávat ho jako odpovídající.</span><span class="sxs-lookup"><span data-stu-id="217ae-115">When your end users interact with your app, they expect it to be responsive.</span></span>  <span data-ttu-id="217ae-116">Zadáním nebo zpracování příkazu by nikdy zablokovat.</span><span class="sxs-lookup"><span data-stu-id="217ae-116">Typing or command handling should never be blocked.</span></span>  <span data-ttu-id="217ae-117">Nápověda by měla překryvné rychle nebo uvolňovat, pokud uživatel pokračuje zadáním.</span><span class="sxs-lookup"><span data-stu-id="217ae-117">Help should pop up quickly or give up if the user continues typing.</span></span>  <span data-ttu-id="217ae-118">Aplikace by měla zabránění blokování vlákna uživatelského rozhraní s dlouhou výpočtů, které aplikace zaregistrované, pomalá.</span><span class="sxs-lookup"><span data-stu-id="217ae-118">Your app should avoid blocking the UI thread with long computations that make the app feel sluggish.</span></span>  
  
 <span data-ttu-id="217ae-119">Další informace o Roslyn kompilátory najdete [dotnet/roslyn](https://github.com/dotnet/roslyn) úložišti na Githubu.</span><span class="sxs-lookup"><span data-stu-id="217ae-119">For more information about Roslyn compilers, visit the [dotnet/roslyn](https://github.com/dotnet/roslyn) repo on GitHub.</span></span>
 <!-- TODO: replace with link to Roslyn conceptual docs once that's published -->
  
## <a name="just-the-facts"></a><span data-ttu-id="217ae-120">Právě tato fakta</span><span class="sxs-lookup"><span data-stu-id="217ae-120">Just the Facts</span></span>  
 <span data-ttu-id="217ae-121">Vezměte v úvahu následující skutečnosti při ladění výkonu a vytváření přizpůsobivý aplikací rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="217ae-121">Consider these facts when tuning performance and creating responsive .NET Framework apps.</span></span>  
  
### <a name="fact-1-dont-prematurely-optimize"></a><span data-ttu-id="217ae-122">Fakt 1: Není předčasně optimalizovat.</span><span class="sxs-lookup"><span data-stu-id="217ae-122">Fact 1: Don’t prematurely optimize</span></span>  
 <span data-ttu-id="217ae-123">Psaní kódu, který je složitější, než je nutné způsobuje údržby, ladění a leštění náklady.</span><span class="sxs-lookup"><span data-stu-id="217ae-123">Writing code that is more complex than it needs to be incurs maintenance, debugging, and polishing costs.</span></span>  <span data-ttu-id="217ae-124">Zkušení programátoři mít intuitivní pochopit postup řešení problémů kódování a napsat kód, efektivnější.</span><span class="sxs-lookup"><span data-stu-id="217ae-124">Experienced programmers have an intuitive grasp of how to solve coding problems and write more efficient code.</span></span>  <span data-ttu-id="217ae-125">Nicméně se někdy předčasně optimalizovat svůj kód.</span><span class="sxs-lookup"><span data-stu-id="217ae-125">However, they sometimes prematurely optimize their code.</span></span>  <span data-ttu-id="217ae-126">Například zatřiďovací tabulku používají, když jednoduchých polí by stačit, nebo použijte složitá ukládání do mezipaměti, může nastat únik paměti místo jednoduše recomputing hodnoty.</span><span class="sxs-lookup"><span data-stu-id="217ae-126">For example, they use a hash table when a simple array would suffice, or use complicated caching that may leak memory instead of simply recomputing values.</span></span>  <span data-ttu-id="217ae-127">I v případě, že jste programátory prostředí, doporučujeme testování výkonu a analyzovat kód, když najít problémy.</span><span class="sxs-lookup"><span data-stu-id="217ae-127">Even if you’re an experience programmer, you should test for performance and analyze your code when you find issues.</span></span>  
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a><span data-ttu-id="217ae-128">Fakt 2: Pokud jste nejsou měření, můžete se uhodnutí</span><span class="sxs-lookup"><span data-stu-id="217ae-128">Fact 2: If you’re not measuring, you’re guessing</span></span>  
 <span data-ttu-id="217ae-129">Nemáte ležet profily a měření.</span><span class="sxs-lookup"><span data-stu-id="217ae-129">Profiles and measurements don’t lie.</span></span>  <span data-ttu-id="217ae-130">Profily zobrazit, zda je úplným načtením procesoru nebo jestli se zablokuje na v/v disku.</span><span class="sxs-lookup"><span data-stu-id="217ae-130">Profiles show you whether the CPU is fully loaded or whether you’re blocked on disk I/O.</span></span>  <span data-ttu-id="217ae-131">Profily uvedeno, jaký typ a velikost paměti, že přidělování a jestli je vaše procesoru výdaje mnoho času v [uvolňování paměti](../../../docs/standard/garbage-collection/index.md) (GC).</span><span class="sxs-lookup"><span data-stu-id="217ae-131">Profiles tell you what kind and how much memory you’re allocating and whether your CPU is spending a lot of time in [garbage collection](../../../docs/standard/garbage-collection/index.md) (GC).</span></span>  
  
 <span data-ttu-id="217ae-132">By měl nastavit výkonnostní cíle pro klíče zákazníka prostředí nebo scénářů, ve vaší aplikaci a zápis testů k měření výkonu.</span><span class="sxs-lookup"><span data-stu-id="217ae-132">You should set performance goals for key customer experiences or scenarios in your app and write tests to measure performance.</span></span>  <span data-ttu-id="217ae-133">Prozkoumat selhání testů s použitím metodu exponenciální: použití profilů k vás, můžete předpokládat, co může být problém a testování vaší předpoklad s experimentu nebo kód změnit.</span><span class="sxs-lookup"><span data-stu-id="217ae-133">Investigate failing tests by applying the scientific method: use profiles to guide you, hypothesize what the issue might be, and test your hypothesis with an experiment or code change.</span></span>  <span data-ttu-id="217ae-134">Vytvořte měření výkonu standardních hodnot v čase s regulární testování, můžete izolovat změny, které způsobí regresí výkonu.</span><span class="sxs-lookup"><span data-stu-id="217ae-134">Establish baseline performance measurements over time with regular testing, so you can isolate changes that cause regressions in performance.</span></span>  <span data-ttu-id="217ae-135">Blíží výkonu pracovní přísných způsobem, budete muset plýtvání časem při s aktualizacemi kódu, které nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="217ae-135">By approaching performance work in a rigorous way, you’ll avoid wasting time with code updates you don’t need.</span></span>  
  
### <a name="fact-3-good-tools-make-all-the-difference"></a><span data-ttu-id="217ae-136">Fakt 3: Dobrý nástroje usnadňují všechny rozdílu</span><span class="sxs-lookup"><span data-stu-id="217ae-136">Fact 3: Good tools make all the difference</span></span>  
 <span data-ttu-id="217ae-137">Dobrý nástroje umožňují rychle rozbalit největších problémů s výkonem (procesoru, paměti nebo disk) a nápovědy, vyhledejte kód, který způsobí, že tyto kritická místa.</span><span class="sxs-lookup"><span data-stu-id="217ae-137">Good tools let you drill quickly into the biggest performance issues (CPU, memory, or disk) and help you locate the code that causes those bottlenecks.</span></span>  <span data-ttu-id="217ae-138">Microsoft, jako dodává celou řadu nástrojů výkonu [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling), [nástroj pro analýzu Windows Phone](http://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f), a [nástroje PerfView](http://www.microsoft.com/download/details.aspx?id=28567).</span><span class="sxs-lookup"><span data-stu-id="217ae-138">Microsoft ships a variety of performance tools such as [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling), [Windows Phone Analysis Tool](http://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f), and [PerfView](http://www.microsoft.com/download/details.aspx?id=28567).</span></span>  
  
 <span data-ttu-id="217ae-139">Nástroje PerfView je bezplatná a amazingly výkonný nástroj, který pomáhá zaměřit se na hloubkové problémy, jako je/v diskových operací GC – události a paměti.</span><span class="sxs-lookup"><span data-stu-id="217ae-139">PerfView is a free and amazingly powerful tool that helps you focus on deep issues such as disk I/O, GC events, and memory.</span></span>  <span data-ttu-id="217ae-140">Můžete zaznamenat související s výkonem [trasování událostí pro Windows](../../../docs/framework/wcf/samples/etw-tracing.md) událostí (ETW) a zobrazení snadno jednu aplikaci, podle procesu, na zásobníku a na vláken informace.</span><span class="sxs-lookup"><span data-stu-id="217ae-140">You can capture performance-related [Event Tracing for Windows](../../../docs/framework/wcf/samples/etw-tracing.md) (ETW) events and view easily per app, per process, per stack, and per thread information.</span></span>  <span data-ttu-id="217ae-141">Nástroje PerfView ukazuje, kolik a jaký druh paměti přidělí vaší aplikace, a které funkce nebo volání zásobníky přispívat kolik k přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="217ae-141">PerfView shows you how much and what kind of memory your app allocates, and which functions or call stacks contribute how much to the memory allocations.</span></span> <span data-ttu-id="217ae-142">Podrobnosti najdete v tématu bohaté témata nápovědy, ukázky a videa, které jsou součástí nástroje (například [nástroje PerfView kurzy](http://channel9.msdn.com/Series/PerfView-Tutorial) na webu Channel 9).</span><span class="sxs-lookup"><span data-stu-id="217ae-142">For details, see the rich help topics, demos, and videos included with the tool (such as the [PerfView tutorials](http://channel9.msdn.com/Series/PerfView-Tutorial) on Channel 9).</span></span>  
  
### <a name="fact-4-its-all-about-allocations"></a><span data-ttu-id="217ae-143">Fakt 4: Všechno se točí kolem přidělení</span><span class="sxs-lookup"><span data-stu-id="217ae-143">Fact 4: It’s all about allocations</span></span>  
 <span data-ttu-id="217ae-144">Může si myslíte, že vytváření reaguje aplikace rozhraní .NET Framework je o algoritmů, například pomocí rychlé řazení místo bublin řazení, ale které se nevztahuje na případ.</span><span class="sxs-lookup"><span data-stu-id="217ae-144">You might think that building a responsive .NET Framework app is all about algorithms, such as using quick sort instead of bubble sort, but that's not the case.</span></span>  <span data-ttu-id="217ae-145">Největších faktorem sestavení fungující aplikace je přidělování paměti, zejména v případě, že vaše aplikace je moc velká nebo zpracovává velké objemy dat.</span><span class="sxs-lookup"><span data-stu-id="217ae-145">The biggest factor in building a responsive app is allocating memory, especially when your app is very large or processes large amounts of data.</span></span>  
  
 <span data-ttu-id="217ae-146">Téměř všechny pracovní k vytvoření fungující IDE vyskytne s překladačem nové rozhraní API podílejí zabraňující přidělení a správě ukládání do mezipaměti strategie.</span><span class="sxs-lookup"><span data-stu-id="217ae-146">Almost all the work to build responsive IDE experiences with the new compiler APIs involved avoiding allocations and managing caching strategies.</span></span>  <span data-ttu-id="217ae-147">Trasování nástroje PerfView zobrazit výkon nové kompilátory jazyka C# a Visual Basic je zřídka procesoru vázána.</span><span class="sxs-lookup"><span data-stu-id="217ae-147">PerfView traces show that the performance of the new C# and Visual Basic compilers is rarely CPU bound.</span></span>  <span data-ttu-id="217ae-148">Kompilátory může být vstupně-výstupních operací vázaný při čtení stovky tisíc nebo miliony řádků kódu, čtení metadat, nebo generování generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="217ae-148">The compilers can be I/O bound when reading hundreds of thousands or millions of lines of code, reading metadata, or emitting generated code.</span></span>  <span data-ttu-id="217ae-149">Uživatelské rozhraní se zpozdí vlákno jsou téměř všechny kvůli uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="217ae-149">The UI thread delays are nearly all due to garbage collection.</span></span>  <span data-ttu-id="217ae-150">Uvolňování paměti rozhraní .NET Framework je vysoce vyladěných výkonu a většinu práce nemá současně, zatímco spouští kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="217ae-150">The .NET Framework GC is highly tuned for performance and does much of its work concurrently while app code executes.</span></span>  <span data-ttu-id="217ae-151">Však můžete aktivovat jeden přidělení nákladné [gen2](../../../docs/standard/garbage-collection/fundamentals.md) kolekce, zastavování všechna vlákna.</span><span class="sxs-lookup"><span data-stu-id="217ae-151">However, a single allocation can trigger an expensive [gen2](../../../docs/standard/garbage-collection/fundamentals.md) collection, stopping all threads.</span></span>  
  
## <a name="common-allocations-and-examples"></a><span data-ttu-id="217ae-152">Běžné přidělování a příklady</span><span class="sxs-lookup"><span data-stu-id="217ae-152">Common allocations and examples</span></span>  
 <span data-ttu-id="217ae-153">Příklady výrazů v této části jsou skryté přidělení, které se zobrazují malé.</span><span class="sxs-lookup"><span data-stu-id="217ae-153">The example expressions in this section have hidden allocations that appear small.</span></span>  <span data-ttu-id="217ae-154">Pokud velké aplikace provede výrazy dostatek časy, ale mohou příčiny stovky v megabajtech, i gigabajtů přidělení.</span><span class="sxs-lookup"><span data-stu-id="217ae-154">However, if a large app executes the expressions enough times, they can causes hundreds of megabytes, even gigabytes, of allocations.</span></span>  <span data-ttu-id="217ae-155">Například jedna minuta testy, které simulované zadáním pro vývojáře v editoru přidělené gigabajty paměti a vedla týmem výkonu a zaměřit se na zadání scénáře.</span><span class="sxs-lookup"><span data-stu-id="217ae-155">For example, one-minute tests that simulated a developer’s typing in the editor allocated gigabytes of memory and led the performance team to focus on typing scenarios.</span></span>  
  
### <a name="boxing"></a><span data-ttu-id="217ae-156">Zabalení</span><span class="sxs-lookup"><span data-stu-id="217ae-156">Boxing</span></span>  
 <span data-ttu-id="217ae-157">[Zabalení](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) nastane, když hodnota typy, obvykle za provozu v zásobníku nebo v datech jsou struktury uzavřen do objektu.</span><span class="sxs-lookup"><span data-stu-id="217ae-157">[Boxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) occurs when value types that normally live on the stack or in data structures are wrapped in an object.</span></span>  <span data-ttu-id="217ae-158">To znamená přidělit objekt pro uložení dat a poté se vraťte ukazatel na objekt.</span><span class="sxs-lookup"><span data-stu-id="217ae-158">That is, you allocate an object to hold the data, and then return a pointer to the object.</span></span>  <span data-ttu-id="217ae-159">Rozhraní .NET Framework někdy oknech hodnoty z důvodu podpis metody nebo typ umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="217ae-159">The .NET Framework sometimes boxes values due to the signature of a method or the type of a storage location.</span></span>  <span data-ttu-id="217ae-160">Zabalení typ hodnoty v objektu přidělení paměti příčiny.</span><span class="sxs-lookup"><span data-stu-id="217ae-160">Wrapping a value type in an object causes memory allocation.</span></span>  <span data-ttu-id="217ae-161">Mnoho zabalení operací můžete přispívat, megabajtech nebo gigabajtech přidělení do vaší aplikace, což znamená, že vaše aplikace způsobí, že další GC.</span><span class="sxs-lookup"><span data-stu-id="217ae-161">Many boxing operations can contribute megabytes or gigabytes of allocations to your app, which means that your app will cause more GCs.</span></span> <span data-ttu-id="217ae-162">Rozhraní .NET Framework a kompilátory jazyka vyhnout zabalení, pokud je to možné, ale někdy dojde při očekáváte minimálně.</span><span class="sxs-lookup"><span data-stu-id="217ae-162">The .NET Framework and the language compilers avoid boxing when possible, but sometimes it happens when you least expect it.</span></span>  
  
 <span data-ttu-id="217ae-163">Zabalení v nástroje PerfView najdete otevřete trasování a podívejte se na zásobníky alokační haldě GC pod názvem procesu vaší aplikace (Nezapomeňte, že nástroje PerfView sestavy o všech procesů).</span><span class="sxs-lookup"><span data-stu-id="217ae-163">To see boxing in PerfView, open a trace and look at GC Heap Alloc Stacks under your app’s process name (remember, PerfView reports on all processes).</span></span>  <span data-ttu-id="217ae-164">Pokud se zobrazí typy jako <xref:System.Int32?displayProperty=nameWithType> a <xref:System.Char?displayProperty=nameWithType> v rámci přidělených jsou zabalení typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="217ae-164">If you see types like <xref:System.Int32?displayProperty=nameWithType> and <xref:System.Char?displayProperty=nameWithType> under allocations, you are boxing value types.</span></span>  <span data-ttu-id="217ae-165">Výběr jedním z těchto typů zobrazí zásobníky a funkce, ve kterých jsou zabalená.</span><span class="sxs-lookup"><span data-stu-id="217ae-165">Choosing one of these types will show the stacks and functions in which they are boxed.</span></span>  
  
 <span data-ttu-id="217ae-166">**Příklad 1: řetězcových metod a hodnotu argumenty typů**</span><span class="sxs-lookup"><span data-stu-id="217ae-166">**Example 1: string methods and value type arguments**</span></span>  
  
 <span data-ttu-id="217ae-167">Tento ukázkový kód ukazuje potenciálně nepotřebné a nadměrnému zabalení:</span><span class="sxs-lookup"><span data-stu-id="217ae-167">This sample code illustrates potentially unnecessary and excessive boxing:</span></span>  
  
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
  
 <span data-ttu-id="217ae-168">Tento kód poskytuje funkce protokolování, aby aplikace může zavolat `Log` funkce často, může být miliony časy.</span><span class="sxs-lookup"><span data-stu-id="217ae-168">This code provides logging functionality, so an app may call the `Log` function frequently, maybe millions of times.</span></span>  <span data-ttu-id="217ae-169">Problém je, že volání `string.Format` překládá se <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> přetížení.</span><span class="sxs-lookup"><span data-stu-id="217ae-169">The problem is that the call to `string.Format` resolves to the <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> overload.</span></span>  
  
 <span data-ttu-id="217ae-170">Toto přetížení vyžaduje rozhraní .NET Framework pro pole `int` hodnoty do objektů předejte toto volání metody.</span><span class="sxs-lookup"><span data-stu-id="217ae-170">This overload requires the .NET Framework to box the `int` values into objects to pass them to this method call.</span></span>  <span data-ttu-id="217ae-171">Částečné opravu je volání `id.ToString()` a `size.ToString()` a předat všechny řetězce (které jsou objekty) `string.Format` volání.</span><span class="sxs-lookup"><span data-stu-id="217ae-171">A partial fix is to call `id.ToString()` and `size.ToString()` and pass all strings (which are objects) to the `string.Format` call.</span></span>  <span data-ttu-id="217ae-172">Volání metody `ToString()` přidělit řetězec, ale, že přidělení přesto dojde v `string.Format`.</span><span class="sxs-lookup"><span data-stu-id="217ae-172">Calling `ToString()` does allocate a string, but that allocation will happen anyway inside `string.Format`.</span></span>  
  
 <span data-ttu-id="217ae-173">Zvažte to tuto základní volat na `string.Format` je právě zřetězení řetězců, takže může místo toho napište tento kód:</span><span class="sxs-lookup"><span data-stu-id="217ae-173">You might consider that this basic call to `string.Format` is just string concatenation, so you might write this code instead:</span></span>  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 <span data-ttu-id="217ae-174">Ale tohoto řádku kódu zavádí zabalení přidělení, protože se zkompiluje do <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="217ae-174">However, that line of code introduces a boxing allocation because it compiles to <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span></span>  <span data-ttu-id="217ae-175">Rozhraní .NET Framework musí pole znak, který má být vyvolán literálu `Concat`</span><span class="sxs-lookup"><span data-stu-id="217ae-175">The .NET Framework must box the character literal to invoke `Concat`</span></span>  
  
 <span data-ttu-id="217ae-176">**Opravte například 1**</span><span class="sxs-lookup"><span data-stu-id="217ae-176">**Fix for example 1**</span></span>  
  
 <span data-ttu-id="217ae-177">Dokončení opravy je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="217ae-177">The complete fix is simple.</span></span>  <span data-ttu-id="217ae-178">Právě nahradí znak literálu s řetězcový literál, který způsobuje žádné zabalení, protože řetězce jsou již objekty:</span><span class="sxs-lookup"><span data-stu-id="217ae-178">Just replace the character literal with a string literal, which incurs no boxing because strings are already objects:</span></span>  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 <span data-ttu-id="217ae-179">**Příklad 2: zabalení výčtu**</span><span class="sxs-lookup"><span data-stu-id="217ae-179">**Example 2: enum boxing**</span></span>  
  
 <span data-ttu-id="217ae-180">V tomto příkladu je zodpovědná za obrovské množství přidělení nového kompilátory jazyka C# a Visual Basic z důvodu často používají typů výčtu, zejména v operacích vyhledávání slovníku.</span><span class="sxs-lookup"><span data-stu-id="217ae-180">This example was responsible for a huge amount of allocation in the new C# and Visual Basic compilers due to frequent use of enumeration types, especially in dictionary lookup operations.</span></span>  
  
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
  
 <span data-ttu-id="217ae-181">Tento problém je velmi malé.</span><span class="sxs-lookup"><span data-stu-id="217ae-181">This problem is very subtle.</span></span>  <span data-ttu-id="217ae-182">Nástroje PerfView by ohlásit jako <xref:System.Enum.GetHashCode> zabalení, protože metoda oknech základní reprezentaci typu výčtu důvodů implementace.</span><span class="sxs-lookup"><span data-stu-id="217ae-182">PerfView would report this as <xref:System.Enum.GetHashCode> boxing because the method boxes the underlying representation of the enumeration type, for implementation reasons.</span></span>  <span data-ttu-id="217ae-183">Pokud se podíváte úzce v nástroje PerfView, mohou se zobrazit dvě zabalení přidělení pro každé volání <xref:System.Enum.GetHashCode>.</span><span class="sxs-lookup"><span data-stu-id="217ae-183">If you look closely in PerfView, you may see two boxing allocations for each call to <xref:System.Enum.GetHashCode>.</span></span>   <span data-ttu-id="217ae-184">Kompilátor vloží jednu a rozhraní .NET Framework vloží na druhý.</span><span class="sxs-lookup"><span data-stu-id="217ae-184">The compiler inserts one, and the .NET Framework inserts the other.</span></span>  
  
 <span data-ttu-id="217ae-185">**Opravte například 2**</span><span class="sxs-lookup"><span data-stu-id="217ae-185">**Fix for example 2**</span></span>  
  
 <span data-ttu-id="217ae-186">Můžete snadno vyhnout obou přidělení přetypování k základní reprezentaci před voláním <xref:System.Enum.GetHashCode>:</span><span class="sxs-lookup"><span data-stu-id="217ae-186">You can easily avoid both allocations by casting to the underlying representation before calling <xref:System.Enum.GetHashCode>:</span></span>  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 <span data-ttu-id="217ae-187">Další běžné zdroj zabalení na výčtové typy je <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="217ae-187">Another common source of boxing on enumeration types is the <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="217ae-188">Argument předaný <xref:System.Enum.HasFlag%28System.Enum%29> má zabaleny.</span><span class="sxs-lookup"><span data-stu-id="217ae-188">The argument passed to <xref:System.Enum.HasFlag%28System.Enum%29> has to be boxed.</span></span>  <span data-ttu-id="217ae-189">Ve většině případů nahrazení volání <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> s bitové testu je jednodušší a bez přidělení.</span><span class="sxs-lookup"><span data-stu-id="217ae-189">In most cases, replacing calls to <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> with a bitwise test is simpler and allocation-free.</span></span>  
  
 <span data-ttu-id="217ae-190">První fakt výkonu mějte na paměti (to znamená, že nemáte optimalizace předčasně) a nespouštět přepisování všech vašich kódech tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="217ae-190">Keep the first performance fact in mind (that is, don’t prematurely optimize) and don’t start rewriting all your code in this way.</span></span>    <span data-ttu-id="217ae-191">Mějte na paměti tyto zabalení nákladů, ale měnit kód až po profilace aplikace a hledání aktivní body.</span><span class="sxs-lookup"><span data-stu-id="217ae-191">Be aware of these boxing costs, but change your code only after profiling your app and finding the hot spots.</span></span>  
  
### <a name="strings"></a><span data-ttu-id="217ae-192">Řetězce</span><span class="sxs-lookup"><span data-stu-id="217ae-192">Strings</span></span>  
 <span data-ttu-id="217ae-193">Manipulace s řetězci jsou některé z největších culprits pro přidělení a jejich často zobrazí v nástroje PerfView v horní pět přidělení.</span><span class="sxs-lookup"><span data-stu-id="217ae-193">String manipulations are some of the biggest culprits for allocations, and they often show up in PerfView in the top five allocations.</span></span>  <span data-ttu-id="217ae-194">Programů používá řetězce pro serializaci JSON a rozhraní REST API.</span><span class="sxs-lookup"><span data-stu-id="217ae-194">Programs use strings for serialization, JSON, and REST APIs.</span></span>  <span data-ttu-id="217ae-195">Řetězce můžete použít jako programový konstanty pro spolupráci s systémy, pokud nelze použít výčtové typy.</span><span class="sxs-lookup"><span data-stu-id="217ae-195">You can use strings as programmatic constants for interoperating with systems when you can’t use enumeration types.</span></span>  <span data-ttu-id="217ae-196">Pokud vaše profilace ukazuje, že řetězce jsou vysoce ovlivňují výkon, vyhledejte volání <xref:System.String> metody, jako <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>a tak dále.</span><span class="sxs-lookup"><span data-stu-id="217ae-196">When your profiling shows that strings are highly affecting performance, look for calls to <xref:System.String> methods such as <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, and so on.</span></span>  <span data-ttu-id="217ae-197">Pomocí <xref:System.Text.StringBuilder> předejdete náklady na vytvoření jeden řetězec z mnoha pomáhá částí, ale i přidělování <xref:System.Text.StringBuilder> objektu se může stát úzkým místem, které potřebujete ke správě.</span><span class="sxs-lookup"><span data-stu-id="217ae-197">Using <xref:System.Text.StringBuilder> to avoid the cost of creating one string from many pieces helps, but even allocating the <xref:System.Text.StringBuilder> object might become a bottleneck that you need to manage.</span></span>  
  
 <span data-ttu-id="217ae-198">**Příklad 3: operace s řetězci**</span><span class="sxs-lookup"><span data-stu-id="217ae-198">**Example 3: string operations**</span></span>  
  
 <span data-ttu-id="217ae-199">Kompilátor jazyka C# měl tento kód, který zapíše text formátovaný komentáře doc XML:</span><span class="sxs-lookup"><span data-stu-id="217ae-199">The C# compiler had this code that writes the text of a formatted XML doc comment:</span></span>  
  
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
  
 <span data-ttu-id="217ae-200">Uvidíte, že tento kód provede spoustu zacházení s řetězci.</span><span class="sxs-lookup"><span data-stu-id="217ae-200">You can see that this code does a lot of string manipulation.</span></span>  <span data-ttu-id="217ae-201">Kód používá metod knihovny rozdělit řádky do samostatné řetězce, oříznout mezera, zkontrolujte, zda argument `text` je komentáře jazyka XML dokumentace a k extrahování dílčích řetězců z řádků.</span><span class="sxs-lookup"><span data-stu-id="217ae-201">The code uses library methods to split lines into separate strings, to trim white space, to check whether the argument `text` is an XML documentation comment, and to extract substrings from lines.</span></span>  
  
 <span data-ttu-id="217ae-202">Na první řádek uvnitř `WriteFormattedDocComment`, `text.Split` volání přiděluje nový element tři pole jako argument pokaždé, když je volána.</span><span class="sxs-lookup"><span data-stu-id="217ae-202">On the first line inside `WriteFormattedDocComment`, the `text.Split` call allocates a new three-element array as the argument every time it’s called.</span></span>  <span data-ttu-id="217ae-203">Kompilátor má vyvolat kód přidělit pokaždé, když toto pole.</span><span class="sxs-lookup"><span data-stu-id="217ae-203">The compiler has to emit code to allocate this array each time.</span></span>  <span data-ttu-id="217ae-204">Je to způsobeno kompilátor není známo, pokud <xref:System.String.Split%2A> ukládá pole někde kde pole by se mohly změnit jiným kódem, které by ovlivnily pozdější volání `WriteFormattedDocComment`.</span><span class="sxs-lookup"><span data-stu-id="217ae-204">That’s because the compiler doesn’t know if <xref:System.String.Split%2A> stores the array somewhere where the array might be modified by other code, which would affect later calls to `WriteFormattedDocComment`.</span></span>  <span data-ttu-id="217ae-205">Volání <xref:System.String.Split%2A> také přiděluje řetězec pro každý řádek v `text` a přiděluje další paměť k provedení operace.</span><span class="sxs-lookup"><span data-stu-id="217ae-205">The call to <xref:System.String.Split%2A> also allocates a string for every line in `text` and allocates other memory to perform the operation.</span></span>  
  
 <span data-ttu-id="217ae-206">`WriteFormattedDocComment` má tři volání <xref:System.String.TrimStart%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="217ae-206">`WriteFormattedDocComment` has three calls to the <xref:System.String.TrimStart%2A> method.</span></span>  <span data-ttu-id="217ae-207">Dva jsou v informacích o vnitřní smyčky, které duplicitní práci a přidělení.</span><span class="sxs-lookup"><span data-stu-id="217ae-207">Two are in inner loops that duplicate work and allocations.</span></span>  <span data-ttu-id="217ae-208">Chcete-li nejhorší záleží, volání <xref:System.String.TrimStart%2A> metoda bez argumentů přiděluje prázdné pole (pro `params` parametr) kromě výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="217ae-208">To make matters worse, calling the <xref:System.String.TrimStart%2A> method with no arguments allocates an empty array (for the `params` parameter) in addition to the string result.</span></span>  
  
 <span data-ttu-id="217ae-209">Nakonec je volání <xref:System.String.Substring%2A> metodu, která obvykle přiděluje nový řetězec.</span><span class="sxs-lookup"><span data-stu-id="217ae-209">Lastly, there is a call to the <xref:System.String.Substring%2A> method, which usually allocates a new string.</span></span>  
  
 <span data-ttu-id="217ae-210">**Opravte například 3**</span><span class="sxs-lookup"><span data-stu-id="217ae-210">**Fix for example 3**</span></span>  
  
 <span data-ttu-id="217ae-211">Na rozdíl od předchozích příkladech nemůže malé úpravy opravit tyto přidělení.</span><span class="sxs-lookup"><span data-stu-id="217ae-211">Unlike the earlier examples, small edits cannot fix these allocations.</span></span>  <span data-ttu-id="217ae-212">Budete muset krok zpět, podívejte se na problém a bezkódovém přístupu jinak.</span><span class="sxs-lookup"><span data-stu-id="217ae-212">You need to step back, look at the problem, and approach it differently.</span></span>  <span data-ttu-id="217ae-213">Například můžete všimnout, který argument `WriteFormattedDocComment()` je řetězec, který obsahuje všechny informace, které potřebuje metodu, takže kód udělat další indexování místo přidělování mnoho částečné řetězce.</span><span class="sxs-lookup"><span data-stu-id="217ae-213">For example, you'll notice that the argument to `WriteFormattedDocComment()` is a string that has all the information that the method needs, so the code could do more indexing instead of allocating many partial strings.</span></span>  
  
 <span data-ttu-id="217ae-214">Kompilátoru výkonu team řešit všechny tyto přidělení kódem takto:</span><span class="sxs-lookup"><span data-stu-id="217ae-214">The compiler’s performance team tackled all these allocations with code like this:</span></span>  
  
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
  
 <span data-ttu-id="217ae-215">První verze součásti `WriteFormattedDocComment()` přidělené pole, několik dílčích řetězců a oříznutý substring společně s prázdnou `params` pole.</span><span class="sxs-lookup"><span data-stu-id="217ae-215">The first version of `WriteFormattedDocComment()` allocated an array, several substrings, and a trimmed substring along with an empty `params` array.</span></span>  <span data-ttu-id="217ae-216">Je také zkontrolovat `"///"`.</span><span class="sxs-lookup"><span data-stu-id="217ae-216">It also checked for `"///"`.</span></span>  <span data-ttu-id="217ae-217">Revidovaný kód používá jenom indexování a přiděluje nic.</span><span class="sxs-lookup"><span data-stu-id="217ae-217">The revised code uses only indexing and allocates nothing.</span></span>  <span data-ttu-id="217ae-218">Najde první znak, který není mezera a kontroly znak po znaku zobrazíte, zda text začíná `"///"`.</span><span class="sxs-lookup"><span data-stu-id="217ae-218">It finds the first character that is not white space, and then checks character by character to see if the string starts with `"///"`.</span></span>  <span data-ttu-id="217ae-219">Nový kód používá `IndexOfFirstNonWhiteSpaceChar` místo <xref:System.String.TrimStart%2A> vrátit první index (za zadaný počáteční index), kde dojde k neprázdný znak.</span><span class="sxs-lookup"><span data-stu-id="217ae-219">The new code uses `IndexOfFirstNonWhiteSpaceChar` instead of <xref:System.String.TrimStart%2A> to return the first index (after a specified start index) where a non-whitespace character occurs.</span></span>  <span data-ttu-id="217ae-220">Oprava není dokončena, ale uvidíte, jak se má použít podobné opravy pro kompletního řešení.</span><span class="sxs-lookup"><span data-stu-id="217ae-220">The fix is not complete, but you can see how to apply similar fixes for a complete solution.</span></span>  <span data-ttu-id="217ae-221">Použitím tohoto přístupu napříč kódem, můžete odebrat všechny přidělení v `WriteFormattedDocComment()`.</span><span class="sxs-lookup"><span data-stu-id="217ae-221">By applying this approach throughout the code, you can remove all allocations in `WriteFormattedDocComment()`.</span></span>  
  
 <span data-ttu-id="217ae-222">**Příklad 4: StringBuilder**</span><span class="sxs-lookup"><span data-stu-id="217ae-222">**Example 4: StringBuilder**</span></span>  
  
 <span data-ttu-id="217ae-223">Tento příklad používá <xref:System.Text.StringBuilder> objektu.</span><span class="sxs-lookup"><span data-stu-id="217ae-223">This example uses a <xref:System.Text.StringBuilder> object.</span></span>  <span data-ttu-id="217ae-224">Název typu úplné pro obecné typy vygeneruje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="217ae-224">The following function generates a full type name for generic types:</span></span>  
  
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
  
 <span data-ttu-id="217ae-225">Zaměřuje se na řádek, který vytvoří nový <xref:System.Text.StringBuilder> instance.</span><span class="sxs-lookup"><span data-stu-id="217ae-225">The focus is on the line that creates a new <xref:System.Text.StringBuilder> instance.</span></span>  <span data-ttu-id="217ae-226">Kód způsobí, že přidělení pro `sb.ToString()` a interních přidělování v rámci <xref:System.Text.StringBuilder> implementace, ale nemůže ovládat těchto přidělení, pokud chcete, aby výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="217ae-226">The code causes an allocation for `sb.ToString()` and internal allocations within the <xref:System.Text.StringBuilder> implementation, but you cannot control those allocations if you want the string result.</span></span>  
  
 <span data-ttu-id="217ae-227">**Opravte například 4**</span><span class="sxs-lookup"><span data-stu-id="217ae-227">**Fix for example 4**</span></span>  
  
 <span data-ttu-id="217ae-228">Chcete-li odstranit `StringBuilder` objektu přidělení, mezipaměti objekt.</span><span class="sxs-lookup"><span data-stu-id="217ae-228">To fix the `StringBuilder` object allocation, cache the  object.</span></span>  <span data-ttu-id="217ae-229">I ukládání jediné instance, který může získat zahozeny může výrazně zvýšit výkon.</span><span class="sxs-lookup"><span data-stu-id="217ae-229">Even caching a single instance that might get thrown away can improve performance significantly.</span></span>  <span data-ttu-id="217ae-230">Toto je funkce nové implementace vynechání všechny kód s výjimkou nové první a poslední řádky:</span><span class="sxs-lookup"><span data-stu-id="217ae-230">This is the function’s new implementation, omitting all the code except for the new first and last lines:</span></span>  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 <span data-ttu-id="217ae-231">Klíčovými částmi jsou nové `AcquireBuilder()` a `GetStringAndReleaseBuilder()` funkce:</span><span class="sxs-lookup"><span data-stu-id="217ae-231">The key parts are the new `AcquireBuilder()` and `GetStringAndReleaseBuilder()` functions:</span></span>  
  
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
  
 <span data-ttu-id="217ae-232">Protože nové kompilátory použít dělení na vlákna, použijte tyto implementace vlákno statické pole (<xref:System.ThreadStaticAttribute> atribut) do mezipaměti <xref:System.Text.StringBuilder>, a pravděpodobně můžete vynecháte `ThreadStatic` deklarace.</span><span class="sxs-lookup"><span data-stu-id="217ae-232">Because the new compilers use threading, these implementations use a thread-static field (<xref:System.ThreadStaticAttribute> attribute) to cache the <xref:System.Text.StringBuilder>, and you likely can forgo the `ThreadStatic` declaration.</span></span>  <span data-ttu-id="217ae-233">Vlákno statické pole obsahuje jedinečnou hodnotu pro každý podproces, který se spustí tento kód.</span><span class="sxs-lookup"><span data-stu-id="217ae-233">The thread-static field holds a unique value for each thread that executes this code.</span></span>  
  
 <span data-ttu-id="217ae-234">`AcquireBuilder()` Vrátí uložená v mezipaměti <xref:System.Text.StringBuilder> instance, pokud je jedna po vymazáním a nastavení pole nebo mezipaměti na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="217ae-234">`AcquireBuilder()` returns the cached <xref:System.Text.StringBuilder> instance if there is one, after clearing it and setting the field or cache to null.</span></span>  <span data-ttu-id="217ae-235">V opačném `AcquireBuilder()` vytvoří novou instanci a vrátí ji, ponechat sadu pole nebo mezipaměti na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="217ae-235">Otherwise, `AcquireBuilder()` creates a new instance and returns it, leaving the field or cache set to null.</span></span>  
  
 <span data-ttu-id="217ae-236">Když jste hotovi s <xref:System.Text.StringBuilder> , zavoláte `GetStringAndReleaseBuilder()` získat výsledném řetězci, uložte <xref:System.Text.StringBuilder> instance v mezipaměti na pole a pak vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="217ae-236">When you’re done with <xref:System.Text.StringBuilder> , you call `GetStringAndReleaseBuilder()` to get the string result, save the <xref:System.Text.StringBuilder> instance in the field or cache, and then return the result.</span></span>  <span data-ttu-id="217ae-237">Je možné pro provedení znovu zadat Tento kód a vytvořte více <xref:System.Text.StringBuilder> objekty (i když k tomu jenom občas dojde).</span><span class="sxs-lookup"><span data-stu-id="217ae-237">It is possible for execution to re-enter this code and to create multiple <xref:System.Text.StringBuilder> objects (although that rarely happens).</span></span>  <span data-ttu-id="217ae-238">Nástroje kód uloží jenom poslední vydané <xref:System.Text.StringBuilder> instance pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="217ae-238">The code saves only the last released <xref:System.Text.StringBuilder> instance for later use.</span></span>  <span data-ttu-id="217ae-239">Tento jednoduchý ukládání do mezipaměti strategie výrazně snížit přidělení v nové kompilátory.</span><span class="sxs-lookup"><span data-stu-id="217ae-239">This simple caching strategy significantly reduced allocations in the new compilers.</span></span>  <span data-ttu-id="217ae-240">Součásti rozhraní .NET Framework a MSBuild ("MSBuild") podobný postup použít ke zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="217ae-240">Parts of the .NET Framework and MSBuild ("MSBuild") use a similar technique to improve performance.</span></span>  
  
 <span data-ttu-id="217ae-241">Tato strategie jednoduché ukládání do mezipaměti dodržuje pravidla návrh dobrý mezipaměti, protože má velikost zakončení.</span><span class="sxs-lookup"><span data-stu-id="217ae-241">This simple caching strategy adheres to good cache design because it has a size cap.</span></span>  <span data-ttu-id="217ae-242">V původním, což znamená další náklady na údržbu je však nyní než další kód.</span><span class="sxs-lookup"><span data-stu-id="217ae-242">However, there is more code now than in the original, which means more maintenance costs.</span></span>  <span data-ttu-id="217ae-243">Ukládání do mezipaměti strategie by měl použít, pouze v případě, že jste nalezené problémy s výkonem a nástroje PerfView ukázaly, že <xref:System.Text.StringBuilder> přidělení jsou významné Přispěvatel.</span><span class="sxs-lookup"><span data-stu-id="217ae-243">You should adopt the caching strategy only if you’ve found a performance problem, and PerfView has shown that <xref:System.Text.StringBuilder> allocations are a significant contributor.</span></span>  
  
### <a name="linq-and-lambdas"></a><span data-ttu-id="217ae-244">LINQ a lambdas</span><span class="sxs-lookup"><span data-stu-id="217ae-244">LINQ and lambdas</span></span>  
 <span data-ttu-id="217ae-245">Pomocí Language-Integrated Query (LINQ) a lambda výrazů je skvělým příklad použití výkonné funkce, které může později zjistíte, že budete muset přepište kód přestane být významný dopad na výkon.</span><span class="sxs-lookup"><span data-stu-id="217ae-245">Using Language-Integrated Query (LINQ) and lambda expressions is a great example of using productive features that you might later find you need to rewrite if the code becomes a significant impact on performance.</span></span>  
  
 <span data-ttu-id="217ae-246">**Příklad 5: Lambdas, seznam\<T > a rozhraní IEnumerable\<T >**</span><span class="sxs-lookup"><span data-stu-id="217ae-246">**Example 5: Lambdas, List\<T>, and IEnumerable\<T>**</span></span>  
  
 <span data-ttu-id="217ae-247">Tento příklad používá [LINQ a kódu funkční stylu](http://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) symbol vyhledejte v kompilátoru modelu zadaný řetězec názvu:</span><span class="sxs-lookup"><span data-stu-id="217ae-247">This example uses [LINQ and functional style code](http://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) to find a symbol in the compiler’s model, given a name string:</span></span>  
  
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
  
 <span data-ttu-id="217ae-248">Nové kompilátoru a prostředí IDE postavené na něm volat `FindMatchingSymbol()` velmi často a že jsou několik skrytá přidělení v tato funkce jediný řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="217ae-248">The new compiler and the IDE experiences built on it call `FindMatchingSymbol()` very frequently, and there are several hidden allocations in this function’s single line of code.</span></span>  <span data-ttu-id="217ae-249">Pro zjištění těchto přidělení, nejprve jediný řádek kódu funkce rozdělení na dva řádky:</span><span class="sxs-lookup"><span data-stu-id="217ae-249">To examine those allocations, first split the function’s single line of code into two lines:</span></span>  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 <span data-ttu-id="217ae-250">V prvním řádku [výrazu lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)`s => s.Name == name`[zavře přes](http://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) místní proměnné `name`.</span><span class="sxs-lookup"><span data-stu-id="217ae-250">In the first line, the [lambda expression](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)`s => s.Name == name`[closes over](http://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) the local variable `name`.</span></span>  <span data-ttu-id="217ae-251">To znamená, že kromě přidělování objekt pro [delegovat](~/docs/csharp/language-reference/keywords/delegate.md) , `predicate` obsahuje, kód přiděluje statická třída pro uložení prostředí, které jsou zaznamenány hodnotu `name`.</span><span class="sxs-lookup"><span data-stu-id="217ae-251">This means that in addition to allocating an object for the [delegate](~/docs/csharp/language-reference/keywords/delegate.md) that `predicate` holds, the code allocates a static class to hold the environment that captures the value of `name`.</span></span>  <span data-ttu-id="217ae-252">Kompilátor generuje kód takto:</span><span class="sxs-lookup"><span data-stu-id="217ae-252">The compiler generates code like the following:</span></span>  
  
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
  
 <span data-ttu-id="217ae-253">Dva `new` přidělení (jeden pro třídu prostředí) a jeden pro delegáta jsou nyní explicitní.</span><span class="sxs-lookup"><span data-stu-id="217ae-253">The two `new` allocations (one for the environment class and one for the delegate) are explicit now.</span></span>  
  
 <span data-ttu-id="217ae-254">Nyní podívejte se na volání `FirstOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="217ae-254">Now look at the call to `FirstOrDefault`.</span></span> <span data-ttu-id="217ae-255">Tato metoda rozšíření na <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typ způsobuje přidělení příliš.</span><span class="sxs-lookup"><span data-stu-id="217ae-255">This extension method on the <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> type incurs an allocation too.</span></span>  <span data-ttu-id="217ae-256">Protože `FirstOrDefault` trvá <xref:System.Collections.Generic.IEnumerable%601> objekt jako svůj první argument, můžete rozšířit volání následující kód (zjednodušená trochu diskusi):</span><span class="sxs-lookup"><span data-stu-id="217ae-256">Because `FirstOrDefault` takes an <xref:System.Collections.Generic.IEnumerable%601> object as its first argument, you can expand the call to the following code (simplified a bit for discussion):</span></span>  
  
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
  
 <span data-ttu-id="217ae-257">`symbols` Proměnná má typ <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="217ae-257">The `symbols` variable has type <xref:System.Collections.Generic.List%601>.</span></span>  <span data-ttu-id="217ae-258"><xref:System.Collections.Generic.List%601> – Typ kolekce implementuje <xref:System.Collections.Generic.IEnumerable%601> a cleverly definuje enumerátor (<xref:System.Collections.Generic.IEnumerator%601> rozhraní), <xref:System.Collections.Generic.List%601> implementuje s `struct`.</span><span class="sxs-lookup"><span data-stu-id="217ae-258">The <xref:System.Collections.Generic.List%601> collection type implements <xref:System.Collections.Generic.IEnumerable%601> and cleverly defines an enumerator (<xref:System.Collections.Generic.IEnumerator%601> interface) that <xref:System.Collections.Generic.List%601> implements with a `struct`.</span></span>  <span data-ttu-id="217ae-259">Pomocí strukturou místo třídu znamená obvykle vyhnout rozdělení haldy, které se pak může ovlivnit výkon kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="217ae-259">Using a structure instead of a class means that you usually avoid any heap allocations, which, in turn, can affect garbage collection performance.</span></span>  <span data-ttu-id="217ae-260">Výčty jsou obvykle používány v jazyce `foreach` smyčky, která využívá strukturu enumerátor je vrácený v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="217ae-260">Enumerators are typically used with the language’s `foreach` loop, which uses the enumerator structure as it is returned on the call stack.</span></span>  <span data-ttu-id="217ae-261">Zvyšování ukazatel zásobníku volání aby uvolnil prostor pro objekt nemá vliv na způsob přidělení haldy nemá GC.</span><span class="sxs-lookup"><span data-stu-id="217ae-261">Incrementing the call stack pointer to make room for an object does not affect GC the way a heap allocation does.</span></span>  
  
 <span data-ttu-id="217ae-262">V případě rozšířená `FirstOrDefault` volání kód potřebuje volat `GetEnumerator()` na <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="217ae-262">In the case of the expanded `FirstOrDefault` call, the code needs to call `GetEnumerator()` on an <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  <span data-ttu-id="217ae-263">Přiřazení `symbols` k `enumerable` proměnné typu `IEnumerable<Symbol>` ztratí informace, které se objekt skutečné <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="217ae-263">Assigning `symbols` to the `enumerable` variable of type `IEnumerable<Symbol>` loses the information that the actual object is a <xref:System.Collections.Generic.List%601>.</span></span>  <span data-ttu-id="217ae-264">To znamená, že když kód načte enumerátor s `enumerable.GetEnumerator()`, rozhraní .NET Framework je pole vrácené struktura přiřadit ho k `enumerator` proměnné.</span><span class="sxs-lookup"><span data-stu-id="217ae-264">This means that when the code fetches the enumerator with `enumerable.GetEnumerator()`, the .NET Framework has to box the returned structure to assign it to the `enumerator` variable.</span></span>  
  
 <span data-ttu-id="217ae-265">**Opravte například 5**</span><span class="sxs-lookup"><span data-stu-id="217ae-265">**Fix for example 5**</span></span>  
  
 <span data-ttu-id="217ae-266">Oprava je přepsání `FindMatchingSymbol` šest řádků kódu, které jsou stále stručné sdělení, snadno přečíst a pochopit a snadnou údržbou nahraďte jeho jediný řádek kódu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="217ae-266">The fix is to rewrite `FindMatchingSymbol` as follows, replacing its single line of code with six lines of code that are still concise, easy to read and understand, and easy to maintain:</span></span>  
  
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
  
 <span data-ttu-id="217ae-267">Tento kód nepoužívá rozšiřující metody, lambdas nebo výčty LINQ a budou vám účtovány žádné přidělení.</span><span class="sxs-lookup"><span data-stu-id="217ae-267">This code doesn’t use LINQ extension methods, lambdas, or enumerators, and it incurs no allocations.</span></span>  <span data-ttu-id="217ae-268">Nejsou žádné přidělení, protože kompilátor uvidíte, že `symbols` kolekce <xref:System.Collections.Generic.List%601> a může svázat výsledný enumerátor (strukturou) místní proměnné s správný typ. předejdete zabalení.</span><span class="sxs-lookup"><span data-stu-id="217ae-268">There are no allocations because the compiler can see that the `symbols` collection is a <xref:System.Collections.Generic.List%601> and can bind the resulting enumerator (a structure) to a local variable with the right type to avoid boxing.</span></span>  <span data-ttu-id="217ae-269">Původní verze této funkce se skvělé příklad výrazovou sílu jazyka C# a rozhraní .NET Framework na produktivitu.</span><span class="sxs-lookup"><span data-stu-id="217ae-269">The original version of this function was a great example of the expressive power of C# and the productivity of the .NET Framework.</span></span>  <span data-ttu-id="217ae-270">Tato verze nové a efektivnější uchovává tyto vlastnosti bez přidání jakékoli složitý kód k údržbě.</span><span class="sxs-lookup"><span data-stu-id="217ae-270">This new and more efficient version preserves those qualities without adding any complex code to maintain.</span></span>  
  
### <a name="async-method-caching"></a><span data-ttu-id="217ae-271">Asynchronní metoda ukládání do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="217ae-271">Async method caching</span></span>  
 <span data-ttu-id="217ae-272">Další příklad ukazuje častých problémů, když se pokusíte použít výsledky uložené v mezipaměti v [asynchronní](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7) metoda.</span><span class="sxs-lookup"><span data-stu-id="217ae-272">The next example shows a common problem when you try to use cached results in an [async](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7) method.</span></span>  
  
 <span data-ttu-id="217ae-273">**Příklad 6: ukládání do mezipaměti v asynchronní metody**</span><span class="sxs-lookup"><span data-stu-id="217ae-273">**Example 6: caching in async methods**</span></span>  
  
 <span data-ttu-id="217ae-274">Funkce Visual Studio IDE založený na nové kompilátory jazyka C# a Visual Basic často načtení stromy syntaxe a kompilátory použít asynchronní při tak zachovat přizpůsobivý Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="217ae-274">The Visual Studio IDE features built on the new C# and Visual Basic compilers frequently fetch syntax trees, and the compilers use async when doing so to keep Visual Studio responsive.</span></span>  <span data-ttu-id="217ae-275">Tady je první verze součásti kód, který může zapsat získat stromu syntaxe:</span><span class="sxs-lookup"><span data-stu-id="217ae-275">Here’s the first version of the code you might write to get a syntax tree:</span></span>  
  
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
  
 <span data-ttu-id="217ae-276">Uvidíte, že volání `GetSyntaxTreeAsync()` vytvoří `Parser`, analyzuje kód a potom se vrátí <xref:System.Threading.Tasks.Task> objekt, `Task<SyntaxTree>`.</span><span class="sxs-lookup"><span data-stu-id="217ae-276">You can see that calling `GetSyntaxTreeAsync()` instantiates a `Parser`, parses the code, and then returns a <xref:System.Threading.Tasks.Task> object, `Task<SyntaxTree>`.</span></span>  <span data-ttu-id="217ae-277">Je nákladné část přidělování `Parser` instance a analýze kódu.</span><span class="sxs-lookup"><span data-stu-id="217ae-277">The expensive part is allocating the `Parser` instance and parsing the code.</span></span>  <span data-ttu-id="217ae-278">Funkce vrátí hodnotu <xref:System.Threading.Tasks.Task> , aby mohli volající await analýzy práce a uvolněte vlákna uživatelského rozhraní spolupracovat s vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="217ae-278">The function returns a <xref:System.Threading.Tasks.Task> so that callers can await the parsing work and free the UI thread to be responsive to user input.</span></span>  
  
 <span data-ttu-id="217ae-279">Několik funkcí sady Visual Studio může pokusit získat stejném stromu syntaxe tak může zapsat následující kód pro ukládání do mezipaměti analýzy výsledek ušetříte čas a přidělení.</span><span class="sxs-lookup"><span data-stu-id="217ae-279">Several Visual Studio features might try to get the same syntax tree, so you might write the following code to cache the parsing result to save time and allocations.</span></span>  <span data-ttu-id="217ae-280">Tento kód však způsobuje přidělení:</span><span class="sxs-lookup"><span data-stu-id="217ae-280">However, this code incurs an allocation:</span></span>  
  
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
  
 <span data-ttu-id="217ae-281">Uvidíte, že má nový kód s ukládáním do mezipaměti `SyntaxTree` pole s názvem `cachedResult`.</span><span class="sxs-lookup"><span data-stu-id="217ae-281">You see that the new code with caching has a `SyntaxTree` field named `cachedResult`.</span></span>  <span data-ttu-id="217ae-282">Pokud toto pole má hodnotu null, `GetSyntaxTreeAsync()` provádí práce a uloží výsledek v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="217ae-282">When this field is null, `GetSyntaxTreeAsync()` does the work and saves the result in the cache.</span></span>  <span data-ttu-id="217ae-283">`GetSyntaxTreeAsync()` Vrátí `SyntaxTree` objektu.</span><span class="sxs-lookup"><span data-stu-id="217ae-283">`GetSyntaxTreeAsync()` returns the `SyntaxTree` object.</span></span>  <span data-ttu-id="217ae-284">Problém je, že když máte `async` – funkce typu `Task<SyntaxTree>`, a vrátí hodnotu typu `SyntaxTree`, kompilátor vydává kód přidělit úlohu pro uložení výsledek (pomocí `Task<SyntaxTree>.FromResult()`).</span><span class="sxs-lookup"><span data-stu-id="217ae-284">The problem is that when you have an `async` function of type `Task<SyntaxTree>`, and you return a value of type `SyntaxTree`, the compiler emits code to allocate a Task to hold the result (by using `Task<SyntaxTree>.FromResult()`).</span></span>  <span data-ttu-id="217ae-285">Úloha je označena jako dokončená a výsledkem je ihned k dispozici.</span><span class="sxs-lookup"><span data-stu-id="217ae-285">The Task is marked as completed, and the result is immediately available.</span></span>  <span data-ttu-id="217ae-286">V kódu pro nové kompilátory <xref:System.Threading.Tasks.Task> objekty, které již byly dokončeny tak často to uchycení tyto přidělení zlepšila odezvu zaznamenatelný dopad došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="217ae-286">In the code for the new compilers, <xref:System.Threading.Tasks.Task> objects that were already completed occurred so often that fixing these allocations improved responsiveness noticeably.</span></span>  
  
 <span data-ttu-id="217ae-287">**Opravte například 6**</span><span class="sxs-lookup"><span data-stu-id="217ae-287">**Fix for example 6**</span></span>  
  
 <span data-ttu-id="217ae-288">Chcete-li odebrat dokončené <xref:System.Threading.Tasks.Task> přidělení, můžete mezipaměti objekt úlohy dokončené výsledkem:</span><span class="sxs-lookup"><span data-stu-id="217ae-288">To remove the completed <xref:System.Threading.Tasks.Task> allocation, you can cache the Task object with the completed result:</span></span>  
  
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
  
 <span data-ttu-id="217ae-289">Tento kód změní typ `cachedResult` k `Task<SyntaxTree>` a využívá `async` pomocné funkce, která obsahuje původní kód `GetSyntaxTreeAsync()`.</span><span class="sxs-lookup"><span data-stu-id="217ae-289">This code changes the type of `cachedResult` to `Task<SyntaxTree>` and employs an `async` helper function that holds the original code from `GetSyntaxTreeAsync()`.</span></span>  <span data-ttu-id="217ae-290">`GetSyntaxTreeAsync()` Teď používá [null slučovací operátor](~/docs/csharp/language-reference/operators/null-conditional-operator.md) vrátit `cachedResult` , pokud není null.</span><span class="sxs-lookup"><span data-stu-id="217ae-290">`GetSyntaxTreeAsync()` now uses the [null coalescing operator](~/docs/csharp/language-reference/operators/null-conditional-operator.md) to return `cachedResult` if it isn't null.</span></span>  <span data-ttu-id="217ae-291">Pokud `cachedResult` má hodnotu null, pak `GetSyntaxTreeAsync()` volání `GetSyntaxTreeUncachedAsync()` a ukládá do mezipaměti výsledek.</span><span class="sxs-lookup"><span data-stu-id="217ae-291">If `cachedResult` is null, then `GetSyntaxTreeAsync()` calls `GetSyntaxTreeUncachedAsync()` and caches the result.</span></span>  <span data-ttu-id="217ae-292">Všimněte si, že `GetSyntaxTreeAsync()` není await volání `GetSyntaxTreeUncachedAsync()` jako kód běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="217ae-292">Notice that `GetSyntaxTreeAsync()` doesn’t await the call to `GetSyntaxTreeUncachedAsync()` as the code would normally.</span></span>  <span data-ttu-id="217ae-293">Nepoužíváte await znamená že v případě `GetSyntaxTreeUncachedAsync()` vrátí jeho <xref:System.Threading.Tasks.Task> objekt, `GetSyntaxTreeAsync()` hned vrátí <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="217ae-293">Not using await means that when `GetSyntaxTreeUncachedAsync()` returns its <xref:System.Threading.Tasks.Task> object, `GetSyntaxTreeAsync()` immediately returns the <xref:System.Threading.Tasks.Task>.</span></span>  <span data-ttu-id="217ae-294">Nyní v mezipaměti výsledkem je, <xref:System.Threading.Tasks.Task>, takže neexistují žádné přidělení vrátit výsledky uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="217ae-294">Now, the cached result is a <xref:System.Threading.Tasks.Task>, so there are no allocations to return the cached result.</span></span>  
  
### <a name="additional-considerations"></a><span data-ttu-id="217ae-295">Další informace</span><span class="sxs-lookup"><span data-stu-id="217ae-295">Additional considerations</span></span>  
 <span data-ttu-id="217ae-296">Zde naleznete několik více bodů o možných problémech ve velkých aplikací nebo aplikace, které zpracovávají velké množství dat.</span><span class="sxs-lookup"><span data-stu-id="217ae-296">Here are a few more points about potential problems in large apps or apps that process a lot of data.</span></span>  
  
 <span data-ttu-id="217ae-297">**slovník**</span><span class="sxs-lookup"><span data-stu-id="217ae-297">**Dictionaries**</span></span>  
  
 <span data-ttu-id="217ae-298">Slovník ubiquitously slouží v mnoha aplikacích a když slovník jsou velmi vhodné a ze své podstaty efektivní.</span><span class="sxs-lookup"><span data-stu-id="217ae-298">Dictionaries are used ubiquitously in many programs, and though dictionaries are very convenient and inherently efficient.</span></span>  <span data-ttu-id="217ae-299">Však se často používají nesprávně.</span><span class="sxs-lookup"><span data-stu-id="217ae-299">However, they’re often used inappropriately.</span></span>  <span data-ttu-id="217ae-300">V sadě Visual Studio a nové kompilátory analýza ukazuje řadu slovníků obsahovala jeden element nebo byly prázdné.</span><span class="sxs-lookup"><span data-stu-id="217ae-300">In Visual Studio and the new compilers, analysis shows that many of the dictionaries contained a single element or were empty.</span></span>  <span data-ttu-id="217ae-301">Prázdná <xref:System.Collections.Generic.Dictionary%602> má deset polí a zabírá 48 bajtů v haldě na x86 počítače.</span><span class="sxs-lookup"><span data-stu-id="217ae-301">An empty <xref:System.Collections.Generic.Dictionary%602> has ten fields and occupies 48 bytes on the heap on an x86 machine.</span></span>  <span data-ttu-id="217ae-302">Slovník jsou skvělé, pokud potřebujete datová struktura mapování nebo asociovaných s konstanta čas vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="217ae-302">Dictionaries are great when you need a mapping or associative data structure with constant-time lookup.</span></span>  <span data-ttu-id="217ae-303">Ale pokud máte pouze několik elementy, je odpady velké množství místa pomocí slovníku.</span><span class="sxs-lookup"><span data-stu-id="217ae-303">However, when you have only a few elements, you waste a lot of space by using a dictionary.</span></span>  <span data-ttu-id="217ae-304">Místo toho, například je může interaktivně projděte `List<KeyValuePair\<K,V>>`, stejně tak rychlé.</span><span class="sxs-lookup"><span data-stu-id="217ae-304">Instead, for example, you could iteratively look through a `List<KeyValuePair\<K,V>>`, just as fast.</span></span>  <span data-ttu-id="217ae-305">Pokud používáte slovník pouze pro zatížení s daty a pak čtení z něj (velmi běžný vzor), pomocí seřazené pole vyhledávání N(log(N)) může být téměř jako rychlé, v závislosti na počtu prvky, které používáte.</span><span class="sxs-lookup"><span data-stu-id="217ae-305">If you use a dictionary only to load it with data and then read from it (a very common pattern), using a sorted array with an N(log(N)) lookup might be nearly as fast, depending on the number of elements you're using.</span></span>  
  
 <span data-ttu-id="217ae-306">**Třídy a struktury**</span><span class="sxs-lookup"><span data-stu-id="217ae-306">**Classes vs. structures**</span></span>  
  
 <span data-ttu-id="217ae-307">Způsobem třídy a struktury poskytují kompromis classic místa a času k ladění aplikací.</span><span class="sxs-lookup"><span data-stu-id="217ae-307">In a way, classes and structures provide a classic space/time tradeoff for tuning your apps.</span></span>  <span data-ttu-id="217ae-308">Třídy zpoplatněná 12 bajtů režijní náklady na x86 počítač i v případě, že mají žádná pole, ale jsou nenákladné předat kolem, protože trvá ukazatel odkazovat na instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="217ae-308">Classes incur 12 bytes of overhead on an x86 machine even if they have no fields, but they are inexpensive to pass around because it only takes a pointer to refer to a class instance.</span></span>  <span data-ttu-id="217ae-309">Struktury žádné přidělení haldy dojít, pokud nejsou v do pole, ale když předat velké struktury jako argumenty funkce nebo návratové hodnoty, dojde čas procesoru atomicky zkopírujte všechny členy datové struktury.</span><span class="sxs-lookup"><span data-stu-id="217ae-309">Structures incur no heap allocations if they aren’t boxed, but when you pass large structures as function arguments or return values, it takes CPU time to atomically copy all the data members of the structures.</span></span>  <span data-ttu-id="217ae-310">Sledujte opakovaná volání vlastnosti, které vrátí struktury a mezipaměti vlastnosti na hodnotu v místní proměnné, aby se zabránilo nadměrnému data kopírování.</span><span class="sxs-lookup"><span data-stu-id="217ae-310">Watch out for repeated calls to properties that return structures, and cache the property’s value in a local variable to avoid excessive data copying.</span></span>  
  
 <span data-ttu-id="217ae-311">**Mezipaměti**</span><span class="sxs-lookup"><span data-stu-id="217ae-311">**Caches**</span></span>  
  
 <span data-ttu-id="217ae-312">Běžné efektu výkonu je výsledky do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="217ae-312">A common performance trick is to cache results.</span></span>  <span data-ttu-id="217ae-313">Mezipaměť bez velikost zakončení nebo vyřazení zásad však může být nevrácenou pamětí.</span><span class="sxs-lookup"><span data-stu-id="217ae-313">However, a cache without a size cap or disposal policy can be a memory leak.</span></span>  <span data-ttu-id="217ae-314">Při zpracování velkých objemů dat, pokud přidržením velké množství paměti v mezipaměti, může způsobit uvolňování paměti pro přepsání výhod vaše vyhledávání z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="217ae-314">When processing large amounts of data, if you hold on to a lot of memory in caches, you can cause garbage collection to override the benefits of your cached lookups.</span></span>  
  
 <span data-ttu-id="217ae-315">V tomto článku jsme probrali, jak byste měli vědět příznaky výkonu problémové místo, které může mít vliv na rychlost reakce vaší aplikace, hlavně pro velké systémům nebo systémům, které zpracovávají velké množství dat.</span><span class="sxs-lookup"><span data-stu-id="217ae-315">In this article, we discussed how you should be aware of performance bottleneck symptoms that can affect your app's responsiveness, especially for large systems or systems that process a large amount of data.</span></span> <span data-ttu-id="217ae-316">Běžné culprits zahrnují zabalení, manipulace s řetězci, LINQ a lambda, ukládání do mezipaměti asynchronní metody ukládání do mezipaměti bez velikost limit nebo vyřazení zásady, nevhodných použití slovník a předávání kolem struktury.</span><span class="sxs-lookup"><span data-stu-id="217ae-316">Common culprits include boxing, string manipulations, LINQ and lambda, caching in async methods, caching without a size limit or disposal policy, inappropriate use of dictionaries, and passing around structures.</span></span>  <span data-ttu-id="217ae-317">Mějte na paměti čtyři fakty k ladění aplikací:</span><span class="sxs-lookup"><span data-stu-id="217ae-317">Keep in mind the four facts for tuning your apps:</span></span>  
  
-   <span data-ttu-id="217ae-318">Nemáte předčasně optimalizovat – produktivitu a ladit aplikace při rozpoznání problémy.</span><span class="sxs-lookup"><span data-stu-id="217ae-318">Don’t prematurely optimize – be productive and tune your app when you spot problems.</span></span>  
  
-   <span data-ttu-id="217ae-319">Profily nejsou ležet – jste uhodnutí, pokud nejsou měření.</span><span class="sxs-lookup"><span data-stu-id="217ae-319">Profiles don’t lie – you’re guessing if you’re not measuring.</span></span>  
  
-   <span data-ttu-id="217ae-320">Dobrý nástroje proveďte všechny rozdíl – stažení nástroje PerfView a vyzkoušejte ji.</span><span class="sxs-lookup"><span data-stu-id="217ae-320">Good tools make all the difference – download PerfView and try it out.</span></span>  
  
-   <span data-ttu-id="217ae-321">O přidělení – to znamená kde týmem platformy kompilátoru stráví většinu doba pro jejich zvýšení výkonu nové kompilátory je všechny.</span><span class="sxs-lookup"><span data-stu-id="217ae-321">It's all about allocations – that is where the compiler platform team spent most of their time improving the performance of the new compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="217ae-322">Viz také</span><span class="sxs-lookup"><span data-stu-id="217ae-322">See Also</span></span>  
 [<span data-ttu-id="217ae-323">Video prezentace v tomto tématu</span><span class="sxs-lookup"><span data-stu-id="217ae-323">Video of presentation of this topic</span></span>](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)  
 [<span data-ttu-id="217ae-324">Průvodce začátečníka profilací výkonu</span><span class="sxs-lookup"><span data-stu-id="217ae-324">Beginners Guide to Performance Profiling</span></span>](/visualstudio/profiling/beginners-guide-to-performance-profiling)  
 [<span data-ttu-id="217ae-325">Výkon</span><span class="sxs-lookup"><span data-stu-id="217ae-325">Performance</span></span>](../../../docs/framework/performance/index.md)  
 [<span data-ttu-id="217ae-326">Tipy pro zvýšení výkonu rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="217ae-326">.NET Performance Tips</span></span>](http://msdn.microsoft.com/library/ms973839.aspx)  
 [<span data-ttu-id="217ae-327">Nástroj pro analýzu výkonu Windows Phone</span><span class="sxs-lookup"><span data-stu-id="217ae-327">Windows Phone Performance Analysis Tool</span></span>](http://msdn.microsoft.com/magazine/hh781024.aspx)  
 [<span data-ttu-id="217ae-328">Najít kritická místa aplikace pomocí sady Visual Studio Profiler</span><span class="sxs-lookup"><span data-stu-id="217ae-328">Find Application Bottlenecks with Visual Studio Profiler</span></span>](http://msdn.microsoft.com/magazine/cc337887.aspx)  
 [<span data-ttu-id="217ae-329">Channel 9 kurzy nástroje PerfView</span><span class="sxs-lookup"><span data-stu-id="217ae-329">Channel 9 PerfView tutorials</span></span>](http://channel9.msdn.com/Series/PerfView-Tutorial)  
 [<span data-ttu-id="217ae-330">Tipy pro zvýšení výkonu vysoké úrovně</span><span class="sxs-lookup"><span data-stu-id="217ae-330">High-level Performance Tips</span></span>](http://curah.microsoft.com/4604/improving-your-net-apps-startup-performance)  
 [<span data-ttu-id="217ae-331">DotNet/roslyn úložišti na Githubu</span><span class="sxs-lookup"><span data-stu-id="217ae-331">dotnet/roslyn repo on GitHub</span></span>](https://github.com/dotnet/roslyn)
