---
title: "Rozhraní hostování CLR přidaná v rozhraní .NET Framework 4 a 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61231715a24978e7fe57b2c9e87e7968dc0fdbc5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="89d59-102">Rozhraní hostování CLR přidaná v rozhraní .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="89d59-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="89d59-103">Tato část popisuje rozhraní, která nespravované hostitelů můžete použít k integraci common language runtime (CLR) v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]a novější verze do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="89d59-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], and later versions into their applications.</span></span> <span data-ttu-id="89d59-104">Tato rozhraní poskytují metody pro hostitele ke konfiguraci a načtení modulu runtime do procesu.</span><span class="sxs-lookup"><span data-stu-id="89d59-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="89d59-105">Od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], všechny hostingu rozhraní mít následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="89d59-105">Starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], all hosting interfaces have the following characteristics:</span></span>  
  
-   <span data-ttu-id="89d59-106">Používají správu životního cyklu (`AddRef` a `Release`), zapouzdření (implicitní kontextu) a `QueryInterface` z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="89d59-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
-   <span data-ttu-id="89d59-107">Existuje nepoužívejte typy modelu COM, jako `BSTR`, `SAFEARRAY`, nebo `VARIANT`.</span><span class="sxs-lookup"><span data-stu-id="89d59-107">There do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
-   <span data-ttu-id="89d59-108">Nejsou žádné modely typu apartment, agregace nebo registru aktivace, použít [funkce CoCreateInstance](http://go.microsoft.com/fwlink/?LinkId=142894).</span><span class="sxs-lookup"><span data-stu-id="89d59-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](http://go.microsoft.com/fwlink/?LinkId=142894).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="89d59-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="89d59-109">In This Section</span></span>  
 [<span data-ttu-id="89d59-110">ICLRAppDomainResourceMonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89d59-110">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="89d59-111">Poskytuje metody, které zkontrolovat doménu aplikace využití paměti a procesoru.</span><span class="sxs-lookup"><span data-stu-id="89d59-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="89d59-112">ICLRDomainManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89d59-112">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 <span data-ttu-id="89d59-113">Umožňuje na hostiteli a poté zadejte správce domény aplikace, který se použije k chybě při inicializaci výchozí doméně aplikace a k určení inicializační vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="89d59-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="89d59-114">ICLRGCManager2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89d59-114">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 <span data-ttu-id="89d59-115">Poskytuje [setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metoda, která umožňuje pro hostitele a nastavte velikost segmentu kolekce paměti a maximální velikost systém kolekce paměti generace 0 hodnoty větší než `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="89d59-115">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="89d59-116">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89d59-116">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 <span data-ttu-id="89d59-117">Poskytuje metody vrátit konkrétní verzi modulu CLR se zobrazí seznam všech nainstalovaných CLRs, seznamu všechny moduly Runtime v procesu, vraťte rozhraní aktivace a zjistit verze CLR používá ke kompilaci sestavení.</span><span class="sxs-lookup"><span data-stu-id="89d59-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="89d59-118">ICLRMetaHostPolicy – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89d59-118">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="89d59-119">Poskytuje [getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metoda, která poskytuje CLR rozhraní na základě zásad kritéria, spravované sestavení, verze a konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="89d59-119">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="89d59-120">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89d59-120">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 <span data-ttu-id="89d59-121">Poskytuje metody, které vracejí informace o konkrétní modul runtime, včetně verze, adresář a stavové zatížení.</span><span class="sxs-lookup"><span data-stu-id="89d59-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="89d59-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89d59-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 <span data-ttu-id="89d59-123">Poskytuje základní globální statické funkce pro podepisování sestavení se silnými názvy.</span><span class="sxs-lookup"><span data-stu-id="89d59-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="89d59-124">Všechny [iclrstrongname –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) metody vrací standardní hodnoty HRESULT COM.</span><span class="sxs-lookup"><span data-stu-id="89d59-124">All the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="89d59-125">ICLRStrongName2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89d59-125">ICLRStrongName2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 <span data-ttu-id="89d59-126">Poskytuje možnost vytvořit silné názvy pomocí skupiny zabezpečení (SHA-256, SHA-384 a SHA-512) algoritmy Hash SHA-2.</span><span class="sxs-lookup"><span data-stu-id="89d59-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="89d59-127">ICLRTask2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89d59-127">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 <span data-ttu-id="89d59-128">Obsahuje všechny funkce [iclrtask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); kromě toho poskytuje metody, které umožňují zrušení vláken na opožděno na aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="89d59-128">Provides all the functionality of the [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="89d59-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="89d59-129">Related Sections</span></span>  
 [<span data-ttu-id="89d59-130">Zastaralá rozhraní a třídy typu Coclass pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="89d59-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="89d59-131">Popisuje rozhraní hostování součástí rozhraní .NET Framework verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="89d59-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="89d59-132">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="89d59-132">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="89d59-133">Popisuje rozhraní hostování součástí rozhraní .NET Framework verze 2.0, 3.0 a 3.5.</span><span class="sxs-lookup"><span data-stu-id="89d59-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="89d59-134">Hostování</span><span class="sxs-lookup"><span data-stu-id="89d59-134">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="89d59-135">Představuje hostování v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="89d59-135">Introduces hosting in the .NET Framework.</span></span>
