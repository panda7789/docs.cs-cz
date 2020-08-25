---
title: Slovníček k technologii .NET
description: Zjistěte význam vybraných termínů používaných v dokumentaci .NET.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: c984a29208d8680de3c04f6b4d16c6f41afedc71
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812338"
---
# <a name="net-glossary"></a><span data-ttu-id="3e9cd-103">Slovníček k technologii .NET</span><span class="sxs-lookup"><span data-stu-id="3e9cd-103">.NET Glossary</span></span>

<span data-ttu-id="3e9cd-104">Hlavním cílem tohoto glosáře je objasnit význam vybraných termínů a zkratek, které se v dokumentaci .NET často objevují bez definic.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="3e9cd-105">AOT</span><span class="sxs-lookup"><span data-stu-id="3e9cd-105">AOT</span></span>

<span data-ttu-id="3e9cd-106">Předem-včas kompilátor.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="3e9cd-107">Podobně jako [JIT](#jit), tento kompilátor také překládá [Il](#il) do strojového kódu.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="3e9cd-108">Na rozdíl od kompilace JIT proběhne kompilace AOT před provedením aplikace a obvykle se provádí v jiném počítači.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="3e9cd-109">Vzhledem k tomu, že řetězy nástrojů AOT nejsou kompilovány za běhu, nemusí minimalizovat čas strávený kompilací.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-109">Because AOT tool chains don't compile at run time, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="3e9cd-110">To znamená, že můžou věnovat více času optimalizaci.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="3e9cd-111">Vzhledem k tomu, že kontext AOT je celá aplikace, provede kompilátor AOT také propojení mezi moduly a analýzou celého programu, což znamená, že jsou následovány všechny odkazy a je vytvořen jediný spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

<span data-ttu-id="3e9cd-112">Viz [CoreRT](#corert) a [.NET Native](#net-native).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-112">See [CoreRT](#corert) and [.NET Native](#net-native).</span></span>

## <a name="aspnet"></a><span data-ttu-id="3e9cd-113">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3e9cd-113">ASP.NET</span></span>

<span data-ttu-id="3e9cd-114">Původní implementace ASP.NET, která je dodávána s .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-114">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="3e9cd-115">Někdy ASP.NET je zastřešující termín, který odkazuje na implementace ASP.NET, včetně ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-115">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="3e9cd-116">To znamená, že podmínka přenáší v rámci určité instance je určena podle kontextu.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-116">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="3e9cd-117">Pokud chcete, aby bylo jasné, že nepoužíváte ASP.NET, použijte k tomu ASP.NET 4. x, které by znamenaly obě implementace.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-117">Refer to ASP.NET 4.x when you want to make it clear that you're not using ASP.NET to mean both implementations.</span></span>

<span data-ttu-id="3e9cd-118">Další informace najdete v [dokumentaci k ASP.NET](/aspnet/#pivot=aspnet).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-118">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="3e9cd-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3e9cd-119">ASP.NET Core</span></span>

<span data-ttu-id="3e9cd-120">Vysoce výkonná a open source implementace ASP.NET pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-120">A cross-platform, high-performance, open-source implementation of ASP.NET.</span></span>

<span data-ttu-id="3e9cd-121">Viz [dokumentace ASP.NET Core](/aspnet/#pivot=core).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-121">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="3e9cd-122">sestavení</span><span class="sxs-lookup"><span data-stu-id="3e9cd-122">assembly</span></span>

<span data-ttu-id="3e9cd-123">Soubor *. dll* / *. exe* , který může obsahovat kolekci rozhraní API, která mohou být volána aplikacemi nebo jinými sestaveními.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-123">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by applications or other assemblies.</span></span>

<span data-ttu-id="3e9cd-124">Sestavení může obsahovat typy, jako jsou rozhraní, třídy, struktury, výčty a Delegáti.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-124">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="3e9cd-125">Sestavení ve složce *bin* projektu jsou někdy označována jako *binární soubory*.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-125">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="3e9cd-126">Viz také [Knihovna](#library).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-126">See also [library](#library).</span></span>

## <a name="bcl"></a><span data-ttu-id="3e9cd-127">BCL</span><span class="sxs-lookup"><span data-stu-id="3e9cd-127">BCL</span></span>

<span data-ttu-id="3e9cd-128">Základní knihovna tříd.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-128">Base Class Library.</span></span> <span data-ttu-id="3e9cd-129">Označují se také jako *knihovny rozhraní*.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-129">Also known as *framework libraries*.</span></span>

<span data-ttu-id="3e9cd-130">Sada knihoven, které tvoří systém. \* (a do omezeného rozsahu Microsoft. \* ) obsažené.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-130">A set of libraries that comprise the System.\* (and to a limited extent Microsoft.\*) namespaces.</span></span> <span data-ttu-id="3e9cd-131">BCL je pro obecné účely rozhraní nižší úrovně, které používá aplikační architektury vyšší úrovně, například ASP.NET Core, sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-131">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span>

<span data-ttu-id="3e9cd-132">Zdrojový kód BCL pro [.NET 5 a novější verze (včetně .NET Core 2.1-3.1)](#net-5-and-later-versions) je obsažen v [úložišti modulu .NET runtime](https://github.com/dotnet/runtime).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-132">The source code of the BCL for [.NET 5 and later versions (including .NET Core 2.1-3.1)](#net-5-and-later-versions) is contained in the [.NET runtime repository](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="3e9cd-133">Většina rozhraní BCL API pro tuto novější implementaci rozhraní .NET je také k dispozici v .NET Framework, takže si tento zdrojový kód můžete představit jako rozvětvení zdrojového kódu .NET Framework BCL.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-133">The majority of the BCL APIs for this newer implementation of .NET are also available in .NET Framework, so you can think of this source code as a fork of the .NET Framework BCL source code.</span></span>

## <a name="clr"></a><span data-ttu-id="3e9cd-134">CLR</span><span class="sxs-lookup"><span data-stu-id="3e9cd-134">CLR</span></span>

<span data-ttu-id="3e9cd-135">Modul CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="3e9cd-135">Common Language Runtime.</span></span>

<span data-ttu-id="3e9cd-136">Přesný význam závisí na kontextu.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-136">The exact meaning depends on the context.</span></span> <span data-ttu-id="3e9cd-137">Modul CLR (Common Language Runtime) obvykle odkazuje na modul runtime [.NET Framework](#net-framework) nebo modul runtime [rozhraní .NET 5 a novějších verzí (včetně .NET Core 2.1-3.1)](#net-5-and-later-versions).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-137">Common Language Runtime usually refers to the runtime of [.NET Framework](#net-framework) or the runtime of [.NET 5 and later versions (including .NET Core 2.1-3.1)](#net-5-and-later-versions).</span></span>

<span data-ttu-id="3e9cd-138">Modul CLR zpracovává přidělování a správu paměti.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-138">A CLR handles memory allocation and management.</span></span> <span data-ttu-id="3e9cd-139">CLR je také virtuálním počítačem, který nespouští pouze aplikace, ale také generuje a kompiluje kód průběžně pomocí kompilátoru [JIT](#jit) .</span><span class="sxs-lookup"><span data-stu-id="3e9cd-139">A CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a [JIT](#jit) compiler.</span></span>

<span data-ttu-id="3e9cd-140">Implementace CLR pro .NET Framework je pouze Windows.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-140">The CLR implementation for .NET Framework is Windows only.</span></span>

<span data-ttu-id="3e9cd-141">Implementace CLR pro .NET 5 a novější verze (označovaná také jako základní CLR) je sestavena ze stejného základu kódu jako modul CLR .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-141">The CLR implementation for .NET 5 and later versions (also known as the Core CLR) is built from the same code base as the .NET Framework CLR.</span></span> <span data-ttu-id="3e9cd-142">Základní CLR byl původně modulem runtime programu Silverlight a byl navržen pro spouštění na více platformách, konkrétně v systému Windows a OS X. Je to pořád modul runtime pro [více platforem](#cross-platform) , který teď zahrnuje podporu pro spoustu distribucí Linux.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-142">Originally, the Core CLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. It's still a [cross-platform](#cross-platform) runtime, now including support for many Linux distributions.</span></span>

<span data-ttu-id="3e9cd-143">Viz také [modul runtime](#runtime).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-143">See also [runtime](#runtime).</span></span>

## <a name="core-clr"></a><span data-ttu-id="3e9cd-144">Core CLR</span><span class="sxs-lookup"><span data-stu-id="3e9cd-144">Core CLR</span></span>

<span data-ttu-id="3e9cd-145">Modul CLR (Common Language Runtime [) pro rozhraní .NET 5 a novější verze (včetně .NET Core 2.1-3.1)](#net-5-and-later-versions).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-145">The Common Language Runtime for [.NET 5 and later versions (including .NET Core 2.1-3.1)](#net-5-and-later-versions).</span></span>

<span data-ttu-id="3e9cd-146">Viz [CLR](#clr)</span><span class="sxs-lookup"><span data-stu-id="3e9cd-146">See [CLR](#clr)</span></span>

## <a name="corert"></a><span data-ttu-id="3e9cd-147">CoreRT</span><span class="sxs-lookup"><span data-stu-id="3e9cd-147">CoreRT</span></span>

<span data-ttu-id="3e9cd-148">Na rozdíl od [CLR](#clr)není CoreRT virtuálním počítačem, což znamená, že nezahrnuje zařízení pro generování a běh kódu průběžně, protože nezahrnuje [JIT](#jit).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-148">In contrast to the [CLR](#clr), CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="3e9cd-149">Nicméně obsahuje [GC](#gc) a možnost identifikace typu za běhu (RTTI) a reflexe.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-149">It does, however, include the [GC](#gc) and the ability for run-time type identification (RTTI) and reflection.</span></span> <span data-ttu-id="3e9cd-150">Nicméně systém jeho typů je navržen tak, aby se metadata pro reflexi nevyžadovala.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-150">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="3e9cd-151">Nevyžadování metadat umožňuje mít řetěz nástrojů [AOT](#aot) , který může propojit nadbytečné metadata a (důležitější je) identifikovat kód, který aplikace nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-151">Not requiring metadata enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="3e9cd-152">CoreRT je ve vývoji.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-152">CoreRT is in development.</span></span>

<span data-ttu-id="3e9cd-153">Přečtěte si [Úvod do .NET Native a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-153">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span></span>

## <a name="cross-platform"></a><span data-ttu-id="3e9cd-154">pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="3e9cd-154">cross-platform</span></span>

<span data-ttu-id="3e9cd-155">Možnost vyvíjet a spouštět aplikaci, která se dá použít v několika různých operačních systémech, jako jsou Linux, Windows a iOS, aniž by se musely přepsat speciálně pro každé z nich.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-155">The ability to develop and execute an application that can be used on multiple different operating systems, such as Linux, Windows, and iOS, without having to rewrite specifically for each one.</span></span> <span data-ttu-id="3e9cd-156">To umožňuje opakované použití kódu a konzistenci mezi aplikacemi na různých platformách.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-156">This enables code reuse and consistency between applications on different platforms.</span></span>

## <a name="ecosystem"></a><span data-ttu-id="3e9cd-157">ekosystému</span><span class="sxs-lookup"><span data-stu-id="3e9cd-157">ecosystem</span></span>

<span data-ttu-id="3e9cd-158">Veškerý běhový software, vývojové nástroje a komunitní prostředky, které se používají k sestavování a spouštění aplikací pro danou technologii.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-158">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="3e9cd-159">Pojem "ekosystém .NET" se od podobných termínů, jako je například .NET Stack, liší v zahrnutí aplikací a knihoven třetích stran.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-159">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="3e9cd-160">Tady je příklad ve větě:</span><span class="sxs-lookup"><span data-stu-id="3e9cd-160">Here's an example in a sentence:</span></span>

- <span data-ttu-id="3e9cd-161">"Motivací za [.NET Standard](#net-standard) je vytvoření větší jednotnosti v ekosystému .NET."</span><span class="sxs-lookup"><span data-stu-id="3e9cd-161">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span>

## <a name="framework"></a><span data-ttu-id="3e9cd-162">rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e9cd-162">framework</span></span>

<span data-ttu-id="3e9cd-163">Obecně platí komplexní kolekce rozhraní API, která usnadňují vývoj a nasazování aplikací, které jsou založeny na konkrétní technologii.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-163">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="3e9cd-164">V tomto obecném smyslu jsou příklady aplikačních rozhraní ASP.NET Core a model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-164">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="3e9cd-165">Viz také [Knihovna](#library).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-165">See also [library](#library).</span></span>

<span data-ttu-id="3e9cd-166">Slovo "Framework" má v následujících termínech jiný význam:</span><span class="sxs-lookup"><span data-stu-id="3e9cd-166">The word "framework" has a different meaning in the following terms:</span></span>

- [<span data-ttu-id="3e9cd-167">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="3e9cd-167">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="3e9cd-168">Cílová architektura</span><span class="sxs-lookup"><span data-stu-id="3e9cd-168">target framework</span></span>](#target-framework)
- [<span data-ttu-id="3e9cd-169">TFM (moniker cílového rozhraní .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="3e9cd-169">TFM (target framework moniker)</span></span>](#tfm)
- [<span data-ttu-id="3e9cd-170">aplikace závislá na rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e9cd-170">framework-dependent app</span></span>](../core/deploying/index.md#publish-framework-dependent)

<span data-ttu-id="3e9cd-171">V dokumentaci k starší verzi rozhraní .NET "rozhraní" někdy odkazuje na [implementaci rozhraní .NET](#implementation-of-net).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-171">In legacy .NET documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="3e9cd-172">Například článek může volat rozhraní .NET 5 a Framework.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-172">For example, an article may call .NET 5 a framework.</span></span>

## <a name="gc"></a><span data-ttu-id="3e9cd-173">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="3e9cd-173">GC</span></span>

<span data-ttu-id="3e9cd-174">Systém uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-174">Garbage collector.</span></span>

<span data-ttu-id="3e9cd-175">Systém uvolňování paměti je implementace automatické správy paměti.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-175">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="3e9cd-176">GC uvolňuje paměť obsazená objekty, které se již nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-176">The GC frees memory occupied by objects that are no longer in use.</span></span>

<span data-ttu-id="3e9cd-177">Viz [shromažďování paměti](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-177">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="3e9cd-178">IL</span><span class="sxs-lookup"><span data-stu-id="3e9cd-178">IL</span></span>

<span data-ttu-id="3e9cd-179">Převodní jazyk.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-179">Intermediate language.</span></span>

<span data-ttu-id="3e9cd-180">Jazyky vyšší úrovně .NET, jako je C#, se zkompiluje do nezávislá sady instrukcí pro hardware, která se označuje jako Intermediate Language (IL).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-180">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="3e9cd-181">IL se někdy označuje jako MSIL (Microsoft IL) nebo CIL (Common IL).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-181">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="3e9cd-182">JIT</span><span class="sxs-lookup"><span data-stu-id="3e9cd-182">JIT</span></span>

<span data-ttu-id="3e9cd-183">Kompilátor za běhu.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-183">Just-in-time compiler.</span></span>

<span data-ttu-id="3e9cd-184">Podobně jako [AOT](#aot)tento kompilátor překládá [Il](#il) na strojový kód, který procesor rozumí.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-184">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="3e9cd-185">Na rozdíl od AOT probíhá kompilace JIT na vyžádání a je provedena na stejném počítači, na kterém je nutné kód spustit.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-185">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="3e9cd-186">Vzhledem k tomu, že během provádění aplikace dojde k kompilaci JIT, doba kompilace je součástí doby běhu.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-186">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="3e9cd-187">Kompilátory JIT proto musí vyvážit čas strávený optimalizací kódu proti úsporám, které může výsledný kód vyvolat.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-187">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="3e9cd-188">Kompilátor JIT ale zná skutečný hardware a může vývojářům zdarma dodávat různé implementace.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-188">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="3e9cd-189">implementace rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="3e9cd-189">implementation of .NET</span></span>

<span data-ttu-id="3e9cd-190">Implementace rozhraní .NET zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="3e9cd-190">An implementation of .NET includes:</span></span>

- <span data-ttu-id="3e9cd-191">Jeden nebo více modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-191">One or more runtimes.</span></span> <span data-ttu-id="3e9cd-192">Příklady: [CLR](#clr), [CoreRT](#corert).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-192">Examples: [CLR](#clr), [CoreRT](#corert).</span></span>
- <span data-ttu-id="3e9cd-193">Knihovna tříd, která implementuje verzi .NET Standard a může obsahovat další rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-193">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="3e9cd-194">Příklady: [BCLs](#bcl) pro [.NET Framework](#net-framework) a [.NET 5 a novější verze (včetně .NET Core 2.1-3.1)](#net-5-and-later-versions).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-194">Examples: the [BCLs](#bcl) for [.NET Framework](#net-framework) and [.NET 5 and later versions (including .NET Core 2.1-3.1)](#net-5-and-later-versions).</span></span>
- <span data-ttu-id="3e9cd-195">Volitelně jeden nebo více aplikačních architektur.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-195">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="3e9cd-196">Příklady: [ASP.NET](#aspnet), model Windows Forms a WPF jsou součástí .NET Framework a .NET 5.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-196">Examples: [ASP.NET](#aspnet), Windows Forms, and WPF are included in the .NET Framework and .NET 5.</span></span>
- <span data-ttu-id="3e9cd-197">Volitelně vývojové nástroje.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-197">Optionally, development tools.</span></span> <span data-ttu-id="3e9cd-198">Některé vývojové nástroje se sdílejí mezi více implementacemi.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-198">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="3e9cd-199">Příklady implementací rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="3e9cd-199">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="3e9cd-200">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="3e9cd-200">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="3e9cd-201">.NET 5 a novější verze (včetně .NET Core 2.1-3.1</span><span class="sxs-lookup"><span data-stu-id="3e9cd-201">.NET 5 and later versions (including .NET Core 2.1-3.1</span></span>](#net-5-and-later-versions)
- [<span data-ttu-id="3e9cd-202">Univerzální platforma Windows (UPW)</span><span class="sxs-lookup"><span data-stu-id="3e9cd-202">Universal Windows Platform (UWP)</span></span>](#uwp)
- [<span data-ttu-id="3e9cd-203">Mono</span><span class="sxs-lookup"><span data-stu-id="3e9cd-203">Mono</span></span>](#mono)

## <a name="library"></a><span data-ttu-id="3e9cd-204">knihovna</span><span class="sxs-lookup"><span data-stu-id="3e9cd-204">library</span></span>

<span data-ttu-id="3e9cd-205">Kolekce rozhraní API, která mohou být volána aplikacemi nebo jinými knihovnami.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-205">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="3e9cd-206">Knihovna .NET se skládá z jednoho nebo více [sestavení](#assembly).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-206">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="3e9cd-207">Slova Library a [Framework](#framework) se často používají jako synonyma.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-207">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="mono"></a><span data-ttu-id="3e9cd-208">Mono</span><span class="sxs-lookup"><span data-stu-id="3e9cd-208">Mono</span></span>

<span data-ttu-id="3e9cd-209">Mono je open source implementace .NET pro [různé platformy](#cross-platform) , která se používá hlavně v případě, že je potřeba malý modul runtime.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-209">Mono is an open source, [cross-platform](#cross-platform) .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="3e9cd-210">Je to modul runtime, který vychází z aplikací Xamarin na zařízeních s Androidem, Mac, iOS, tvOS a watchOS a primárně se zaměřuje na aplikace, které vyžadují malé nároky.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-210">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS, and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="3e9cd-211">Podporuje všechny aktuálně publikované verze .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-211">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="3e9cd-212">V minulosti implementovala mono větší rozhraní API .NET Framework a emuluje některé z nejoblíbenějších funkcí v systému UNIX.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-212">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="3e9cd-213">Někdy se používá ke spouštění aplikací .NET, které spoléhají na tyto možnosti v systému UNIX.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-213">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="3e9cd-214">Mono se obvykle používá s [kompilátorem za běhu](#jit), ale také obsahuje úplný [statický kompilátor (předem zkompilování)](#aot) , který se používá na platformách, jako je iOS.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-214">Mono is typically used with a [just-in-time compiler](#jit), but it also features a full [static compiler (ahead-of-time compilation)](#aot) that is used on platforms like iOS.</span></span>

<span data-ttu-id="3e9cd-215">Podívejte se na [dokumentaci k mono](https://www.mono-project.com/docs/).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-215">See the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="3e9cd-216">.NET</span><span class="sxs-lookup"><span data-stu-id="3e9cd-216">.NET</span></span>

<span data-ttu-id="3e9cd-217">Termín pro [.NET Standard](#net-standard) a všechny implementace a úlohy [.NET](#implementation-of-net) .</span><span class="sxs-lookup"><span data-stu-id="3e9cd-217">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="3e9cd-218">Vždy plně velkými písmeny, nikdy ".NET".</span><span class="sxs-lookup"><span data-stu-id="3e9cd-218">Always fully capitalized, never ".Net".</span></span>

<span data-ttu-id="3e9cd-219">Když se uvolní [.NET 5](#net-5-and-later-versions) (aktuálně ve verzi Preview), bude doporučená implementace .NET pro všechny nové vývojové prostředí .NET, takže v některých kontextech ".NET" bude znamenat ".NET 5 a novější verze".</span><span class="sxs-lookup"><span data-stu-id="3e9cd-219">When [.NET 5](#net-5-and-later-versions) (currently in preview) is released, it will be the recommended .NET implementation for all new .NET development, and so in some contexts ".NET" will imply ".NET 5 and later versions."</span></span>

<span data-ttu-id="3e9cd-220">Projděte si [příručku .NET](index.yml)</span><span class="sxs-lookup"><span data-stu-id="3e9cd-220">See the [.NET guide](index.yml)</span></span>

## <a name="net-5-and-later-versions"></a><span data-ttu-id="3e9cd-221">.NET 5 a novější verze</span><span class="sxs-lookup"><span data-stu-id="3e9cd-221">.NET 5 and later versions</span></span>

<span data-ttu-id="3e9cd-222">Vysoce výkonná a open source implementace .NET pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-222">A cross-platform, high-performance, open-source implementation of .NET.</span></span> <span data-ttu-id="3e9cd-223">Zahrnuje modul[CLR](#clr)(Common Language Runtime), modul runtime [AOT](#aot) ([CoreRT](#corert), ve vývoji), knihovnu základní třídy ([BCL](#bcl)) a [sadu .NET SDK](#net-sdk).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-223">Includes a Common Language Runtime ([CLR](#clr)), an [AOT](#aot) runtime ([CoreRT](#corert), in development), a Base Class Library ([BCL](#bcl)), and the [.NET SDK](#net-sdk).</span></span>

<span data-ttu-id="3e9cd-224">Starší verze této implementace rozhraní .NET se označují jako .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-224">Earlier versions of this .NET implementation are known as .NET Core.</span></span> <span data-ttu-id="3e9cd-225">.NET 5,0 je další verze, která následuje po .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-225">.NET 5.0 is the next version following .NET Core 3.1.</span></span> <span data-ttu-id="3e9cd-226">Verze 4 byla vynechána, aby nedocházelo k matoucí této novější implementace .NET se starší implementací, která se označuje jako [.NET Framework](#net-framework).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-226">Version 4 was skipped to avoid confusing this newer implementation of .NET with the older implementation that is known as [.NET Framework](#net-framework).</span></span> <span data-ttu-id="3e9cd-227">Aktuální verze .NET Framework je 4,8.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-227">The current version of .NET Framework is 4.8.</span></span>

<span data-ttu-id="3e9cd-228">Viz [.NET](../core/index.yml).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-228">See [.NET](../core/index.yml).</span></span>

## <a name="net-cli"></a><span data-ttu-id="3e9cd-229">ROZHRANÍ .NET CLI</span><span class="sxs-lookup"><span data-stu-id="3e9cd-229">.NET CLI</span></span>

<span data-ttu-id="3e9cd-230">Sada nástrojů pro více platforem pro vývoj aplikací a knihoven pro [rozhraní .NET 5 a novější verze (včetně .NET Core 2.1-3.1)](#net-5-and-later-versions).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-230">A cross-platform toolchain for developing applications and libraries for [.NET 5 and later versions (including .NET Core 2.1-3.1)](#net-5-and-later-versions).</span></span> <span data-ttu-id="3e9cd-231">Označuje se také jako .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-231">Also known as the .NET Core CLI.</span></span>

<span data-ttu-id="3e9cd-232">Viz [rozhraní .NET CLI](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-232">See [.NET CLI](../core/tools/index.md).</span></span>

## <a name="net-core"></a><span data-ttu-id="3e9cd-233">.NET Core</span><span class="sxs-lookup"><span data-stu-id="3e9cd-233">.NET Core</span></span>

<span data-ttu-id="3e9cd-234">Viz [.NET 5 a novější verze](#net-5-and-later-versions).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-234">See [.NET 5 and later versions](#net-5-and-later-versions).</span></span>

## <a name="net-framework"></a><span data-ttu-id="3e9cd-235">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="3e9cd-235">.NET Framework</span></span>

<span data-ttu-id="3e9cd-236">Implementace rozhraní .NET, která běží pouze v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-236">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="3e9cd-237">Zahrnuje modul[CLR](#clr)(Common Language Runtime), knihovnu základních tříd ([BCL](#bcl)) a knihovny aplikačních rozhraní, jako je například [ASP.NET](#aspnet), model Windows Forms a WPF.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-237">Includes the Common Language Runtime ([CLR](#clr)), the Base Class Library ([BCL](#bcl)), and application framework libraries such as [ASP.NET](#aspnet), Windows Forms, and WPF.</span></span>

<span data-ttu-id="3e9cd-238">Viz [průvodce .NET Framework](../framework/index.yml).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-238">See [.NET Framework Guide](../framework/index.yml).</span></span>

## <a name="net-native"></a><span data-ttu-id="3e9cd-239">.NET Native</span><span class="sxs-lookup"><span data-stu-id="3e9cd-239">.NET Native</span></span>

<span data-ttu-id="3e9cd-240">Řetěz nástrojů kompilátoru, který vytváří nativní kód před časem ([AOT](#aot)), na rozdíl od[JIT](#jit)(just-in-time).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-240">A compiler tool chain that produces native code ahead-of-time ([AOT](#aot)), as opposed to just-in-time ([JIT](#jit)).</span></span>

<span data-ttu-id="3e9cd-241">Kompilace probíhá na počítači vývojáře podobně jako kompilátor jazyka C++ a linker funguje.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-241">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="3e9cd-242">Odebírá nepoužitý kód a stráví více času optimalizací.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-242">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="3e9cd-243">Extrahuje kód z knihoven a sloučí je do spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-243">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="3e9cd-244">Výsledkem je jeden modul, který představuje celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-244">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="3e9cd-245">UWP byla první aplikační architektura, kterou .NET Native podporuje.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-245">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="3e9cd-246">Nyní podporujeme vytváření nativních konzolových aplikací pro Windows, macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-246">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="3e9cd-247">Viz [Úvod do .NET Native a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="3e9cd-247">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-sdk"></a><span data-ttu-id="3e9cd-248">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="3e9cd-248">.NET SDK</span></span>

<span data-ttu-id="3e9cd-249">Sada knihoven a nástrojů, které vývojářům umožňují vytvářet aplikace a knihovny .NET pro [rozhraní .NET 5 a novější verze (včetně .NET Core 2.1-3.1)](#net-5-and-later-versions).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-249">A set of libraries and tools that allow developers to create .NET applications and libraries for [.NET 5 and later versions (including .NET Core 2.1-3.1)](#net-5-and-later-versions).</span></span> <span data-ttu-id="3e9cd-250">Označuje se také jako .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-250">Also known as the .NET Core SDK.</span></span>

<span data-ttu-id="3e9cd-251">Zahrnuje [rozhraní .NET CLI](#net-cli) pro vytváření aplikací, knihovny .NET a běhové prostředí pro sestavování a spouštění aplikací a spustitelný soubor dotnet (*dotnet.exe*), který spouští příkazy rozhraní příkazového řádku a spouští aplikace.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-251">Includes the [.NET CLI](#net-cli) for building apps, .NET libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="3e9cd-252">Viz [Přehled sady .NET SDK](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-252">See [.NET SDK Overview](../core/sdk.md).</span></span>

## <a name="net-standard"></a><span data-ttu-id="3e9cd-253">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="3e9cd-253">.NET Standard</span></span>

<span data-ttu-id="3e9cd-254">Formální specifikace rozhraní .NET API, které jsou k dispozici v každé implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-254">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="3e9cd-255">Specifikace .NET Standard se v dokumentaci někdy označuje jako knihovna.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-255">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="3e9cd-256">Vzhledem k tomu, že knihovna obsahuje implementace rozhraní API, nikoli pouze specifikace (rozhraní), je pro volání .NET Standard "Library" zavádějící.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-256">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span>

<span data-ttu-id="3e9cd-257">Viz [.NET Standard](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-257">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="3e9cd-258">NGEN</span><span class="sxs-lookup"><span data-stu-id="3e9cd-258">NGEN</span></span>

<span data-ttu-id="3e9cd-259">Generování nativních (imagí)</span><span class="sxs-lookup"><span data-stu-id="3e9cd-259">Native (image) generation.</span></span>

<span data-ttu-id="3e9cd-260">Tuto technologii si můžete představit jako trvalý kompilátor [JIT](#jit) .</span><span class="sxs-lookup"><span data-stu-id="3e9cd-260">You can think of this technology as a persistent [JIT](#jit) compiler.</span></span> <span data-ttu-id="3e9cd-261">Obvykle kompiluje kód na počítači, kde je spuštěn kód, ale kompilace obvykle probíhá v době instalace.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-261">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="3e9cd-262">balíček</span><span class="sxs-lookup"><span data-stu-id="3e9cd-262">package</span></span>

<span data-ttu-id="3e9cd-263">Balíček NuGet &mdash; nebo pouze balíček &mdash; je soubor *. zip* s jedním nebo více sestaveními se stejným názvem společně s dalšími metadaty, jako je jméno autora.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-263">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="3e9cd-264">Soubor *. zip* má příponu *. nupkg* a může obsahovat prostředky, jako jsou soubory *DLL* a *XML* soubory pro použití s více cílovými rozhraními a verzemi.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-264">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="3e9cd-265">Při instalaci v aplikaci nebo knihovně jsou příslušné prostředky vybrány na základě cílového rozhraní určeného aplikací nebo knihovnou.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-265">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="3e9cd-266">Prostředky, které definují rozhraní, jsou ve složce *ref* a assety definující implementaci jsou ve složce *lib* .</span><span class="sxs-lookup"><span data-stu-id="3e9cd-266">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="3e9cd-267">platforma</span><span class="sxs-lookup"><span data-stu-id="3e9cd-267">platform</span></span>

<span data-ttu-id="3e9cd-268">Operační systém a hardware, na kterém běží, jako je Windows, macOS, Linux, iOS a Android.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-268">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="3e9cd-269">Tady jsou příklady použití ve větách:</span><span class="sxs-lookup"><span data-stu-id="3e9cd-269">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="3e9cd-270">".NET Core je implementace .NET pro různé platformy."</span><span class="sxs-lookup"><span data-stu-id="3e9cd-270">".NET Core is a cross-platform implementation of .NET."</span></span>
- <span data-ttu-id="3e9cd-271">"Profily PCL reprezentují platformy Microsoft, zatímco .NET Standard nezávislá na platformu."</span><span class="sxs-lookup"><span data-stu-id="3e9cd-271">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="3e9cd-272">Starší verze dokumentace rozhraní .NET někdy používá "platformu .NET" k označení [implementace .NET](#implementation-of-net) nebo [zásobníku](#stack) .NET, včetně všech implementací.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-272">Legacy .NET documentation sometimes uses ".NET platform" to mean either an [implementation of .NET](#implementation-of-net) or the .NET [stack](#stack) including all implementations.</span></span> <span data-ttu-id="3e9cd-273">Obě tato použití se od sebe snaží získat zaměňovatelné s primárním (operačním nebo hardwarovým) významem, takže se z těchto použití vyhneme.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-273">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we try to avoid these usages.</span></span>

<span data-ttu-id="3e9cd-274">Pojem "platforma" má v frázi "vývojářské platformy" jiný význam, který odkazuje na software, který poskytuje nástroje a knihovny pro sestavování a spouštění aplikací.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-274">"Platform" has a different meaning in the phrase "developer platform," which refers to software that provides tools and libraries for building and running apps.</span></span> <span data-ttu-id="3e9cd-275">.NET je open source platforma pro vývoj na různých platformách pro vytváření mnoha různých typů aplikací.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-275">.NET is a cross-platform, open source developer platform for building many different types of applications.</span></span>

## <a name="runtime"></a><span data-ttu-id="3e9cd-276">modul runtime</span><span class="sxs-lookup"><span data-stu-id="3e9cd-276">runtime</span></span>

<span data-ttu-id="3e9cd-277">Obecně platí, že spouštěcí prostředí pro spravovaný program.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-277">In general, the execution environment for a managed program.</span></span> <span data-ttu-id="3e9cd-278">Operační systém je součástí běhového prostředí, ale není součástí modulu .NET Runtime.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-278">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="3e9cd-279">Tady je několik příkladů prostředí .NET runtime v tomto smyslu slova:</span><span class="sxs-lookup"><span data-stu-id="3e9cd-279">Here are some examples of .NET runtimes in this sense of the word:</span></span>

- <span data-ttu-id="3e9cd-280">Modul[CLR](#clr)(Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="3e9cd-280">Common Language Runtime ([CLR](#clr))</span></span>
- <span data-ttu-id="3e9cd-281">.NET Native (pro UWP)</span><span class="sxs-lookup"><span data-stu-id="3e9cd-281">.NET Native (for UWP)</span></span>
- <span data-ttu-id="3e9cd-282">Mono runtime</span><span class="sxs-lookup"><span data-stu-id="3e9cd-282">Mono runtime</span></span>

<span data-ttu-id="3e9cd-283">Slovo "runtime" má v následujících kontextech jiný význam:</span><span class="sxs-lookup"><span data-stu-id="3e9cd-283">The word "runtime" has a different meaning in the following contexts:</span></span>

* <span data-ttu-id="3e9cd-284">[Stránka pro stažení rozhraní .NET](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-284">The [.NET download page](https://dotnet.microsoft.com/download).</span></span>

  <span data-ttu-id="3e9cd-285">"Modul runtime" zde znamená [CLR](#clr) společně s knihovnou [BCL](#bcl) (architektury Framework), které si můžete stáhnout a nainstalovat na počítač, abyste mohli na počítači spouštět aplikace [závislé na architektuře](../core/deploying/index.md#publish-framework-dependent) .</span><span class="sxs-lookup"><span data-stu-id="3e9cd-285">"Runtime" here means the [CLR](#clr) together with the [BCL](#bcl) (framework libraries), that you can download and install on a machine so that you can run [framework-dependent](../core/deploying/index.md#publish-framework-dependent) apps on the machine.</span></span>

* <span data-ttu-id="3e9cd-286">[Identifikátor modulu runtime (RID)](../core/rid-catalog.md) pro [rozhraní .NET 5 a novější verze (včetně .NET Core 2.1-3.1)](#net-5-and-later-versions).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-286">The [Runtime Identifier (RID)](../core/rid-catalog.md) for [.NET 5 and later versions (including .NET Core 2.1-3.1)](#net-5-and-later-versions).</span></span>

  <span data-ttu-id="3e9cd-287">"Za běhu" se rozumí platforma operačního systému a architektura procesoru, na které běží aplikace .NET, například: `linux-x64` .</span><span class="sxs-lookup"><span data-stu-id="3e9cd-287">"Runtime" here means the OS platform and CPU architecture that a .NET app runs on, for example: `linux-x64`.</span></span>

<span data-ttu-id="3e9cd-288">Starší verze dokumentace rozhraní .NET někdy používá "modul runtime" v tom smyslu [implementace .NET](#implementation-of-net), jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="3e9cd-288">Legacy .NET documentation sometimes uses "runtime" in the sense of an [implementation of .NET](#implementation-of-net), as in the following examples:</span></span>

- <span data-ttu-id="3e9cd-289">"Různé moduly runtime .NET implementují konkrétní verze .NET Standard."</span><span class="sxs-lookup"><span data-stu-id="3e9cd-289">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="3e9cd-290">"Knihovny určené ke spuštění na více modulech runtime by měly cílit na toto rozhraní."</span><span class="sxs-lookup"><span data-stu-id="3e9cd-290">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="3e9cd-291">(odkazování na .NET Standard)</span><span class="sxs-lookup"><span data-stu-id="3e9cd-291">(referring to .NET Standard)</span></span>
- <span data-ttu-id="3e9cd-292">"Různé moduly runtime .NET implementují konkrétní verze .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-292">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="3e9cd-293">…</span><span class="sxs-lookup"><span data-stu-id="3e9cd-293">…</span></span> <span data-ttu-id="3e9cd-294">Každá verze modulu .NET runtime inzeruje nejvyšší .NET Standard verzi, kterou podporuje...</span><span class="sxs-lookup"><span data-stu-id="3e9cd-294">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

## <a name="stack"></a><span data-ttu-id="3e9cd-295">stack</span><span class="sxs-lookup"><span data-stu-id="3e9cd-295">stack</span></span>

<span data-ttu-id="3e9cd-296">Sada programovacích technologií používaných společně k sestavování a spouštění aplikací.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-296">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="3e9cd-297">Rozhraní .NET Stack odkazuje na .NET Standard a všechny implementace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-297">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="3e9cd-298">Fráze ".NET Stack" může odkazovat na jednu implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-298">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span>

## <a name="target-framework"></a><span data-ttu-id="3e9cd-299">Cílová architektura</span><span class="sxs-lookup"><span data-stu-id="3e9cd-299">target framework</span></span>

<span data-ttu-id="3e9cd-300">Kolekce rozhraní API, na kterých závisí aplikace .NET nebo knihovna</span><span class="sxs-lookup"><span data-stu-id="3e9cd-300">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="3e9cd-301">Aplikace nebo knihovna může cílit na verzi .NET Standard (například .NET Standard 2,0), což je specifikace standardizované sady rozhraní API napříč všemi implementacemi .NET.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-301">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is a specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="3e9cd-302">Aplikace nebo knihovna může také cílit na verzi konkrétní implementace rozhraní .NET. v takovém případě získá přístup k rozhraním API pro konkrétní implementaci.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-302">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="3e9cd-303">Například aplikace, která se zaměřuje na Xamarin. iOS, získá přístup k obálkám rozhraní API iOS poskytovaných v Xamarin.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-303">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="3e9cd-304">Pro některé cílové architektury (například .NET Framework) jsou dostupná rozhraní API definovaná sestaveními, která implementuje implementace rozhraní .NET v systému, což může zahrnovat rozhraní API pro rozhraní Application Framework (například ASP.NET, WinForms).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-304">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="3e9cd-305">Pro cílové architektury založené na balíčku (například .NET Standard a .NET Core) jsou rozhraní API architektury definovaná balíčky nainstalovanými v aplikaci nebo knihovně.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-305">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="3e9cd-306">V takovém případě cílové rozhraní implicitně určuje balíček, který odkazuje na všechny balíčky, které dohromady tvoří rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-306">In that case, the target framework implicitly specifies a package that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="3e9cd-307">Viz [cílová rozhraní](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-307">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="3e9cd-308">TFM</span><span class="sxs-lookup"><span data-stu-id="3e9cd-308">TFM</span></span>

<span data-ttu-id="3e9cd-309">Moniker cílového rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-309">Target framework moniker.</span></span>

<span data-ttu-id="3e9cd-310">Formát standardizovaného tokenu pro určení cílové architektury aplikace nebo knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-310">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="3e9cd-311">Cílová rozhraní jsou obvykle odkazována krátkým názvem, například `net462` .</span><span class="sxs-lookup"><span data-stu-id="3e9cd-311">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="3e9cd-312">Dlouhý tvar TFM (například. NETFramework, Version = 4.6.2) existuje, ale obecně se nepoužívá k určení cílové architektury.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-312">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="3e9cd-313">Viz [cílová rozhraní](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-313">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="3e9cd-314">UWP</span><span class="sxs-lookup"><span data-stu-id="3e9cd-314">UWP</span></span>

<span data-ttu-id="3e9cd-315">Univerzální platforma Windows.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-315">Universal Windows Platform.</span></span>

<span data-ttu-id="3e9cd-316">Implementace .NET, která se používá k vytváření moderních, dotykové aplikace a softwaru Windows pro Internet věcí (IoT).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-316">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="3e9cd-317">Je navržený tak, aby sjednotí různé typy zařízení, na které můžete chtít cílit, včetně počítačů, tabletů, telefonů a i konzoly Xbox.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-317">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phones, and even the Xbox.</span></span> <span data-ttu-id="3e9cd-318">UWP nabízí spoustu služeb, jako je centralizované úložiště aplikací, spouštěcí prostředí (kontejneru AppContainer) a sada rozhraní API systému Windows, které se mají použít místo Win32 (WinRT).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-318">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="3e9cd-319">Aplikace můžou být napsané v jazyce C++, C#, Visual Basic a JavaScriptu.</span><span class="sxs-lookup"><span data-stu-id="3e9cd-319">Apps can be written in C++, C#, Visual Basic, and JavaScript.</span></span> <span data-ttu-id="3e9cd-320">Při použití jazyka C# a Visual Basic rozhraní API .NET poskytuje rozhraní .NET 5 a novější verze (včetně .NET Core 2.1-3.1).</span><span class="sxs-lookup"><span data-stu-id="3e9cd-320">When using C# and Visual Basic, the .NET APIs are provided by .NET 5 and later versions (including .NET Core 2.1-3.1).</span></span>

## <a name="see-also"></a><span data-ttu-id="3e9cd-321">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e9cd-321">See also</span></span>

- [<span data-ttu-id="3e9cd-322">Průvodce .NET</span><span class="sxs-lookup"><span data-stu-id="3e9cd-322">.NET Guide</span></span>](index.yml)
- [<span data-ttu-id="3e9cd-323">Průvodce .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3e9cd-323">.NET Framework Guide</span></span>](../framework/index.yml)
- [<span data-ttu-id="3e9cd-324">.NET Core</span><span class="sxs-lookup"><span data-stu-id="3e9cd-324">.NET Core</span></span>](../core/index.yml)
- [<span data-ttu-id="3e9cd-325">ASP.NET – přehled</span><span class="sxs-lookup"><span data-stu-id="3e9cd-325">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)
- [<span data-ttu-id="3e9cd-326">Přehled ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3e9cd-326">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)
