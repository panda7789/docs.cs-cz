---
title: Slovníček k technologii .NET
description: Zjistěte význam vybraných termínů použitých v dokumentaci k rozhraní .NET.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 590d44ac64bc2b86ed0a082ae5185cf60b28c36c
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291567"
---
# <a name="net-glossary"></a><span data-ttu-id="bccb4-103">Slovníček k technologii .NET</span><span class="sxs-lookup"><span data-stu-id="bccb4-103">.NET Glossary</span></span>

<span data-ttu-id="bccb4-104">Primárním cílem tohoto glosáře je objasnit významy vybraných termínů a akronymů, které se často objevují v dokumentaci .NET bez definic.</span><span class="sxs-lookup"><span data-stu-id="bccb4-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="bccb4-105">AOT</span><span class="sxs-lookup"><span data-stu-id="bccb4-105">AOT</span></span>

<span data-ttu-id="bccb4-106">Překladač dopředu.</span><span class="sxs-lookup"><span data-stu-id="bccb4-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="bccb4-107">Podobně jako [JIT](#jit), tento kompilátor také překládá [IL](#il) na strojový kód.</span><span class="sxs-lookup"><span data-stu-id="bccb4-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="bccb4-108">Na rozdíl od kompilace JIT kompilace AOT se stane před spuštěním aplikace a obvykle se provádí na jiném počítači.</span><span class="sxs-lookup"><span data-stu-id="bccb4-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="bccb4-109">Vzhledem k tomu, že řetězce nástrojů AOT nekompilují za běhu, nemusí minimalizovat čas strávený kompilací.</span><span class="sxs-lookup"><span data-stu-id="bccb4-109">Because AOT tool chains don't compile at runtime, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="bccb4-110">To znamená, že mohou trávit více času optimalizací.</span><span class="sxs-lookup"><span data-stu-id="bccb4-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="bccb4-111">Vzhledem k tomu, že kontext AOT je celá aplikace, kompilátor AOT také provádí propojení mezi moduly a analýzu celého programu, což znamená, že jsou dodržovány všechny odkazy a je vytvořen jeden spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="bccb4-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

