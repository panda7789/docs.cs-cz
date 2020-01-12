---
title: Co je zastaralé v .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
ms.openlocfilehash: eda60ce9e1396805541229c9756b13cdd167dc72
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901338"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a><span data-ttu-id="5d45f-102">Zastaralé položky v knihovně tříd .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5d45f-102">What's obsolete in the .NET Framework class library</span></span>

<span data-ttu-id="5d45f-103">.NET se v průběhu času mění.</span><span class="sxs-lookup"><span data-stu-id="5d45f-103">.NET changes over time.</span></span> <span data-ttu-id="5d45f-104">Každá nová verze přidává nové typy a členy typu, které poskytují nové funkce.</span><span class="sxs-lookup"><span data-stu-id="5d45f-104">Each new version adds new types and type members that provide new functionality.</span></span> <span data-ttu-id="5d45f-105">Existující typy a jejich členové se také mění v průběhu času.</span><span class="sxs-lookup"><span data-stu-id="5d45f-105">Existing types and their members also change over time.</span></span> <span data-ttu-id="5d45f-106">Některé typy jsou například méně důležité, protože technologie, kterou podporují, je nahrazena novou technologií a některé metody jsou nahrazené novějšími metodami, které jsou pro vás nějakým způsobem nadřazené.</span><span class="sxs-lookup"><span data-stu-id="5d45f-106">For example, some types become less important as the technology they support is replaced by a new technology, and some methods are superseded by newer methods that are superior in some way.</span></span>

