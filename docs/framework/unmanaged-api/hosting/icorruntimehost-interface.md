---
title: ICorRuntimeHost – rozhraní
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
ms.openlocfilehash: 4b8018bb84dea08987d91f351b1ab0d9f3b48c56
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503897"
---
# <a name="icorruntimehost-interface"></a><span data-ttu-id="87a99-102">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87a99-102">ICorRuntimeHost Interface</span></span>
<span data-ttu-id="87a99-103">Poskytuje metody, které umožňují hostiteli explicitně spustit a zastavit modul CLR (Common Language Runtime), vytvořit a nakonfigurovat domény aplikace, získat přístup k výchozí doméně a vytvořit výčet všech domén spuštěných v procesu.</span><span class="sxs-lookup"><span data-stu-id="87a99-103">Provides methods that enable the host to start and stop the common language runtime (CLR) explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>  
  
 <span data-ttu-id="87a99-104">V .NET Framework verze 2,0 je toto rozhraní nahrazeno [ICLRRuntimeHost](iclrruntimehost-interface.md).</span><span class="sxs-lookup"><span data-stu-id="87a99-104">In the .NET Framework version 2.0, this interface is superceded by [ICLRRuntimeHost](iclrruntimehost-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87a99-105">Metody</span><span class="sxs-lookup"><span data-stu-id="87a99-105">Methods</span></span>  
  
|<span data-ttu-id="87a99-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-106">Method</span></span>|<span data-ttu-id="87a99-107">Description</span><span class="sxs-lookup"><span data-stu-id="87a99-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87a99-108">CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-108">CloseEnum Method</span></span>](icorruntimehost-closeenum-method.md)|<span data-ttu-id="87a99-109">Obnoví enumerátor domény zpátky na začátek seznamu domén.</span><span class="sxs-lookup"><span data-stu-id="87a99-109">Resets a domain enumerator back to the beginning of the domain list.</span></span>|  
|[<span data-ttu-id="87a99-110">CreateDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-110">CreateDomain Method</span></span>](icorruntimehost-createdomain-method.md)|<span data-ttu-id="87a99-111">Vytvoří doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="87a99-111">Creates an application domain.</span></span> <span data-ttu-id="87a99-112">Volající obdrží ukazatel rozhraní typu <xref:System._AppDomain> na instanci typu <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="87a99-112">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>|  
|[<span data-ttu-id="87a99-113">CreateDomainEx – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-113">CreateDomainEx Method</span></span>](icorruntimehost-createdomainex-method.md)|<span data-ttu-id="87a99-114">Vytvoří doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="87a99-114">Creates an application domain.</span></span> <span data-ttu-id="87a99-115">Tato metoda umožňuje volajícímu předat instanci IAppDomainSetup – ke konfiguraci dalších funkcí vrácené <xref:System._AppDomain> instance.</span><span class="sxs-lookup"><span data-stu-id="87a99-115">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>|  
|[<span data-ttu-id="87a99-116">CreateDomainSetup – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-116">CreateDomainSetup Method</span></span>](icorruntimehost-createdomainsetup-method.md)|<span data-ttu-id="87a99-117">Načte ukazatel rozhraní typu `IAppDomainSetup` na <xref:System.AppDomainSetup> instanci.</span><span class="sxs-lookup"><span data-stu-id="87a99-117">Gets an interface pointer of type `IAppDomainSetup` to an <xref:System.AppDomainSetup> instance.</span></span> <span data-ttu-id="87a99-118">`IAppDomainSetup`poskytuje metody pro konfiguraci aspektů aplikační domény před jejich vytvořením.</span><span class="sxs-lookup"><span data-stu-id="87a99-118">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>|  
|[<span data-ttu-id="87a99-119">CreateEvidence – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-119">CreateEvidence Method</span></span>](icorruntimehost-createevidence-method.md)|<span data-ttu-id="87a99-120">Načte ukazatel rozhraní typu <xref:System.Security.Principal.IIdentity> , který umožňuje hostiteli vytvořit legitimaci zabezpečení, která bude předána [CreateDomain –](icorruntimehost-createdomain-method.md) nebo [CreateDomainEx –](icorruntimehost-createdomainex-method.md).</span><span class="sxs-lookup"><span data-stu-id="87a99-120">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity>, which allows the host to create security evidence to pass to [CreateDomain](icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md).</span></span>|  
|[<span data-ttu-id="87a99-121">CreateLogicalThreadState – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-121">CreateLogicalThreadState Method</span></span>](icorruntimehost-createlogicalthreadstate-method.md)|<span data-ttu-id="87a99-122">Nepoužívat.</span><span class="sxs-lookup"><span data-stu-id="87a99-122">Do not use.</span></span>|  
|[<span data-ttu-id="87a99-123">CurrentDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-123">CurrentDomain Method</span></span>](icorruntimehost-currentdomain-method.md)|<span data-ttu-id="87a99-124">Načte ukazatel rozhraní typu <xref:System._AppDomain> , který představuje doménu načtenou v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="87a99-124">Gets an interface pointer of type <xref:System._AppDomain> that represents the domain loaded on the current thread.</span></span>|  
|[<span data-ttu-id="87a99-125">DeleteLogicalThreadState – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-125">DeleteLogicalThreadState Method</span></span>](icorruntimehost-deletelogicalthreadstate-method.md)|<span data-ttu-id="87a99-126">Nepoužívat.</span><span class="sxs-lookup"><span data-stu-id="87a99-126">Do not use.</span></span>|  
|[<span data-ttu-id="87a99-127">EnumDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-127">EnumDomains Method</span></span>](icorruntimehost-enumdomains-method.md)|<span data-ttu-id="87a99-128">Získá enumerátor pro domény v aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="87a99-128">Gets an enumerator for the domains in the current process.</span></span>|  
|[<span data-ttu-id="87a99-129">GetConfiguration – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-129">GetConfiguration Method</span></span>](icorruntimehost-getconfiguration-method.md)|<span data-ttu-id="87a99-130">Získává objekt, který umožňuje hostiteli určit konfiguraci zpětného volání CLR.</span><span class="sxs-lookup"><span data-stu-id="87a99-130">Gets an object that allows the host to specify the callback configuration of the CLR.</span></span>|  
|[<span data-ttu-id="87a99-131">GetDefaultDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-131">GetDefaultDomain Method</span></span>](icorruntimehost-getdefaultdomain-method.md)|<span data-ttu-id="87a99-132">Načte ukazatel rozhraní typu <xref:System._AppDomain> , který představuje výchozí doménu pro aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="87a99-132">Gets an interface pointer of type <xref:System._AppDomain> that represents the default domain for the current process.</span></span>|  
|[<span data-ttu-id="87a99-133">LocksHeldByLogicalThread – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-133">LocksHeldByLogicalThread Method</span></span>](icorruntimehost-locksheldbylogicalthread-method.md)|<span data-ttu-id="87a99-134">Nepoužívat.</span><span class="sxs-lookup"><span data-stu-id="87a99-134">Do not use.</span></span>|  
|[<span data-ttu-id="87a99-135">MapFile – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-135">MapFile Method</span></span>](icorruntimehost-mapfile-method.md)|<span data-ttu-id="87a99-136">Namapuje zadaný soubor na paměť.</span><span class="sxs-lookup"><span data-stu-id="87a99-136">Maps the specified file into memory.</span></span> <span data-ttu-id="87a99-137">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="87a99-137">This method is obsolete.</span></span>|  
|[<span data-ttu-id="87a99-138">NextDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-138">NextDomain Method</span></span>](icorruntimehost-nextdomain-method.md)|<span data-ttu-id="87a99-139">Získá ukazatel rozhraní do další domény ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="87a99-139">Gets an interface pointer to the next domain in the enumeration.</span></span>|  
|[<span data-ttu-id="87a99-140">Start – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-140">Start Method</span></span>](icorruntimehost-start-method.md)|<span data-ttu-id="87a99-141">Spustí modul CLR.</span><span class="sxs-lookup"><span data-stu-id="87a99-141">Starts the CLR.</span></span>|  
|[<span data-ttu-id="87a99-142">Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-142">Stop Method</span></span>](icorruntimehost-stop-method.md)|<span data-ttu-id="87a99-143">Zastaví provádění kódu v modulu runtime pro aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="87a99-143">Stops the execution of code in the runtime for the current process.</span></span>|  
|[<span data-ttu-id="87a99-144">SwitchInLogicalThreadState – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-144">SwitchInLogicalThreadState Method</span></span>](icorruntimehost-switchinlogicalthreadstate-method.md)|<span data-ttu-id="87a99-145">Nepoužívat.</span><span class="sxs-lookup"><span data-stu-id="87a99-145">Do not use.</span></span>|  
|[<span data-ttu-id="87a99-146">SwitchOutLogicalThreadState – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-146">SwitchOutLogicalThreadState Method</span></span>](icorruntimehost-switchoutlogicalthreadstate-method.md)|<span data-ttu-id="87a99-147">Nepoužívat.</span><span class="sxs-lookup"><span data-stu-id="87a99-147">Do not use.</span></span>|  
|[<span data-ttu-id="87a99-148">UnloadDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="87a99-148">UnloadDomain Method</span></span>](icorruntimehost-unloaddomain-method.md)|<span data-ttu-id="87a99-149">Uvolní zadanou doménu aplikace z aktuálního procesu.</span><span class="sxs-lookup"><span data-stu-id="87a99-149">Unloads the specified application domain from the current process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="87a99-150">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87a99-150">Requirements</span></span>  
 <span data-ttu-id="87a99-151">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87a99-151">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87a99-152">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="87a99-152">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87a99-153">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="87a99-153">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87a99-154">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="87a99-154">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87a99-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87a99-155">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="87a99-156">Hosting</span><span class="sxs-lookup"><span data-stu-id="87a99-156">Hosting</span></span>](index.md)
- [<span data-ttu-id="87a99-157">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87a99-157">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- <span data-ttu-id="87a99-158">[Hostitelé modulu runtime](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87a99-158">[Runtime Hosts](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
- [<span data-ttu-id="87a99-159">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="87a99-159">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="87a99-160">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="87a99-160">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
