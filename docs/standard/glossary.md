---
title: Slovníček k technologii .NET
description: Zjistěte význam vybraných termínů používaných v dokumentaci .NET.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 9bca68753a93721e48d1ff90aa7baf3a147da0ee
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708201"
---
# <a name="net-glossary"></a><span data-ttu-id="c92e7-103">Slovníček k technologii .NET</span><span class="sxs-lookup"><span data-stu-id="c92e7-103">.NET Glossary</span></span>

<span data-ttu-id="c92e7-104">Hlavním cílem tohoto glosáře je objasnit význam vybraných termínů a zkratek, které se v dokumentaci .NET často objevují bez definic.</span><span class="sxs-lookup"><span data-stu-id="c92e7-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="c92e7-105">AOT</span><span class="sxs-lookup"><span data-stu-id="c92e7-105">AOT</span></span>

<span data-ttu-id="c92e7-106">Předem-včas kompilátor.</span><span class="sxs-lookup"><span data-stu-id="c92e7-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="c92e7-107">Podobně jako [JIT](#jit), tento kompilátor také překládá [Il](#il) do strojového kódu.</span><span class="sxs-lookup"><span data-stu-id="c92e7-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="c92e7-108">Na rozdíl od kompilace JIT proběhne kompilace AOT před provedením aplikace a obvykle se provádí v jiném počítači.</span><span class="sxs-lookup"><span data-stu-id="c92e7-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="c92e7-109">Vzhledem k tomu, že řetězy nástrojů AOT nejsou kompilovány za běhu, nemusí minimalizovat čas strávený kompilací.</span><span class="sxs-lookup"><span data-stu-id="c92e7-109">Because AOT tool chains don't compile at runtime, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="c92e7-110">To znamená, že můžou věnovat více času optimalizaci.</span><span class="sxs-lookup"><span data-stu-id="c92e7-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="c92e7-111">Vzhledem k tomu, že kontext AOT je celá aplikace, provede kompilátor AOT také propojení mezi moduly a analýzou celého programu, což znamená, že jsou následovány všechny odkazy a je vytvořen jediný spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="c92e7-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

