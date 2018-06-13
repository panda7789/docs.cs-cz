---
title: .NET – Glosář
description: Zjistěte význam vybrané termínů používaných v dokumentaci k rozhraní .NET.
author: tdykstra
ms.author: tdykstra
ms.date: 07/08/2017
ms.technology: dotnet-standard
ms.openlocfilehash: 195fbb799432b9d01a5faf301c9f8f2d1edfa1ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579402"
---
# <a name="net-glossary"></a><span data-ttu-id="224bc-103">.NET – Glosář</span><span class="sxs-lookup"><span data-stu-id="224bc-103">.NET Glossary</span></span>

<span data-ttu-id="224bc-104">Hlavním cílem, který tento glosář je objasnit významy vybrané podmínky a zkratky, které se zobrazují často v dokumentaci k rozhraní .NET bez definic.</span><span class="sxs-lookup"><span data-stu-id="224bc-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="224bc-105">AOT</span><span class="sxs-lookup"><span data-stu-id="224bc-105">AOT</span></span>

<span data-ttu-id="224bc-106">Napřed předčasné kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="224bc-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="224bc-107">Podobně jako [JIT](#jit), tento kompilátoru také překládá [IL](#il) kódu počítače.</span><span class="sxs-lookup"><span data-stu-id="224bc-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="224bc-108">Na rozdíl od JIT – kompilace probíhá kompilace AOT předtím, než se spustí aplikace a obvykle provádí na jiný počítač.</span><span class="sxs-lookup"><span data-stu-id="224bc-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="224bc-109">Protože nástroj řetězy AOT nemáte kompilace za běhu, nemají minimalizovat čas strávený kompilace.</span><span class="sxs-lookup"><span data-stu-id="224bc-109">Because AOT tool chains don't compile at runtime, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="224bc-110">To znamená, že se můžete tráví další optimalizace času.</span><span class="sxs-lookup"><span data-stu-id="224bc-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="224bc-111">Vzhledem k tomu, že kontextu AOT bude celá aplikace se provádí kompilátoru AOT taky propojení mezi modulu a analýzy celého programu, což znamená, že všechny odkazy dodržíte a vytváří jeden spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="224bc-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

## <a name="aspnet"></a><span data-ttu-id="224bc-112">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="224bc-112">ASP.NET</span></span> 

<span data-ttu-id="224bc-113">Původní implementace technologie ASP.NET, který se dodává s rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="224bc-113">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="224bc-114">Někdy ASP.NET je také souhrnný název, který odkazuje na obou implementace technologie ASP.NET, včetně ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="224bc-114">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="224bc-115">Což znamená, že termín představuje v jakékoli dané instanci je určen podle kontextu.</span><span class="sxs-lookup"><span data-stu-id="224bc-115">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="224bc-116">Odkazovat na technologii ASP.NET 4.x, pokud chcete, aby bylo jasné, které nepoužívají ASP.NET rozumí obou implementace.</span><span class="sxs-lookup"><span data-stu-id="224bc-116">Refer to ASP.NET 4.x when you want to make it clear that you’re not using ASP.NET to mean both implementations.</span></span> 

