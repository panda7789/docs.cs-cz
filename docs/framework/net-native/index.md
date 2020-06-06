---
title: Kompilování aplikací pomocí .NET Native
ms.date: 03/30/2017
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
ms.openlocfilehash: 1f176e81905fe68c6d740a13240fe814659a7a59
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128379"
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="187b4-102">Kompilování aplikací pomocí .NET Native</span><span class="sxs-lookup"><span data-stu-id="187b4-102">Compiling Apps with .NET Native</span></span>

<span data-ttu-id="187b4-103">.NET Native je předkompilační technologie pro sestavování a nasazování aplikací pro Windows, které jsou součástí sady Visual Studio 2015 a novějších verzí.</span><span class="sxs-lookup"><span data-stu-id="187b4-103">.NET Native is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="187b4-104">Automaticky zkompiluje vydanou verzi aplikací, které jsou napsány ve spravovaném kódu (C# nebo Visual Basic) a cílí na .NET Framework a Windows 10 do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="187b4-104">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>

<span data-ttu-id="187b4-105">Aplikace, které cílí na .NET Framework, jsou obvykle kompilovány do jazyka IL (Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="187b4-105">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="187b4-106">V době běhu překládá kompilátor JIT (just-in-time) IL na nativní kód.</span><span class="sxs-lookup"><span data-stu-id="187b4-106">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="187b4-107">Naproti tomu .NET Native zkompiluje aplikace pro Windows přímo do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="187b4-107">In contrast, .NET Native compiles Windows apps directly to native code.</span></span> <span data-ttu-id="187b4-108">Pro vývojáře to znamená:</span><span class="sxs-lookup"><span data-stu-id="187b4-108">For developers, this means:</span></span>

- <span data-ttu-id="187b4-109">Vaše aplikace se zaměřením na výkon nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="187b4-109">Your apps feature the performance of native code.</span></span> <span data-ttu-id="187b4-110">Výkon je obvykle nadřazený kódu, který je nejprve zkompilován do IL a poté zkompilován do nativního kódu kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="187b4-110">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span>

- <span data-ttu-id="187b4-111">Můžete pokračovat v programu v jazyce C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="187b4-111">You can continue to program in C# or Visual Basic.</span></span>

- <span data-ttu-id="187b4-112">Můžete nadále využívat prostředky poskytované .NET Framework, včetně knihovny tříd, automatické správy paměti a uvolňování paměti a zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="187b4-112">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>

<span data-ttu-id="187b4-113">Pro uživatele vašich aplikací .NET Native nabízí tyto výhody:</span><span class="sxs-lookup"><span data-stu-id="187b4-113">For users of your apps, .NET Native offers these advantages:</span></span>

- <span data-ttu-id="187b4-114">Rychlejší doba provádění většiny aplikací a scénářů.</span><span class="sxs-lookup"><span data-stu-id="187b4-114">Faster execution times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="187b4-115">Rychlejší časy spuštění většiny aplikací a scénářů.</span><span class="sxs-lookup"><span data-stu-id="187b4-115">Faster startup times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="187b4-116">Nízké náklady na nasazení a aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="187b4-116">Low deployment and update costs.</span></span>

- <span data-ttu-id="187b4-117">Optimalizované využití paměti aplikace.</span><span class="sxs-lookup"><span data-stu-id="187b4-117">Optimized app memory usage.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="187b4-118">Pro většinu aplikací a scénářů nabízí .NET Native výrazně rychlejší dobu spuštění a špičkový výkon v porovnání s aplikací zkompilovanou do IL nebo do image NGEN.</span><span class="sxs-lookup"><span data-stu-id="187b4-118">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="187b4-119">Výsledky se ale můžou lišit.</span><span class="sxs-lookup"><span data-stu-id="187b4-119">However, your results may vary.</span></span> <span data-ttu-id="187b4-120">Chcete-li zajistit, aby vaše aplikace využila vylepšení výkonu .NET Native, měli byste porovnat jeho výkon s verzí non-.NET Native vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="187b4-120">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="187b4-121">Další informace najdete v tématu [Přehled relace výkonu](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span><span class="sxs-lookup"><span data-stu-id="187b4-121">For more information, see [Performance Session Overview](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span></span>

<span data-ttu-id="187b4-122">Ale .NET Native zahrnuje více než kompilaci do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="187b4-122">But .NET Native involves more than a compilation to native code.</span></span> <span data-ttu-id="187b4-123">Transformuje způsob, jakým se sestavují a spouštějí aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="187b4-123">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="187b4-124">Zejména jde o toto:</span><span class="sxs-lookup"><span data-stu-id="187b4-124">In particular:</span></span>

- <span data-ttu-id="187b4-125">V průběhu předkompilace jsou požadované části .NET Framework staticky propojeny do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="187b4-125">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="187b4-126">To umožňuje aplikaci běžet s knihovnami místních aplikací .NET Framework a kompilátor provede globální analýzu pro doručení služby WINS výkonu.</span><span class="sxs-lookup"><span data-stu-id="187b4-126">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="187b4-127">V důsledku toho aplikace spouští konzistentně rychleji, i když .NET Framework aktualizace.</span><span class="sxs-lookup"><span data-stu-id="187b4-127">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>

- <span data-ttu-id="187b4-128">Modul runtime .NET Native je optimalizován pro statickou předkompilaci a v obrovské většině případů nabízí špičkový výkon.</span><span class="sxs-lookup"><span data-stu-id="187b4-128">The .NET Native runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="187b4-129">Ve stejnou dobu zachovává základní funkce reflexe, které vývojáři hledají tak, aby byly tak produktivní.</span><span class="sxs-lookup"><span data-stu-id="187b4-129">At the same time, it retains the core reflection features that developers find so productive.</span></span>

- <span data-ttu-id="187b4-130">.NET Native používá stejný back-end jako kompilátor jazyka C++, který je optimalizován pro statické scénáře předkompilace.</span><span class="sxs-lookup"><span data-stu-id="187b4-130">.NET Native uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>

<span data-ttu-id="187b4-131">.NET Native je možné přenést výhody z hlediska výkonu pro vývojáře spravovaného kódu, protože používá stejné nebo podobné nástroje jako C++ v digestoři, jak je znázorněno v této tabulce.</span><span class="sxs-lookup"><span data-stu-id="187b4-131">.NET Native is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>

||<span data-ttu-id="187b4-132">.NET Native</span><span class="sxs-lookup"><span data-stu-id="187b4-132">.NET Native</span></span>|<span data-ttu-id="187b4-133">C++</span><span class="sxs-lookup"><span data-stu-id="187b4-133">C++</span></span>|
|-|----------------------------------------------------------------|-----------|
|<span data-ttu-id="187b4-134">Knihovny</span><span class="sxs-lookup"><span data-stu-id="187b4-134">Libraries</span></span>|<span data-ttu-id="187b4-135">.NET Framework + prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="187b4-135">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="187b4-136">Win32 + prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="187b4-136">Win32 + Windows Runtime</span></span>|
|<span data-ttu-id="187b4-137">Compiler</span><span class="sxs-lookup"><span data-stu-id="187b4-137">Compiler</span></span>|<span data-ttu-id="187b4-138">Kompilátor pro optimalizaci UTC</span><span class="sxs-lookup"><span data-stu-id="187b4-138">UTC optimizing compiler</span></span>|<span data-ttu-id="187b4-139">Kompilátor pro optimalizaci UTC</span><span class="sxs-lookup"><span data-stu-id="187b4-139">UTC optimizing compiler</span></span>|
|<span data-ttu-id="187b4-140">Nainstalována</span><span class="sxs-lookup"><span data-stu-id="187b4-140">Deployed</span></span>|<span data-ttu-id="187b4-141">Soubory připravené ke spuštění</span><span class="sxs-lookup"><span data-stu-id="187b4-141">Ready-to-run binaries</span></span>|<span data-ttu-id="187b4-142">Hotové binární soubory připravené k běhu (ASM)</span><span class="sxs-lookup"><span data-stu-id="187b4-142">Ready-to-run binaries (ASM)</span></span>|
|<span data-ttu-id="187b4-143">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="187b4-143">Runtime</span></span>|<span data-ttu-id="187b4-144">MRT. dll (minimální modul CLR Runtime)</span><span class="sxs-lookup"><span data-stu-id="187b4-144">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="187b4-145">CRT. dll (běhové prostředí C)</span><span class="sxs-lookup"><span data-stu-id="187b4-145">CRT.dll (C Runtime)</span></span>|

<span data-ttu-id="187b4-146">Pro aplikace pro Windows pro Windows 10 nahrajete .NET Native binárních souborů kompilace kódu v balíčcích aplikací (soubory. appx) do Windows Storu.</span><span class="sxs-lookup"><span data-stu-id="187b4-146">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="187b4-147">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="187b4-147">In This Section</span></span>

<span data-ttu-id="187b4-148">Další informace o vývoji aplikací pomocí kompilace kódu .NET Native najdete v těchto tématech:</span><span class="sxs-lookup"><span data-stu-id="187b4-148">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>

- [<span data-ttu-id="187b4-149">Začínáme s kompilací kódu .NET Native: Návod k vývojovému prostředí</span><span class="sxs-lookup"><span data-stu-id="187b4-149">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](getting-started-with-net-native.md)

- <span data-ttu-id="187b4-150">[.NET Native a kompilace:](net-native-and-compilation.md) Jak .NET Native zkompiluje projekt do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="187b4-150">[.NET Native and Compilation:](net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>

- [<span data-ttu-id="187b4-151">Reflexe a .NET Native</span><span class="sxs-lookup"><span data-stu-id="187b4-151">Reflection and .NET Native</span></span>](reflection-and-net-native.md)

  - [<span data-ttu-id="187b4-152">Rozhraní API, která závisí na reflexi</span><span class="sxs-lookup"><span data-stu-id="187b4-152">APIs That Rely on Reflection</span></span>](apis-that-rely-on-reflection.md)

  - [<span data-ttu-id="187b4-153">Informace o rozhraní API reflexe</span><span class="sxs-lookup"><span data-stu-id="187b4-153">Reflection API Reference</span></span>](net-native-reflection-api-reference.md)

  - [<span data-ttu-id="187b4-154">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="187b4-154">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)

- [<span data-ttu-id="187b4-155">Serializace a metadata</span><span class="sxs-lookup"><span data-stu-id="187b4-155">Serialization and Metadata</span></span>](serialization-and-metadata.md)

- [<span data-ttu-id="187b4-156">Migrace aplikace pro Windows Store do .NET Native</span><span class="sxs-lookup"><span data-stu-id="187b4-156">Migrating Your Windows Store App to .NET Native</span></span>](migrating-your-windows-store-app-to-net-native.md)

- [<span data-ttu-id="187b4-157">Obecné řešení potíží s .NET Native</span><span class="sxs-lookup"><span data-stu-id="187b4-157">.NET Native General Troubleshooting</span></span>](net-native-general-troubleshooting.md)