<span data-ttu-id="c92e7-112">Viz [CoreRT](#corert) a [.NET Native](#net-native).</span><span class="sxs-lookup"><span data-stu-id="c92e7-112">See [CoreRT](#corert) and [.NET Native](#net-native).</span></span>

## <a name="aspnet"></a><span data-ttu-id="c92e7-113">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c92e7-113">ASP.NET</span></span> 

<span data-ttu-id="c92e7-114">Původní implementace ASP.NET, která je dodávána s .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c92e7-114">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="c92e7-115">Někdy ASP.NET je zastřešující termín, který odkazuje na implementace ASP.NET, včetně ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c92e7-115">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="c92e7-116">To znamená, že podmínka přenáší v rámci určité instance je určena podle kontextu.</span><span class="sxs-lookup"><span data-stu-id="c92e7-116">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="c92e7-117">Pokud chcete, aby bylo jasné, že nepoužíváte ASP.NET, použijte k tomu ASP.NET 4. x, které by znamenaly obě implementace.</span><span class="sxs-lookup"><span data-stu-id="c92e7-117">Refer to ASP.NET 4.x when you want to make it clear that you’re not using ASP.NET to mean both implementations.</span></span> 

<span data-ttu-id="c92e7-118">Další informace najdete v [dokumentaci k ASP.NET](/aspnet/#pivot=aspnet).</span><span class="sxs-lookup"><span data-stu-id="c92e7-118">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="c92e7-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c92e7-119">ASP.NET Core</span></span>

<span data-ttu-id="c92e7-120">Vysoce výkonná implementace Open Source ASP.NET založená na .NET Core pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="c92e7-120">A cross-platform, high-performance, open source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="c92e7-121">Viz [dokumentace ASP.NET Core](/aspnet/#pivot=core).</span><span class="sxs-lookup"><span data-stu-id="c92e7-121">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="c92e7-122">sestavení</span><span class="sxs-lookup"><span data-stu-id="c92e7-122">assembly</span></span>

<span data-ttu-id="c92e7-123">Soubor *. dll*/ *. exe* , který může obsahovat kolekci rozhraní API, která mohou být volána aplikacemi nebo jinými sestaveními.</span><span class="sxs-lookup"><span data-stu-id="c92e7-123">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by applications or other assemblies.</span></span>

<span data-ttu-id="c92e7-124">Sestavení může obsahovat typy, jako jsou rozhraní, třídy, struktury, výčty a Delegáti.</span><span class="sxs-lookup"><span data-stu-id="c92e7-124">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="c92e7-125">Sestavení ve složce *bin* projektu jsou někdy označována jako *binární soubory*.</span><span class="sxs-lookup"><span data-stu-id="c92e7-125">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="c92e7-126">Viz také [Knihovna](#library).</span><span class="sxs-lookup"><span data-stu-id="c92e7-126">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="c92e7-127">CLR</span><span class="sxs-lookup"><span data-stu-id="c92e7-127">CLR</span></span>

<span data-ttu-id="c92e7-128">Modul CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="c92e7-128">Common Language Runtime.</span></span>

<span data-ttu-id="c92e7-129">Přesný význam závisí na kontextu, ale obvykle se odkazuje na modul runtime .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c92e7-129">The exact meaning depends on the context, but this usually refers to the runtime of the .NET Framework.</span></span> <span data-ttu-id="c92e7-130">Modul CLR zpracovává přidělování a správu paměti.</span><span class="sxs-lookup"><span data-stu-id="c92e7-130">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="c92e7-131">CLR je také virtuálním počítačem, který nespouští pouze aplikace, ale také generuje a kompiluje kód průběžně pomocí kompilátoru [JIT](#jit) .</span><span class="sxs-lookup"><span data-stu-id="c92e7-131">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a [JIT](#jit) compiler.</span></span> <span data-ttu-id="c92e7-132">Aktuální implementace Microsoft CLR je jenom Windows.</span><span class="sxs-lookup"><span data-stu-id="c92e7-132">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="c92e7-133">CoreCLR</span><span class="sxs-lookup"><span data-stu-id="c92e7-133">CoreCLR</span></span>

<span data-ttu-id="c92e7-134">Modul CLR (Common Language Runtime) .NET Core</span><span class="sxs-lookup"><span data-stu-id="c92e7-134">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="c92e7-135">Tento CLR je sestaven ze stejné základní znakové sady jako CLR.</span><span class="sxs-lookup"><span data-stu-id="c92e7-135">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="c92e7-136">Původně CoreCLR byl modul runtime Silverlight a byl navržený tak, aby běžel na více platformách, konkrétně Windows a OS X. CoreCLR je teď součástí .NET Core a představuje zjednodušenou verzi CLR.</span><span class="sxs-lookup"><span data-stu-id="c92e7-136">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="c92e7-137">Je to pořád modul runtime pro [více platforem](#cross-platform) , který teď zahrnuje podporu pro spoustu distribucí Linux.</span><span class="sxs-lookup"><span data-stu-id="c92e7-137">It's still a [cross-platform](#cross-platform) runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="c92e7-138">CoreCLR je také virtuální počítač s možnostmi JIT a spouštění kódu.</span><span class="sxs-lookup"><span data-stu-id="c92e7-138">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="c92e7-139">CoreFX</span><span class="sxs-lookup"><span data-stu-id="c92e7-139">CoreFX</span></span>

<span data-ttu-id="c92e7-140">Základní knihovna tříd .NET Core (BCL)</span><span class="sxs-lookup"><span data-stu-id="c92e7-140">.NET Core Base Class Library (BCL)</span></span>

<span data-ttu-id="c92e7-141">Sada knihoven, které tvoří systém.\* (a do oboru názvů Microsoft.\*) s omezeným rozsahem.</span><span class="sxs-lookup"><span data-stu-id="c92e7-141">A set of libraries that comprise the System.\* (and to a limited extent Microsoft.\*) namespaces.</span></span> <span data-ttu-id="c92e7-142">BCL je pro obecné účely rozhraní nižší úrovně, které používá aplikační architektury vyšší úrovně, například ASP.NET Core, sestavení.</span><span class="sxs-lookup"><span data-stu-id="c92e7-142">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="c92e7-143">Zdrojový kód .NET Core BCL je obsažen v [úložišti modulu runtime .NET Core](https://github.com/dotnet/runtime).</span><span class="sxs-lookup"><span data-stu-id="c92e7-143">The source code of the .NET Core BCL is contained in the [.NET Core runtime repository](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="c92e7-144">Většina rozhraní API .NET Core je však také k dispozici v .NET Framework, takže si CoreFX můžete představit jako rozvětvení .NET Framework BCL.</span><span class="sxs-lookup"><span data-stu-id="c92e7-144">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="c92e7-145">CoreRT</span><span class="sxs-lookup"><span data-stu-id="c92e7-145">CoreRT</span></span>

<span data-ttu-id="c92e7-146">Modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c92e7-146">.NET Core runtime.</span></span>

<span data-ttu-id="c92e7-147">Na rozdíl od CLR/CoreCLR není CoreRT virtuálním počítačem, což znamená, že nezahrnuje zařízení pro generování a spouštění kódu průběžně, protože nezahrnuje [JIT](#jit).</span><span class="sxs-lookup"><span data-stu-id="c92e7-147">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="c92e7-148">Nicméně obsahuje [GC](#gc) a možnost identifikace typu modulu runtime (RTTI) a reflexe.</span><span class="sxs-lookup"><span data-stu-id="c92e7-148">It does, however, include the [GC](#gc) and the ability for runtime type identification (RTTI) and reflection.</span></span> <span data-ttu-id="c92e7-149">Nicméně systém jeho typů je navržen tak, aby se metadata pro reflexi nevyžadovala.</span><span class="sxs-lookup"><span data-stu-id="c92e7-149">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="c92e7-150">To umožňuje, aby byl řetěz nástrojů [AOT](#aot) , který může propojit nadbytečné metadata a (důležitější je důležitější) identifikovat kód, který aplikace nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="c92e7-150">This enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="c92e7-151">CoreRT je ve vývoji.</span><span class="sxs-lookup"><span data-stu-id="c92e7-151">CoreRT is in development.</span></span>

<span data-ttu-id="c92e7-152">Přečtěte si [Úvod do .NET Native a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span><span class="sxs-lookup"><span data-stu-id="c92e7-152">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span></span>

## <a name="cross-platform"></a><span data-ttu-id="c92e7-153">pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="c92e7-153">cross-platform</span></span>

<span data-ttu-id="c92e7-154">Možnost vyvíjet a spouštět aplikaci, která se dá použít na více různých operačních systémech, jako jsou Linux, Windows a iOS, aniž by bylo nutné je znovu zapisovat.</span><span class="sxs-lookup"><span data-stu-id="c92e7-154">The ability to develop and execute an application that can be used on multiple different operating systems, such as Linux, Windows and iOS, without having to re-write specifically for each one.</span></span> <span data-ttu-id="c92e7-155">To umožňuje opětovné použití kódu a konzistenci mezi aplikacemi na různých platformách.</span><span class="sxs-lookup"><span data-stu-id="c92e7-155">This enables code re-use and consistency between applications on different platforms.</span></span>

## <a name="ecosystem"></a><span data-ttu-id="c92e7-156">ekosystému</span><span class="sxs-lookup"><span data-stu-id="c92e7-156">ecosystem</span></span>

<span data-ttu-id="c92e7-157">Veškerý běhový software, vývojové nástroje a komunitní prostředky, které se používají k sestavování a spouštění aplikací pro danou technologii.</span><span class="sxs-lookup"><span data-stu-id="c92e7-157">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="c92e7-158">Pojem "ekosystém .NET" se od podobných termínů, jako je například .NET Stack, liší v zahrnutí aplikací a knihoven třetích stran.</span><span class="sxs-lookup"><span data-stu-id="c92e7-158">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="c92e7-159">Tady je příklad ve větě:</span><span class="sxs-lookup"><span data-stu-id="c92e7-159">Here's an example in a sentence:</span></span>

- <span data-ttu-id="c92e7-160">"Motivací za [.NET Standard](#net-standard) je vytvoření větší jednotnosti v ekosystému .NET."</span><span class="sxs-lookup"><span data-stu-id="c92e7-160">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span> 

## <a name="framework"></a><span data-ttu-id="c92e7-161">rozhraní</span><span class="sxs-lookup"><span data-stu-id="c92e7-161">framework</span></span>

<span data-ttu-id="c92e7-162">Obecně platí komplexní kolekce rozhraní API, která usnadňují vývoj a nasazování aplikací, které jsou založeny na konkrétní technologii.</span><span class="sxs-lookup"><span data-stu-id="c92e7-162">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="c92e7-163">V tomto obecném smyslu jsou příklady aplikačních rozhraní ASP.NET Core a model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c92e7-163">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="c92e7-164">Viz také [Knihovna](#library).</span><span class="sxs-lookup"><span data-stu-id="c92e7-164">See also [library](#library).</span></span>

<span data-ttu-id="c92e7-165">Slovo "Framework" má konkrétnější technický význam v následujících termínech:</span><span class="sxs-lookup"><span data-stu-id="c92e7-165">The word "framework" has a more specific technical meaning in the following terms:</span></span>

- [<span data-ttu-id="c92e7-166">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="c92e7-166">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="c92e7-167">Cílová architektura</span><span class="sxs-lookup"><span data-stu-id="c92e7-167">target framework</span></span>](#target-framework)
- [<span data-ttu-id="c92e7-168">TFM (moniker cílového rozhraní .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="c92e7-168">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="c92e7-169">V existující dokumentaci "Framework" někdy odkazuje na [implementaci rozhraní .NET](#implementation-of-net).</span><span class="sxs-lookup"><span data-stu-id="c92e7-169">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="c92e7-170">Například článek může volat rozhraní .NET Core do architektury.</span><span class="sxs-lookup"><span data-stu-id="c92e7-170">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="c92e7-171">V této dokumentaci plánujeme toto matoucí využívání eliminovat.</span><span class="sxs-lookup"><span data-stu-id="c92e7-171">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="c92e7-172">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="c92e7-172">GC</span></span>

<span data-ttu-id="c92e7-173">Systém uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c92e7-173">Garbage collector.</span></span>

<span data-ttu-id="c92e7-174">Systém uvolňování paměti je implementace automatické správy paměti.</span><span class="sxs-lookup"><span data-stu-id="c92e7-174">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="c92e7-175">GC uvolňuje paměť obsazená objekty, které se již nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="c92e7-175">The GC frees memory occupied by objects that are no longer in use.</span></span> 

<span data-ttu-id="c92e7-176">Viz [shromažďování paměti](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="c92e7-176">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="c92e7-177">IL</span><span class="sxs-lookup"><span data-stu-id="c92e7-177">IL</span></span>

<span data-ttu-id="c92e7-178">Převodní jazyk.</span><span class="sxs-lookup"><span data-stu-id="c92e7-178">Intermediate language.</span></span>

<span data-ttu-id="c92e7-179">Jazyky .NET vyšší úrovně, například C#, se zkompiluje až do nezávislá sady instrukcí hardware, která se označuje jako Intermediate Language (IL).</span><span class="sxs-lookup"><span data-stu-id="c92e7-179">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="c92e7-180">IL se někdy označuje jako MSIL (Microsoft IL) nebo CIL (Common IL).</span><span class="sxs-lookup"><span data-stu-id="c92e7-180">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="c92e7-181">JIT</span><span class="sxs-lookup"><span data-stu-id="c92e7-181">JIT</span></span>

<span data-ttu-id="c92e7-182">Kompilátor za běhu.</span><span class="sxs-lookup"><span data-stu-id="c92e7-182">Just-in-time compiler.</span></span>

<span data-ttu-id="c92e7-183">Podobně jako [AOT](#aot)tento kompilátor překládá [Il](#il) na strojový kód, který procesor rozumí.</span><span class="sxs-lookup"><span data-stu-id="c92e7-183">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="c92e7-184">Na rozdíl od AOT probíhá kompilace JIT na vyžádání a je provedena na stejném počítači, na kterém je nutné kód spustit.</span><span class="sxs-lookup"><span data-stu-id="c92e7-184">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="c92e7-185">Vzhledem k tomu, že během provádění aplikace dojde k kompilaci JIT, doba kompilace je součástí doby běhu.</span><span class="sxs-lookup"><span data-stu-id="c92e7-185">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="c92e7-186">Kompilátory JIT proto musí vyvážit čas strávený optimalizací kódu proti úsporám, které může výsledný kód vyvolat.</span><span class="sxs-lookup"><span data-stu-id="c92e7-186">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="c92e7-187">Kompilátor JIT ale zná skutečný hardware a může vývojářům zdarma dodávat různé implementace.</span><span class="sxs-lookup"><span data-stu-id="c92e7-187">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="c92e7-188">implementace rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="c92e7-188">implementation of .NET</span></span>

<span data-ttu-id="c92e7-189">Implementace rozhraní .NET zahrnuje následující:</span><span class="sxs-lookup"><span data-stu-id="c92e7-189">An implementation of .NET includes the following:</span></span>

- <span data-ttu-id="c92e7-190">Jeden nebo více modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="c92e7-190">One or more runtimes.</span></span> <span data-ttu-id="c92e7-191">Příklady: CLR, CoreCLR, CoreRT.</span><span class="sxs-lookup"><span data-stu-id="c92e7-191">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="c92e7-192">Knihovna tříd, která implementuje verzi .NET Standard a může obsahovat další rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c92e7-192">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="c92e7-193">Příklady: .NET Framework základní knihovny tříd, knihovna základních tříd .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c92e7-193">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="c92e7-194">Volitelně jeden nebo více aplikačních architektur.</span><span class="sxs-lookup"><span data-stu-id="c92e7-194">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="c92e7-195">Příklady: ASP.NET, model Windows Forms a WPF jsou obsaženy v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c92e7-195">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="c92e7-196">Volitelně vývojové nástroje.</span><span class="sxs-lookup"><span data-stu-id="c92e7-196">Optionally, development tools.</span></span> <span data-ttu-id="c92e7-197">Některé vývojové nástroje se sdílejí mezi více implementacemi.</span><span class="sxs-lookup"><span data-stu-id="c92e7-197">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="c92e7-198">Příklady implementací rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="c92e7-198">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="c92e7-199">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="c92e7-199">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="c92e7-200">.NET Core</span><span class="sxs-lookup"><span data-stu-id="c92e7-200">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="c92e7-201">Univerzální platforma Windows (UPW)</span><span class="sxs-lookup"><span data-stu-id="c92e7-201">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="c92e7-202">knihovna</span><span class="sxs-lookup"><span data-stu-id="c92e7-202">library</span></span>

<span data-ttu-id="c92e7-203">Kolekce rozhraní API, která mohou být volána aplikacemi nebo jinými knihovnami.</span><span class="sxs-lookup"><span data-stu-id="c92e7-203">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="c92e7-204">Knihovna .NET se skládá z jednoho nebo více [sestavení](#assembly).</span><span class="sxs-lookup"><span data-stu-id="c92e7-204">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="c92e7-205">Slova Library a [Framework](#framework) se často používají jako synonyma.</span><span class="sxs-lookup"><span data-stu-id="c92e7-205">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="c92e7-206">metapackage</span><span class="sxs-lookup"><span data-stu-id="c92e7-206">metapackage</span></span>

<span data-ttu-id="c92e7-207">Balíček NuGet, který nemá žádnou vlastní knihovnu, ale je jenom seznam závislostí.</span><span class="sxs-lookup"><span data-stu-id="c92e7-207">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="c92e7-208">Zahrnuté balíčky mohou volitelně vytvořit rozhraní API pro cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="c92e7-208">The included packages can optionally establish the API for a target framework.</span></span>

<span data-ttu-id="c92e7-209">Viz [balíčky, metabalíčky a architektury](../core/packages.md) .</span><span class="sxs-lookup"><span data-stu-id="c92e7-209">See [Packages, Metapackages and Frameworks](../core/packages.md)</span></span>

## <a name="mono"></a><span data-ttu-id="c92e7-210">Mono</span><span class="sxs-lookup"><span data-stu-id="c92e7-210">Mono</span></span>

<span data-ttu-id="c92e7-211">Mono je open source implementace .NET pro [různé platformy](#cross-platform) , která se používá hlavně v případě, že je potřeba malý modul runtime.</span><span class="sxs-lookup"><span data-stu-id="c92e7-211">Mono is an open source, [cross-platform](#cross-platform) .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="c92e7-212">Je to modul runtime, který pracuje s aplikacemi Xamarin na Androidu, Macu, iOS, tvOS a watchOS a zaměřuje se hlavně na aplikace, které vyžadují malé nároky.</span><span class="sxs-lookup"><span data-stu-id="c92e7-212">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="c92e7-213">Podporuje všechny aktuálně publikované verze .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c92e7-213">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="c92e7-214">V minulosti implementovala mono větší rozhraní API .NET Framework a emuluje některé z nejoblíbenějších funkcí v systému UNIX.</span><span class="sxs-lookup"><span data-stu-id="c92e7-214">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="c92e7-215">Někdy se používá ke spouštění aplikací .NET, které spoléhají na tyto možnosti v systému UNIX.</span><span class="sxs-lookup"><span data-stu-id="c92e7-215">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="c92e7-216">Mono se obvykle používá s kompilátorem za běhu, ale také obsahuje úplný statický kompilátor (předem zkompilování), který se používá na platformách, jako je iOS.</span><span class="sxs-lookup"><span data-stu-id="c92e7-216">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="c92e7-217">Další informace o mono najdete v [dokumentaci k mono](https://www.mono-project.com/docs/).</span><span class="sxs-lookup"><span data-stu-id="c92e7-217">To learn more about Mono, see the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="c92e7-218">.NET</span><span class="sxs-lookup"><span data-stu-id="c92e7-218">.NET</span></span>

<span data-ttu-id="c92e7-219">Termín pro [.NET Standard](#net-standard) a všechny implementace a úlohy [.NET](#implementation-of-net) .</span><span class="sxs-lookup"><span data-stu-id="c92e7-219">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="c92e7-220">Vždy velkými písmeny, nikdy ".NET".</span><span class="sxs-lookup"><span data-stu-id="c92e7-220">Always capitalized, never ".Net".</span></span>

<span data-ttu-id="c92e7-221">Projděte si [příručku .NET](index.md)</span><span class="sxs-lookup"><span data-stu-id="c92e7-221">See the [.NET Guide](index.md)</span></span>

## <a name="net-core"></a><span data-ttu-id="c92e7-222">.NET Core</span><span class="sxs-lookup"><span data-stu-id="c92e7-222">.NET Core</span></span> 

<span data-ttu-id="c92e7-223">Vysoce výkonná a open source implementace .NET pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="c92e7-223">A cross-platform, high-performance, open source implementation of .NET.</span></span> <span data-ttu-id="c92e7-224">Zahrnuje základní modul CLR (Common Language Runtime) (CoreCLR), základní modul runtime AOT (CoreRT, ve vývoji), základní knihovnu základních tříd a základní sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="c92e7-224">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="c92e7-225">Viz [.NET Core](../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="c92e7-225">See [.NET Core](../core/index.md).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="c92e7-226">Rozhraní příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="c92e7-226">.NET Core CLI</span></span>

<span data-ttu-id="c92e7-227">Sada nástrojů pro více platforem pro vývoj aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c92e7-227">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="c92e7-228">Viz [nástroje rozhraní příkazového řádku (CLI) .NET Core](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="c92e7-228">See [.NET Core command-line interface (CLI) tools](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="c92e7-229">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c92e7-229">.NET Core SDK</span></span>

<span data-ttu-id="c92e7-230">Sada knihoven a nástrojů, které vývojářům umožňují vytvářet aplikace a knihovny .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c92e7-230">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="c92e7-231">Zahrnuje [.NET Core CLI](#net-core-cli) pro sestavování aplikací, knihoven .NET Core a modulu runtime pro vytváření a spouštění aplikací a spustitelný soubor dotnet (*dotnet. exe*), který spouští příkazy rozhraní příkazového řádku a spouští aplikace.</span><span class="sxs-lookup"><span data-stu-id="c92e7-231">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="c92e7-232">Další informace najdete v tématu [přehled .NET Core SDK](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="c92e7-232">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="c92e7-233">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="c92e7-233">.NET Framework</span></span>

<span data-ttu-id="c92e7-234">Implementace rozhraní .NET, která běží pouze v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c92e7-234">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="c92e7-235">Zahrnuje modul CLR (Common Language Runtime), knihovnu základních tříd a knihovny aplikačních architektur, jako jsou ASP.NET, model Windows Forms a WPF.</span><span class="sxs-lookup"><span data-stu-id="c92e7-235">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="c92e7-236">Viz [průvodce .NET Framework](../framework/index.md).</span><span class="sxs-lookup"><span data-stu-id="c92e7-236">See [.NET Framework Guide](../framework/index.md).</span></span>

## <a name="net-native"></a><span data-ttu-id="c92e7-237">.NET Native</span><span class="sxs-lookup"><span data-stu-id="c92e7-237">.NET Native</span></span>

<span data-ttu-id="c92e7-238">Řetěz nástrojů kompilátoru, který vytváří nativní kód před časem (AOT), na rozdíl od JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="c92e7-238">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="c92e7-239">Kompilace probíhá na počítači vývojáře, podobně jako C++ kompilátor a linker funguje.</span><span class="sxs-lookup"><span data-stu-id="c92e7-239">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="c92e7-240">Odebírá nepoužitý kód a stráví více času optimalizací.</span><span class="sxs-lookup"><span data-stu-id="c92e7-240">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="c92e7-241">Extrahuje kód z knihoven a sloučí je do spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="c92e7-241">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="c92e7-242">Výsledkem je jeden modul, který představuje celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c92e7-242">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="c92e7-243">UWP byla první aplikační architektura, kterou .NET Native podporuje.</span><span class="sxs-lookup"><span data-stu-id="c92e7-243">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="c92e7-244">Nyní podporujeme vytváření nativních konzolových aplikací pro Windows, macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="c92e7-244">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="c92e7-245">Viz [Úvod do .NET Native a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="c92e7-245">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="c92e7-246">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="c92e7-246">.NET Standard</span></span>

<span data-ttu-id="c92e7-247">Formální specifikace rozhraní .NET API, které jsou k dispozici v každé implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="c92e7-247">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="c92e7-248">Specifikace .NET Standard se v dokumentaci někdy označuje jako knihovna.</span><span class="sxs-lookup"><span data-stu-id="c92e7-248">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="c92e7-249">Vzhledem k tomu, že knihovna obsahuje implementace rozhraní API, nikoli pouze specifikace (rozhraní), je pro volání .NET Standard "Library" zavádějící.</span><span class="sxs-lookup"><span data-stu-id="c92e7-249">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="c92e7-250">V této dokumentaci plánujeme toto použití eliminovat, s výjimkou odkazu na název .NET Standard Metapackage (`NETStandard.Library`).</span><span class="sxs-lookup"><span data-stu-id="c92e7-250">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="c92e7-251">Viz [.NET Standard](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="c92e7-251">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="c92e7-252">NGEN</span><span class="sxs-lookup"><span data-stu-id="c92e7-252">NGEN</span></span>

<span data-ttu-id="c92e7-253">Generování nativních (imagí)</span><span class="sxs-lookup"><span data-stu-id="c92e7-253">Native (image) generation.</span></span>

<span data-ttu-id="c92e7-254">Tuto technologii si můžete představit jako trvalý kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="c92e7-254">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="c92e7-255">Obvykle kompiluje kód na počítači, kde je spuštěn kód, ale kompilace obvykle probíhá v době instalace.</span><span class="sxs-lookup"><span data-stu-id="c92e7-255">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="c92e7-256">balíček</span><span class="sxs-lookup"><span data-stu-id="c92e7-256">package</span></span>

<span data-ttu-id="c92e7-257">Balíček NuGet &mdash; nebo pouze balíček &mdash; je soubor *. zip* s jedním nebo více sestaveními se stejným názvem společně s dalšími metadaty, jako je jméno autora.</span><span class="sxs-lookup"><span data-stu-id="c92e7-257">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="c92e7-258">Soubor *. zip* má příponu *. nupkg* a může obsahovat prostředky, jako jsou soubory *DLL* a *XML* soubory pro použití s více cílovými rozhraními a verzemi.</span><span class="sxs-lookup"><span data-stu-id="c92e7-258">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="c92e7-259">Při instalaci v aplikaci nebo knihovně jsou příslušné prostředky vybrány na základě cílového rozhraní určeného aplikací nebo knihovnou.</span><span class="sxs-lookup"><span data-stu-id="c92e7-259">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="c92e7-260">Prostředky, které definují rozhraní, jsou ve složce *ref* a assety definující implementaci jsou ve složce *lib* .</span><span class="sxs-lookup"><span data-stu-id="c92e7-260">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="c92e7-261">platforma</span><span class="sxs-lookup"><span data-stu-id="c92e7-261">platform</span></span>

<span data-ttu-id="c92e7-262">Operační systém a hardware, na kterém běží, jako je Windows, macOS, Linux, iOS a Android.</span><span class="sxs-lookup"><span data-stu-id="c92e7-262">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="c92e7-263">Tady jsou příklady použití ve větách:</span><span class="sxs-lookup"><span data-stu-id="c92e7-263">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="c92e7-264">".NET Core je implementace .NET pro různé platformy."</span><span class="sxs-lookup"><span data-stu-id="c92e7-264">".NET Core is a cross-platform implementation of .NET."</span></span> 
- <span data-ttu-id="c92e7-265">"Profily PCL reprezentují platformy Microsoft, zatímco .NET Standard nezávislá na platformu."</span><span class="sxs-lookup"><span data-stu-id="c92e7-265">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="c92e7-266">Dokumentace rozhraní .NET často používá "platformu .NET", která znamená implementaci .NET nebo .NET Stack včetně všech implementací.</span><span class="sxs-lookup"><span data-stu-id="c92e7-266">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="c92e7-267">Obě tato použití se z tohoto hlediska snaží obměňujte s primárním (operačním nebo hardwarovým) významem, takže plánujeme tato použití z dokumentace eliminovat.</span><span class="sxs-lookup"><span data-stu-id="c92e7-267">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="c92e7-268">modul runtime</span><span class="sxs-lookup"><span data-stu-id="c92e7-268">runtime</span></span>

<span data-ttu-id="c92e7-269">Spouštěcí prostředí pro spravovaný program.</span><span class="sxs-lookup"><span data-stu-id="c92e7-269">The execution environment for a managed program.</span></span>

<span data-ttu-id="c92e7-270">Operační systém je součástí běhového prostředí, ale není součástí modulu .NET Runtime.</span><span class="sxs-lookup"><span data-stu-id="c92e7-270">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="c92e7-271">Tady je několik příkladů prostředí .NET Runtime:</span><span class="sxs-lookup"><span data-stu-id="c92e7-271">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="c92e7-272">Common Language Runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="c92e7-272">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="c92e7-273">Core Common Language Runtime (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="c92e7-273">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="c92e7-274">.NET Native (pro UWP)</span><span class="sxs-lookup"><span data-stu-id="c92e7-274">.NET Native (for UWP)</span></span>
- <span data-ttu-id="c92e7-275">Mono runtime</span><span class="sxs-lookup"><span data-stu-id="c92e7-275">Mono runtime</span></span>

<span data-ttu-id="c92e7-276">Dokumentace rozhraní .NET někdy používá "runtime", což znamená implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="c92e7-276">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="c92e7-277">Například v následujících větách "runtime" by se měla nahradit výrazem "implementace":</span><span class="sxs-lookup"><span data-stu-id="c92e7-277">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="c92e7-278">"Různé moduly runtime .NET implementují konkrétní verze .NET Standard."</span><span class="sxs-lookup"><span data-stu-id="c92e7-278">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="c92e7-279">"Knihovny určené ke spuštění na více modulech runtime by měly cílit na toto rozhraní."</span><span class="sxs-lookup"><span data-stu-id="c92e7-279">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="c92e7-280">(odkazování na .NET Standard)</span><span class="sxs-lookup"><span data-stu-id="c92e7-280">(referring to .NET Standard)</span></span>
- <span data-ttu-id="c92e7-281">"Různé moduly runtime .NET implementují konkrétní verze .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c92e7-281">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="c92e7-282">…</span><span class="sxs-lookup"><span data-stu-id="c92e7-282">…</span></span> <span data-ttu-id="c92e7-283">Každá verze modulu .NET runtime inzeruje nejvyšší .NET Standard verzi, kterou podporuje...</span><span class="sxs-lookup"><span data-stu-id="c92e7-283">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="c92e7-284">Plánujeme toto nekonzistentní použití eliminovat.</span><span class="sxs-lookup"><span data-stu-id="c92e7-284">We plan to eliminate this inconsistent usage.</span></span> 

## <a name="stack"></a><span data-ttu-id="c92e7-285">stack</span><span class="sxs-lookup"><span data-stu-id="c92e7-285">stack</span></span>

<span data-ttu-id="c92e7-286">Sada programovacích technologií používaných společně k sestavování a spouštění aplikací.</span><span class="sxs-lookup"><span data-stu-id="c92e7-286">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="c92e7-287">Rozhraní .NET Stack odkazuje na .NET Standard a všechny implementace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="c92e7-287">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="c92e7-288">Fráze ".NET Stack" může odkazovat na jednu implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="c92e7-288">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span> 

## <a name="target-framework"></a><span data-ttu-id="c92e7-289">Cílová architektura</span><span class="sxs-lookup"><span data-stu-id="c92e7-289">target framework</span></span>

<span data-ttu-id="c92e7-290">Kolekce rozhraní API, na kterých závisí aplikace .NET nebo knihovna</span><span class="sxs-lookup"><span data-stu-id="c92e7-290">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="c92e7-291">Aplikace nebo knihovna může cílit na verzi .NET Standard (například .NET Standard 2,0), což je specifikace pro standardizovanou sadu rozhraní API napříč všemi implementacemi .NET.</span><span class="sxs-lookup"><span data-stu-id="c92e7-291">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="c92e7-292">Aplikace nebo knihovna může také cílit na verzi konkrétní implementace rozhraní .NET. v takovém případě získá přístup k rozhraním API pro konkrétní implementaci.</span><span class="sxs-lookup"><span data-stu-id="c92e7-292">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="c92e7-293">Například aplikace, která se zaměřuje na Xamarin. iOS, získá přístup k obálkám rozhraní API iOS poskytovaných v Xamarin.</span><span class="sxs-lookup"><span data-stu-id="c92e7-293">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="c92e7-294">Pro některé cílové architektury (například .NET Framework) jsou dostupná rozhraní API definovaná sestaveními, která implementuje implementace rozhraní .NET v systému, což může zahrnovat rozhraní API pro rozhraní Application Framework (například ASP.NET, WinForms).</span><span class="sxs-lookup"><span data-stu-id="c92e7-294">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="c92e7-295">Pro cílové architektury založené na balíčku (například .NET Standard a .NET Core) jsou rozhraní API architektury definovaná balíčky nainstalovanými v aplikaci nebo knihovně.</span><span class="sxs-lookup"><span data-stu-id="c92e7-295">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="c92e7-296">V takovém případě cílové rozhraní implicitně určuje Metapackage, který odkazuje na všechny balíčky, které dohromady tvoří rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c92e7-296">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="c92e7-297">Viz [cílová rozhraní](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="c92e7-297">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="c92e7-298">TFM</span><span class="sxs-lookup"><span data-stu-id="c92e7-298">TFM</span></span>

<span data-ttu-id="c92e7-299">Moniker cílového rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c92e7-299">Target framework moniker.</span></span>

<span data-ttu-id="c92e7-300">Formát standardizovaného tokenu pro určení cílové architektury aplikace nebo knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="c92e7-300">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="c92e7-301">Cílová rozhraní jsou obvykle odkazována krátkým názvem, například `net462`.</span><span class="sxs-lookup"><span data-stu-id="c92e7-301">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="c92e7-302">Dlouhý tvar TFM (například. NETFramework, Version = 4.6.2) existuje, ale obecně se nepoužívá k určení cílové architektury.</span><span class="sxs-lookup"><span data-stu-id="c92e7-302">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="c92e7-303">Viz [cílová rozhraní](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="c92e7-303">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="c92e7-304">UWP</span><span class="sxs-lookup"><span data-stu-id="c92e7-304">UWP</span></span>

<span data-ttu-id="c92e7-305">Univerzální platforma Windows.</span><span class="sxs-lookup"><span data-stu-id="c92e7-305">Universal Windows Platform.</span></span>

<span data-ttu-id="c92e7-306">Implementace .NET, která se používá k vytváření moderních, dotykové aplikace a softwaru Windows pro Internet věcí (IoT).</span><span class="sxs-lookup"><span data-stu-id="c92e7-306">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="c92e7-307">Je navržený tak, aby sjednotí různé typy zařízení, na které můžete chtít cílit, včetně počítačů, tabletů, phablets, telefonů a i konzoly Xbox.</span><span class="sxs-lookup"><span data-stu-id="c92e7-307">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phablets, phones, and even the Xbox.</span></span> <span data-ttu-id="c92e7-308">UWP nabízí spoustu služeb, jako je centralizované úložiště aplikací, spouštěcí prostředí (kontejneru AppContainer) a sada rozhraní API systému Windows, které se mají použít místo Win32 (WinRT).</span><span class="sxs-lookup"><span data-stu-id="c92e7-308">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="c92e7-309">Aplikace se dají zapisovat do C++, C#Visual Basic a JavaScriptu.</span><span class="sxs-lookup"><span data-stu-id="c92e7-309">Apps can be written in C++, C#, Visual Basic, and JavaScript.</span></span> <span data-ttu-id="c92e7-310">Při použití C# a Visual Basic rozhraní API .NET poskytuje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c92e7-310">When using C# and Visual Basic, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="c92e7-311">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c92e7-311">See also</span></span>

- [<span data-ttu-id="c92e7-312">Průvodce technologií .NET</span><span class="sxs-lookup"><span data-stu-id="c92e7-312">.NET Guide</span></span>](index.md)
- [<span data-ttu-id="c92e7-313">Průvodce rozhraním .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c92e7-313">.NET Framework Guide</span></span>](../framework/index.md)
- [<span data-ttu-id="c92e7-314">.NET Core</span><span class="sxs-lookup"><span data-stu-id="c92e7-314">.NET Core</span></span>](../core/index.md)
- [<span data-ttu-id="c92e7-315">ASP.NET – přehled</span><span class="sxs-lookup"><span data-stu-id="c92e7-315">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)
- [<span data-ttu-id="c92e7-316">Přehled ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c92e7-316">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)
