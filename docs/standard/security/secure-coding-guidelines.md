---
title: Pokyny k zabezpečenému kódování pro .NET
description: Navrhněte kód pro práci s. Vynuceně vynucovat oprávnění a jiné vynucování, které pomůžou zabránit škodlivému kódu v přístupu k datům nebo provádět jiné akce.
ms.date: 07/15/2020
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET], security
- code security, options
- security-neutral code
- security [.NET], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
ms.openlocfilehash: a05e0cec2814be88ac835d05601d5cf5f66383c3
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555953"
---
# <a name="secure-coding-guidelines"></a><span data-ttu-id="b4505-103">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="b4505-103">Secure coding guidelines</span></span>

<span data-ttu-id="b4505-104">Většina kódu aplikace může jednoduše použít infrastrukturu implementovanou rozhraním .NET.</span><span class="sxs-lookup"><span data-stu-id="b4505-104">Most application code can simply use the infrastructure implemented by .NET.</span></span> <span data-ttu-id="b4505-105">V některých případech je potřeba další zabezpečení specifické pro aplikace, které je postavené buď rozšířením systému zabezpečení, nebo pomocí nových ad hoc metod.</span><span class="sxs-lookup"><span data-stu-id="b4505-105">In some cases, additional application-specific security is required, built either by extending the security system or by using new ad hoc methods.</span></span>

<span data-ttu-id="b4505-106">Pomocí vynuceného oprávnění .NET a dalšího vynucování ve vašem kódu byste měli nasazovat bariéry, aby nedocházelo ke škodlivému kódu v přístupu k informacím, které nechcete mít nebo by prováděly jiné nežádoucí akce.</span><span class="sxs-lookup"><span data-stu-id="b4505-106">Using .NET enforced permissions and other enforcement in your code, you should erect barriers to prevent malicious code from accessing information that you don't want it to have or performing other undesirable actions.</span></span> <span data-ttu-id="b4505-107">Navíc je nutné přeškrtnout rovnováhu mezi zabezpečením a použitelností ve všech očekávaných scénářích pomocí důvěryhodného kódu.</span><span class="sxs-lookup"><span data-stu-id="b4505-107">Additionally, you must strike a balance between security and usability in all the expected scenarios using trusted code.</span></span>

<span data-ttu-id="b4505-108">Tento přehled popisuje různé způsoby, jak kód může být navržen pro práci se systémem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b4505-108">This overview describes the different ways code can be designed to work with the security system.</span></span>

## <a name="securing-resource-access"></a><span data-ttu-id="b4505-109">Zabezpečení přístupu k prostředkům</span><span class="sxs-lookup"><span data-stu-id="b4505-109">Securing resource access</span></span>

<span data-ttu-id="b4505-110">Při navrhování a psaní kódu musíte chránit a omezit přístup k prostředkům, zejména při použití nebo vyvolání kódu neznámého původu.</span><span class="sxs-lookup"><span data-stu-id="b4505-110">When designing and writing your code, you need to protect and limit the access that code has to resources, especially when using or invoking code of unknown origin.</span></span> <span data-ttu-id="b4505-111">Mějte proto na paměti následující postupy, abyste zajistili, že je váš kód zabezpečený:</span><span class="sxs-lookup"><span data-stu-id="b4505-111">So, keep in mind the following techniques to ensure your code is secure:</span></span>

- <span data-ttu-id="b4505-112">Nepoužívejte zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="b4505-112">Do not use Code Access Security (CAS).</span></span>

- <span data-ttu-id="b4505-113">Nepoužívejte částečně důvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="b4505-113">Do not use partial trusted code.</span></span>

- <span data-ttu-id="b4505-114">Nepoužívejte atribut [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) (APTCA).</span><span class="sxs-lookup"><span data-stu-id="b4505-114">Do not use the [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) attribute (APTCA).</span></span>

- <span data-ttu-id="b4505-115">Nepoužívejte vzdálenou komunikaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="b4505-115">Do not use .NET Remoting.</span></span>