<span data-ttu-id="224bc-117">V tématu [dokumentace k technologii ASP.NET](/aspnet/#pivot=aspnet).</span><span class="sxs-lookup"><span data-stu-id="224bc-117">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="224bc-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="224bc-118">ASP.NET Core</span></span>

<span data-ttu-id="224bc-119">Platformě, vysoce výkonné open source implementace technologie ASP.NET založený na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="224bc-119">A cross-platform, high-performance, open source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="224bc-120">V tématu [ASP.NET Core dokumentaci](/aspnet/#pivot=core).</span><span class="sxs-lookup"><span data-stu-id="224bc-120">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="224bc-121">sestavení</span><span class="sxs-lookup"><span data-stu-id="224bc-121">assembly</span></span>

<span data-ttu-id="224bc-122">A *.dll*/*.exe* soubor, který obsahuje kolekci rozhraní API, kterou lze volat aplikace nebo jiné sestavení.</span><span class="sxs-lookup"><span data-stu-id="224bc-122">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by apps or other assemblies.</span></span>

<span data-ttu-id="224bc-123">Sestavení může obsahovat typy jako je rozhraní, třídy, struktury, výčty a delegáti.</span><span class="sxs-lookup"><span data-stu-id="224bc-123">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="224bc-124">Sestavení v projektu *bin* složky se někdy označují jako *binární soubory*.</span><span class="sxs-lookup"><span data-stu-id="224bc-124">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="224bc-125">Viz také [knihovny](#library).</span><span class="sxs-lookup"><span data-stu-id="224bc-125">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="224bc-126">CLR</span><span class="sxs-lookup"><span data-stu-id="224bc-126">CLR</span></span>

<span data-ttu-id="224bc-127">Modul Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="224bc-127">Common Language Runtime.</span></span>

<span data-ttu-id="224bc-128">Přesný význam závisí na kontext, ale to obvykle odkazuje na modul runtime rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="224bc-128">The exact meaning depends on the context, but this usually refers to the runtime of the .NET Framework.</span></span> <span data-ttu-id="224bc-129">Modul CLR zpracovává přidělování paměti a správu.</span><span class="sxs-lookup"><span data-stu-id="224bc-129">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="224bc-130">Modul CLR je také virtuální počítač, který nejen spustí aplikace, ale také generuje a kompilovaný kód na průběžně pomocí JIT kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="224bc-130">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a JIT compiler.</span></span> <span data-ttu-id="224bc-131">Aktuální implementace Microsoft CLR je pouze v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="224bc-131">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="224bc-132">CoreCLR</span><span class="sxs-lookup"><span data-stu-id="224bc-132">CoreCLR</span></span>

<span data-ttu-id="224bc-133">.NET core modul Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="224bc-133">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="224bc-134">Tato CLR je sestaven z stejný kód základní jako modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="224bc-134">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="224bc-135">Původně CoreCLR byl běhové prostředí Silverlight a byl navržen ke spuštění na více platforem, konkrétně Windows a OS X. CoreCLR je teď součástí .NET Core a představuje zjednodušenou verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="224bc-135">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="224bc-136">Stále je nyní včetně podpory pro velkém množství distribucí Linux modulu runtime křížové platformy.</span><span class="sxs-lookup"><span data-stu-id="224bc-136">It's still a cross platform runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="224bc-137">Virtuální počítač s možností provádění JIT a kód je také CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="224bc-137">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="224bc-138">CoreFX</span><span class="sxs-lookup"><span data-stu-id="224bc-138">CoreFX</span></span>

<span data-ttu-id="224bc-139">Knihovny .NET core základní třídu (BCL)</span><span class="sxs-lookup"><span data-stu-id="224bc-139">.NET Core Base Class Library (BCL)</span></span>

<span data-ttu-id="224bc-140">Obory názvů sadu knihoven, které tvoří System.* (a v omezené míře Microsoft.*).</span><span class="sxs-lookup"><span data-stu-id="224bc-140">A set of libraries that comprise the System.* (and to a limited extent  Microsoft.*) namespaces.</span></span> <span data-ttu-id="224bc-141">BCL je obecné účely, nižší úrovně rozhraní, které vychází z vyšší úrovně rozhraní aplikace, jako je ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="224bc-141">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="224bc-142">Zdrojový kód BCL základní .NET je součástí [CoreFX úložiště](https://github.com/dotnet/corefx).</span><span class="sxs-lookup"><span data-stu-id="224bc-142">The source code of the .NET Core BCL is contained in the [CoreFX repository](https://github.com/dotnet/corefx).</span></span> <span data-ttu-id="224bc-143">Však většiny rozhraní API .NET Core jsou také k dispozici v rozhraní .NET Framework, proto si můžete představit CoreFX jako pokračovatelem BCL rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="224bc-143">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="224bc-144">CoreRT</span><span class="sxs-lookup"><span data-stu-id="224bc-144">CoreRT</span></span>

<span data-ttu-id="224bc-145">.NET core runtime.</span><span class="sxs-lookup"><span data-stu-id="224bc-145">.NET Core runtime.</span></span>

<span data-ttu-id="224bc-146">Na rozdíl od CLR nebo CoreCLR, CoreRT není virtuální počítač, což znamená, neobsahuje zařízení pro generování a spuštění kódu na průběžně, protože neobsahuje [JIT](#jit).</span><span class="sxs-lookup"><span data-stu-id="224bc-146">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="224bc-147">, Ale zahrnout [GC](#gc) a možnost identifikace typu modulu runtime (RTTI) a reflexe.</span><span class="sxs-lookup"><span data-stu-id="224bc-147">It does, however, include the [GC](#gc) and the ability for runtime type identification (RTTI) and reflection.</span></span> <span data-ttu-id="224bc-148">Jeho systém typ je však navržené tak, aby metadata pro reflexi není povinné.</span><span class="sxs-lookup"><span data-stu-id="224bc-148">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="224bc-149">Díky tomu, že [AOT](#aot) nástroj řetězec, který můžete propojit tokeny nadbytečné metadata a identifikovat (důležitější) kód, který nepoužívá aplikaci.</span><span class="sxs-lookup"><span data-stu-id="224bc-149">This enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="224bc-150">CoreRT je ve vývoji.</span><span class="sxs-lookup"><span data-stu-id="224bc-150">CoreRT is in development.</span></span>

<span data-ttu-id="224bc-151">V tématu [Úvod do .NET Native a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="224bc-151">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="ecosystem"></a><span data-ttu-id="224bc-152">ekosystém</span><span class="sxs-lookup"><span data-stu-id="224bc-152">ecosystem</span></span>

<span data-ttu-id="224bc-153">Všechny runtime softwaru, nástroje pro vývoj a komunitní zdroje, které se používají k vytvoření a spuštění aplikace pro daný technologii.</span><span class="sxs-lookup"><span data-stu-id="224bc-153">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="224bc-154">Termín ".NET ekosystém" se liší od podobné podmínky, jako je například ".NET zásobníku" v jeho zahrnutí aplikacím třetích stran a knihovny.</span><span class="sxs-lookup"><span data-stu-id="224bc-154">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="224bc-155">Tady je příklad ve větě:</span><span class="sxs-lookup"><span data-stu-id="224bc-155">Here's an example in a sentence:</span></span>

- <span data-ttu-id="224bc-156">"Motivace za [.NET Standard](#net-standard) navázat větší jednotnost v ekosystému .NET."</span><span class="sxs-lookup"><span data-stu-id="224bc-156">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span> 

## <a name="framework"></a><span data-ttu-id="224bc-157">rozhraní</span><span class="sxs-lookup"><span data-stu-id="224bc-157">framework</span></span>

<span data-ttu-id="224bc-158">Obecně platí komplexní kolekci rozhraní API, která usnadňuje vývoj a nasazení aplikací, které jsou založeny na konkrétní technologie.</span><span class="sxs-lookup"><span data-stu-id="224bc-158">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="224bc-159">V této obecné smysl jsou příklady aplikační architektury ASP.NET Core a systém Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="224bc-159">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="224bc-160">Viz také [knihovny](#library).</span><span class="sxs-lookup"><span data-stu-id="224bc-160">See also [library](#library).</span></span>

<span data-ttu-id="224bc-161">Slovo "framework" má více zvláštní význam technické v následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="224bc-161">The word "framework" has a more specific technical meaning in the following terms:</span></span>
* [<span data-ttu-id="224bc-162">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="224bc-162">.NET Framework</span></span>](#net-framework)
* [<span data-ttu-id="224bc-163">Cílová architektura</span><span class="sxs-lookup"><span data-stu-id="224bc-163">target framework</span></span>](#target-framework)
* [<span data-ttu-id="224bc-164">TFM (Přezdívka cílový framework)</span><span class="sxs-lookup"><span data-stu-id="224bc-164">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="224bc-165">Ve stávající dokumentaci "framework" někdy odkazuje [implementace rozhraní .NET](#implementation-of-net).</span><span class="sxs-lookup"><span data-stu-id="224bc-165">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="224bc-166">Článek například může volat .NET Core rozhraní.</span><span class="sxs-lookup"><span data-stu-id="224bc-166">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="224bc-167">Plánujeme toto matoucí použití v dokumentaci k odstranění.</span><span class="sxs-lookup"><span data-stu-id="224bc-167">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="224bc-168">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="224bc-168">GC</span></span>

<span data-ttu-id="224bc-169">Systém uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="224bc-169">Garbage collector.</span></span>

<span data-ttu-id="224bc-170">Uvolňování paměti je implementací Automatická správa paměti.</span><span class="sxs-lookup"><span data-stu-id="224bc-170">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="224bc-171">Globální Katalog uvolní paměť obsazená objekty, které jsou již používán.</span><span class="sxs-lookup"><span data-stu-id="224bc-171">The GC frees memory occupied by objects that are no longer in use.</span></span> 

<span data-ttu-id="224bc-172">V tématu [uvolňování paměti](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="224bc-172">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="224bc-173">IL</span><span class="sxs-lookup"><span data-stu-id="224bc-173">IL</span></span>

<span data-ttu-id="224bc-174">Převodní jazyk.</span><span class="sxs-lookup"><span data-stu-id="224bc-174">Intermediate language.</span></span>

<span data-ttu-id="224bc-175">Vyšší úrovně jazyky rozhraní .NET, jako je C#, zkompilovat dolů sadu instrukcí bez ohledu na hardware, což se označuje jako zprostředkující jazyk (IL).</span><span class="sxs-lookup"><span data-stu-id="224bc-175">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="224bc-176">IL se někdy označuje jako MSIL (Microsoft IL) nebo soubor CIL (běžné IL).</span><span class="sxs-lookup"><span data-stu-id="224bc-176">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="224bc-177">JIT</span><span class="sxs-lookup"><span data-stu-id="224bc-177">JIT</span></span>

<span data-ttu-id="224bc-178">Kompilátor za běhu.</span><span class="sxs-lookup"><span data-stu-id="224bc-178">Just-in-time compiler.</span></span>

<span data-ttu-id="224bc-179">Podobně jako [AOT](#aot), tento kompilátoru překládá [IL](#il) kódu počítače, která funguje s technologií procesoru.</span><span class="sxs-lookup"><span data-stu-id="224bc-179">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="224bc-180">Na rozdíl od AOT JIT – kompilace probíhá na vyžádání a provádí na stejný počítač, který je potřeba spustit kód.</span><span class="sxs-lookup"><span data-stu-id="224bc-180">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="224bc-181">Vzhledem k tomu, že JIT – kompilace dojde při spuštění aplikace, době potřebné ke kompilaci je součástí čas spuštění.</span><span class="sxs-lookup"><span data-stu-id="224bc-181">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="224bc-182">Kompilátory JIT tedy mít vyvážit čas strávený optimalizace kódu proti úspory, který může vytvářet výsledný kód.</span><span class="sxs-lookup"><span data-stu-id="224bc-182">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="224bc-183">Ale JIT zná skutečné hardwarové a můžete uvolnit vývojáři nemusíte se dodávají spolu různé implementace.</span><span class="sxs-lookup"><span data-stu-id="224bc-183">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="224bc-184">implementace rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="224bc-184">implementation of .NET</span></span>

<span data-ttu-id="224bc-185">Implementace rozhraní .NET zahrnuje následující položky:</span><span class="sxs-lookup"><span data-stu-id="224bc-185">An implementation of .NET includes the following:</span></span>

- <span data-ttu-id="224bc-186">Jeden nebo více moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="224bc-186">One or more runtimes.</span></span> <span data-ttu-id="224bc-187">Příklady: CLR, CoreCLR, CoreRT.</span><span class="sxs-lookup"><span data-stu-id="224bc-187">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="224bc-188">Knihovna tříd, který implementuje verzi .NET Standard a může zahrnovat další rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="224bc-188">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="224bc-189">Příklady: Knihovna rozhraní .NET Framework základní třídy, knihovny .NET Core základní třídy.</span><span class="sxs-lookup"><span data-stu-id="224bc-189">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="224bc-190">Volitelně můžete jeden nebo více aplikací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="224bc-190">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="224bc-191">Příklady: ASP.NET, Windows Forms a WPF jsou zahrnuty v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="224bc-191">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="224bc-192">Volitelně můžete nástroje pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="224bc-192">Optionally, development tools.</span></span> <span data-ttu-id="224bc-193">Některé nástroje pro vývoj jsou sdílena mezi několika implementace.</span><span class="sxs-lookup"><span data-stu-id="224bc-193">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="224bc-194">Příklady implementace rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="224bc-194">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="224bc-195">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="224bc-195">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="224bc-196">.NET Core</span><span class="sxs-lookup"><span data-stu-id="224bc-196">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="224bc-197">Univerzální platforma Windows (UPW)</span><span class="sxs-lookup"><span data-stu-id="224bc-197">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="224bc-198">knihovna</span><span class="sxs-lookup"><span data-stu-id="224bc-198">library</span></span>

<span data-ttu-id="224bc-199">Sada rozhraní API, kterou lze volat aplikace nebo jiné knihovny.</span><span class="sxs-lookup"><span data-stu-id="224bc-199">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="224bc-200">Knihovny .NET, se skládá z jednoho nebo více [sestavení](#assembly).</span><span class="sxs-lookup"><span data-stu-id="224bc-200">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="224bc-201">Knihovna slova a [framework](#framework) se často používají jako synonyma.</span><span class="sxs-lookup"><span data-stu-id="224bc-201">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="224bc-202">metapackage</span><span class="sxs-lookup"><span data-stu-id="224bc-202">metapackage</span></span>

<span data-ttu-id="224bc-203">Balíček NuGet, který nemá žádné knihovny samostatně, ale je pouze seznam závislosti.</span><span class="sxs-lookup"><span data-stu-id="224bc-203">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="224bc-204">Zahrnuté balíčky můžete volitelně vytvořit rozhraní API pro cílové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="224bc-204">The included packages can optionally establish the API for a target framework.</span></span>

<span data-ttu-id="224bc-205">V tématu [balíčků, Metapackages a architektury](../core/packages.md)</span><span class="sxs-lookup"><span data-stu-id="224bc-205">See [Packages, Metapackages and Frameworks](../core/packages.md)</span></span>

## <a name="mono"></a><span data-ttu-id="224bc-206">Mono</span><span class="sxs-lookup"><span data-stu-id="224bc-206">Mono</span></span>

<span data-ttu-id="224bc-207">Mono je implementace rozhraní .NET, která se používá hlavně, když se vyžaduje malé runtime.</span><span class="sxs-lookup"><span data-stu-id="224bc-207">Mono is a .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="224bc-208">Je modul runtime, která pohání aplikace Xamarin pro Android, Mac, iOS, tvOS a watchOS a se zaměřuje především na aplikace, které vyžadují malé nároky.</span><span class="sxs-lookup"><span data-stu-id="224bc-208">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="224bc-209">Podporuje všechny aktuálně publikovaná verze .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="224bc-209">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="224bc-210">V minulosti Mono implementována větší rozhraní API rozhraní .NET Framework a emulovaných některé z nejčastěji používané funkcí v systému Unix.</span><span class="sxs-lookup"><span data-stu-id="224bc-210">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="224bc-211">Někdy se používá ke spouštění aplikací .NET, které jsou závislé na tyto funkce v systému Unix.</span><span class="sxs-lookup"><span data-stu-id="224bc-211">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="224bc-212">Mono se obvykle používá s kompilátorem za běhu, ale nabízí i úplné statické kompilátoru (napřed předčasné kompilace), který se používá na platformách, jako je iOS.</span><span class="sxs-lookup"><span data-stu-id="224bc-212">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="224bc-213">Další informace o Mono, najdete v článku [Mono dokumentaci](https://www.mono-project.com/docs/).</span><span class="sxs-lookup"><span data-stu-id="224bc-213">To learn more about Mono, see the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="224bc-214">.NET</span><span class="sxs-lookup"><span data-stu-id="224bc-214">.NET</span></span>

<span data-ttu-id="224bc-215">Termín zastřešující [.NET Standard](#net-standard) a všechny [implementace rozhraní .NET](#implementation-of-net) a úlohy.</span><span class="sxs-lookup"><span data-stu-id="224bc-215">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="224bc-216">Vždy velkými písmeny, nikdy ".Net".</span><span class="sxs-lookup"><span data-stu-id="224bc-216">Always capitalized, never ".Net".</span></span>

<span data-ttu-id="224bc-217">Najdete v článku [.NET Průvodce](index.md)</span><span class="sxs-lookup"><span data-stu-id="224bc-217">See the [.NET Guide](index.md)</span></span>

## <a name="net-core"></a><span data-ttu-id="224bc-218">.NET Core</span><span class="sxs-lookup"><span data-stu-id="224bc-218">.NET Core</span></span> 

<span data-ttu-id="224bc-219">Implementace rozhraní .NET a platformy, vysoce výkonné open source.</span><span class="sxs-lookup"><span data-stu-id="224bc-219">A cross-platform, high-performance, open source implementation of .NET.</span></span> <span data-ttu-id="224bc-220">Obsahuje základní Common Language Runtime (CoreCLR), AOT Core Runtime (vývojem CoreRT), základní základní knihovny tříd a Core SDK.</span><span class="sxs-lookup"><span data-stu-id="224bc-220">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="224bc-221">V tématu [.NET Core](../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="224bc-221">See [.NET Core](../core/index.md).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="224bc-222">.NET core rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="224bc-222">.NET Core CLI</span></span>

<span data-ttu-id="224bc-223">Napříč platformami nástrojů pro vývoj aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="224bc-223">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="224bc-224">V tématu [nástrojů rozhraní příkazového řádku (CLI) .NET Core](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="224bc-224">See [.NET Core command-line interface (CLI) tools](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="224bc-225">.NET core SDK</span><span class="sxs-lookup"><span data-stu-id="224bc-225">.NET Core SDK</span></span>

<span data-ttu-id="224bc-226">Sada knihovny a nástroje, které umožňují vývojářům vytvářet aplikace .NET Core a knihovny.</span><span class="sxs-lookup"><span data-stu-id="224bc-226">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="224bc-227">Zahrnuje [.NET Core rozhraní příkazového řádku](#net-core-cli) pro vytváření aplikací, knihovny .NET Core a modulu runtime pro vytváření a spouštění aplikací a dotnet spustitelný soubor (*dotnet.exe*), spouští příkazy rozhraní příkazového řádku a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="224bc-227">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="224bc-228">V tématu [.NET Core SDK přehled](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="224bc-228">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="224bc-229">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="224bc-229">.NET Framework</span></span>

<span data-ttu-id="224bc-230">Implementace rozhraní .NET, který spouští pouze v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="224bc-230">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="224bc-231">Zahrnuje Common Language Runtime (CLR), základní knihovny tříd a knihovny framework aplikace například ASP.NET, Windows Forms a WPF.</span><span class="sxs-lookup"><span data-stu-id="224bc-231">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="224bc-232">V tématu [rozhraní .NET Framework – průvodce](../framework/index.md).</span><span class="sxs-lookup"><span data-stu-id="224bc-232">See [.NET Framework Guide](../framework/index.md).</span></span>

## <a name="net-native"></a><span data-ttu-id="224bc-233">.NET Native</span><span class="sxs-lookup"><span data-stu-id="224bc-233">.NET Native</span></span>

<span data-ttu-id="224bc-234">Nástroj řetěz kompilátoru, která vytváří nativního kódu napřed předčasné (AOT), a v běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="224bc-234">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="224bc-235">Probíhá kompilace na počítači vývojáře, podobně jako C++ kompilátoru a linkeru funguje.</span><span class="sxs-lookup"><span data-stu-id="224bc-235">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="224bc-236">Odebere nepoužívané kódu a stráví déle optimalizace ho.</span><span class="sxs-lookup"><span data-stu-id="224bc-236">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="224bc-237">Extrahuje kód z knihovny a sloučí je do spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="224bc-237">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="224bc-238">Výsledkem je jeden modul, který představuje celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="224bc-238">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="224bc-239">UWP byla první rozhraní nepodporuje nativní rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="224bc-239">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="224bc-240">Teď podporujeme vytvářet nativní konzole aplikace pro Windows, systému macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="224bc-240">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="224bc-241">V tématu [Úvod do .NET Native a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="224bc-241">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="224bc-242">Standardní rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="224bc-242">.NET Standard</span></span>

<span data-ttu-id="224bc-243">Formální specifikaci rozhraní API .NET, které jsou dostupné v každé implementace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="224bc-243">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="224bc-244">Specifikace .NET Standard, se někdy nazývá knihovnu v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="224bc-244">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="224bc-245">Knihovnu zahrnuje implementace rozhraní API, ne jenom specifikace (rozhraní), a proto je zavádějící volat .NET Standard "knihovna".</span><span class="sxs-lookup"><span data-stu-id="224bc-245">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="224bc-246">Plánujeme eliminovat toto využití z dokumentace, s výjimkou v souvislosti s aplikací název .NET Standard metapackage (`NETStandard.Library`).</span><span class="sxs-lookup"><span data-stu-id="224bc-246">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="224bc-247">V tématu [.NET Standard](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="224bc-247">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="224bc-248">NGEN</span><span class="sxs-lookup"><span data-stu-id="224bc-248">NGEN</span></span>

<span data-ttu-id="224bc-249">Generování nativních (obrázek).</span><span class="sxs-lookup"><span data-stu-id="224bc-249">Native (image) generation.</span></span>

<span data-ttu-id="224bc-250">Tato technologie si lze představit jako trvalé kompilátoru za běhu.</span><span class="sxs-lookup"><span data-stu-id="224bc-250">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="224bc-251">Zkompiluje obvykle kódu na počítači, kde se spustí kód, ale kompilace obvykle dochází v době instalace.</span><span class="sxs-lookup"><span data-stu-id="224bc-251">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="224bc-252">Balíček</span><span class="sxs-lookup"><span data-stu-id="224bc-252">package</span></span>

<span data-ttu-id="224bc-253">Balíček NuGet &mdash; nebo právě balíčku &mdash; je *.zip* soubor s jedno nebo více sestavení se stejným názvem spolu s další metadata, jako je například jméno autora.</span><span class="sxs-lookup"><span data-stu-id="224bc-253">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="224bc-254">*.Zip* soubor má *.nupkg* rozšíření a může obsahovat prostředky, jako například *.dll* soubory a *.xml* souborů pro použití s několika cílů rozhraní a verze.</span><span class="sxs-lookup"><span data-stu-id="224bc-254">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="224bc-255">Při instalaci v aplikaci nebo knihovny, jsou vybrány příslušné prostředky založené na rozhraní target framework určeného aplikace nebo knihovny.</span><span class="sxs-lookup"><span data-stu-id="224bc-255">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="224bc-256">Prostředky, které definují rozhraní jsou v *ref* složky a prostředky, které definují implementace *lib* složky.</span><span class="sxs-lookup"><span data-stu-id="224bc-256">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="224bc-257">platforma</span><span class="sxs-lookup"><span data-stu-id="224bc-257">platform</span></span>

<span data-ttu-id="224bc-258">Operační systém a hardwaru, který běží na, například Windows, systému macOS, Linux, iOS a Android.</span><span class="sxs-lookup"><span data-stu-id="224bc-258">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="224bc-259">Zde jsou příklady využití v věty:</span><span class="sxs-lookup"><span data-stu-id="224bc-259">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="224bc-260">".NET core je implementace a platformy .NET."</span><span class="sxs-lookup"><span data-stu-id="224bc-260">".NET Core is a cross-platform implementation of .NET."</span></span> 
- <span data-ttu-id="224bc-261">"PCL profily představují platformy Microsoft, zatímco .NET Standard nerozlišuje platformy."</span><span class="sxs-lookup"><span data-stu-id="224bc-261">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="224bc-262">V rozhraní .NET dokumentaci často používá "Platformě .NET" rozumí buď implementace rozhraní .NET nebo zásobníku v rozhraní .NET, včetně všech implementace.</span><span class="sxs-lookup"><span data-stu-id="224bc-262">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="224bc-263">Obě tyto použití často zmatení s primární význam (operačního systému nebo hardware), takže plánujeme tyto použití v dokumentaci k odstranění.</span><span class="sxs-lookup"><span data-stu-id="224bc-263">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="224bc-264">modul runtime</span><span class="sxs-lookup"><span data-stu-id="224bc-264">runtime</span></span>

<span data-ttu-id="224bc-265">Spuštění prostředí spravované programu.</span><span class="sxs-lookup"><span data-stu-id="224bc-265">The execution environment for a managed program.</span></span>

<span data-ttu-id="224bc-266">Je součástí běhové prostředí operačního systému, ale není součástí modulu runtime rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="224bc-266">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="224bc-267">Tady jsou některé příklady moduly runtime rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="224bc-267">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="224bc-268">Common Language Runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="224bc-268">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="224bc-269">Základní Common Language Runtime (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="224bc-269">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="224bc-270">.NET native (pro UPW)</span><span class="sxs-lookup"><span data-stu-id="224bc-270">.NET Native (for UWP)</span></span>
- <span data-ttu-id="224bc-271">Monofonní runtime</span><span class="sxs-lookup"><span data-stu-id="224bc-271">Mono runtime</span></span>

<span data-ttu-id="224bc-272">V dokumentaci k rozhraní .NET, někdy používá "runtime" znamená úplně implementace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="224bc-272">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="224bc-273">Například v následujícím věty "runtime" měl by být nahrazen "implementace":</span><span class="sxs-lookup"><span data-stu-id="224bc-273">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="224bc-274">"Různé moduly runtime .NET implementovat určité verze .NET Standard."</span><span class="sxs-lookup"><span data-stu-id="224bc-274">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="224bc-275">"Toto rozhraní by měl knihovny, které jsou určeny ke spuštění na víc runtimes cíle."</span><span class="sxs-lookup"><span data-stu-id="224bc-275">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="224bc-276">(odkazující na .NET Standard)</span><span class="sxs-lookup"><span data-stu-id="224bc-276">(referring to .NET Standard)</span></span>
- <span data-ttu-id="224bc-277">"Různé moduly runtime .NET implementovat určité verze .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="224bc-277">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="224bc-278">…</span><span class="sxs-lookup"><span data-stu-id="224bc-278">…</span></span> <span data-ttu-id="224bc-279">Každou verzi modulu runtime .NET inzeruje nejvyšší .NET Standard verze, kterou podporuje..."</span><span class="sxs-lookup"><span data-stu-id="224bc-279">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="224bc-280">Plánujeme eliminovat toto nekonzistentní použití.</span><span class="sxs-lookup"><span data-stu-id="224bc-280">We plan to eliminate this inconsistent usage.</span></span> 

## <a name="stack"></a><span data-ttu-id="224bc-281">stack</span><span class="sxs-lookup"><span data-stu-id="224bc-281">stack</span></span>

<span data-ttu-id="224bc-282">Sada programování technologie, které se společně používají k sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="224bc-282">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="224bc-283">"Zásobníku .NET" odkazuje na všechny implementace rozhraní .NET a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="224bc-283">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="224bc-284">Frázi ".NET zásobníku" mohou odkazovat na jednu implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="224bc-284">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span> 

## <a name="target-framework"></a><span data-ttu-id="224bc-285">Cílová architektura</span><span class="sxs-lookup"><span data-stu-id="224bc-285">target framework</span></span>

<span data-ttu-id="224bc-286">Kolekce rozhraní API, která využívá aplikace .NET nebo knihovny.</span><span class="sxs-lookup"><span data-stu-id="224bc-286">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="224bc-287">Aplikace nebo knihovny, můžete vybrat verzi Standard .NET (například .NET standardní 2.0), což je specifikace pro standardizované sadu rozhraní API přes všechny implementace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="224bc-287">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="224bc-288">Aplikace nebo knihovna můžete také cílení na verzi konkrétní implementace rozhraní .NET, ve které případ se získá přístup k rozhraní API pro konkrétní implementaci.</span><span class="sxs-lookup"><span data-stu-id="224bc-288">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="224bc-289">Například aplikace, která je cílena Xamarin.iOS získá přístup k rozhraní API pro zadaný Xamarin iOS obálky.</span><span class="sxs-lookup"><span data-stu-id="224bc-289">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="224bc-290">Pro některé cílové rozhraní (například rozhraní .NET Framework) k dispozici rozhraní API jsou definovány sestavení, která nainstaluje rozhraní .NET implementace v systému, což může zahrnovat aplikační rozhraní API (například ASP.NET, WinForms).</span><span class="sxs-lookup"><span data-stu-id="224bc-290">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="224bc-291">Rozhraní API pro balíček na základě cílové rozhraní (například .NET Standard a .NET Core), jsou definované balíčky nainstalované v aplikaci nebo knihovny.</span><span class="sxs-lookup"><span data-stu-id="224bc-291">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="224bc-292">V takovém případě cílovém Frameworku, který určuje implicitně metapackage, který odkazuje na všechny balíčky, které společně tvoří rozhraní.</span><span class="sxs-lookup"><span data-stu-id="224bc-292">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="224bc-293">V tématu [cílové rozhraní](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="224bc-293">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="224bc-294">TFM</span><span class="sxs-lookup"><span data-stu-id="224bc-294">TFM</span></span>

<span data-ttu-id="224bc-295">Cílový framework přezdívka.</span><span class="sxs-lookup"><span data-stu-id="224bc-295">Target framework moniker.</span></span>

<span data-ttu-id="224bc-296">Standardizovaná tokenu formát pro zadání cílové rozhraní aplikace .NET nebo knihovny.</span><span class="sxs-lookup"><span data-stu-id="224bc-296">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="224bc-297">Cílové rozhraní jsou obvykle odkazuje krátký název, například `net462`.</span><span class="sxs-lookup"><span data-stu-id="224bc-297">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="224bc-298">Dlouhá TFMs (například. NETFramework, verze = 4.6.2) existují, ale nejsou obecně používány k určení cílové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="224bc-298">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="224bc-299">V tématu [cílové rozhraní](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="224bc-299">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="224bc-300">UWP</span><span class="sxs-lookup"><span data-stu-id="224bc-300">UWP</span></span>

<span data-ttu-id="224bc-301">Univerzální platformy Windows.</span><span class="sxs-lookup"><span data-stu-id="224bc-301">Universal Windows Platform.</span></span>

<span data-ttu-id="224bc-302">Implementace rozhraní .NET, který se používá pro vytváření moderní, dotykovým ovládáním aplikace systému Windows a software pro Internet věcí (IoT).</span><span class="sxs-lookup"><span data-stu-id="224bc-302">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="224bc-303">Je určený ke sjednocení různé typy zařízení, které chcete zacílit, včetně počítače, tablety, phablets, telefony a i Xbox.</span><span class="sxs-lookup"><span data-stu-id="224bc-303">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phablets, phones, and even the Xbox.</span></span> <span data-ttu-id="224bc-304">UWP poskytuje mnoho služeb, jako je například centralizované app storu, prostředí provádění (AppContainer) a sadu rozhraní API systému Windows tak, aby používal místo Win32 (WinRT).</span><span class="sxs-lookup"><span data-stu-id="224bc-304">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="224bc-305">Aplikace může být napsané v jazyce C++, C#, VB.NET a JavaScript.</span><span class="sxs-lookup"><span data-stu-id="224bc-305">Apps can be written in C++, C#, VB.NET, and JavaScript.</span></span> <span data-ttu-id="224bc-306">Při použití jazyka C# a VB.NET, rozhraní API .NET jsou poskytovány .NET Core.</span><span class="sxs-lookup"><span data-stu-id="224bc-306">When using C# and VB.NET, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="224bc-307">Viz také</span><span class="sxs-lookup"><span data-stu-id="224bc-307">See also</span></span>

[<span data-ttu-id="224bc-308">Průvodce technologií .NET</span><span class="sxs-lookup"><span data-stu-id="224bc-308">.NET Guide</span></span>](index.md)  
[<span data-ttu-id="224bc-309">Průvodce rozhraním .NET Framework</span><span class="sxs-lookup"><span data-stu-id="224bc-309">.NET Framework Guide</span></span>](../framework/index.md)  
[<span data-ttu-id="224bc-310">.NET Core</span><span class="sxs-lookup"><span data-stu-id="224bc-310">.NET Core</span></span>](../core/index.md)  
[<span data-ttu-id="224bc-311">Přehled technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="224bc-311">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)  
[<span data-ttu-id="224bc-312">Přehled ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="224bc-312">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)  

