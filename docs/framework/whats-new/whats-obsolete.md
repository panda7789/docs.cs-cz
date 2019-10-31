---
title: Zastaralé položky v knihovně tříd .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
ms.openlocfilehash: 4de441ff55c3728f43742d6e467deeb47f400507
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140596"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a><span data-ttu-id="f6a51-102">Zastaralé položky v knihovně tříd .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f6a51-102">What's obsolete in the .NET Framework class library</span></span>

<span data-ttu-id="f6a51-103">.NET Framework se v průběhu času mění.</span><span class="sxs-lookup"><span data-stu-id="f6a51-103">The .NET Framework changes over time.</span></span> <span data-ttu-id="f6a51-104">Každá nová verze přidává nové typy a členy typu, které poskytují nové funkce.</span><span class="sxs-lookup"><span data-stu-id="f6a51-104">Each new version adds new types and type members that provide new functionality.</span></span> <span data-ttu-id="f6a51-105">Existující typy a jejich členové se také mění v průběhu času.</span><span class="sxs-lookup"><span data-stu-id="f6a51-105">Existing types and their members also change over time.</span></span> <span data-ttu-id="f6a51-106">Některé typy jsou například méně důležité, protože technologie, kterou podporují, je nahrazena novou technologií a některé metody jsou nahrazené novějšími metodami, které jsou vhodnější nebo jsou pro něj plně funkční.</span><span class="sxs-lookup"><span data-stu-id="f6a51-106">For example, some types become less important as the technology they support is replaced by a new technology, and some methods are superseded by newer methods that are either more convenient or more full-featured.</span></span>

