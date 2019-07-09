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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d295d0b35b4b93425c825f75857881a2e2ddc57
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660894"
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="a4ff9-102">Kompilování aplikací pomocí .NET Native</span><span class="sxs-lookup"><span data-stu-id="a4ff9-102">Compiling Apps with .NET Native</span></span>

<span data-ttu-id="a4ff9-103">.NET native se technologie předkompilace pro sestavování a nasazování aplikací pro Windows, která je součástí sady Visual Studio 2015 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-103">.NET Native is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="a4ff9-104">Automaticky kompilaci verze vydání aplikace, které jsou zapsané ve spravovaném kódu (C# nebo Visual Basic) a do nativního kódu, který cílí na rozhraní .NET Framework a Windows 10.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-104">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>

<span data-ttu-id="a4ff9-105">Obvykle aplikace, které cílí rozhraní .NET Framework jsou kompilovány do (IL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="a4ff9-105">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="a4ff9-106">V době spuštění přeloží kompilátor just-in-time (JIT) IL na nativní kód.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-106">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="a4ff9-107">.NET Native zkompiluje naproti tomu aplikace Windows přímo do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-107">In contrast, .NET Native compiles Windows apps directly to native code.</span></span> <span data-ttu-id="a4ff9-108">Pro vývojáře to znamená, že:</span><span class="sxs-lookup"><span data-stu-id="a4ff9-108">For developers, this means:</span></span>

- <span data-ttu-id="a4ff9-109">Vaše aplikace funkcí výkonu nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-109">Your apps feature the performance of native code.</span></span> <span data-ttu-id="a4ff9-110">Obvykle se výkon vynikající kód, který je nejprve zkompilován do IL a potom kompilovány do nativního kódu, kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-110">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span>

- <span data-ttu-id="a4ff9-111">Můžete pokračovat v aplikaci C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-111">You can continue to program in C# or Visual Basic.</span></span>

- <span data-ttu-id="a4ff9-112">Můžete nadále využívat prostředky poskytované rozhraní .NET Framework, včetně jeho knihovny tříd, správu a uvolňování paměti kolekce automatické paměti a zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-112">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>

<span data-ttu-id="a4ff9-113">Pro uživatele aplikací .NET Native nabízí tyto výhody:</span><span class="sxs-lookup"><span data-stu-id="a4ff9-113">For users of your apps, .NET Native offers these advantages:</span></span>

- <span data-ttu-id="a4ff9-114">Rychlejší spuštění s úspěšností pro většinu scénářů a aplikací.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-114">Faster execution times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="a4ff9-115">Rychlejší spuštění pro většinu scénářů a aplikací.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-115">Faster startup times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="a4ff9-116">Nízké náklady na nasazení a aktualizace.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-116">Low deployment and update costs.</span></span>

- <span data-ttu-id="a4ff9-117">Optimalizované využití paměti aplikace.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-117">Optimized app memory usage.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a4ff9-118">Pro většinu scénářů a aplikací .NET Native nabízí výrazně rychlejší spouštění a špičkový výkon ve srovnání s aplikace zkompilována do IL nebo do NGEN image.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-118">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="a4ff9-119">Vaše výsledky se však může mírně lišit.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-119">However, your results may vary.</span></span> <span data-ttu-id="a4ff9-120">Aby bylo zajištěno, že aplikace má prospěch z vylepšení výkonu .NET Native, porovnejte svůj výkon pomocí bez – .NET Native verze vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-120">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="a4ff9-121">Další informace najdete v tématu [přehled výkonnostní relace](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span><span class="sxs-lookup"><span data-stu-id="a4ff9-121">For more information, see [Performance Session Overview](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span></span>

<span data-ttu-id="a4ff9-122">Ale .NET Native vyžaduje více než kompilace do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-122">But .NET Native involves more than a compilation to native code.</span></span> <span data-ttu-id="a4ff9-123">Se mění způsob, jakým, že aplikace rozhraní .NET Framework jsou vytvořené a spustit.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-123">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="a4ff9-124">Zejména:</span><span class="sxs-lookup"><span data-stu-id="a4ff9-124">In particular:</span></span>

- <span data-ttu-id="a4ff9-125">Při předkompilaci požadované části rozhraní .NET Framework staticky propojené do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-125">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="a4ff9-126">To umožňuje aplikaci spustit s knihovnami místní aplikace rozhraní .NET Framework, a kompilátor provede globální analýzu k zajištění výkonu wins.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-126">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="a4ff9-127">V důsledku toho aplikace budou spouštět rychleji i po aktualizace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-127">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>

- <span data-ttu-id="a4ff9-128">Modul runtime .NET Native je optimalizovaná pro statické předkompilace a v převážné většině případů nabízí vynikající výkon.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-128">The .NET Native runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="a4ff9-129">Ve stejnou dobu zůstane zachován reflexe základní funkce, které najít tak produktivitu vývojářů.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-129">At the same time, it retains the core reflection features that developers find so productive.</span></span>

- <span data-ttu-id="a4ff9-130">.NET native používá stejnou back-endu jako C++ kompilátoru, který je optimalizovaný pro statické předkompilace scénáře.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-130">.NET Native uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>

<span data-ttu-id="a4ff9-131">.NET native se bude moct přinést výhody výkonu C++ do spravovaného kódu vývojáři, protože používá stejné nebo podobné nástroje jako C++ pod pokličkou, jak je znázorněno v této tabulce.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-131">.NET Native is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>

||<span data-ttu-id="a4ff9-132">.NET Native</span><span class="sxs-lookup"><span data-stu-id="a4ff9-132">.NET Native</span></span>|<span data-ttu-id="a4ff9-133">C++</span><span class="sxs-lookup"><span data-stu-id="a4ff9-133">C++</span></span>|
|-|----------------------------------------------------------------|-----------|
|<span data-ttu-id="a4ff9-134">Knihovny</span><span class="sxs-lookup"><span data-stu-id="a4ff9-134">Libraries</span></span>|<span data-ttu-id="a4ff9-135">Rozhraní .NET Framework a prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="a4ff9-135">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="a4ff9-136">Win32 a prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="a4ff9-136">Win32 + Windows Runtime</span></span>|
|<span data-ttu-id="a4ff9-137">Kompilátor</span><span class="sxs-lookup"><span data-stu-id="a4ff9-137">Compiler</span></span>|<span data-ttu-id="a4ff9-138">Optimalizující kompilátor UTC</span><span class="sxs-lookup"><span data-stu-id="a4ff9-138">UTC optimizing compiler</span></span>|<span data-ttu-id="a4ff9-139">Optimalizující kompilátor UTC</span><span class="sxs-lookup"><span data-stu-id="a4ff9-139">UTC optimizing compiler</span></span>|
|<span data-ttu-id="a4ff9-140">nasazení</span><span class="sxs-lookup"><span data-stu-id="a4ff9-140">Deployed</span></span>|<span data-ttu-id="a4ff9-141">Připraveno ke spuštění binárních souborů</span><span class="sxs-lookup"><span data-stu-id="a4ff9-141">Ready-to-run binaries</span></span>|<span data-ttu-id="a4ff9-142">Připraveno ke spuštění binárních souborů (ASM)</span><span class="sxs-lookup"><span data-stu-id="a4ff9-142">Ready-to-run binaries (ASM)</span></span>|
|<span data-ttu-id="a4ff9-143">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="a4ff9-143">Runtime</span></span>|<span data-ttu-id="a4ff9-144">MRT.dll (Minimal CLR Runtime)</span><span class="sxs-lookup"><span data-stu-id="a4ff9-144">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="a4ff9-145">CRT.dll (C Runtime)</span><span class="sxs-lookup"><span data-stu-id="a4ff9-145">CRT.dll (C Runtime)</span></span>|

<span data-ttu-id="a4ff9-146">Pro aplikace Windows pro Windows 10 nahrát binární soubory nativní kompilační kód .NET v aplikaci balíčky (soubory .appx) pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-146">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a4ff9-147">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a4ff9-147">In This Section</span></span>

<span data-ttu-id="a4ff9-148">Další informace o vývoji aplikací s nativní kompilací kódu .NET najdete v těchto tématech:</span><span class="sxs-lookup"><span data-stu-id="a4ff9-148">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>

- [<span data-ttu-id="a4ff9-149">Začínáme s .NET kompilace nativního kódu: Průvodce prostředí pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="a4ff9-149">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)

- <span data-ttu-id="a4ff9-150">[.NET native a kompilace:](../../../docs/framework/net-native/net-native-and-compilation.md) .NET Native jak zkompiluje projekt do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a4ff9-150">[.NET Native and Compilation:](../../../docs/framework/net-native/net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>

- [<span data-ttu-id="a4ff9-151">Reflexe a .NET Native</span><span class="sxs-lookup"><span data-stu-id="a4ff9-151">Reflection and .NET Native</span></span>](../../../docs/framework/net-native/reflection-and-net-native.md)

  - [<span data-ttu-id="a4ff9-152">Rozhraní API, která závisí na reflexi</span><span class="sxs-lookup"><span data-stu-id="a4ff9-152">APIs That Rely on Reflection</span></span>](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)

  - [<span data-ttu-id="a4ff9-153">Informace o rozhraní API reflexe</span><span class="sxs-lookup"><span data-stu-id="a4ff9-153">Reflection API Reference</span></span>](../../../docs/framework/net-native/net-native-reflection-api-reference.md)

  - [<span data-ttu-id="a4ff9-154">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="a4ff9-154">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)

- [<span data-ttu-id="a4ff9-155">Serializace a metadata</span><span class="sxs-lookup"><span data-stu-id="a4ff9-155">Serialization and Metadata</span></span>](../../../docs/framework/net-native/serialization-and-metadata.md)

- [<span data-ttu-id="a4ff9-156">Migrace aplikace pro Windows Store do .NET Native</span><span class="sxs-lookup"><span data-stu-id="a4ff9-156">Migrating Your Windows Store App to .NET Native</span></span>](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)

- [<span data-ttu-id="a4ff9-157">Obecné řešení potíží s .NET Native</span><span class="sxs-lookup"><span data-stu-id="a4ff9-157">.NET Native General Troubleshooting</span></span>](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
