---
title: .NET – Glosář
description: Přečtěte si významu vybraných termínů používaných v dokumentaci k rozhraní .NET.
author: tdykstra
ms.author: tdykstra
ms.date: 07/08/2017
ms.technology: dotnet-standard
ms.openlocfilehash: 11fad691021ec897348177c67134750e72b4ff7c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44062959"
---
# <a name="net-glossary"></a><span data-ttu-id="54407-103">.NET – Glosář</span><span class="sxs-lookup"><span data-stu-id="54407-103">.NET Glossary</span></span>

<span data-ttu-id="54407-104">Hlavním cílem tento glosář je objasnit význam vybrané podmínky a zkratky, které se často zobrazují v dokumentaci k .NET bez definic.</span><span class="sxs-lookup"><span data-stu-id="54407-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="54407-105">AOT</span><span class="sxs-lookup"><span data-stu-id="54407-105">AOT</span></span>

<span data-ttu-id="54407-106">Kompilátor ahead of time.</span><span class="sxs-lookup"><span data-stu-id="54407-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="54407-107">Podobně jako [JIT](#jit), tento kompilátor se také přeloží [IL](#il) do strojového kódu.</span><span class="sxs-lookup"><span data-stu-id="54407-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="54407-108">Na rozdíl od kompilace JIT kompilace AOT se stane, než aplikace spouští a se obvykle provádí v jiném počítači.</span><span class="sxs-lookup"><span data-stu-id="54407-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="54407-109">Protože řetězce nástrojů AOT není kompilaci za běhu, nemají minimalizovat čas strávený kompilaci.</span><span class="sxs-lookup"><span data-stu-id="54407-109">Because AOT tool chains don't compile at runtime, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="54407-110">To znamená, že může věnovat víc času optimalizace.</span><span class="sxs-lookup"><span data-stu-id="54407-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="54407-111">Protože kontextu AOT celé aplikace, provádí kompilátor AOT také propojení mezi moduly a analýzu celého programu, což znamená, že jsou všechny odkazy a a je vytvořen jeden spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="54407-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

## <a name="aspnet"></a><span data-ttu-id="54407-112">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="54407-112">ASP.NET</span></span> 

<span data-ttu-id="54407-113">Původní implementace technologie ASP.NET, která se dodává s rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54407-113">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="54407-114">Někdy je technologie ASP.NET se o zastřešující pojem, který odkazuje na obou implementacích technologie ASP.NET, včetně ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="54407-114">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="54407-115">Význam, který představuje výraz v jakékoli dané instance se určuje podle kontextu.</span><span class="sxs-lookup"><span data-stu-id="54407-115">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="54407-116">Odkazovat na technologii ASP.NET 4.x, pokud chcete, aby bylo jasné, které nejsou pomocí technologie ASP.NET k označení obou implementacích.</span><span class="sxs-lookup"><span data-stu-id="54407-116">Refer to ASP.NET 4.x when you want to make it clear that you’re not using ASP.NET to mean both implementations.</span></span> 

