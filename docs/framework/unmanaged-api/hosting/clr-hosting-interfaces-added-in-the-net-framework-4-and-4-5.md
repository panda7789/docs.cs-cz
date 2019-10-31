---
title: Rozhraní hostování CLR přidaná v rozhraní .NET Framework 4 a 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: aea88430d8f83234a1568bcaf433c2a75492e23a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195915"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="9c8c9-102">Rozhraní hostování CLR přidaná v rozhraní .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="9c8c9-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="9c8c9-103">Tato část popisuje rozhraní, která nespravované hostitele můžou použít k integraci modulu CLR (Common Language Runtime) v .NET Framework 4, .NET Framework 4,5 a novějších verzích do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="9c8c9-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework 4, .NET Framework 4.5, and later versions into their applications.</span></span> <span data-ttu-id="9c8c9-104">Tato rozhraní poskytují metody pro hostitele ke konfiguraci a načtení modulu runtime do procesu.</span><span class="sxs-lookup"><span data-stu-id="9c8c9-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="9c8c9-105">Počínaje .NET Framework 4 mají všechna hostující rozhraní následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="9c8c9-105">Starting with the .NET Framework 4, all hosting interfaces have the following characteristics:</span></span>  
  
- <span data-ttu-id="9c8c9-106">Používají správu životnosti (`AddRef` a `Release`), zapouzdření (implicitní kontext) a `QueryInterface` z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="9c8c9-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
- <span data-ttu-id="9c8c9-107">Nepoužívají typy COM, jako `BSTR`, `SAFEARRAY`nebo `VARIANT`.</span><span class="sxs-lookup"><span data-stu-id="9c8c9-107">They do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
- <span data-ttu-id="9c8c9-108">Neexistují žádné modely Apartment, agregace ani aktivace registru, které používají [funkci CoCreateInstance](https://go.microsoft.com/fwlink/?LinkId=142894).</span><span class="sxs-lookup"><span data-stu-id="9c8c9-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](https://go.microsoft.com/fwlink/?LinkId=142894).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c8c9-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9c8c9-109">In This Section</span></span>  
 [<span data-ttu-id="9c8c9-110">ICLRAppDomainResourceMonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c8c9-110">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="9c8c9-111">Poskytuje metody, které kontrolují paměť a využití procesoru v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c8c9-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="9c8c9-112">ICLRDomainManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c8c9-112">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 <span data-ttu-id="9c8c9-113">Umožňuje hostiteli zadat správce aplikační domény, který se použije k inicializaci výchozí domény aplikace, a zadat vlastnosti inicializace.</span><span class="sxs-lookup"><span data-stu-id="9c8c9-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="9c8c9-114">ICLRGCManager2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c8c9-114">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 <span data-ttu-id="9c8c9-115">Poskytuje metodu [SetGCStartupLimitsEx –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) , která umožňuje hostiteli nastavit velikost segmentu uvolňování paměti a maximální velikost 0. generace systému uvolňování paměti na hodnoty větší než `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="9c8c9-115">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="9c8c9-116">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c8c9-116">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 <span data-ttu-id="9c8c9-117">Poskytuje metody, které vracejí konkrétní verzi CLR, vypíše všechny nainstalované CLRs, vypíše všechny vnitroprocesové moduly runtime, vrátí aktivační rozhraní a zjistí verzi CLR použitou pro zkompilování sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c8c9-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="9c8c9-118">ICLRMetaHostPolicy – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c8c9-118">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="9c8c9-119">Poskytuje metodu [GetRequestedRuntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) , která poskytuje rozhraní CLR na základě kritérií zásad, spravovaného sestavení, verze a konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="9c8c9-119">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="9c8c9-120">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c8c9-120">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 <span data-ttu-id="9c8c9-121">Poskytuje metody, které vracejí informace o konkrétním modulu runtime, včetně verze, adresáře a stavu zatížení.</span><span class="sxs-lookup"><span data-stu-id="9c8c9-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="9c8c9-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c8c9-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 <span data-ttu-id="9c8c9-123">Poskytuje základní globální statické funkce pro podepisování sestavení se silnými názvy.</span><span class="sxs-lookup"><span data-stu-id="9c8c9-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="9c8c9-124">Všechny metody [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) vrací standardní model COM HRESULTs.</span><span class="sxs-lookup"><span data-stu-id="9c8c9-124">All the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="9c8c9-125">ICLRStrongName2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c8c9-125">ICLRStrongName2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 <span data-ttu-id="9c8c9-126">Poskytuje možnost vytvářet silné názvy pomocí skupiny SHA-2 algoritmů Secure Hash (SHA-256, SHA-384 a SHA-512).</span><span class="sxs-lookup"><span data-stu-id="9c8c9-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="9c8c9-127">ICLRTask2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c8c9-127">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 <span data-ttu-id="9c8c9-128">Poskytuje všechny funkce [rozhraní ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); Kromě toho poskytuje metody, které umožňují, aby bylo přerušení vlákna zpožděno v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="9c8c9-128">Provides all the functionality of the [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9c8c9-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9c8c9-129">Related Sections</span></span>  
 [<span data-ttu-id="9c8c9-130">Zastaralá rozhraní a třídy typu Coclass pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="9c8c9-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="9c8c9-131">Popisuje rozhraní hostování poskytovaná pomocí .NET Framework verze 1,0 a 1,1.</span><span class="sxs-lookup"><span data-stu-id="9c8c9-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="9c8c9-132">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="9c8c9-132">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="9c8c9-133">Popisuje rozhraní hostování poskytovaná pomocí .NET Framework verze 2,0, 3,0 a 3,5.</span><span class="sxs-lookup"><span data-stu-id="9c8c9-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="9c8c9-134">Hostování</span><span class="sxs-lookup"><span data-stu-id="9c8c9-134">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="9c8c9-135">Zavádí hostování v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9c8c9-135">Introduces hosting in the .NET Framework.</span></span>