<span data-ttu-id="f6a51-107">.NET Framework a modul CLR (Common Language Runtime) se snaží podporovat zpětnou kompatibilitu (umožňující aplikacím vyvinutým pomocí jedné verze .NET Framework běžet v další verzi .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="f6a51-107">The .NET Framework and the common language runtime strive to support backward compatibility (allowing applications that were developed with one version of the .NET Framework to run on the next version of the .NET Framework).</span></span> <span data-ttu-id="f6a51-108">Díky tomu je obtížné jednoduše odebrat typ nebo člen typu.</span><span class="sxs-lookup"><span data-stu-id="f6a51-108">This makes it difficult to simply remove a type or a type member.</span></span> <span data-ttu-id="f6a51-109">Místo toho .NET Framework označuje, že typ nebo člen typu by již neměl být použit tak, že ho označíte jako zastaralé nebo zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f6a51-109">Instead, the .NET Framework indicates that a type or a type member should no longer be used by marking it as obsolete or deprecated.</span></span> <span data-ttu-id="f6a51-110">Zahození typu nebo členu zahrnuje označení IT, aby se vývojáři dozvěděli, že se o jeho odebrání projeví a mají čas na reakci.</span><span class="sxs-lookup"><span data-stu-id="f6a51-110">Deprecating a type or a member involves marking it so that developers are aware it will go away and have time to respond to its removal.</span></span> <span data-ttu-id="f6a51-111">Stávající kód, který používá typ nebo člen, však nadále běží v nové verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f6a51-111">However, existing code that uses the type or member continues to run in the new version of the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="f6a51-112">*Zastaralé* a *zastaralé* výrazy mají stejný význam při použití na typy a členy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f6a51-112">The terms *obsolete* and *deprecated* have the same meaning when applied to the types and members of the .NET Framework.</span></span>

## <a name="the-obsoleteattribute-attribute"></a><span data-ttu-id="f6a51-113">Atribut ObsoleteAttribute</span><span class="sxs-lookup"><span data-stu-id="f6a51-113">The ObsoleteAttribute attribute</span></span>

<span data-ttu-id="f6a51-114">.NET Framework označuje, že typ nebo člen typu je zastaralý, označením s atributem <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f6a51-114">The .NET Framework indicates that a type or type member is obsolete by marking it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="f6a51-115">Použití atributu na typ nebo člen označuje, že typ nebo člen bude v některé budoucí verzi .NET Framework odebrán, aniž by došlo k narušení zkompilovaného kódu, který používá daného člena.</span><span class="sxs-lookup"><span data-stu-id="f6a51-115">Applying the attribute to a type or member indicates that type or member will be removed in some future version of the .NET Framework without breaking compiled code that uses that member.</span></span>

<span data-ttu-id="f6a51-116">Kromě toho, že je typ nebo člen typu zastaralý, <xref:System.ObsoleteAttribute> definuje způsob, jakým kompilátor zpracovává zdrojový kód, který obsahuje daný typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="f6a51-116">In addition to indicating that a type or a type member is obsolete, <xref:System.ObsoleteAttribute> defines how the compiler handles source code that includes that type or member.</span></span> <span data-ttu-id="f6a51-117">Kompilátor může kompilovat kód, ale generovat zprávu upozornění nebo může zacházet s používáním typu nebo členu jako chyby.</span><span class="sxs-lookup"><span data-stu-id="f6a51-117">The compiler can compile the code but emit a warning message, or it can treat the use of the type or member as an error.</span></span> <span data-ttu-id="f6a51-118">V prvním případě může být kód úspěšně zkompilován, ale varovná zpráva označuje, že typ nebo člen je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="f6a51-118">In the first case, the code can successfully compile, but a warning message indicates that the type or member is obsolete.</span></span> <span data-ttu-id="f6a51-119">Ve druhém případě kompilace dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="f6a51-119">In the second case, compilation fails.</span></span>

<span data-ttu-id="f6a51-120">I v případě, že kompilace vytvoří chybu namísto zprávy upozornění, <xref:System.ObsoleteAttribute> nemá vliv na chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="f6a51-120">Even if compilation produces an error instead of a warning message, <xref:System.ObsoleteAttribute> does not affect run-time behavior.</span></span> <span data-ttu-id="f6a51-121">To znamená, že aplikace, které používají typ nebo člena a které byly úspěšně kompilovány, budou vždy spouštěny úspěšně.</span><span class="sxs-lookup"><span data-stu-id="f6a51-121">That is, applications that use the type or member and that have compiled successfully will always run successfully.</span></span> <span data-ttu-id="f6a51-122">Pouze pokus o rekompilaci aplikace, která používá typ nebo člen, se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="f6a51-122">Only the attempt to recompile an application that uses the type or member fails.</span></span>

## <a name="how-to-handle-obsolete-types-and-members"></a><span data-ttu-id="f6a51-123">Postup zpracování zastaralých typů a členů</span><span class="sxs-lookup"><span data-stu-id="f6a51-123">How to handle obsolete types and members</span></span>

<span data-ttu-id="f6a51-124">Když upgradujete a znovu zkompilujete stávající kód pomocí zastaralého typu nebo členu, který vytvoří upozornění kompilátoru v aplikaci, je dokonale přijatelné.</span><span class="sxs-lookup"><span data-stu-id="f6a51-124">When you upgrade and recompile existing code, using an obsolete type or member that produces a compiler warning in your application is perfectly acceptable.</span></span> <span data-ttu-id="f6a51-125">Měli byste ale zkontrolovat zprávu s upozorněním kompilátoru, abyste zjistili, jestli byste měli změnit kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="f6a51-125">However, you should review the compiler warning message to determine whether you should change your application code.</span></span> <span data-ttu-id="f6a51-126">Pokud zpráva neodkazuje na vhodnou alternativu, měli byste provést jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="f6a51-126">If the message does not point to a suitable alternative, you should do either of the following:</span></span>

- <span data-ttu-id="f6a51-127">Pokud je to možné, změňte kód tak, že odeberete použití typu nebo členu.</span><span class="sxs-lookup"><span data-stu-id="f6a51-127">Change your code by removing the use of the type or member, if possible.</span></span>

     <span data-ttu-id="f6a51-128">-nebo-</span><span class="sxs-lookup"><span data-stu-id="f6a51-128">-or-</span></span>

- <span data-ttu-id="f6a51-129">Přečtěte si dokumentaci k této technologické oblasti a určete, jak reagovat na vyřazení.</span><span class="sxs-lookup"><span data-stu-id="f6a51-129">Review the documentation for this technology area to determine how to respond to the deprecation.</span></span>

<span data-ttu-id="f6a51-130">Můžete se rozhodnout, že nebudete znovu kompilovat existující kód v novější verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f6a51-130">You may choose not to recompile existing code against a later version of the .NET Framework.</span></span> <span data-ttu-id="f6a51-131">Místo toho můžete určit verzi .NET Framework, na kterou se má existující zkompilovaný kód spouštět.</span><span class="sxs-lookup"><span data-stu-id="f6a51-131">Instead, you can specify the version of the .NET Framework against which your existing compiled code runs.</span></span> <span data-ttu-id="f6a51-132">Předpokládejme například, že máte aplikaci s názvem app1. exe, která byla zkompilována proti .NET Framework 3,5, ale chcete, aby aplikace běžela v .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="f6a51-132">For example, suppose that you have an application named app1.exe that was compiled against the .NET Framework 3.5, but you want the application to run against the .NET Framework 4.5.</span></span> <span data-ttu-id="f6a51-133">To vyžaduje následující kroky:</span><span class="sxs-lookup"><span data-stu-id="f6a51-133">This requires the following steps:</span></span>

1. <span data-ttu-id="f6a51-134">Vytvořte konfigurační soubor pro hlavní spustitelný soubor a pojmenujte jej *AppName*. exe. config, kde *AppName* je název spustitelného souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f6a51-134">Create a configuration file for your main executable and name it *appName*.exe.config, where *appName* is the name of the application executable.</span></span> <span data-ttu-id="f6a51-135">Pro aplikaci s názvem app1. exe v našem příkladu byste vytvořili konfigurační soubor s názvem app1. exe. config.</span><span class="sxs-lookup"><span data-stu-id="f6a51-135">For the application named app1.exe in our example, you would create a configuration file named app1.exe.config.</span></span>

2. <span data-ttu-id="f6a51-136">Do konfiguračního souboru přidejte následující.</span><span class="sxs-lookup"><span data-stu-id="f6a51-136">Add the following to the configuration file.</span></span>

    ```xml
    <configuration>
       <startup> 
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

<span data-ttu-id="f6a51-137">V následující tabulce jsou uvedeny řetězcové hodnoty, které můžete přiřadit k atributu `version` pro cílení na konkrétní verzi .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f6a51-137">The following table lists the string values that you can assign to the `version` attribute to target a specific version of the .NET Framework:</span></span>

|<span data-ttu-id="f6a51-138">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f6a51-138">.NET Framework version</span></span>|<span data-ttu-id="f6a51-139">`version` řetězec</span><span class="sxs-lookup"><span data-stu-id="f6a51-139">`version` string</span></span>|
|-|-|
|<span data-ttu-id="f6a51-140">4,8</span><span class="sxs-lookup"><span data-stu-id="f6a51-140">4.8</span></span>|<span data-ttu-id="f6a51-141">4\.0</span><span class="sxs-lookup"><span data-stu-id="f6a51-141">v4.0</span></span>|
|<span data-ttu-id="f6a51-142">4,7 (včetně 4.7.1 a 4.7.2)</span><span class="sxs-lookup"><span data-stu-id="f6a51-142">4.7 (including 4.7.1 and 4.7.2)</span></span>|<span data-ttu-id="f6a51-143">4\.0</span><span class="sxs-lookup"><span data-stu-id="f6a51-143">v4.0</span></span>|
|<span data-ttu-id="f6a51-144">4,6 (včetně 4.6.1 a 4.6.2)</span><span class="sxs-lookup"><span data-stu-id="f6a51-144">4.6 (including 4.6.1 and 4.6.2)</span></span>|<span data-ttu-id="f6a51-145">4\.0</span><span class="sxs-lookup"><span data-stu-id="f6a51-145">v4.0</span></span>|
|<span data-ttu-id="f6a51-146">4,5 (včetně 4.5.1 a 4.5.2)</span><span class="sxs-lookup"><span data-stu-id="f6a51-146">4.5 (including 4.5.1 and 4.5.2)</span></span>|<span data-ttu-id="f6a51-147">4\.0</span><span class="sxs-lookup"><span data-stu-id="f6a51-147">v4.0</span></span>|
|<span data-ttu-id="f6a51-148">4</span><span class="sxs-lookup"><span data-stu-id="f6a51-148">4</span></span>|<span data-ttu-id="f6a51-149">4\.0</span><span class="sxs-lookup"><span data-stu-id="f6a51-149">v4.0</span></span>|
|<span data-ttu-id="f6a51-150">3.5</span><span class="sxs-lookup"><span data-stu-id="f6a51-150">3.5</span></span>|<span data-ttu-id="f6a51-151">v 2.0.50727</span><span class="sxs-lookup"><span data-stu-id="f6a51-151">v2.0.50727</span></span>|
|<span data-ttu-id="f6a51-152">2.0</span><span class="sxs-lookup"><span data-stu-id="f6a51-152">2.0</span></span>|<span data-ttu-id="f6a51-153">v 2.0.50727</span><span class="sxs-lookup"><span data-stu-id="f6a51-153">v2.0.50727</span></span>|
|<span data-ttu-id="f6a51-154">1.1</span><span class="sxs-lookup"><span data-stu-id="f6a51-154">1.1</span></span>|<span data-ttu-id="f6a51-155">v 1.1.4322</span><span class="sxs-lookup"><span data-stu-id="f6a51-155">v1.1.4322</span></span>|
|<span data-ttu-id="f6a51-156">1.0</span><span class="sxs-lookup"><span data-stu-id="f6a51-156">1.0</span></span>|<span data-ttu-id="f6a51-157">v 1.0.3705</span><span class="sxs-lookup"><span data-stu-id="f6a51-157">v1.0.3705</span></span>|

## <a name="obsolete-lists-for-the-net-framework-45-and-later-versions"></a><span data-ttu-id="f6a51-158">Zastaralé seznamy pro .NET Framework 4,5 a novější verze</span><span class="sxs-lookup"><span data-stu-id="f6a51-158">Obsolete lists for the .NET Framework 4.5 and later versions</span></span>

- [<span data-ttu-id="f6a51-159">Zastaralé typy</span><span class="sxs-lookup"><span data-stu-id="f6a51-159">Obsolete Types</span></span>](obsolete-types.md)
- [<span data-ttu-id="f6a51-160">Zastaralé členy</span><span class="sxs-lookup"><span data-stu-id="f6a51-160">Obsolete Members</span></span>](obsolete-members.md)

## <a name="obsolete-lists-for-previous-versions"></a><span data-ttu-id="f6a51-161">Zastaralé seznamy pro předchozí verze</span><span class="sxs-lookup"><span data-stu-id="f6a51-161">Obsolete lists for previous versions</span></span>

- <span data-ttu-id="f6a51-162">[Zastaralé typy v .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f6a51-162">[Obsolete Types in the .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span></span>

- <span data-ttu-id="f6a51-163">[Zastaralí členové v .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f6a51-163">[Obsolete Members in the .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span></span>

- <span data-ttu-id="f6a51-164">[Seznam zastaralých .NET Framework 3,5](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="f6a51-164">[.NET Framework 3.5 Obsolete List](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span></span>

- <span data-ttu-id="f6a51-165">[Seznam zastaralých .NET Framework 2,0](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="f6a51-165">[.NET Framework 2.0 Obsolete List](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="f6a51-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6a51-166">See also</span></span>

- [<span data-ttu-id="f6a51-167">\<element > supportedRuntime</span><span class="sxs-lookup"><span data-stu-id="f6a51-167">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