- <span data-ttu-id="b4505-116">Nepoužívejte model DCOM (Distributed Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="b4505-116">Do not use Distributed Component Object Model (DCOM).</span></span>

- <span data-ttu-id="b4505-117">Nepoužívejte binární formátovací moduly.</span><span class="sxs-lookup"><span data-stu-id="b4505-117">Do not use binary formatters.</span></span>

<span data-ttu-id="b4505-118">Zabezpečení přístupu kódu a kód transparentní z hlediska zabezpečení nejsou podporovány jako hranice zabezpečení s částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="b4505-118">Code Access Security and Security-Transparent Code are not supported as a security boundary with partially trusted code.</span></span> <span data-ttu-id="b4505-119">Kód neznámého původu nedoporučujeme načítat ani spouštět, pokud nejsou nastavená alternativní bezpečnostní opatření.</span><span class="sxs-lookup"><span data-stu-id="b4505-119">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span> <span data-ttu-id="b4505-120">Alternativní bezpečnostní opatření:</span><span class="sxs-lookup"><span data-stu-id="b4505-120">The alternative security measures are:</span></span>

- <span data-ttu-id="b4505-121">Virtualizace</span><span class="sxs-lookup"><span data-stu-id="b4505-121">Virtualization</span></span>

- <span data-ttu-id="b4505-122">AppContainers</span><span class="sxs-lookup"><span data-stu-id="b4505-122">AppContainers</span></span>

- <span data-ttu-id="b4505-123">Uživatelé a oprávnění operačního systému (OS)</span><span class="sxs-lookup"><span data-stu-id="b4505-123">Operating system (OS) users and permissions</span></span>

- <span data-ttu-id="b4505-124">Kontejnery Hyper-V</span><span class="sxs-lookup"><span data-stu-id="b4505-124">Hyper-V containers</span></span>

## <a name="security-neutral-code"></a><span data-ttu-id="b4505-125">Neutrální kód pro zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b4505-125">Security-neutral code</span></span>

<span data-ttu-id="b4505-126">Kód neutrální z hlediska zabezpečení nijak nedělá explicitně se systémem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b4505-126">Security-neutral code does nothing explicit with the security system.</span></span> <span data-ttu-id="b4505-127">Spouští se bez jakýchkoli oprávnění, která obdrží.</span><span class="sxs-lookup"><span data-stu-id="b4505-127">It runs with whatever permissions it receives.</span></span> <span data-ttu-id="b4505-128">Přestože aplikace, které nedokázaly zachytit výjimky zabezpečení přidružené k chráněným operacím (například použití souborů, sítě atd.), mohou způsobit neošetřenou výjimku, kód neutrální od zabezpečení stále využívá technologie zabezpečení v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="b4505-128">Although applications that fail to catch security exceptions associated with protected operations (such as using files, networking, and so on) can result in an unhandled exception, security-neutral code still takes advantage of the security technologies in .NET.</span></span>

<span data-ttu-id="b4505-129">Knihovna neutrální od zabezpečení má zvláštní charakteristiky, které byste měli pochopit.</span><span class="sxs-lookup"><span data-stu-id="b4505-129">A security-neutral library has special characteristics that you should understand.</span></span> <span data-ttu-id="b4505-130">Předpokládejme, že vaše knihovna poskytuje prvky rozhraní API, které používají soubory, nebo volání nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="b4505-130">Suppose your library provides API elements that use files or call unmanaged code.</span></span> <span data-ttu-id="b4505-131">Pokud váš kód nemá odpovídající oprávnění, nebude spuštěn, jak je popsáno.</span><span class="sxs-lookup"><span data-stu-id="b4505-131">If your code doesn't have the corresponding permission, it won't run as described.</span></span> <span data-ttu-id="b4505-132">Nicméně i v případě, že má kód oprávnění, musí mít jakýkoli kód aplikace, který ji volá, stejné oprávnění, aby fungoval.</span><span class="sxs-lookup"><span data-stu-id="b4505-132">However, even if the code has the permission, any application code that calls it must have the same permission in order to work.</span></span> <span data-ttu-id="b4505-133">Pokud volající kód nemá správné oprávnění, <xref:System.Security.SecurityException> zobrazí se jako výsledek procházení zásobníku zabezpečení přístupu kódu.</span><span class="sxs-lookup"><span data-stu-id="b4505-133">If the calling code doesn't have the right permission, a <xref:System.Security.SecurityException> appears as a result of the code access security stack walk.</span></span>

## <a name="application-code-that-isnt-a-reusable-component"></a><span data-ttu-id="b4505-134">Kód aplikace, který není opakovaně použitelná součást</span><span class="sxs-lookup"><span data-stu-id="b4505-134">Application code that isn't a reusable component</span></span>

<span data-ttu-id="b4505-135">Pokud je váš kód součástí aplikace, která nebude volána jiným kódem, zabezpečení je jednoduché a speciální kódování nemusí být vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="b4505-135">If your code is part of an application that won't be called by other code, security is simple and special coding might not be required.</span></span> <span data-ttu-id="b4505-136">Nezapomeňte však, že škodlivý kód může zavolat váš kód.</span><span class="sxs-lookup"><span data-stu-id="b4505-136">However, remember that malicious code can call your code.</span></span> <span data-ttu-id="b4505-137">I když zabezpečení přístupu kódu může zabránit škodlivému kódu v přístupu k prostředkům, může takový kód pořád číst hodnoty polí nebo vlastností, které mohou obsahovat citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="b4505-137">While code access security might stop malicious code from accessing resources, such code could still read values of your fields or properties that might contain sensitive information.</span></span>

<span data-ttu-id="b4505-138">Kromě toho, pokud kód akceptuje vstup uživatele z Internetu nebo jiných nespolehlivých zdrojů, musíte mít pozor na škodlivý vstup.</span><span class="sxs-lookup"><span data-stu-id="b4505-138">Additionally, if your code accepts user input from the Internet or other unreliable sources, you must be careful about malicious input.</span></span>

## <a name="managed-wrapper-to-native-code-implementation"></a><span data-ttu-id="b4505-139">Spravovaná obálka s implementací nativního kódu</span><span class="sxs-lookup"><span data-stu-id="b4505-139">Managed wrapper to native code implementation</span></span>

<span data-ttu-id="b4505-140">Obvykle v tomto scénáři jsou některé užitečné funkce implementovány v nativním kódu, který chcete zpřístupnit spravovanému kódu.</span><span class="sxs-lookup"><span data-stu-id="b4505-140">Typically in this scenario, some useful functionality is implemented in native code that you want to make available to managed code.</span></span> <span data-ttu-id="b4505-141">Spravované obálky lze snadno psát pomocí volání platforem nebo zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="b4505-141">Managed wrappers are easy to write using either platform invoke or COM interop.</span></span> <span data-ttu-id="b4505-142">Nicméně pokud to uděláte, volající na vašich obálkách musí mít oprávnění nespravovaného kódu, aby bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="b4505-142">However, if you do this, callers of your wrappers must have unmanaged code rights in order to succeed.</span></span> <span data-ttu-id="b4505-143">V části výchozí zásady to znamená, že kód stažený z intranetu nebo z Internetu nebude fungovat s obálkami.</span><span class="sxs-lookup"><span data-stu-id="b4505-143">Under default policy, this means that code downloaded from an intranet or the Internet won't work with the wrappers.</span></span>

<span data-ttu-id="b4505-144">Místo poskytování nespravovaných oprávnění kódu pro všechny aplikace, které používají tyto obálky, je lepší poskytnout tato práva pouze kódu obálky.</span><span class="sxs-lookup"><span data-stu-id="b4505-144">Instead of giving unmanaged code rights to all applications that use these wrappers, it's better to give these rights only to the wrapper code.</span></span> <span data-ttu-id="b4505-145">Pokud základní funkce zveřejňuje žádné prostředky a implementace je také bezpečná, Obálka musí vyhodnotit její práva, což umožní jakémukoli volání prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="b4505-145">If the underlying functionality exposes no resources and the implementation is likewise safe, the wrapper only needs to assert its rights, which enables any code to call through it.</span></span> <span data-ttu-id="b4505-146">V případě, že se jedná o prostředky, musí být kódování zabezpečení stejné jako v případě kódu knihovny popsané v další části.</span><span class="sxs-lookup"><span data-stu-id="b4505-146">When resources are involved, security coding should be the same as the library code case described in the next section.</span></span> <span data-ttu-id="b4505-147">Vzhledem k tomu, že obálka potenciálně vystavuje volajícím tyto prostředky, pečlivé ověření bezpečnosti nativního kódu je nezbytné a je odpovědností obálky.</span><span class="sxs-lookup"><span data-stu-id="b4505-147">Because the wrapper is potentially exposing callers to these resources, careful verification of the safety of the native code is necessary and is the wrapper's responsibility.</span></span>

## <a name="library-code-that-exposes-protected-resources"></a><span data-ttu-id="b4505-148">Kód knihovny, který zveřejňuje chráněné prostředky</span><span class="sxs-lookup"><span data-stu-id="b4505-148">Library code that exposes protected resources</span></span>

<span data-ttu-id="b4505-149">Následující přístup je nejužitečnější, tedy potenciálně nebezpečný (Pokud je to správně proveden) pro kódování zabezpečení: vaše knihovna slouží jako rozhraní pro jiný kód pro přístup k určitým prostředkům, které nejsou jinak dostupné, stejně jako třídy .NET vynutila oprávnění pro prostředky, které používají.</span><span class="sxs-lookup"><span data-stu-id="b4505-149">The following approach is the most powerful and hence potentially dangerous (if done incorrectly) for security coding: your library serves as an interface for other code to access certain resources that aren't otherwise available, just as the .NET classes enforce permissions for the resources they use.</span></span> <span data-ttu-id="b4505-150">Bez ohledu na to, jaký stav vystavíte, musí váš kód nejdřív vyžadovat oprávnění odpovídající prostředku (to znamená, že musí provést kontrolu zabezpečení) a pak obvykle vyhodnotit jeho práva k provedení skutečné operace.</span><span class="sxs-lookup"><span data-stu-id="b4505-150">Wherever you expose a resource, your code must first demand the permission appropriate to the resource (that is, it must perform a security check) and then typically assert its rights to perform the actual operation.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4505-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4505-151">See also</span></span>

- [<span data-ttu-id="b4505-152">Zabezpečení stavových dat</span><span class="sxs-lookup"><span data-stu-id="b4505-152">Securing State Data</span></span>](securing-state-data.md)
- [<span data-ttu-id="b4505-153">Zabezpečení a uživatelský vstup</span><span class="sxs-lookup"><span data-stu-id="b4505-153">Security and User Input</span></span>](security-and-user-input.md)
- [<span data-ttu-id="b4505-154">Zabezpečení a konflikty časování</span><span class="sxs-lookup"><span data-stu-id="b4505-154">Security and Race Conditions</span></span>](security-and-race-conditions.md)
- [<span data-ttu-id="b4505-155">Zabezpečení a průběžné vytváření kódu</span><span class="sxs-lookup"><span data-stu-id="b4505-155">Security and On-the-Fly Code Generation</span></span>](security-and-on-the-fly-code-generation.md)
- [<span data-ttu-id="b4505-156">Zabezpečení na základě rolí</span><span class="sxs-lookup"><span data-stu-id="b4505-156">Role-Based Security</span></span>](role-based-security.md)
- [<span data-ttu-id="b4505-157">ASP.NET Core zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b4505-157">ASP.NET Core Security</span></span>](/aspnet/core/security/)