<span data-ttu-id="54407-117">Zobrazit [dokumentace k ASP.NET](/aspnet/#pivot=aspnet).</span><span class="sxs-lookup"><span data-stu-id="54407-117">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="54407-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="54407-118">ASP.NET Core</span></span>

<span data-ttu-id="54407-119">Platformově univerzální, vysoce výkonná open source implementace technologie ASP.NET založená na rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="54407-119">A cross-platform, high-performance, open source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="54407-120">Zobrazit [dokumentace k ASP.NET Core](/aspnet/#pivot=core).</span><span class="sxs-lookup"><span data-stu-id="54407-120">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="54407-121">sestavení</span><span class="sxs-lookup"><span data-stu-id="54407-121">assembly</span></span>

<span data-ttu-id="54407-122">A *.dll*/*.exe* soubor, který může obsahovat sadu rozhraní API, která je možné vyvolat v aplikacích nebo jiná sestavení.</span><span class="sxs-lookup"><span data-stu-id="54407-122">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by apps or other assemblies.</span></span>

<span data-ttu-id="54407-123">Sestavení může obsahovat typy, jako jsou rozhraní, třídy, struktury, výčty a delegáti.</span><span class="sxs-lookup"><span data-stu-id="54407-123">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="54407-124">Sestavení v projektu *bin* složky jsou někdy označovány jako *binární soubory*.</span><span class="sxs-lookup"><span data-stu-id="54407-124">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="54407-125">Viz také [knihovny](#library).</span><span class="sxs-lookup"><span data-stu-id="54407-125">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="54407-126">CLR</span><span class="sxs-lookup"><span data-stu-id="54407-126">CLR</span></span>

<span data-ttu-id="54407-127">Modul Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="54407-127">Common Language Runtime.</span></span>

<span data-ttu-id="54407-128">Přesné význam závisí na kontextu, ale to se obvykle odkazuje na modul runtime rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54407-128">The exact meaning depends on the context, but this usually refers to the runtime of the .NET Framework.</span></span> <span data-ttu-id="54407-129">Modul CLR zpracovává přidělení paměti a správu.</span><span class="sxs-lookup"><span data-stu-id="54407-129">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="54407-130">Modul CLR je také virtuální počítač, který nejen spustí aplikace, ale také vygeneruje a zkompiluje kód v běhu pomocí kompilátoru JIT.</span><span class="sxs-lookup"><span data-stu-id="54407-130">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a JIT compiler.</span></span> <span data-ttu-id="54407-131">Aktuální implementace Microsoft CLR je jenom pro Windows.</span><span class="sxs-lookup"><span data-stu-id="54407-131">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="54407-132">CoreCLR</span><span class="sxs-lookup"><span data-stu-id="54407-132">CoreCLR</span></span>

<span data-ttu-id="54407-133">.NET core CLR.</span><span class="sxs-lookup"><span data-stu-id="54407-133">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="54407-134">Tato CLR je sestaven z základní jako CLR stejný kód.</span><span class="sxs-lookup"><span data-stu-id="54407-134">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="54407-135">Původně CoreCLR byl modul runtime technologie Silverlight a byl navržen pro spouštění na více platforem, konkrétně Windows a OS X. CoreCLR je teď součástí sady .NET Core a představuje zjednodušenou verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="54407-135">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="54407-136">Je stále modulu runtime napříč platformami, nyní včetně podpory pro řadu distribucí systému Linux.</span><span class="sxs-lookup"><span data-stu-id="54407-136">It's still a cross platform runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="54407-137">CoreCLR je také virtuální počítač s možností spouštění JIT a kód.</span><span class="sxs-lookup"><span data-stu-id="54407-137">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="54407-138">CoreFX</span><span class="sxs-lookup"><span data-stu-id="54407-138">CoreFX</span></span>

<span data-ttu-id="54407-139">Knihovna základních tříd .NET core (BCL)</span><span class="sxs-lookup"><span data-stu-id="54407-139">.NET Core Base Class Library (BCL)</span></span>

<span data-ttu-id="54407-140">Oborech názvů sadu knihoven, které tvoří System.\* (a do jisté míry oborů Microsoft.\*).</span><span class="sxs-lookup"><span data-stu-id="54407-140">A set of libraries that comprise the System.\* (and to a limited extent  Microsoft.\*) namespaces.</span></span> <span data-ttu-id="54407-141">Obecné rozhraní framework nižší úrovně, která vycházejí vyšší úrovně aplikačních architektur, jako je ASP.NET Core, je BCL.</span><span class="sxs-lookup"><span data-stu-id="54407-141">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="54407-142">Zdrojový kód .NET Core BCL je součástí [CoreFX úložiště](https://github.com/dotnet/corefx).</span><span class="sxs-lookup"><span data-stu-id="54407-142">The source code of the .NET Core BCL is contained in the [CoreFX repository](https://github.com/dotnet/corefx).</span></span> <span data-ttu-id="54407-143">Většina rozhraní API .NET Core jsou však také k dispozici v rozhraní .NET Framework, tak CoreFX si můžete představit jako fork BCL rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54407-143">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="54407-144">CoreRT</span><span class="sxs-lookup"><span data-stu-id="54407-144">CoreRT</span></span>

<span data-ttu-id="54407-145">Modul runtime .NET core.</span><span class="sxs-lookup"><span data-stu-id="54407-145">.NET Core runtime.</span></span>

<span data-ttu-id="54407-146">Na rozdíl od CLR/CoreCLR, CoreRT není virtuální počítač, což znamená, že neobsahuje funkce pro generování a spuštění kódu v běhu, protože neobsahuje [JIT](#jit).</span><span class="sxs-lookup"><span data-stu-id="54407-146">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="54407-147">, Ale patří [GC](#gc) a možnost identifikace typu modulu runtime (RTTI) a reflexe.</span><span class="sxs-lookup"><span data-stu-id="54407-147">It does, however, include the [GC](#gc) and the ability for runtime type identification (RTTI) and reflection.</span></span> <span data-ttu-id="54407-148">Ale jeho typ systému je navržený tak, aby metadata pro účely reflexe není povinné.</span><span class="sxs-lookup"><span data-stu-id="54407-148">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="54407-149">Díky tomu máte [AOT](#aot) nástroj řetězec, který můžete propojit tokeny nadbytečný metadat a (důležitější) identifikovat kód, který se aplikace nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="54407-149">This enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="54407-150">CoreRT je ve vývoji.</span><span class="sxs-lookup"><span data-stu-id="54407-150">CoreRT is in development.</span></span>

<span data-ttu-id="54407-151">Zobrazit [Úvod do .NET Native a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="54407-151">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="ecosystem"></a><span data-ttu-id="54407-152">Ekosystém</span><span class="sxs-lookup"><span data-stu-id="54407-152">ecosystem</span></span>

<span data-ttu-id="54407-153">Všechny softwarové modulu runtime, vývojové nástroje a komunitní zdroje, které se používají k vytváření a spouštění aplikací pro dané technologii.</span><span class="sxs-lookup"><span data-stu-id="54407-153">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="54407-154">Termín "Ekosystému .NET" se liší od podobných podmínek, jako je například "Zásobník .NET" v jeho zařazení aplikace třetích stran a knihoven.</span><span class="sxs-lookup"><span data-stu-id="54407-154">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="54407-155">Tady je příklad ve větě:</span><span class="sxs-lookup"><span data-stu-id="54407-155">Here's an example in a sentence:</span></span>

- <span data-ttu-id="54407-156">"Motivace za [.NET Standard](#net-standard) navázat větší sjednocení v ekosystému .NET."</span><span class="sxs-lookup"><span data-stu-id="54407-156">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span> 

## <a name="framework"></a><span data-ttu-id="54407-157">rozhraní</span><span class="sxs-lookup"><span data-stu-id="54407-157">framework</span></span>

<span data-ttu-id="54407-158">Obecně platí komplexní kolekce rozhraní API, který usnadňuje vývoj a nasazování aplikací, které jsou založeny na konkrétní technologii.</span><span class="sxs-lookup"><span data-stu-id="54407-158">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="54407-159">V tomto obecném smyslu tento pojem ASP.NET Core a Windows Forms jsou příkladem aplikačních architektur.</span><span class="sxs-lookup"><span data-stu-id="54407-159">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="54407-160">Viz také [knihovny](#library).</span><span class="sxs-lookup"><span data-stu-id="54407-160">See also [library](#library).</span></span>

<span data-ttu-id="54407-161">Slovo "rozhraní" má konkrétnější technické význam v následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="54407-161">The word "framework" has a more specific technical meaning in the following terms:</span></span>
* [<span data-ttu-id="54407-162">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="54407-162">.NET Framework</span></span>](#net-framework)
* [<span data-ttu-id="54407-163">Cílová architektura</span><span class="sxs-lookup"><span data-stu-id="54407-163">target framework</span></span>](#target-framework)
* [<span data-ttu-id="54407-164">TFM (moniker cílového rozhraní framework)</span><span class="sxs-lookup"><span data-stu-id="54407-164">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="54407-165">Ve stávající dokumentaci "rozhraní" někdy odkazuje [implementace .NET](#implementation-of-net).</span><span class="sxs-lookup"><span data-stu-id="54407-165">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="54407-166">Článek například může volat .NET Core rozhraní.</span><span class="sxs-lookup"><span data-stu-id="54407-166">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="54407-167">Plánujeme, chcete-li odstranit tento matoucí využití v dokumentaci ke službě.</span><span class="sxs-lookup"><span data-stu-id="54407-167">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="54407-168">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="54407-168">GC</span></span>

<span data-ttu-id="54407-169">Systém uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="54407-169">Garbage collector.</span></span>

<span data-ttu-id="54407-170">Uvolňování paměti je implementace Automatická správa paměti.</span><span class="sxs-lookup"><span data-stu-id="54407-170">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="54407-171">Uvolňování paměti uvolní paměť obsazena objekty, které jsou už používá.</span><span class="sxs-lookup"><span data-stu-id="54407-171">The GC frees memory occupied by objects that are no longer in use.</span></span> 

<span data-ttu-id="54407-172">Zobrazit [uvolňování](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="54407-172">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="54407-173">IL</span><span class="sxs-lookup"><span data-stu-id="54407-173">IL</span></span>

<span data-ttu-id="54407-174">Převodní jazyk.</span><span class="sxs-lookup"><span data-stu-id="54407-174">Intermediate language.</span></span>

<span data-ttu-id="54407-175">Vyšší úrovně jazyků .NET, jako je C#, kompilovat dolů sada instrukcí nezávislá na hardwaru, která se nazývá Intermediate Language (IL).</span><span class="sxs-lookup"><span data-stu-id="54407-175">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="54407-176">IL se někdy označuje jako jazyk MSIL (Microsoft IL) nebo soubor CIL (Common IL).</span><span class="sxs-lookup"><span data-stu-id="54407-176">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="54407-177">JIT</span><span class="sxs-lookup"><span data-stu-id="54407-177">JIT</span></span>

<span data-ttu-id="54407-178">Kompilátor Just-in-time.</span><span class="sxs-lookup"><span data-stu-id="54407-178">Just-in-time compiler.</span></span>

<span data-ttu-id="54407-179">Podobně jako [AOT](#aot), tento kompilátor překládá [IL](#il) do strojového kódu, která analyzuje procesoru.</span><span class="sxs-lookup"><span data-stu-id="54407-179">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="54407-180">Na rozdíl od kompilaci AOT kompilace JIT se stane, na vyžádání a provádí ve stejném počítači, který je potřeba spouštět kód.</span><span class="sxs-lookup"><span data-stu-id="54407-180">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="54407-181">Vzhledem k tomu, že během provádění dojde k JIT kompilaci, kompilace je součástí čas spuštění.</span><span class="sxs-lookup"><span data-stu-id="54407-181">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="54407-182">Kompilátory JIT tedy mít vyvážit dobu strávenou optimalizace kódu proti úspory, které mohou způsobit výsledný kód.</span><span class="sxs-lookup"><span data-stu-id="54407-182">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="54407-183">Ale zná skutečné hardwarové JIT a můžete uvolnit vývojáře od přitom nutné dodávat jedná o rozdílné implementace.</span><span class="sxs-lookup"><span data-stu-id="54407-183">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="54407-184">implementace rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="54407-184">implementation of .NET</span></span>

<span data-ttu-id="54407-185">Implementace .NET zahrnuje následující položky:</span><span class="sxs-lookup"><span data-stu-id="54407-185">An implementation of .NET includes the following:</span></span>

- <span data-ttu-id="54407-186">Jeden nebo více modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="54407-186">One or more runtimes.</span></span> <span data-ttu-id="54407-187">Příklady: CoreRT CLR, CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="54407-187">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="54407-188">Knihovna tříd, který implementuje na verzi .NET Standard a může taky obsahovat další rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="54407-188">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="54407-189">Příklady: Základní knihovny tříd .NET Framework, knihovně základních tříd .NET Core.</span><span class="sxs-lookup"><span data-stu-id="54407-189">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="54407-190">Volitelně můžete jeden nebo více aplikačních architektur.</span><span class="sxs-lookup"><span data-stu-id="54407-190">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="54407-191">Příklady: ASP.NET, Windows Forms a WPF jsou zahrnuty v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54407-191">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="54407-192">Volitelně můžete nástroje pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="54407-192">Optionally, development tools.</span></span> <span data-ttu-id="54407-193">Některé vývojové nástroje jsou sdíleny více implementací.</span><span class="sxs-lookup"><span data-stu-id="54407-193">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="54407-194">Příklady implementace .NET:</span><span class="sxs-lookup"><span data-stu-id="54407-194">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="54407-195">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="54407-195">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="54407-196">.NET Core</span><span class="sxs-lookup"><span data-stu-id="54407-196">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="54407-197">Univerzální platforma Windows (UPW)</span><span class="sxs-lookup"><span data-stu-id="54407-197">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="54407-198">knihovna</span><span class="sxs-lookup"><span data-stu-id="54407-198">library</span></span>

<span data-ttu-id="54407-199">Kolekce rozhraní API, která mohou být volány aplikací nebo jiné knihovny.</span><span class="sxs-lookup"><span data-stu-id="54407-199">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="54407-200">Knihovna .NET se skládá z jedné nebo více [sestavení](#assembly).</span><span class="sxs-lookup"><span data-stu-id="54407-200">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="54407-201">Knihovna slova a [framework](#framework) se často používají jako synonyma.</span><span class="sxs-lookup"><span data-stu-id="54407-201">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="54407-202">Microsoft.aspnetcore.all</span><span class="sxs-lookup"><span data-stu-id="54407-202">metapackage</span></span>

<span data-ttu-id="54407-203">Balíček NuGet, který nemá žádná knihovna samostatně, ale je pouze seznam závislostí.</span><span class="sxs-lookup"><span data-stu-id="54407-203">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="54407-204">Na zahrnuté balíčky můžete volitelně vytvořit rozhraní API pro cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="54407-204">The included packages can optionally establish the API for a target framework.</span></span>

<span data-ttu-id="54407-205">Zobrazit [balíčky, Metabalíčky a architektury](../core/packages.md)</span><span class="sxs-lookup"><span data-stu-id="54407-205">See [Packages, Metapackages and Frameworks](../core/packages.md)</span></span>

## <a name="mono"></a><span data-ttu-id="54407-206">Mono</span><span class="sxs-lookup"><span data-stu-id="54407-206">Mono</span></span>

<span data-ttu-id="54407-207">Mono je implementace .NET, který se používá hlavně při malý modul runtime je povinný.</span><span class="sxs-lookup"><span data-stu-id="54407-207">Mono is a .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="54407-208">Je modul runtime, který zajišťuje provoz aplikací v Xamarinu na Android, Mac, iOS, tvOS a watchOS a se zaměřuje především na aplikace, které vyžadují malé náklady.</span><span class="sxs-lookup"><span data-stu-id="54407-208">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="54407-209">Podporuje všechny aktuálně publikované verze .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="54407-209">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="54407-210">V minulosti Mono implementovaná větší API rozhraní .NET Framework a emulované některé z nejoblíbenějších funkcí v systému Unix.</span><span class="sxs-lookup"><span data-stu-id="54407-210">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="54407-211">Někdy se používá ke spouštění aplikací .NET, které využívají tyto funkce v systému Unix.</span><span class="sxs-lookup"><span data-stu-id="54407-211">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="54407-212">Mono se obvykle používá s kompilátorem za běhu, ale obsahuje taky celý statický kompilátor (ahead of time kompilace), který se používá na platformách, jako je iOS.</span><span class="sxs-lookup"><span data-stu-id="54407-212">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="54407-213">Další informace o Mono, najdete v článku [dokumentace Mono](https://www.mono-project.com/docs/).</span><span class="sxs-lookup"><span data-stu-id="54407-213">To learn more about Mono, see the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="54407-214">.NET</span><span class="sxs-lookup"><span data-stu-id="54407-214">.NET</span></span>

<span data-ttu-id="54407-215">Zastřešující pojem pro [.NET Standard](#net-standard) a všechny [implementace .NET](#implementation-of-net) a úlohy.</span><span class="sxs-lookup"><span data-stu-id="54407-215">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="54407-216">Vždy velkými písmeny, nikdy ".Net".</span><span class="sxs-lookup"><span data-stu-id="54407-216">Always capitalized, never ".Net".</span></span>

<span data-ttu-id="54407-217">Zobrazit [Průvodce technologií .NET](index.md)</span><span class="sxs-lookup"><span data-stu-id="54407-217">See the [.NET Guide](index.md)</span></span>

## <a name="net-core"></a><span data-ttu-id="54407-218">.NET Core</span><span class="sxs-lookup"><span data-stu-id="54407-218">.NET Core</span></span> 

<span data-ttu-id="54407-219">Napříč platformami, vysoce výkonná open source implementace .NET.</span><span class="sxs-lookup"><span data-stu-id="54407-219">A cross-platform, high-performance, open source implementation of .NET.</span></span> <span data-ttu-id="54407-220">Zahrnuje základní Common Language Runtime (CoreCLR), Core Runtime AOT (ve vývoji CoreRT), základní knihovny tříd Base a Core SDK.</span><span class="sxs-lookup"><span data-stu-id="54407-220">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="54407-221">Zobrazit [.NET Core](../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="54407-221">See [.NET Core](../core/index.md).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="54407-222">.NET core CLI</span><span class="sxs-lookup"><span data-stu-id="54407-222">.NET Core CLI</span></span>

<span data-ttu-id="54407-223">Multiplatformní sadu nástrojů pro vývoj aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="54407-223">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="54407-224">Zobrazit [nástroje rozhraní příkazového řádku (CLI) pro .NET Core](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="54407-224">See [.NET Core command-line interface (CLI) tools](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="54407-225">.NET core SDK</span><span class="sxs-lookup"><span data-stu-id="54407-225">.NET Core SDK</span></span>

<span data-ttu-id="54407-226">Sada knihovny a nástroje, které umožňují vývojářům vytvářet aplikace .NET Core a knihovny.</span><span class="sxs-lookup"><span data-stu-id="54407-226">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="54407-227">Zahrnuje [rozhraní příkazového řádku .NET Core](#net-core-cli) pro vývoj aplikací, knihoven .NET Core a modul runtime pro sestavování a spouštění aplikací a dotnet spustitelný soubor (*dotnet.exe*), který spouští příkazy rozhraní příkazového řádku a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="54407-227">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="54407-228">Zobrazit [Přehled sady SDK .NET Core](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="54407-228">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="54407-229">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="54407-229">.NET Framework</span></span>

<span data-ttu-id="54407-230">Implementace rozhraní .NET, na kterém běží pouze na Windows.</span><span class="sxs-lookup"><span data-stu-id="54407-230">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="54407-231">Zahrnuje Common Language Runtime (CLR), základní knihovny tříd a rozhraní framework knihovny aplikací, jako je ASP.NET, Windows Forms a WPF.</span><span class="sxs-lookup"><span data-stu-id="54407-231">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="54407-232">Zobrazit [rozhraní .NET Framework – průvodce](../framework/index.md).</span><span class="sxs-lookup"><span data-stu-id="54407-232">See [.NET Framework Guide](../framework/index.md).</span></span>

## <a name="net-native"></a><span data-ttu-id="54407-233">.NET Native</span><span class="sxs-lookup"><span data-stu-id="54407-233">.NET Native</span></span>

<span data-ttu-id="54407-234">Řetěz kompilátoru nástroj, který vytváří nativní kód ahead-of-time (AOT), na rozdíl od just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="54407-234">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="54407-235">Probíhá kompilace na počítači pro vývojáře podobným způsobem, jakým C++ kompilátor a propojovací program funguje.</span><span class="sxs-lookup"><span data-stu-id="54407-235">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="54407-236">Odebere nevyužité kódu a tráví víc času na jeho optimalizace.</span><span class="sxs-lookup"><span data-stu-id="54407-236">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="54407-237">Extrahuje z knihovny kódu a sloučí je do spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="54407-237">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="54407-238">Výsledkem je jeden modul, který představuje celé aplikace.</span><span class="sxs-lookup"><span data-stu-id="54407-238">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="54407-239">UPW se první aplikační platformu .NET Native nepodporují.</span><span class="sxs-lookup"><span data-stu-id="54407-239">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="54407-240">Nyní podporujeme sestavování nativních konzolové aplikace pro Windows, macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="54407-240">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="54407-241">Zobrazit [Úvod do .NET Native a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="54407-241">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="54407-242">.NET standard</span><span class="sxs-lookup"><span data-stu-id="54407-242">.NET Standard</span></span>

<span data-ttu-id="54407-243">Formální specifikaci rozhraní API pro .NET, které jsou dostupné v jednotlivých implementace .NET.</span><span class="sxs-lookup"><span data-stu-id="54407-243">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="54407-244">Specifikaci .NET Standard se někdy označuje jako knihovna v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="54407-244">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="54407-245">Protože knihovny zahrnuje implementace rozhraní API, nejen specifikace (rozhraní), je zavádějící pro volání .NET Standard "library".</span><span class="sxs-lookup"><span data-stu-id="54407-245">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="54407-246">Chcete-li odstranit tohle využívání v dokumentaci ke službě, s výjimkou v souvislosti s aplikací název .NET Standard Microsoft.aspnetcore.all plánujeme (`NETStandard.Library`).</span><span class="sxs-lookup"><span data-stu-id="54407-246">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="54407-247">Zobrazit [.NET Standard](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="54407-247">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="54407-248">NGEN</span><span class="sxs-lookup"><span data-stu-id="54407-248">NGEN</span></span>

<span data-ttu-id="54407-249">Generování nativního (obrázek).</span><span class="sxs-lookup"><span data-stu-id="54407-249">Native (image) generation.</span></span>

<span data-ttu-id="54407-250">Tuto technologii si lze představit jako trvalé kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="54407-250">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="54407-251">Obvykle zkompiluje kód na počítači, kde je kód spuštěn, ale kompilace obvykle dochází v době instalace.</span><span class="sxs-lookup"><span data-stu-id="54407-251">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="54407-252">Balíček</span><span class="sxs-lookup"><span data-stu-id="54407-252">package</span></span>

<span data-ttu-id="54407-253">Balíček NuGet &mdash; nebo právě balíčku &mdash; je *ZIP* soubor s minimálně jedno sestavení se stejným názvem, společně s další metadata, jako je například jméno autora.</span><span class="sxs-lookup"><span data-stu-id="54407-253">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="54407-254">*ZIP* soubor má *.nupkg* rozšíření a může obsahovat prostředky, jako například *.dll* soubory a *.xml* souborů pro použití s několika cílů architektury a verze.</span><span class="sxs-lookup"><span data-stu-id="54407-254">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="54407-255">Při instalaci v aplikaci nebo knihovny, jsou vybrány příslušné prostředky založené na cílové rozhraní určené aplikace nebo knihovna.</span><span class="sxs-lookup"><span data-stu-id="54407-255">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="54407-256">Prostředky, které definují rozhraní se nacházejí v *ref* složky a prostředky, které definují implementace *lib* složky.</span><span class="sxs-lookup"><span data-stu-id="54407-256">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="54407-257">platforma</span><span class="sxs-lookup"><span data-stu-id="54407-257">platform</span></span>

<span data-ttu-id="54407-258">Operační systém a hardware, který běží na serveru, jako je například Windows, macOS, Linux, iOS a Android.</span><span class="sxs-lookup"><span data-stu-id="54407-258">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="54407-259">Tady jsou příklady použití v věty:</span><span class="sxs-lookup"><span data-stu-id="54407-259">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="54407-260">".NET core je na více platforem implementace rozhraní .NET."</span><span class="sxs-lookup"><span data-stu-id="54407-260">".NET Core is a cross-platform implementation of .NET."</span></span> 
- <span data-ttu-id="54407-261">"PCL profily představují platformy Microsoft, zatímco .NET Standard je nezávislé na platformě."</span><span class="sxs-lookup"><span data-stu-id="54407-261">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="54407-262">Dokumentace k .NET často používá "Platformu .NET" rozumí buď implementace .NET nebo zásobník .NET, včetně všech implementace.</span><span class="sxs-lookup"><span data-stu-id="54407-262">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="54407-263">Obě tyto použití často zmatení s primární význam (operační systém a hardware), takže máme v plánu odstranění těchto použití v dokumentaci ke službě.</span><span class="sxs-lookup"><span data-stu-id="54407-263">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="54407-264">modul runtime</span><span class="sxs-lookup"><span data-stu-id="54407-264">runtime</span></span>

<span data-ttu-id="54407-265">Prostředí pro spuštění spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="54407-265">The execution environment for a managed program.</span></span>

<span data-ttu-id="54407-266">Operační systém je součástí prostředí modulu runtime, ale není součástí modulu runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="54407-266">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="54407-267">Tady je několik příkladů moduly runtime .NET:</span><span class="sxs-lookup"><span data-stu-id="54407-267">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="54407-268">Common Language Runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="54407-268">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="54407-269">Základní Common Language Runtime (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="54407-269">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="54407-270">.NET native (pro UPW)</span><span class="sxs-lookup"><span data-stu-id="54407-270">.NET Native (for UWP)</span></span>
- <span data-ttu-id="54407-271">Modul mono runtime</span><span class="sxs-lookup"><span data-stu-id="54407-271">Mono runtime</span></span>

<span data-ttu-id="54407-272">V dokumentaci k rozhraní .NET, někdy používá "runtime" jejich implementace .NET.</span><span class="sxs-lookup"><span data-stu-id="54407-272">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="54407-273">Například v následujícím věty "runtime" by měla být nahrazena "implementace":</span><span class="sxs-lookup"><span data-stu-id="54407-273">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="54407-274">"Různými moduly runtime .NET implementovat určité verze .NET Standard."</span><span class="sxs-lookup"><span data-stu-id="54407-274">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="54407-275">"Knihovny, které jsou určeny ke spuštění ve více modulů – runtime by měl cíl tohoto rozhraní."</span><span class="sxs-lookup"><span data-stu-id="54407-275">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="54407-276">(odkazující na .NET Standard)</span><span class="sxs-lookup"><span data-stu-id="54407-276">(referring to .NET Standard)</span></span>
- <span data-ttu-id="54407-277">"Různými moduly runtime .NET implementovat určité verze .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="54407-277">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="54407-278">…</span><span class="sxs-lookup"><span data-stu-id="54407-278">…</span></span> <span data-ttu-id="54407-279">Každá verze modulu runtime .NET inzeruje nejvyšší verze .NET Standard, kterou podporuje..."</span><span class="sxs-lookup"><span data-stu-id="54407-279">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="54407-280">Plánujeme, chcete-li odstranit tento nekonzistentní využití.</span><span class="sxs-lookup"><span data-stu-id="54407-280">We plan to eliminate this inconsistent usage.</span></span> 

## <a name="stack"></a><span data-ttu-id="54407-281">stack</span><span class="sxs-lookup"><span data-stu-id="54407-281">stack</span></span>

<span data-ttu-id="54407-282">Sada programování technologie, které se používají společně k vytváření a spouštění aplikací.</span><span class="sxs-lookup"><span data-stu-id="54407-282">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="54407-283">"Zásobník .NET" odkazuje na všechny implementace .NET a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="54407-283">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="54407-284">Fráze "zásobník .NET" mohou odkazovat na jednu implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="54407-284">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span> 

## <a name="target-framework"></a><span data-ttu-id="54407-285">Cílová architektura</span><span class="sxs-lookup"><span data-stu-id="54407-285">target framework</span></span>

<span data-ttu-id="54407-286">Kolekce rozhraní API, která aplikace .NET nebo knihovny se může spolehnout.</span><span class="sxs-lookup"><span data-stu-id="54407-286">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="54407-287">Aplikace nebo knihovny můžete cílení na verzi .NET Standard (například .NET Standard 2.0), což je specifikace pro standardizované sadu rozhraní API přes všechny implementace .NET.</span><span class="sxs-lookup"><span data-stu-id="54407-287">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="54407-288">Aplikace nebo knihovna můžete také cílení na verzi konkrétní implementace rozhraní .NET, ve které malá a velká písmena získá přístup k rozhraním API specifický pro implementaci.</span><span class="sxs-lookup"><span data-stu-id="54407-288">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="54407-289">Například aplikace, která se zaměřuje Xamarin.iOS získá přístup k rozhraní API pro zadaný Xamarin iOS obálky.</span><span class="sxs-lookup"><span data-stu-id="54407-289">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="54407-290">Pro některé cílové architektury (například rozhraní .NET Framework) k dispozici rozhraní API, které jsou definovány pomocí sestavení, která nainstaluje implementace .NET v systému, které mohou být aplikační rozhraní API (například ASP.NET, WinForms).</span><span class="sxs-lookup"><span data-stu-id="54407-290">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="54407-291">Na základě balíčku cílových rozhraní (například .NET Standard a .NET Core) jsou rozhraní API určené balíčky, které jsou nainstalovány v aplikaci nebo knihovny.</span><span class="sxs-lookup"><span data-stu-id="54407-291">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="54407-292">V takovém případě Cílová architektura, která určuje implicitně Microsoft.aspnetcore.all, který odkazuje na všechny balíčky, které společně tvoří rozhraní.</span><span class="sxs-lookup"><span data-stu-id="54407-292">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="54407-293">Zobrazit [platforem](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="54407-293">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="54407-294">TFM</span><span class="sxs-lookup"><span data-stu-id="54407-294">TFM</span></span>

<span data-ttu-id="54407-295">Moniker cílového rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="54407-295">Target framework moniker.</span></span>

<span data-ttu-id="54407-296">Token standardizovaný formát pro zadání cílové rozhraní framework aplikace .NET nebo knihovny.</span><span class="sxs-lookup"><span data-stu-id="54407-296">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="54407-297">Cílové architektury se obvykle odkazuje krátký název, jako například `net462`.</span><span class="sxs-lookup"><span data-stu-id="54407-297">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="54407-298">Dlouhá Tfm (například. NETFramework, verze = 4.6.2) existuje, ale nejsou obecně používá k určení rozhraní .NET framework.</span><span class="sxs-lookup"><span data-stu-id="54407-298">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="54407-299">Zobrazit [platforem](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="54407-299">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="54407-300">UWP</span><span class="sxs-lookup"><span data-stu-id="54407-300">UWP</span></span>

<span data-ttu-id="54407-301">Universal Windows Platform.</span><span class="sxs-lookup"><span data-stu-id="54407-301">Universal Windows Platform.</span></span>

<span data-ttu-id="54407-302">Implementace .NET, která je určená k vytváření moderních, dotykově ovládaný Windows aplikací a softwaru pro Internet věcí (IoT).</span><span class="sxs-lookup"><span data-stu-id="54407-302">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="54407-303">Je určený ke sjednocení různé typy zařízení, které můžete chtít zaměřit, včetně počítače, tablety, phablets, telefony a dokonce i Xbox.</span><span class="sxs-lookup"><span data-stu-id="54407-303">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phablets, phones, and even the Xbox.</span></span> <span data-ttu-id="54407-304">UPW poskytuje mnoho služeb, jako jsou centralizované app storu, spouštěcí prostředí (AppContainer) a sada rozhraní API Windows nahrazujícím Win32 (WinRT).</span><span class="sxs-lookup"><span data-stu-id="54407-304">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="54407-305">Aplikace může být napsané v jazyce C++, C#, VB.NET a JavaScript.</span><span class="sxs-lookup"><span data-stu-id="54407-305">Apps can be written in C++, C#, VB.NET, and JavaScript.</span></span> <span data-ttu-id="54407-306">Při použití jazyka C# a VB.NET, jsou k dispozici rozhraní API .NET pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="54407-306">When using C# and VB.NET, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="54407-307">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54407-307">See also</span></span>

- [<span data-ttu-id="54407-308">Průvodce technologií .NET</span><span class="sxs-lookup"><span data-stu-id="54407-308">.NET Guide</span></span>](index.md)  
- [<span data-ttu-id="54407-309">Průvodce rozhraním .NET Framework</span><span class="sxs-lookup"><span data-stu-id="54407-309">.NET Framework Guide</span></span>](../framework/index.md)  
- [<span data-ttu-id="54407-310">.NET Core</span><span class="sxs-lookup"><span data-stu-id="54407-310">.NET Core</span></span>](../core/index.md)  
- [<span data-ttu-id="54407-311">ASP.NET: Přehled</span><span class="sxs-lookup"><span data-stu-id="54407-311">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)  
- [<span data-ttu-id="54407-312">Přehled ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="54407-312">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)  