<span data-ttu-id="5d45f-107">.NET Framework a modul CLR (Common Language Runtime) se snaží podporovat zpětnou kompatibilitu (což umožňuje aplikacím vyvinutým s jednou verzí .NET Framework běžet v další verzi .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="5d45f-107">.NET Framework and the common language runtime strive to support backward compatibility (allowing applications that were developed with one version of .NET Framework to run on the next version of .NET Framework).</span></span> <span data-ttu-id="5d45f-108">Díky tomu je obtížné jednoduše odebrat typ nebo člen typu.</span><span class="sxs-lookup"><span data-stu-id="5d45f-108">This makes it difficult to simply remove a type or a type member.</span></span> <span data-ttu-id="5d45f-109">Místo toho rozhraní .NET označuje, že typ nebo člen typu by již neměl být použit tak, že ho označíte jako zastaralé nebo zastaralé.</span><span class="sxs-lookup"><span data-stu-id="5d45f-109">Instead, .NET indicates that a type or a type member should no longer be used by marking it as obsolete or deprecated.</span></span> <span data-ttu-id="5d45f-110">Zahození typu nebo členu zahrnuje označení IT, aby se vývojáři dozvěděli, že se o jeho odebrání projeví a mají čas na reakci.</span><span class="sxs-lookup"><span data-stu-id="5d45f-110">Deprecating a type or a member involves marking it so that developers are aware it will go away and have time to respond to its removal.</span></span> <span data-ttu-id="5d45f-111">Stávající kód, který používá typ nebo člen, je však nadále spuštěn v nové verzi rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="5d45f-111">However, existing code that uses the type or member continues to run in the new version of .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="5d45f-112">*Zastaralé* a *zastaralé* výrazy mají stejný význam při použití na typy a členy .NET.</span><span class="sxs-lookup"><span data-stu-id="5d45f-112">The terms *obsolete* and *deprecated* have the same meaning when applied to .NET types and members.</span></span>

## <a name="the-obsoleteattribute-attribute"></a><span data-ttu-id="5d45f-113">Atribut ObsoleteAttribute</span><span class="sxs-lookup"><span data-stu-id="5d45f-113">The ObsoleteAttribute attribute</span></span>

<span data-ttu-id="5d45f-114">.NET Framework označuje, že typ nebo člen typu je zastaralý, označením s atributem <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5d45f-114">The .NET Framework indicates that a type or type member is obsolete by marking it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="5d45f-115">Použití atributu na typ nebo člen označuje, že typ nebo člen bude v některé budoucí verzi .NET Framework odebrán, aniž by došlo k narušení zkompilovaného kódu, který používá daného člena.</span><span class="sxs-lookup"><span data-stu-id="5d45f-115">Applying the attribute to a type or member indicates that type or member will be removed in some future version of the .NET Framework without breaking compiled code that uses that member.</span></span>

<span data-ttu-id="5d45f-116">Kromě toho, že je typ nebo člen typu zastaralý, <xref:System.ObsoleteAttribute> definuje způsob, jakým kompilátor zpracovává zdrojový kód, který obsahuje daný typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="5d45f-116">In addition to indicating that a type or a type member is obsolete, <xref:System.ObsoleteAttribute> defines how the compiler handles source code that includes that type or member.</span></span> <span data-ttu-id="5d45f-117">Kompilátor může kompilovat kód, ale generovat zprávu upozornění nebo může zacházet s používáním typu nebo členu jako chyby.</span><span class="sxs-lookup"><span data-stu-id="5d45f-117">The compiler can compile the code but emit a warning message, or it can treat the use of the type or member as an error.</span></span> <span data-ttu-id="5d45f-118">V prvním případě může být kód úspěšně zkompilován, ale varovná zpráva označuje, že typ nebo člen je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="5d45f-118">In the first case, the code can successfully compile, but a warning message indicates that the type or member is obsolete.</span></span> <span data-ttu-id="5d45f-119">Ve druhém případě kompilace dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="5d45f-119">In the second case, compilation fails.</span></span>

<span data-ttu-id="5d45f-120">I v případě, že kompilace vytvoří chybu namísto zprávy upozornění, <xref:System.ObsoleteAttribute> nemá vliv na chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="5d45f-120">Even if compilation produces an error instead of a warning message, <xref:System.ObsoleteAttribute> does not affect run-time behavior.</span></span> <span data-ttu-id="5d45f-121">To znamená, že aplikace, které používají typ nebo člena a které byly úspěšně kompilovány, budou vždy spouštěny úspěšně.</span><span class="sxs-lookup"><span data-stu-id="5d45f-121">That is, applications that use the type or member and that have compiled successfully will always run successfully.</span></span> <span data-ttu-id="5d45f-122">Pouze pokus o rekompilaci aplikace, která používá typ nebo člen, se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="5d45f-122">Only the attempt to recompile an application that uses the type or member fails.</span></span>

## <a name="how-to-handle-obsolete-types-and-members"></a><span data-ttu-id="5d45f-123">Postup zpracování zastaralých typů a členů</span><span class="sxs-lookup"><span data-stu-id="5d45f-123">How to handle obsolete types and members</span></span>

<span data-ttu-id="5d45f-124">Když upgradujete a znovu zkompilujete stávající kód pomocí zastaralého typu nebo členu, který vytvoří upozornění kompilátoru v aplikaci, je dokonale přijatelné.</span><span class="sxs-lookup"><span data-stu-id="5d45f-124">When you upgrade and recompile existing code, using an obsolete type or member that produces a compiler warning in your application is perfectly acceptable.</span></span> <span data-ttu-id="5d45f-125">Měli byste ale zkontrolovat zprávu s upozorněním kompilátoru, abyste zjistili, jestli byste měli změnit kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d45f-125">However, you should review the compiler warning message to determine whether you should change your application code.</span></span> <span data-ttu-id="5d45f-126">Pokud zpráva neodkazuje na vhodnou alternativu, měli byste provést jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="5d45f-126">If the message does not point to a suitable alternative, you should do either of the following:</span></span>

- <span data-ttu-id="5d45f-127">Pokud je to možné, změňte kód tak, že odeberete použití typu nebo členu.</span><span class="sxs-lookup"><span data-stu-id="5d45f-127">Change your code by removing the use of the type or member, if possible.</span></span>

     <span data-ttu-id="5d45f-128">-nebo-</span><span class="sxs-lookup"><span data-stu-id="5d45f-128">-or-</span></span>

- <span data-ttu-id="5d45f-129">Přečtěte si dokumentaci k této technologické oblasti a určete, jak reagovat na vyřazení.</span><span class="sxs-lookup"><span data-stu-id="5d45f-129">Review the documentation for this technology area to determine how to respond to the deprecation.</span></span>

<span data-ttu-id="5d45f-130">Můžete se rozhodnout, že nebudete znovu kompilovat existující kód v novější verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d45f-130">You may choose not to recompile existing code against a later version of the .NET Framework.</span></span> <span data-ttu-id="5d45f-131">Místo toho můžete určit verzi .NET Framework, na kterou se má existující zkompilovaný kód spouštět.</span><span class="sxs-lookup"><span data-stu-id="5d45f-131">Instead, you can specify the version of the .NET Framework against which your existing compiled code runs.</span></span> <span data-ttu-id="5d45f-132">Předpokládejme například, že máte aplikaci s názvem app1. exe, která byla zkompilována proti .NET Framework 3,5, ale chcete, aby aplikace běžela v .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="5d45f-132">For example, suppose that you have an application named app1.exe that was compiled against the .NET Framework 3.5, but you want the application to run against the .NET Framework 4.5.</span></span> <span data-ttu-id="5d45f-133">To vyžaduje následující kroky:</span><span class="sxs-lookup"><span data-stu-id="5d45f-133">This requires the following steps:</span></span>

1. <span data-ttu-id="5d45f-134">Vytvořte konfigurační soubor pro hlavní spustitelný soubor a pojmenujte jej *AppName*. exe. config, kde *AppName* je název spustitelného souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d45f-134">Create a configuration file for your main executable and name it *appName*.exe.config, where *appName* is the name of the application executable.</span></span> <span data-ttu-id="5d45f-135">Pro aplikaci s názvem *app1. exe* v našem příkladu byste vytvořili konfigurační soubor s názvem *app1. exe. config*.</span><span class="sxs-lookup"><span data-stu-id="5d45f-135">For the application named *app1.exe* in our example, you would create a configuration file named *app1.exe.config*.</span></span>

2. <span data-ttu-id="5d45f-136">Do konfiguračního souboru přidejte následující.</span><span class="sxs-lookup"><span data-stu-id="5d45f-136">Add the following to the configuration file.</span></span>

    ```xml
    <configuration>
       <startup> 
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

<span data-ttu-id="5d45f-137">Chcete-li cílit na konkrétní verzi .NET Framework, přiřaďte k atributu `version` jednu z následujících hodnot řetězce:</span><span class="sxs-lookup"><span data-stu-id="5d45f-137">To target a specific version of .NET Framework, assign one of the following string values to the `version` attribute:</span></span>

|<span data-ttu-id="5d45f-138">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5d45f-138">.NET Framework version</span></span>|<span data-ttu-id="5d45f-139">`version` řetězec</span><span class="sxs-lookup"><span data-stu-id="5d45f-139">`version` string</span></span>|
|-|-|
|<span data-ttu-id="5d45f-140">4.8</span><span class="sxs-lookup"><span data-stu-id="5d45f-140">4.8</span></span>|<span data-ttu-id="5d45f-141">4\.0</span><span class="sxs-lookup"><span data-stu-id="5d45f-141">v4.0</span></span>|
|<span data-ttu-id="5d45f-142">4,7 (včetně 4.7.1 a 4.7.2)</span><span class="sxs-lookup"><span data-stu-id="5d45f-142">4.7 (including 4.7.1 and 4.7.2)</span></span>|<span data-ttu-id="5d45f-143">4\.0</span><span class="sxs-lookup"><span data-stu-id="5d45f-143">v4.0</span></span>|
|<span data-ttu-id="5d45f-144">4,6 (včetně 4.6.1 a 4.6.2)</span><span class="sxs-lookup"><span data-stu-id="5d45f-144">4.6 (including 4.6.1 and 4.6.2)</span></span>|<span data-ttu-id="5d45f-145">4\.0</span><span class="sxs-lookup"><span data-stu-id="5d45f-145">v4.0</span></span>|
|<span data-ttu-id="5d45f-146">4,5 (včetně 4.5.1 a 4.5.2)</span><span class="sxs-lookup"><span data-stu-id="5d45f-146">4.5 (including 4.5.1 and 4.5.2)</span></span>|<span data-ttu-id="5d45f-147">4\.0</span><span class="sxs-lookup"><span data-stu-id="5d45f-147">v4.0</span></span>|
|<span data-ttu-id="5d45f-148">4</span><span class="sxs-lookup"><span data-stu-id="5d45f-148">4</span></span>|<span data-ttu-id="5d45f-149">4\.0</span><span class="sxs-lookup"><span data-stu-id="5d45f-149">v4.0</span></span>|
|<span data-ttu-id="5d45f-150">3.5</span><span class="sxs-lookup"><span data-stu-id="5d45f-150">3.5</span></span>|<span data-ttu-id="5d45f-151">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="5d45f-151">v2.0.50727</span></span>|
|<span data-ttu-id="5d45f-152">2.0</span><span class="sxs-lookup"><span data-stu-id="5d45f-152">2.0</span></span>|<span data-ttu-id="5d45f-153">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="5d45f-153">v2.0.50727</span></span>|
|<span data-ttu-id="5d45f-154">1.1</span><span class="sxs-lookup"><span data-stu-id="5d45f-154">1.1</span></span>|<span data-ttu-id="5d45f-155">v1.1.4322</span><span class="sxs-lookup"><span data-stu-id="5d45f-155">v1.1.4322</span></span>|
|<span data-ttu-id="5d45f-156">1.0</span><span class="sxs-lookup"><span data-stu-id="5d45f-156">1.0</span></span>|<span data-ttu-id="5d45f-157">v1.0.3705</span><span class="sxs-lookup"><span data-stu-id="5d45f-157">v1.0.3705</span></span>|

## <a name="obsolete-apis-for-net-framework-45-and-later-versions"></a><span data-ttu-id="5d45f-158">Zastaralá rozhraní API pro .NET Framework 4,5 a novější verze</span><span class="sxs-lookup"><span data-stu-id="5d45f-158">Obsolete APIs for .NET Framework 4.5 and later versions</span></span>

- [<span data-ttu-id="5d45f-159">Zastaralé typy</span><span class="sxs-lookup"><span data-stu-id="5d45f-159">Obsolete Types</span></span>](obsolete-types.md)
- [<span data-ttu-id="5d45f-160">Zastaralé členy</span><span class="sxs-lookup"><span data-stu-id="5d45f-160">Obsolete Members</span></span>](obsolete-members.md)

## <a name="obsolete-apis-for-previous-versions"></a><span data-ttu-id="5d45f-161">Zastaralá rozhraní API pro předchozí verze</span><span class="sxs-lookup"><span data-stu-id="5d45f-161">Obsolete APIs for previous versions</span></span>

- <span data-ttu-id="5d45f-162">[Zastaralé typy v .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5d45f-162">[Obsolete Types in .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span></span>
- <span data-ttu-id="5d45f-163">[Zastaralí členové ve .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5d45f-163">[Obsolete Members in .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span></span>
- <span data-ttu-id="5d45f-164">[Seznam zastaralých .NET Framework 3,5](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="5d45f-164">[.NET Framework 3.5 Obsolete List](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span></span>
- <span data-ttu-id="5d45f-165">[Seznam zastaralých .NET Framework 2,0](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="5d45f-165">[.NET Framework 2.0 Obsolete List](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="5d45f-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d45f-166">See also</span></span>

- [<span data-ttu-id="5d45f-167">\<element > supportedRuntime</span><span class="sxs-lookup"><span data-stu-id="5d45f-167">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