<span data-ttu-id="bccb4-112">Viz [CoreRT](#corert) a [.NET Native](#net-native).</span><span class="sxs-lookup"><span data-stu-id="bccb4-112">See [CoreRT](#corert) and [.NET Native](#net-native).</span></span>

## <a name="aspnet"></a><span data-ttu-id="bccb4-113">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bccb4-113">ASP.NET</span></span>

<span data-ttu-id="bccb4-114">Původní ASP.NET implementaci, která je dodávána s rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bccb4-114">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="bccb4-115">Někdy je ASP.NET zastřešující termín, který odkazuje na obě ASP.NET implementace, včetně ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="bccb4-115">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="bccb4-116">Význam, který termín nese v dané instanci je určena kontextu.</span><span class="sxs-lookup"><span data-stu-id="bccb4-116">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="bccb4-117">Odkazovat na ASP.NET 4.x, pokud chcete, aby bylo jasné, že nepoužíváte ASP.NET znamená obě implementace.</span><span class="sxs-lookup"><span data-stu-id="bccb4-117">Refer to ASP.NET 4.x when you want to make it clear that you're not using ASP.NET to mean both implementations.</span></span>

<span data-ttu-id="bccb4-118">Viz [dokumentace k ASP.NET](/aspnet/#pivot=aspnet).</span><span class="sxs-lookup"><span data-stu-id="bccb4-118">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="bccb4-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bccb4-119">ASP.NET Core</span></span>

<span data-ttu-id="bccb4-120">Multiplatformní, vysoce výkonná implementace ASP.NET s otevřeným zdrojovým kódem postavená na jádru .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bccb4-120">A cross-platform, high-performance, open-source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="bccb4-121">Viz [dokumentace ASP.NET Core](/aspnet/#pivot=core).</span><span class="sxs-lookup"><span data-stu-id="bccb4-121">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="bccb4-122">sestavení</span><span class="sxs-lookup"><span data-stu-id="bccb4-122">assembly</span></span>

<span data-ttu-id="bccb4-123">Soubor *.dll.exe,*/*.exe* který může obsahovat kolekci souborů API, která mohou být volána aplikacemi nebo jinými sestaveními.</span><span class="sxs-lookup"><span data-stu-id="bccb4-123">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by applications or other assemblies.</span></span>

<span data-ttu-id="bccb4-124">Sestavení může obsahovat typy, jako jsou rozhraní, třídy, struktury, výčty a delegáty.</span><span class="sxs-lookup"><span data-stu-id="bccb4-124">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="bccb4-125">Sestavení ve složce *přihrádky* projektu jsou někdy *označovány*jako binární soubory .</span><span class="sxs-lookup"><span data-stu-id="bccb4-125">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="bccb4-126">Viz také [knihovna](#library).</span><span class="sxs-lookup"><span data-stu-id="bccb4-126">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="bccb4-127">CLR</span><span class="sxs-lookup"><span data-stu-id="bccb4-127">CLR</span></span>

<span data-ttu-id="bccb4-128">Běžný jazyk Runtime.</span><span class="sxs-lookup"><span data-stu-id="bccb4-128">Common Language Runtime.</span></span>

<span data-ttu-id="bccb4-129">Přesný význam závisí na kontextu, ale common language runtime obvykle odkazuje na runtime rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bccb4-129">The exact meaning depends on the context, but Common Language Runtime usually refers to the runtime of .NET Framework.</span></span> <span data-ttu-id="bccb4-130">CLR zpracovává přidělení paměti a správu.</span><span class="sxs-lookup"><span data-stu-id="bccb4-130">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="bccb4-131">CLR je také virtuální počítač, který nejen spouští aplikace, ale také generuje a kompiluje kód průběžně pomocí kompilátoru [JIT.](#jit)</span><span class="sxs-lookup"><span data-stu-id="bccb4-131">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a [JIT](#jit) compiler.</span></span> <span data-ttu-id="bccb4-132">Aktuální implementace Microsoft CLR je pouze systém Windows.</span><span class="sxs-lookup"><span data-stu-id="bccb4-132">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="bccb4-133">CoreCLR</span><span class="sxs-lookup"><span data-stu-id="bccb4-133">CoreCLR</span></span>

<span data-ttu-id="bccb4-134">.NET Core Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="bccb4-134">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="bccb4-135">Tento CLR je sestaven ze stejného základu kódu jako CLR.</span><span class="sxs-lookup"><span data-stu-id="bccb4-135">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="bccb4-136">Původně byl CoreCLR runtime programu Silverlight a byl navržen tak, aby běžel na více platformách, konkrétně na platformách Windows a OS X. CoreCLR je nyní součástí .NET Core a představuje zjednodušenou verzi CLR.</span><span class="sxs-lookup"><span data-stu-id="bccb4-136">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="bccb4-137">Je to stále [runtime napříč](#cross-platform) platformami, nyní včetně podpory mnoha distribucí Linuxu.</span><span class="sxs-lookup"><span data-stu-id="bccb4-137">It's still a [cross-platform](#cross-platform) runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="bccb4-138">CoreCLR je také virtuální počítač s možnostmi JIT a spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="bccb4-138">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="bccb4-139">CoreFX</span><span class="sxs-lookup"><span data-stu-id="bccb4-139">CoreFX</span></span>

<span data-ttu-id="bccb4-140">Knihovna základních tříd .NET Core (BCL)</span><span class="sxs-lookup"><span data-stu-id="bccb4-140">.NET Core Base Class Library (BCL)</span></span>

<span data-ttu-id="bccb4-141">Sada knihoven, které tvoří systém. \* (a v omezené míře\*Microsoft.) obory názvů.</span><span class="sxs-lookup"><span data-stu-id="bccb4-141">A set of libraries that comprise the System.\* (and to a limited extent Microsoft.\*) namespaces.</span></span> <span data-ttu-id="bccb4-142">BCL je obecný účel, nižší úroveň rámce, které vyšší úrovně aplikační architektury, jako je například ASP.NET Core, stavět na.</span><span class="sxs-lookup"><span data-stu-id="bccb4-142">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="bccb4-143">Zdrojový kód souboru .NET Core BCL je obsažen v [úložišti runtime .NET Core](https://github.com/dotnet/runtime).</span><span class="sxs-lookup"><span data-stu-id="bccb4-143">The source code of the .NET Core BCL is contained in the [.NET Core runtime repository](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="bccb4-144">Většina rozhraní API .NET Core jsou však k dispozici také v rozhraní .NET Framework, takže si můžete myslet CoreFX jako rozsvázu rozhraní .NET Framework BCL.</span><span class="sxs-lookup"><span data-stu-id="bccb4-144">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="bccb4-145">CoreRT</span><span class="sxs-lookup"><span data-stu-id="bccb4-145">CoreRT</span></span>

<span data-ttu-id="bccb4-146">Běhový čas jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="bccb4-146">.NET Core runtime.</span></span>

<span data-ttu-id="bccb4-147">Na rozdíl od CLR/CoreCLR, CoreRT není virtuální stroj, což znamená, že nezahrnuje zařízení pro generování a spouštění kódu on-the-fly, protože neobsahuje [JIT](#jit).</span><span class="sxs-lookup"><span data-stu-id="bccb4-147">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="bccb4-148">Zahrnuje však [GC](#gc) a schopnost identifikace typu běhu (RTTI) a reflexe.</span><span class="sxs-lookup"><span data-stu-id="bccb4-148">It does, however, include the [GC](#gc) and the ability for run-time type identification (RTTI) and reflection.</span></span> <span data-ttu-id="bccb4-149">Jeho typ systému je však navržen tak, aby metadata pro reflexi není vyžadována.</span><span class="sxs-lookup"><span data-stu-id="bccb4-149">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="bccb4-150">Nevyžadování metadat umožňuje mít řetězec nástrojů [AOT,](#aot) který může propojit nadbytečná metadata a (což je důležitější) identifikovat kód, který aplikace nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="bccb4-150">Not requiring metadata enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="bccb4-151">CoreRT je ve vývoji.</span><span class="sxs-lookup"><span data-stu-id="bccb4-151">CoreRT is in development.</span></span>

<span data-ttu-id="bccb4-152">Viz [Úvod do .NET Nativní a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span><span class="sxs-lookup"><span data-stu-id="bccb4-152">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span></span>

## <a name="cross-platform"></a><span data-ttu-id="bccb4-153">pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="bccb4-153">cross-platform</span></span>

<span data-ttu-id="bccb4-154">Schopnost vyvíjet a spouštět aplikaci, která může být použita na více různých operačních systémech, jako je Linux, Windows a iOS, aniž by bylo třeba přepisovat konkrétně pro každý z nich.</span><span class="sxs-lookup"><span data-stu-id="bccb4-154">The ability to develop and execute an application that can be used on multiple different operating systems, such as Linux, Windows, and iOS, without having to rewrite specifically for each one.</span></span> <span data-ttu-id="bccb4-155">To umožňuje opětovné použití kódu a konzistence mezi aplikacemi na různých platformách.</span><span class="sxs-lookup"><span data-stu-id="bccb4-155">This enables code reuse and consistency between applications on different platforms.</span></span>

## <a name="ecosystem"></a><span data-ttu-id="bccb4-156">Ekosystému</span><span class="sxs-lookup"><span data-stu-id="bccb4-156">ecosystem</span></span>

<span data-ttu-id="bccb4-157">Veškerý runtime software, vývojové nástroje a komunitní prostředky, které se používají k vytváření a spouštění aplikací pro danou technologii.</span><span class="sxs-lookup"><span data-stu-id="bccb4-157">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="bccb4-158">Termín ".NET ekosystém" se liší od podobných termínů, jako je například "zásobník.NET" v jeho začlenění aplikací a knihoven třetích stran.</span><span class="sxs-lookup"><span data-stu-id="bccb4-158">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="bccb4-159">Zde je příklad ve větě:</span><span class="sxs-lookup"><span data-stu-id="bccb4-159">Here's an example in a sentence:</span></span>

- <span data-ttu-id="bccb4-160">"Motivací [standardu .NET](#net-standard) standard je vytvořit větší jednotnost v ekosystému .NET."</span><span class="sxs-lookup"><span data-stu-id="bccb4-160">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span>

## <a name="framework"></a><span data-ttu-id="bccb4-161">rozhraní</span><span class="sxs-lookup"><span data-stu-id="bccb4-161">framework</span></span>

<span data-ttu-id="bccb4-162">Obecně platí, že komplexní kolekce api, která usnadňuje vývoj a nasazení aplikací, které jsou založeny na konkrétní technologii.</span><span class="sxs-lookup"><span data-stu-id="bccb4-162">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="bccb4-163">V tomto obecném smyslu jsou ASP.NET Core a Windows Forms příklady aplikačních architektur.</span><span class="sxs-lookup"><span data-stu-id="bccb4-163">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="bccb4-164">Viz také [knihovna](#library).</span><span class="sxs-lookup"><span data-stu-id="bccb4-164">See also [library](#library).</span></span>

<span data-ttu-id="bccb4-165">Slovo "rámec" má konkrétnější technický význam v následujících pojmech:</span><span class="sxs-lookup"><span data-stu-id="bccb4-165">The word "framework" has a more specific technical meaning in the following terms:</span></span>

- [<span data-ttu-id="bccb4-166">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="bccb4-166">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="bccb4-167">cílový rámec</span><span class="sxs-lookup"><span data-stu-id="bccb4-167">target framework</span></span>](#target-framework)
- [<span data-ttu-id="bccb4-168">TFM (zástupný název cílového rámce)</span><span class="sxs-lookup"><span data-stu-id="bccb4-168">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="bccb4-169">Ve stávající dokumentaci "framework" někdy odkazuje na [implementaci rozhraní .NET](#implementation-of-net).</span><span class="sxs-lookup"><span data-stu-id="bccb4-169">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="bccb4-170">Například článek může volat .NET Core rámec.</span><span class="sxs-lookup"><span data-stu-id="bccb4-170">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="bccb4-171">Plánujeme odstranit toto matoucí použití z dokumentace.</span><span class="sxs-lookup"><span data-stu-id="bccb4-171">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="bccb4-172">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="bccb4-172">GC</span></span>

<span data-ttu-id="bccb4-173">Popelář.</span><span class="sxs-lookup"><span data-stu-id="bccb4-173">Garbage collector.</span></span>

<span data-ttu-id="bccb4-174">Systém uvolňování paměti je implementací automatické správy paměti.</span><span class="sxs-lookup"><span data-stu-id="bccb4-174">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="bccb4-175">Gc uvolní paměť obsazenou objekty, které se již nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="bccb4-175">The GC frees memory occupied by objects that are no longer in use.</span></span>

<span data-ttu-id="bccb4-176">Viz [Uvolňování paměti](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="bccb4-176">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="bccb4-177">IL</span><span class="sxs-lookup"><span data-stu-id="bccb4-177">IL</span></span>

<span data-ttu-id="bccb4-178">Zprostředkující jazyk.</span><span class="sxs-lookup"><span data-stu-id="bccb4-178">Intermediate language.</span></span>

<span data-ttu-id="bccb4-179">Jazyky .NET vyšší úrovně, například C#, se kompilují do sady instrukcí bez hardwaru, která se nazývá Zprostředkující jazyk (IL).</span><span class="sxs-lookup"><span data-stu-id="bccb4-179">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="bccb4-180">IL se někdy označuje jako MSIL (Microsoft IL) nebo CIL (Common IL).</span><span class="sxs-lookup"><span data-stu-id="bccb4-180">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="bccb4-181">JIT</span><span class="sxs-lookup"><span data-stu-id="bccb4-181">JIT</span></span>

<span data-ttu-id="bccb4-182">Kompilátor just-in-time.</span><span class="sxs-lookup"><span data-stu-id="bccb4-182">Just-in-time compiler.</span></span>

<span data-ttu-id="bccb4-183">Podobně jako [AOT](#aot), tento kompilátor překládá [IL](#il) na strojový kód, který procesor chápe.</span><span class="sxs-lookup"><span data-stu-id="bccb4-183">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="bccb4-184">Na rozdíl od AOT kompilace JIT se provádí na vyžádání a provádí se na stejném počítači, který kód potřebuje ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="bccb4-184">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="bccb4-185">Vzhledem k tomu, že kompilace JIT dochází během provádění aplikace, čas kompilace je součástí běhu.</span><span class="sxs-lookup"><span data-stu-id="bccb4-185">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="bccb4-186">Kompilátory JIT tedy musí vyvážit čas strávený optimalizací kódu proti úsporám, které může výsledný kód vytvořit.</span><span class="sxs-lookup"><span data-stu-id="bccb4-186">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="bccb4-187">Ale JIT zná skutečný hardware a může osvobodit vývojáře od nutnosti doručovat různé implementace.</span><span class="sxs-lookup"><span data-stu-id="bccb4-187">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="bccb4-188">implementace rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="bccb4-188">implementation of .NET</span></span>

<span data-ttu-id="bccb4-189">Implementace rozhraní .NET zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="bccb4-189">An implementation of .NET includes:</span></span>

- <span data-ttu-id="bccb4-190">Jeden nebo více runtimes.</span><span class="sxs-lookup"><span data-stu-id="bccb4-190">One or more runtimes.</span></span> <span data-ttu-id="bccb4-191">Příklady: CLR, CoreCLR, CoreRT.</span><span class="sxs-lookup"><span data-stu-id="bccb4-191">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="bccb4-192">Knihovna tříd, která implementuje verzi standardu .NET a může obsahovat další rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="bccb4-192">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="bccb4-193">Příklady: .NET Framework Base Class Library, .NET Core Base Class Library.</span><span class="sxs-lookup"><span data-stu-id="bccb4-193">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="bccb4-194">Volitelně jeden nebo více rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="bccb4-194">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="bccb4-195">Příklady: ASP.NET, Windows Forms a WPF jsou zahrnuty v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bccb4-195">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="bccb4-196">Volitelně, vývojové nástroje.</span><span class="sxs-lookup"><span data-stu-id="bccb4-196">Optionally, development tools.</span></span> <span data-ttu-id="bccb4-197">Některé vývojové nástroje jsou sdíleny mezi více implementací.</span><span class="sxs-lookup"><span data-stu-id="bccb4-197">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="bccb4-198">Příklady implementací rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="bccb4-198">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="bccb4-199">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="bccb4-199">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="bccb4-200">.NET Core</span><span class="sxs-lookup"><span data-stu-id="bccb4-200">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="bccb4-201">Univerzální platforma Windows (UPW)</span><span class="sxs-lookup"><span data-stu-id="bccb4-201">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="bccb4-202">knihovna</span><span class="sxs-lookup"><span data-stu-id="bccb4-202">library</span></span>

<span data-ttu-id="bccb4-203">Kolekce api, která mohou být volána aplikacemi nebo jinými knihovnami.</span><span class="sxs-lookup"><span data-stu-id="bccb4-203">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="bccb4-204">Knihovna .NET se skládá z jednoho nebo více [sestavení](#assembly).</span><span class="sxs-lookup"><span data-stu-id="bccb4-204">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="bccb4-205">Slova knihovna a [rámec](#framework) jsou často používány synonymně.</span><span class="sxs-lookup"><span data-stu-id="bccb4-205">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="bccb4-206">Metabalíček</span><span class="sxs-lookup"><span data-stu-id="bccb4-206">metapackage</span></span>

<span data-ttu-id="bccb4-207">Balíček NuGet, který nemá vlastní knihovnu, ale je pouze seznam závislostí.</span><span class="sxs-lookup"><span data-stu-id="bccb4-207">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="bccb4-208">Zahrnuté balíčky můžete volitelně vytvořit rozhraní API pro cílové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bccb4-208">The included packages can optionally establish the API for a target framework.</span></span>

<span data-ttu-id="bccb4-209">Viz [Balíčky, metabalíčky a rámce](../core/packages.md)</span><span class="sxs-lookup"><span data-stu-id="bccb4-209">See [Packages, Metapackages, and Frameworks](../core/packages.md)</span></span>

## <a name="mono"></a><span data-ttu-id="bccb4-210">Mono</span><span class="sxs-lookup"><span data-stu-id="bccb4-210">Mono</span></span>

<span data-ttu-id="bccb4-211">Mono je implementace open [source, cross-platform](#cross-platform) .NET, která se používá hlavně v případě, že je vyžadován malý runtime.</span><span class="sxs-lookup"><span data-stu-id="bccb4-211">Mono is an open source, [cross-platform](#cross-platform) .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="bccb4-212">Je to runtime, který pohání aplikace Xamarin v systémech Android, Mac, iOS, tvOS a watchOS a je zaměřen především na aplikace, které vyžadují malé rozměry.</span><span class="sxs-lookup"><span data-stu-id="bccb4-212">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS, and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="bccb4-213">Podporuje všechny aktuálně publikované verze .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="bccb4-213">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="bccb4-214">Mono historicky implementoval větší API rozhraní .NET Framework a emuloval některé z nejpopulárnějších schopností na Unixu.</span><span class="sxs-lookup"><span data-stu-id="bccb4-214">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="bccb4-215">Někdy se používá ke spuštění aplikací .NET, které jsou závislé na těchto funkcích na Unixu.</span><span class="sxs-lookup"><span data-stu-id="bccb4-215">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="bccb4-216">Mono se obvykle používá s kompilátorem just-in-time, ale obsahuje také úplný statický kompilátor (kompilace dopředu času), který se používá na platformách, jako je iOS.</span><span class="sxs-lookup"><span data-stu-id="bccb4-216">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="bccb4-217">Další informace o mono, naleznete [v dokumentaci Mono](https://www.mono-project.com/docs/).</span><span class="sxs-lookup"><span data-stu-id="bccb4-217">To learn more about Mono, see the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="bccb4-218">.NET</span><span class="sxs-lookup"><span data-stu-id="bccb4-218">.NET</span></span>

<span data-ttu-id="bccb4-219">Zastřešující termín pro [standard .NET](#net-standard) a všechny implementace a [úlohy .NET.](#implementation-of-net)</span><span class="sxs-lookup"><span data-stu-id="bccb4-219">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="bccb4-220">Vždy plně kapitalizovaný, nikdy ".Net".</span><span class="sxs-lookup"><span data-stu-id="bccb4-220">Always fully capitalized, never ".Net".</span></span>

<span data-ttu-id="bccb4-221">Zobrazit [průvodce .NET](index.md)</span><span class="sxs-lookup"><span data-stu-id="bccb4-221">See the [.NET Guide](index.md)</span></span>

## <a name="net-core"></a><span data-ttu-id="bccb4-222">.NET Core</span><span class="sxs-lookup"><span data-stu-id="bccb4-222">.NET Core</span></span>

<span data-ttu-id="bccb4-223">Implementace rozhraní .NET s otevřeným zdrojovým kódem napříč platformami a vysokým výkonem.</span><span class="sxs-lookup"><span data-stu-id="bccb4-223">A cross-platform, high-performance, open-source implementation of .NET.</span></span> <span data-ttu-id="bccb4-224">Zahrnuje základní běžný jazyk Runtime (CoreCLR), core AOT Runtime (CoreRT, ve vývoji), základní základní třídy knihovny a základní sdk.</span><span class="sxs-lookup"><span data-stu-id="bccb4-224">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="bccb4-225">Viz [jádro .NET](../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="bccb4-225">See [.NET Core](../core/index.md).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="bccb4-226">Rozhraní příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="bccb4-226">.NET Core CLI</span></span>

<span data-ttu-id="bccb4-227">Řetězec nástrojů pro různé platformy pro vývoj aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bccb4-227">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="bccb4-228">Viz [rozhraní CLI jádra .NET](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="bccb4-228">See [.NET Core CLI](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="bccb4-229">Sada .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="bccb4-229">.NET Core SDK</span></span>

<span data-ttu-id="bccb4-230">Sada knihoven a nástrojů, které vývojářům umožňují vytvářet základní aplikace a knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="bccb4-230">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="bccb4-231">Zahrnuje [rozhraní příkazového příkazu .NET Core](#net-core-cli) pro vytváření aplikací, knihovny .NET Core a modul runtime pro vytváření a spouštění aplikací a spustitelný soubor dotnet (*dotnet.exe),* který spouští příkazy příkazového příkazu příkazového příkazu a spouští aplikace.</span><span class="sxs-lookup"><span data-stu-id="bccb4-231">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="bccb4-232">Viz [přehled sady .NET Core SDK](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="bccb4-232">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="bccb4-233">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="bccb4-233">.NET Framework</span></span>

<span data-ttu-id="bccb4-234">Implementace rozhraní .NET, která běží pouze v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="bccb4-234">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="bccb4-235">Zahrnuje clr (Common Language Runtime), knihovnu základních tříd a knihovny architektury aplikací, jako jsou ASP.NET, Windows Forms a WPF.</span><span class="sxs-lookup"><span data-stu-id="bccb4-235">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="bccb4-236">Viz [Průvodce architekturou .NET](../framework/index.yml).</span><span class="sxs-lookup"><span data-stu-id="bccb4-236">See [.NET Framework Guide](../framework/index.yml).</span></span>

## <a name="net-native"></a><span data-ttu-id="bccb4-237">.NET Native</span><span class="sxs-lookup"><span data-stu-id="bccb4-237">.NET Native</span></span>

<span data-ttu-id="bccb4-238">Řetěz kompilátoru nástroje, který vytváří nativní kód dopředu na čas (AOT), na rozdíl od just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="bccb4-238">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="bccb4-239">Kompilace se děje na počítači vývojáře podobné způsobu, jakým funguje kompilátor jazyka C++ a propojovací program.</span><span class="sxs-lookup"><span data-stu-id="bccb4-239">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="bccb4-240">Odebere nepoužívaný kód a stráví více času optimalizací.</span><span class="sxs-lookup"><span data-stu-id="bccb4-240">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="bccb4-241">Extrahuje kód z knihoven a slučuje je do spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="bccb4-241">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="bccb4-242">Výsledkem je jeden modul, který představuje celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bccb4-242">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="bccb4-243">UPW byl první aplikační rámec podporovaný .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bccb4-243">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="bccb4-244">Nyní podporujeme vytváření nativních konzolových aplikací pro Windows, macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="bccb4-244">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="bccb4-245">Viz [Úvod do .NET Nativní a CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="bccb4-245">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="bccb4-246">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="bccb4-246">.NET Standard</span></span>

<span data-ttu-id="bccb4-247">Formální specifikace rozhraní API .NET, které jsou k dispozici v každé implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="bccb4-247">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="bccb4-248">Specifikace standardu .NET se někdy nazývá knihovna v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="bccb4-248">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="bccb4-249">Vzhledem k tomu, že knihovna obsahuje implementace rozhraní API, nikoli pouze specifikace (rozhraní), je zavádějící volat .NET Standard jako "knihovnu".</span><span class="sxs-lookup"><span data-stu-id="bccb4-249">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="bccb4-250">Toto použití plánujeme vyloučit z dokumentace, s výjimkou odkazu na název`NETStandard.Library`metabalíčku .NET Standard ( ).</span><span class="sxs-lookup"><span data-stu-id="bccb4-250">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="bccb4-251">Viz [standard .NET](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="bccb4-251">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="bccb4-252">Ngen</span><span class="sxs-lookup"><span data-stu-id="bccb4-252">NGEN</span></span>

<span data-ttu-id="bccb4-253">Nativní (image) generace.</span><span class="sxs-lookup"><span data-stu-id="bccb4-253">Native (image) generation.</span></span>

<span data-ttu-id="bccb4-254">Tuto technologii si můžete myslet jako trvalý kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="bccb4-254">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="bccb4-255">Obvykle zkompiluje kód na počítači, kde je kód spuštěn, ale kompilace obvykle dochází v době instalace.</span><span class="sxs-lookup"><span data-stu-id="bccb4-255">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="bccb4-256">Balíček</span><span class="sxs-lookup"><span data-stu-id="bccb4-256">package</span></span>

<span data-ttu-id="bccb4-257">Balíček &mdash; NuGet nebo &mdash; pouze balíček je *soubor ZIP* s jedním nebo více sestaveními se stejným názvem spolu s dalšími metadaty, jako je například jméno autora.</span><span class="sxs-lookup"><span data-stu-id="bccb4-257">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="bccb4-258">Soubor *ZIP* má příponu *.nupkg* a může obsahovat datové zdroje, například soubory *DLL* a *soubory XML,* pro použití s více cílovými rozhraními a verzemi.</span><span class="sxs-lookup"><span data-stu-id="bccb4-258">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="bccb4-259">Při instalaci v aplikaci nebo knihovně jsou příslušné datové zdroje vybrány na základě cílového rozhraní určeného aplikací nebo knihovnou.</span><span class="sxs-lookup"><span data-stu-id="bccb4-259">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="bccb4-260">Datové zdroje, které definují rozhraní, jsou ve složce *ref* a datové zdroje, které definují implementaci, jsou ve složce *lib.*</span><span class="sxs-lookup"><span data-stu-id="bccb4-260">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="bccb4-261">platforma</span><span class="sxs-lookup"><span data-stu-id="bccb4-261">platform</span></span>

<span data-ttu-id="bccb4-262">Operační systém a hardware, na kterých běží, jako jsou Windows, macOS, Linux, iOS a Android.</span><span class="sxs-lookup"><span data-stu-id="bccb4-262">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="bccb4-263">Zde jsou příklady použití ve větách:</span><span class="sxs-lookup"><span data-stu-id="bccb4-263">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="bccb4-264">".NET Core je implementace napříč platformami rozhraní .NET."</span><span class="sxs-lookup"><span data-stu-id="bccb4-264">".NET Core is a cross-platform implementation of .NET."</span></span>
- <span data-ttu-id="bccb4-265">"PcL profily představují platformy společnosti Microsoft, zatímco standard .NET je agnostik na platformě."</span><span class="sxs-lookup"><span data-stu-id="bccb4-265">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="bccb4-266">Dokumentace .NET často používá ".NET platforma" znamenat buď implementaci .NET nebo zásobníku .NET včetně všech implementací.</span><span class="sxs-lookup"><span data-stu-id="bccb4-266">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="bccb4-267">Obě tato použití mají tendenci se zaměňovat s primárním (OS / hardware), takže plánujeme odstranit tato použití z dokumentace.</span><span class="sxs-lookup"><span data-stu-id="bccb4-267">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="bccb4-268">modul runtime</span><span class="sxs-lookup"><span data-stu-id="bccb4-268">runtime</span></span>

<span data-ttu-id="bccb4-269">Prostředí spuštění spravovaného programu.</span><span class="sxs-lookup"><span data-stu-id="bccb4-269">The execution environment for a managed program.</span></span>

<span data-ttu-id="bccb4-270">Operační systém je součástí runtime prostředí, ale není součástí běhu .NET.</span><span class="sxs-lookup"><span data-stu-id="bccb4-270">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="bccb4-271">Zde jsou některé příklady runtimes rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="bccb4-271">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="bccb4-272">Common Language Runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="bccb4-272">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="bccb4-273">Základní běžný jazyk Runtime (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="bccb4-273">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="bccb4-274">.NET Nativní (pro UPW)</span><span class="sxs-lookup"><span data-stu-id="bccb4-274">.NET Native (for UWP)</span></span>
- <span data-ttu-id="bccb4-275">Mono runtime</span><span class="sxs-lookup"><span data-stu-id="bccb4-275">Mono runtime</span></span>

<span data-ttu-id="bccb4-276">Dokumentace .NET někdy používá "runtime" znamenat implementaci .NET.</span><span class="sxs-lookup"><span data-stu-id="bccb4-276">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="bccb4-277">Například v následujícívěti "runtime" by měl být nahrazen "implementace":</span><span class="sxs-lookup"><span data-stu-id="bccb4-277">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="bccb4-278">"Různé runtimes rozhraní .NET implementují konkrétní verze standardu .NET).</span><span class="sxs-lookup"><span data-stu-id="bccb4-278">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="bccb4-279">"Knihovny, které jsou určeny ke spuštění na více runtimes by měl cílit na tento rámec."</span><span class="sxs-lookup"><span data-stu-id="bccb4-279">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="bccb4-280">(s odkazem na standard .NET)</span><span class="sxs-lookup"><span data-stu-id="bccb4-280">(referring to .NET Standard)</span></span>
- <span data-ttu-id="bccb4-281">"Různé runtimes rozhraní .NET implementují konkrétní verze standardu .NET.</span><span class="sxs-lookup"><span data-stu-id="bccb4-281">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="bccb4-282">…</span><span class="sxs-lookup"><span data-stu-id="bccb4-282">…</span></span> <span data-ttu-id="bccb4-283">Každá verze runtime rozhraní .NET inzeruje nejvyšší verzi .NET Standard, kterou podporuje ..."</span><span class="sxs-lookup"><span data-stu-id="bccb4-283">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="bccb4-284">Plánujeme eliminovat toto nekonzistentní použití.</span><span class="sxs-lookup"><span data-stu-id="bccb4-284">We plan to eliminate this inconsistent usage.</span></span>

## <a name="stack"></a><span data-ttu-id="bccb4-285">stack</span><span class="sxs-lookup"><span data-stu-id="bccb4-285">stack</span></span>

<span data-ttu-id="bccb4-286">Sada programovacích technologií, které se používají společně k vytváření a spouštění aplikací.</span><span class="sxs-lookup"><span data-stu-id="bccb4-286">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="bccb4-287">"Zásobník rozhraní .NET" odkazuje na standard .NET a všechny implementace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="bccb4-287">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="bccb4-288">Frázi "zásobník .NET" může odkazovat na jednu implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="bccb4-288">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span>

## <a name="target-framework"></a><span data-ttu-id="bccb4-289">cílový rámec</span><span class="sxs-lookup"><span data-stu-id="bccb4-289">target framework</span></span>

<span data-ttu-id="bccb4-290">Kolekce rozhraní API, na které závisí aplikace nebo knihovna .NET.</span><span class="sxs-lookup"><span data-stu-id="bccb4-290">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="bccb4-291">Aplikace nebo knihovna může cílit na verzi rozhraní .NET Standard (například .NET Standard 2.0), což je specifikace pro standardizovanou sadu rozhraní API ve všech implementacích rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="bccb4-291">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="bccb4-292">Aplikace nebo knihovna může také cílit na verzi konkrétní implementace rozhraní .NET, v takovém případě získá přístup k rozhraním API specifické pro implementaci.</span><span class="sxs-lookup"><span data-stu-id="bccb4-292">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="bccb4-293">Například aplikace, která cílí na Xamarin.iOS získá přístup k obálky rozhraní API poskytované Xamarin.</span><span class="sxs-lookup"><span data-stu-id="bccb4-293">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="bccb4-294">Pro některé cílové architektury (například rozhraní .NET Framework) jsou dostupná rozhraní API definována sestaveními, která implementace .NET nainstaluje do systému, což může zahrnovat rozhraní API rozhraní API rozhraní ap (například ASP.NET, WinForms).</span><span class="sxs-lookup"><span data-stu-id="bccb4-294">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="bccb4-295">Pro cílové architektury založené na balíčcích (například .NET Standard a .NET Core) jsou rozhraní API architektury definována balíčky nainstalovanými v aplikaci nebo knihovně.</span><span class="sxs-lookup"><span data-stu-id="bccb4-295">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="bccb4-296">V takovém případě cílový rámec implicitně určuje metabalíček, který odkazuje na všechny balíčky, které společně tvoří rámec.</span><span class="sxs-lookup"><span data-stu-id="bccb4-296">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="bccb4-297">Viz [Cílové rámce](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="bccb4-297">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="bccb4-298">Tfm</span><span class="sxs-lookup"><span data-stu-id="bccb4-298">TFM</span></span>

<span data-ttu-id="bccb4-299">Zástupný název rozhraní target.</span><span class="sxs-lookup"><span data-stu-id="bccb4-299">Target framework moniker.</span></span>

<span data-ttu-id="bccb4-300">Standardizovaný formát tokenu pro určení cílového rozhraní aplikace nebo knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="bccb4-300">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="bccb4-301">Cílové architektury jsou obvykle odkazovány krátkým názvem, například `net462`.</span><span class="sxs-lookup"><span data-stu-id="bccb4-301">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="bccb4-302">Dlouhodobé TFM (například . NETFramework,Version=4.6.2) existují, ale obecně se nepoužívají k určení cílového rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bccb4-302">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="bccb4-303">Viz [Cílové rámce](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="bccb4-303">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="bccb4-304">UWP</span><span class="sxs-lookup"><span data-stu-id="bccb4-304">UWP</span></span>

<span data-ttu-id="bccb4-305">Univerzální platforma Windows.</span><span class="sxs-lookup"><span data-stu-id="bccb4-305">Universal Windows Platform.</span></span>

<span data-ttu-id="bccb4-306">Implementace rozhraní .NET, která se používá pro vytváření moderních aplikací a softwaru systému Windows s podporou dotykového ovládání pro Internet věcí (IoT).</span><span class="sxs-lookup"><span data-stu-id="bccb4-306">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="bccb4-307">Je navržen tak, aby sjednocovat různé typy zařízení, které můžete chtít cílit, včetně počítačů, tabletů, telefonů, a dokonce i Xbox.</span><span class="sxs-lookup"><span data-stu-id="bccb4-307">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phones, and even the Xbox.</span></span> <span data-ttu-id="bccb4-308">Upwp poskytuje mnoho služeb, jako je například centralizované úložiště aplikací, spuštění prostředí (AppContainer) a sadu windows API pro použití namísto Win32 (WinRT).</span><span class="sxs-lookup"><span data-stu-id="bccb4-308">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="bccb4-309">Aplikace lze psát v jazycích C++, C#, Visual Basic a JavaScript.</span><span class="sxs-lookup"><span data-stu-id="bccb4-309">Apps can be written in C++, C#, Visual Basic, and JavaScript.</span></span> <span data-ttu-id="bccb4-310">Při použití jazyka C# a jazyka Visual Basic jsou rozhraní API .NET poskytována rozhraním .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bccb4-310">When using C# and Visual Basic, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="bccb4-311">Viz také</span><span class="sxs-lookup"><span data-stu-id="bccb4-311">See also</span></span>

- [<span data-ttu-id="bccb4-312">Průvodce rozhraním .NET</span><span class="sxs-lookup"><span data-stu-id="bccb4-312">.NET Guide</span></span>](index.md)
- [<span data-ttu-id="bccb4-313">Průvodce rozhraním .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bccb4-313">.NET Framework Guide</span></span>](../framework/index.yml)
- [<span data-ttu-id="bccb4-314">.NET Core</span><span class="sxs-lookup"><span data-stu-id="bccb4-314">.NET Core</span></span>](../core/index.md)
- [<span data-ttu-id="bccb4-315">přehled ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bccb4-315">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)
- [<span data-ttu-id="bccb4-316">ASP.NET základní přehled</span><span class="sxs-lookup"><span data-stu-id="bccb4-316">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)
