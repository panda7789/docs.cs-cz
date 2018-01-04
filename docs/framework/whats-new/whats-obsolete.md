---
title: "Jaký & č. 39; s zastaralé v knihovně tříd rozhraní .NET Framework"
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d5fc41473c4a3ea812013ee7e5204c22d0a694d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="what39s-obsolete-in-the-net-framework-class-library"></a><span data-ttu-id="f89ae-102">Jaký & č. 39; s zastaralé v knihovně tříd rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f89ae-102">What&#39;s Obsolete in the .NET Framework Class Library</span></span>
<span data-ttu-id="f89ae-103">Rozhraní .NET Framework se mění v čase.</span><span class="sxs-lookup"><span data-stu-id="f89ae-103">The .NET Framework changes over time.</span></span> <span data-ttu-id="f89ae-104">Každá nová verze přidává nové typy a členy typu, které přinášejí nové funkce.</span><span class="sxs-lookup"><span data-stu-id="f89ae-104">Each new version adds new types and type members that provide new functionality.</span></span> <span data-ttu-id="f89ae-105">Existující typy a jejich členové také časem změnit.</span><span class="sxs-lookup"><span data-stu-id="f89ae-105">Existing types and their members also change over time.</span></span> <span data-ttu-id="f89ae-106">Například některé typy stane méně důležité, jako je technologie, které podporují nahrazena novou technologií a některé metody nejsou k dispozici novější metody, které jsou vhodnější nebo obsáhlejší.</span><span class="sxs-lookup"><span data-stu-id="f89ae-106">For example, some types become less important as the technology they support is replaced by a new technology, and some methods are superseded by newer methods that are either more convenient or more full-featured.</span></span>  
  
 <span data-ttu-id="f89ae-107">Rozhraní .NET Framework a modul common language runtime usilují o podporu zpětné kompatibility (povolení aplikace vyvinuté pomocí jedné verze rozhraní .NET Framework ke spuštění na další verzi rozhraní .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="f89ae-107">The .NET Framework and the common language runtime strive to support backward compatibility (allowing applications that were developed with one version of the .NET Framework to run on the next version of the .NET Framework).</span></span> <span data-ttu-id="f89ae-108">Díky tomu je obtížné stačí odstranit určitý typ nebo člen typu.</span><span class="sxs-lookup"><span data-stu-id="f89ae-108">This makes it difficult to simply remove a type or a type member.</span></span> <span data-ttu-id="f89ae-109">Místo toho rozhraní .NET Framework označuje, že typ nebo člen typu by už použít označením jako zastaralé nebo zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f89ae-109">Instead, the .NET Framework indicates that a type or a type member should no longer be used by marking it as obsolete or deprecated.</span></span> <span data-ttu-id="f89ae-110">Místo začne typ nebo člen zahrnuje označením tak, aby vývojáři víte ho bude odstraněn a čas reagovat na jeho odstranění.</span><span class="sxs-lookup"><span data-stu-id="f89ae-110">Deprecating a type or a member involves marking it so that developers are aware it will go away and have time to respond to its removal.</span></span> <span data-ttu-id="f89ae-111">Existující kód, který používá typ nebo člen je však nadále spuštěna v nové verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f89ae-111">However, existing code that uses the type or member continues to run in the new version of the .NET Framework.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f89ae-112">Podmínky *zastaralé* a *zastaralé* mají stejný význam při aplikování typy a členy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f89ae-112">The terms *obsolete* and *deprecated* have the same meaning when applied to the types and members of the .NET Framework.</span></span>  
  
## <a name="the-obsoleteattribute-attribute"></a><span data-ttu-id="f89ae-113">Atribut ObsoleteAttribute</span><span class="sxs-lookup"><span data-stu-id="f89ae-113">The ObsoleteAttribute Attribute</span></span>  
 <span data-ttu-id="f89ae-114">Rozhraní .NET Framework označuje, že typ nebo typ člena je zastaralé se s označením <xref:System.ObsoleteAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="f89ae-114">The .NET Framework indicates that a type or type member is obsolete by marking it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="f89ae-115">Použití atributu pro typ nebo člen označuje, že typ nebo člen se odeberou v některé budoucí verzi rozhraní .NET Framework bez narušení zkompilovaný kód, který použije tento člen.</span><span class="sxs-lookup"><span data-stu-id="f89ae-115">Applying the attribute to a type or member indicates that that type or member will be removed in some future version of the .NET Framework without breaking compiled code that uses that member.</span></span>  
  
 <span data-ttu-id="f89ae-116">Kromě indikující, že typ nebo typ člena je neplatný, <xref:System.ObsoleteAttribute> definuje, jak kompilátor zpracovává zdrojový kód, který obsahuje tento typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="f89ae-116">In addition to indicating that a type or a type member is obsolete, <xref:System.ObsoleteAttribute> defines how the compiler handles source code that includes that type or member.</span></span> <span data-ttu-id="f89ae-117">Kompilátor můžete zkompilovat kód, ale také posílat upozornění, nebo použijte typ nebo člen může považovat za chybu.</span><span class="sxs-lookup"><span data-stu-id="f89ae-117">The compiler can compile the code but emit a warning message, or it can treat the use of the type or member as an error.</span></span> <span data-ttu-id="f89ae-118">V prvním případě můžete úspěšně zkompilovat kód, ale upozornění označuje, že typ nebo člen je zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f89ae-118">In the first case, the code can successfully compile, but a warning message indicates that the type or member is obsolete.</span></span> <span data-ttu-id="f89ae-119">V druhém případě kompilace se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="f89ae-119">In the second case, compilation fails.</span></span>  
  
 <span data-ttu-id="f89ae-120">I když kompilace vytvoří chybu místo zprávu upozornění <xref:System.ObsoleteAttribute> nemá vliv na chování.</span><span class="sxs-lookup"><span data-stu-id="f89ae-120">Even if compilation produces an error instead of a warning message, <xref:System.ObsoleteAttribute> does not affect run-time behavior.</span></span> <span data-ttu-id="f89ae-121">Aplikace, které používají typ nebo člen a byly úspěšně zkompilovány tedy bude vždy úspěšně spuštěna.</span><span class="sxs-lookup"><span data-stu-id="f89ae-121">That is, applications that use the type or member and that have compiled successfully will always run successfully.</span></span> <span data-ttu-id="f89ae-122">Jenom se nezdaří pokus o znovu zkompiluje aplikaci, která používá typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="f89ae-122">Only the attempt to recompile an application that uses the type or member fails.</span></span>  
  
## <a name="how-to-handle-obsolete-types-and-members"></a><span data-ttu-id="f89ae-123">Postupy: zpracování zastaralé typy a členy</span><span class="sxs-lookup"><span data-stu-id="f89ae-123">How to Handle Obsolete Types and Members</span></span>  
 <span data-ttu-id="f89ae-124">Při upgradu a znovu zkompiluje stávající kód, pomocí neplatný typ nebo člen, který vyvolá upozornění kompilátoru v aplikaci je zcela přijatelné.</span><span class="sxs-lookup"><span data-stu-id="f89ae-124">When you upgrade and recompile existing code, using an obsolete type or member that produces a compiler warning in your application is perfectly acceptable.</span></span> <span data-ttu-id="f89ae-125">Ale přečtěte si upozornění kompilátoru k určení, zda byste měli změnit kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="f89ae-125">However, you should review the compiler warning message to determine whether you should change your application code.</span></span> <span data-ttu-id="f89ae-126">Pokud zpráva neukazuje na jinou vhodnou alternativu, proveďte jednu z těchto věcí:</span><span class="sxs-lookup"><span data-stu-id="f89ae-126">If the message does not point to a suitable alternative, you should do either of the following:</span></span>  
  
-   <span data-ttu-id="f89ae-127">Změna kódu odebráním použití typ nebo člen, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="f89ae-127">Change your code by removing the use of the type or member, if possible.</span></span>  
  
     <span data-ttu-id="f89ae-128">-nebo-</span><span class="sxs-lookup"><span data-stu-id="f89ae-128">-or-</span></span>  
  
-   <span data-ttu-id="f89ae-129">Najdete v dokumentaci k této technologické oblasti určit, jak reagovat na zastaralá.</span><span class="sxs-lookup"><span data-stu-id="f89ae-129">Review the documentation for this technology area to determine how to respond to the deprecation.</span></span>  
  
 <span data-ttu-id="f89ae-130">Můžete se rozhodnout nechcete znovu zkompiluje existující kód proti novější verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f89ae-130">You may choose not to recompile existing code against a later version of the .NET Framework.</span></span> <span data-ttu-id="f89ae-131">Místo toho můžete zadat verzi rozhraní .NET Framework, vůči které stávající zkompilovaný kód běží.</span><span class="sxs-lookup"><span data-stu-id="f89ae-131">Instead, you can specify the version of the .NET Framework against which your existing compiled code runs.</span></span> <span data-ttu-id="f89ae-132">Předpokládejme například, že máte aplikaci s názvem app1.exe, který se zkompiluje proti [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], ale chcete, aby aplikace ke spouštění [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f89ae-132">For example, suppose that you have an application named app1.exe that was compiled against the [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], but you want the application to run against the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="f89ae-133">To vyžaduje následující kroky:</span><span class="sxs-lookup"><span data-stu-id="f89ae-133">This requires the following steps:</span></span>  
  
1.  <span data-ttu-id="f89ae-134">Vytvořte konfigurační soubor pro váš hlavní spustitelný soubor s názvem *appName*. exe.config, kde *appName* je název spustitelného souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f89ae-134">Create a configuration file for your main executable and name it *appName*.exe.config, where *appName* is the name of the application executable.</span></span> <span data-ttu-id="f89ae-135">Pro aplikaci s názvem app1.exe v našem příkladu by vytvořit konfigurační soubor s názvem app1.exe.config.</span><span class="sxs-lookup"><span data-stu-id="f89ae-135">For the application named app1.exe in our example, you would create a configuration file named app1.exe.config.</span></span>  
  
2.  <span data-ttu-id="f89ae-136">Přidejte následující do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="f89ae-136">Add the following to the configuration file.</span></span>  
  
    ```xml  
    <configuration>  
       <startup>   
          <supportedRuntime version="v4.0" />  
       </startup>  
    </configuration>  
    ```  
  
 <span data-ttu-id="f89ae-137">Následující tabulka uvádí řetězcové hodnoty, které lze přiřadit `version` atribut k cílení na konkrétní verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f89ae-137">The following table lists the string values that you can assign to the `version` attribute to target a specific version of the .NET Framework.</span></span>  
  
|<span data-ttu-id="f89ae-138">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f89ae-138">.NET Framework version</span></span>|<span data-ttu-id="f89ae-139">`version`řetězec</span><span class="sxs-lookup"><span data-stu-id="f89ae-139">`version` string</span></span>|
|-|-|  
|<span data-ttu-id="f89ae-140">4.7 (včetně 4.7.1)</span><span class="sxs-lookup"><span data-stu-id="f89ae-140">4.7 (including 4.7.1)</span></span>|<span data-ttu-id="f89ae-141">V4.0</span><span class="sxs-lookup"><span data-stu-id="f89ae-141">v4.0</span></span>|  
|<span data-ttu-id="f89ae-142">4.6 (včetně 4.6.1 a 4.6.2)</span><span class="sxs-lookup"><span data-stu-id="f89ae-142">4.6 (including 4.6.1 and 4.6.2)</span></span>|<span data-ttu-id="f89ae-143">V4.0</span><span class="sxs-lookup"><span data-stu-id="f89ae-143">v4.0</span></span>|  
|<span data-ttu-id="f89ae-144">4.5 (včetně 4.5.1 a 4.5.2)</span><span class="sxs-lookup"><span data-stu-id="f89ae-144">4.5 (including 4.5.1 and 4.5.2)</span></span>|<span data-ttu-id="f89ae-145">V4.0</span><span class="sxs-lookup"><span data-stu-id="f89ae-145">v4.0</span></span>|  
|<span data-ttu-id="f89ae-146">4</span><span class="sxs-lookup"><span data-stu-id="f89ae-146">4</span></span>|<span data-ttu-id="f89ae-147">V4.0</span><span class="sxs-lookup"><span data-stu-id="f89ae-147">v4.0</span></span>|  
|<span data-ttu-id="f89ae-148">3.5</span><span class="sxs-lookup"><span data-stu-id="f89ae-148">3.5</span></span>|<span data-ttu-id="f89ae-149">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="f89ae-149">v2.0.50727</span></span>|  
|<span data-ttu-id="f89ae-150">2.0</span><span class="sxs-lookup"><span data-stu-id="f89ae-150">2.0</span></span>|<span data-ttu-id="f89ae-151">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="f89ae-151">v2.0.50727</span></span>|  
|<span data-ttu-id="f89ae-152">1.1</span><span class="sxs-lookup"><span data-stu-id="f89ae-152">1.1</span></span>|<span data-ttu-id="f89ae-153">V1.1.4322</span><span class="sxs-lookup"><span data-stu-id="f89ae-153">v1.1.4322</span></span>|  
|<span data-ttu-id="f89ae-154">1.0</span><span class="sxs-lookup"><span data-stu-id="f89ae-154">1.0</span></span>|<span data-ttu-id="f89ae-155">V1.0.3705</span><span class="sxs-lookup"><span data-stu-id="f89ae-155">v1.0.3705</span></span>|  
  
## <a name="obsolete-lists-for-the-net-framework-45-and-46"></a><span data-ttu-id="f89ae-156">Zastaralé seznamy pro rozhraní .NET Framework 4.5 a 4.6</span><span class="sxs-lookup"><span data-stu-id="f89ae-156">Obsolete Lists for the .NET Framework 4.5 and 4.6</span></span>  
 [<span data-ttu-id="f89ae-157">Zastaralé typy</span><span class="sxs-lookup"><span data-stu-id="f89ae-157">Obsolete Types</span></span>](../../../docs/framework/whats-new/obsolete-types.md)  
  
 [<span data-ttu-id="f89ae-158">Zastaralé členy</span><span class="sxs-lookup"><span data-stu-id="f89ae-158">Obsolete Members</span></span>](../../../docs/framework/whats-new/obsolete-members.md)  
  
## <a name="obsolete-lists-for-previous-versions"></a><span data-ttu-id="f89ae-159">Zastaralé seznamy pro předchozí verze</span><span class="sxs-lookup"><span data-stu-id="f89ae-159">Obsolete Lists for Previous Versions</span></span>  
 [<span data-ttu-id="f89ae-160">Zastaralé typy v rozhraní .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="f89ae-160">Obsolete Types in the .NET Framework 4</span></span>](http://go.microsoft.com/fwlink/?LinkId=224224)  
  
 [<span data-ttu-id="f89ae-161">Zastaralé členy v rozhraní .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="f89ae-161">Obsolete Members in the .NET Framework 4</span></span>](http://go.microsoft.com/fwlink/?LinkId=224227)  
  
 [<span data-ttu-id="f89ae-162">Zastaralý seznam rozhraní .NET framework 3.5</span><span class="sxs-lookup"><span data-stu-id="f89ae-162">.NET Framework 3.5 Obsolete List</span></span>](http://go.microsoft.com/fwlink/?LinkId=163710)  
  
 [<span data-ttu-id="f89ae-163">Zastaralý seznam rozhraní .NET framework 2.0</span><span class="sxs-lookup"><span data-stu-id="f89ae-163">.NET Framework 2.0 Obsolete List</span></span>](http://go.microsoft.com/fwlink/?LinkID=125264)  
  
## <a name="see-also"></a><span data-ttu-id="f89ae-164">Viz také</span><span class="sxs-lookup"><span data-stu-id="f89ae-164">See Also</span></span>  
 [<span data-ttu-id="f89ae-165">\<supportedRuntime > elementu</span><span class="sxs-lookup"><span data-stu-id="f89ae-165">\<supportedRuntime> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
