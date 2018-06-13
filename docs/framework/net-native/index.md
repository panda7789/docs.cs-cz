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
ms.openlocfilehash: 6900bca2bd94f52ea5603c752681163cde52ce19
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457304"
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="421f7-102">Kompilování aplikací pomocí .NET Native</span><span class="sxs-lookup"><span data-stu-id="421f7-102">Compiling Apps with .NET Native</span></span>
[!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="421f7-103"> je předkompilace technologie pro vytváření a nasazování aplikací pro Windows, která je součástí sady Visual Studio 2015 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="421f7-103"> is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="421f7-104">Zkompiluje automaticky prodejní verze aplikace, které jsou zapsány v spravovaného kódu (C# nebo Visual Basic), že cílové rozhraní .NET Framework a Windows 10 do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="421f7-104">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>  
  
 <span data-ttu-id="421f7-105">Aplikace, které cílí na rozhraní .NET Framework jsou obvykle zkompilovány do převodního jazyka (IL).</span><span class="sxs-lookup"><span data-stu-id="421f7-105">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="421f7-106">V době běhu kompilátoru za běhu (JIT) překládá IL do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="421f7-106">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="421f7-107">Naproti tomu [!INCLUDE[net_native](../../../includes/net-native-md.md)] zkompiluje aplikací pro Windows přímo do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="421f7-107">In contrast, [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiles Windows apps directly to native code.</span></span> <span data-ttu-id="421f7-108">Pro vývojáře to znamená:</span><span class="sxs-lookup"><span data-stu-id="421f7-108">For developers, this means:</span></span>  
  
-   <span data-ttu-id="421f7-109">Vaše aplikace funkce výkon nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="421f7-109">Your apps feature the performance of native code.</span></span> <span data-ttu-id="421f7-110">Obvykle bude výkon hodnotu větší než kód, který je napřed zkompilovat IL a pak zkompilují do nativního kódu kompilátoru za běhu.</span><span class="sxs-lookup"><span data-stu-id="421f7-110">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span> 
  
-   <span data-ttu-id="421f7-111">Můžete nadále programu v C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="421f7-111">You can continue to program in C# or Visual Basic.</span></span>  
  
-   <span data-ttu-id="421f7-112">Můžete nadále využívat prostředky poskytované rozhraní .NET Framework, včetně jeho knihovny tříd, správu a uvolňování paměti kolekce automatické paměti a výjimek.</span><span class="sxs-lookup"><span data-stu-id="421f7-112">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>  
  
 <span data-ttu-id="421f7-113">Pro uživatele vaší aplikace [!INCLUDE[net_native](../../../includes/net-native-md.md)] nabízí tyto výhody:</span><span class="sxs-lookup"><span data-stu-id="421f7-113">For users of your apps, [!INCLUDE[net_native](../../../includes/net-native-md.md)] offers these advantages:</span></span>  
  
-   <span data-ttu-id="421f7-114">Rychlejší doby provádění pro většinu aplikací a scénáře.</span><span class="sxs-lookup"><span data-stu-id="421f7-114">Faster execution times for the majority of apps and scenarios.</span></span>
  
-   <span data-ttu-id="421f7-115">Kratší časy spuštění pro většinu aplikací a scénáře.</span><span class="sxs-lookup"><span data-stu-id="421f7-115">Faster startup times for the majority of apps and scenarios.</span></span> 
  
-   <span data-ttu-id="421f7-116">Nízké náklady na nasazení a aktualizace.</span><span class="sxs-lookup"><span data-stu-id="421f7-116">Low deployment and update costs.</span></span>  
  
-   <span data-ttu-id="421f7-117">Optimalizovat využití paměti v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="421f7-117">Optimized app memory usage.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="421f7-118">Valná většina scénáře a aplikace .NET Native nabízí výrazně rychlejší spouštění a vynikající výkon ve srovnání s zkompilovat IL nebo bitovou kopii NGEN aplikace.</span><span class="sxs-lookup"><span data-stu-id="421f7-118">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="421f7-119">Výsledky se však mohou lišit.</span><span class="sxs-lookup"><span data-stu-id="421f7-119">However, your results may vary.</span></span> <span data-ttu-id="421f7-120">Aby se zajistilo, že vaše aplikace využívaly vylepšení výkonu systému .NET Native, byste měli porovnat jeho výkon s u jiných - .NET Native verzi vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="421f7-120">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="421f7-121">Další informace najdete v tématu [přehled výkonnostní relace](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span><span class="sxs-lookup"><span data-stu-id="421f7-121">For more information, see [Performance Session Overview](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span></span>
 
<span data-ttu-id="421f7-122">Ale [!INCLUDE[net_native](../../../includes/net-native-md.md)] zahrnuje více než kompilace nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="421f7-122">But [!INCLUDE[net_native](../../../includes/net-native-md.md)] involves more than a compilation to native code.</span></span> <span data-ttu-id="421f7-123">Ho transformuje způsobu, jakým jsou vytvořené a provést aplikací rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="421f7-123">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="421f7-124">Zejména:</span><span class="sxs-lookup"><span data-stu-id="421f7-124">In particular:</span></span>  
  
-   <span data-ttu-id="421f7-125">Při předkompilaci jsou požadované části rozhraní .NET Framework staticky propojené do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="421f7-125">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="421f7-126">To umožňuje aplikaci spustit s knihovnami místní aplikace rozhraní .NET Framework a kompilátor provádět globální analýzu k poskytování výkonu služby wins.</span><span class="sxs-lookup"><span data-stu-id="421f7-126">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="421f7-127">Výsledkem je aplikace budou spouštět rychleji i po aktualizací rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="421f7-127">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>  
  
-   <span data-ttu-id="421f7-128">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Runtime je optimalizovaná pro statické předkompilaci a v valná většina případů nabízí vyšší výkon.</span><span class="sxs-lookup"><span data-stu-id="421f7-128">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="421f7-129">Ve stejnou dobu zůstane zachován funkce reflexe jádra, které vývojáři najít tak produktivitu.</span><span class="sxs-lookup"><span data-stu-id="421f7-129">At the same time, it retains the core reflection features that developers find so productive.</span></span>  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="421f7-130"> používá stejný zpět ukončení jako C++ compiler, která je optimalizovaná pro statické předkompilace scénáře.</span><span class="sxs-lookup"><span data-stu-id="421f7-130"> uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="421f7-131"> je přináší výhody výkonu C++ na vývojářům spravovaného kódu protože používá nástroje stejné nebo podobné jako C++ pod pokličkou, jak je znázorněno v této tabulce.</span><span class="sxs-lookup"><span data-stu-id="421f7-131"> is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|<span data-ttu-id="421f7-132">C++</span><span class="sxs-lookup"><span data-stu-id="421f7-132">C++</span></span>|  
|-|----------------------------------------------------------------|-----------|  
|<span data-ttu-id="421f7-133">Knihovny</span><span class="sxs-lookup"><span data-stu-id="421f7-133">Libraries</span></span>|<span data-ttu-id="421f7-134">Rozhraní .NET Framework a prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="421f7-134">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="421f7-135">Win32 + prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="421f7-135">Win32 + Windows Runtime</span></span>|  
|<span data-ttu-id="421f7-136">Kompilátoru</span><span class="sxs-lookup"><span data-stu-id="421f7-136">Compiler</span></span>|<span data-ttu-id="421f7-137">Optimalizace kompilátoru UTC</span><span class="sxs-lookup"><span data-stu-id="421f7-137">UTC optimizing compiler</span></span>|<span data-ttu-id="421f7-138">Optimalizace kompilátoru UTC</span><span class="sxs-lookup"><span data-stu-id="421f7-138">UTC optimizing compiler</span></span>|  
|<span data-ttu-id="421f7-139">Nasazení</span><span class="sxs-lookup"><span data-stu-id="421f7-139">Deployed</span></span>|<span data-ttu-id="421f7-140">Binární soubory připravené k použití</span><span class="sxs-lookup"><span data-stu-id="421f7-140">Ready-to-run binaries</span></span>|<span data-ttu-id="421f7-141">Binární soubory připravené k použití (ASM)</span><span class="sxs-lookup"><span data-stu-id="421f7-141">Ready-to-run binaries (ASM)</span></span>|  
|<span data-ttu-id="421f7-142">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="421f7-142">Runtime</span></span>|<span data-ttu-id="421f7-143">MRT.dll (minimální CLR Runtime)</span><span class="sxs-lookup"><span data-stu-id="421f7-143">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="421f7-144">CRT.dll (C Runtime)</span><span class="sxs-lookup"><span data-stu-id="421f7-144">CRT.dll (C Runtime)</span></span>|  
  
 <span data-ttu-id="421f7-145">Pro aplikace pro Windows pro Windows 10 nahrajte kompilace nativního kódu .NET binárních souborů v aplikaci balíčky (soubory .appx) na web Windows Store.</span><span class="sxs-lookup"><span data-stu-id="421f7-145">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="421f7-146">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="421f7-146">In This Section</span></span>  
 <span data-ttu-id="421f7-147">Další informace o vývoji aplikací s nativní kompilace kódu rozhraní .NET naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="421f7-147">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>  
  
-   [<span data-ttu-id="421f7-148">Začínáme s .NET kompilace nativního kódu: návod prostředí vývojáře</span><span class="sxs-lookup"><span data-stu-id="421f7-148">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
-   <span data-ttu-id="421f7-149">[.NET native a kompilace:](../../../docs/framework/net-native/net-native-and-compilation.md) jak .NET Native zkompiluje projekt do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="421f7-149">[.NET Native and Compilation:](../../../docs/framework/net-native/net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>  
  
-   [<span data-ttu-id="421f7-150">Reflexe a .NET Native</span><span class="sxs-lookup"><span data-stu-id="421f7-150">Reflection and .NET Native</span></span>](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    -   [<span data-ttu-id="421f7-151">Rozhraní API, která závisí na reflexi</span><span class="sxs-lookup"><span data-stu-id="421f7-151">APIs That Rely on Reflection</span></span>](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    -   [<span data-ttu-id="421f7-152">Informace o rozhraní API reflexe</span><span class="sxs-lookup"><span data-stu-id="421f7-152">Reflection API Reference</span></span>](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    -   [<span data-ttu-id="421f7-153">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="421f7-153">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
-   [<span data-ttu-id="421f7-154">Serializace a metadata</span><span class="sxs-lookup"><span data-stu-id="421f7-154">Serialization and Metadata</span></span>](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
-   [<span data-ttu-id="421f7-155">Migrace aplikace pro Windows Store do .NET Native</span><span class="sxs-lookup"><span data-stu-id="421f7-155">Migrating Your Windows Store App to .NET Native</span></span>](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
-   [<span data-ttu-id="421f7-156">Obecné řešení potíží s .NET Native</span><span class="sxs-lookup"><span data-stu-id="421f7-156">.NET Native General Troubleshooting</span></span>](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
