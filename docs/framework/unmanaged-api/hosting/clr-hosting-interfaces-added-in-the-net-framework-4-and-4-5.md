---
title: Rozhraní hostování CLR přidaná v rozhraní .NET Framework 4 a 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6405c61429d56b125fd0327824482bf702e41319
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380282"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="bbbde-102">Rozhraní hostování CLR přidaná v rozhraní .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="bbbde-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="bbbde-103">Tato část popisuje nespravovaná rozhraní můžete integrovat common language runtime (CLR) v nastavení používají hostitelé [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], rozhraní .NET Framework 4.5 a novější verze do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="bbbde-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], .NET Framework 4.5, and later versions into their applications.</span></span> <span data-ttu-id="bbbde-104">Tato rozhraní poskytuje metody pro hostitele konfigurace a načtení modulu runtime do procesu.</span><span class="sxs-lookup"><span data-stu-id="bbbde-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="bbbde-105">Počínaje [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], všechny hostitelské rozhraní mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="bbbde-105">Starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], all hosting interfaces have the following characteristics:</span></span>  
  
- <span data-ttu-id="bbbde-106">Správa životního cyklu používají (`AddRef` a `Release`), zapouzdření (implicitní context) a `QueryInterface` z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="bbbde-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
- <span data-ttu-id="bbbde-107">Existuje nepoužívejte typy modelu COM, jako `BSTR`, `SAFEARRAY`, nebo `VARIANT`.</span><span class="sxs-lookup"><span data-stu-id="bbbde-107">There do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
- <span data-ttu-id="bbbde-108">Neexistují žádné modely objektu apartment, agregace nebo aktivace registru, použít [funkce CoCreateInstance](https://go.microsoft.com/fwlink/?LinkId=142894).</span><span class="sxs-lookup"><span data-stu-id="bbbde-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](https://go.microsoft.com/fwlink/?LinkId=142894).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bbbde-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="bbbde-109">In This Section</span></span>  
 [<span data-ttu-id="bbbde-110">ICLRAppDomainResourceMonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bbbde-110">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="bbbde-111">Poskytuje metody, které se kontrolovat využití procesoru a paměti doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="bbbde-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="bbbde-112">ICLRDomainManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bbbde-112">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 <span data-ttu-id="bbbde-113">Umožňuje hostiteli určit, který se použije k inicializaci výchozí domény aplikace a k určení vlastností inicializace správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="bbbde-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="bbbde-114">ICLRGCManager2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bbbde-114">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 <span data-ttu-id="bbbde-115">Poskytuje [setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metodu, která umožňuje hostiteli nastavte velikost segmentu kolekce uvolnění paměti a maximální velikost 0. generace kolekce systému uvolňování paměti na hodnoty vyšší než `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="bbbde-115">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="bbbde-116">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bbbde-116">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 <span data-ttu-id="bbbde-117">Poskytuje metody vrátit konkrétní verzi modulu CLR, seznam všech nainstalovaných CLRs, vypsat všechny moduly Runtime v procesu, vrátí rozhraní aktivace a zjistit verzi modulu CLR použitou ke kompilaci sestavení.</span><span class="sxs-lookup"><span data-stu-id="bbbde-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="bbbde-118">ICLRMetaHostPolicy – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bbbde-118">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="bbbde-119">Poskytuje [getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metodu, která poskytuje rozhraní CLR na základě kritérií zásad, spravované sestavení, verzi a konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="bbbde-119">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="bbbde-120">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bbbde-120">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 <span data-ttu-id="bbbde-121">Poskytuje metody, které vracejí informace o konkrétní modulu runtime, včetně verze, adresáře a načíst stav.</span><span class="sxs-lookup"><span data-stu-id="bbbde-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="bbbde-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bbbde-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 <span data-ttu-id="bbbde-123">Poskytuje základní globální statické funkce pro podepisování sestavení se silnými názvy.</span><span class="sxs-lookup"><span data-stu-id="bbbde-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="bbbde-124">Všechny [iclrstrongname –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) metody vrací standardní COM HRESULT.</span><span class="sxs-lookup"><span data-stu-id="bbbde-124">All the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="bbbde-125">ICLRStrongName2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bbbde-125">ICLRStrongName2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 <span data-ttu-id="bbbde-126">Umožňuje vytvořit silné názvy pomocí algoritmu SHA-2 skupiny Hashovacích algoritmů zabezpečení (SHA-256, SHA-384 a SHA-512).</span><span class="sxs-lookup"><span data-stu-id="bbbde-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="bbbde-127">ICLRTask2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bbbde-127">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 <span data-ttu-id="bbbde-128">Obsahuje všechny funkce, které jsou součástí [iclrtask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); navíc poskytuje metody, které umožňují zrušení vláken k zpozdit u aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="bbbde-128">Provides all the functionality of the [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bbbde-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="bbbde-129">Related Sections</span></span>  
 [<span data-ttu-id="bbbde-130">Zastaralá rozhraní a třídy typu Coclass pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="bbbde-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="bbbde-131">Popisuje rozhraní hostování, opatřeného rozhraní .NET Framework verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="bbbde-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="bbbde-132">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="bbbde-132">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="bbbde-133">Popisuje rozhraní hostování, opatřeného rozhraní .NET Framework verze 2.0, 3.0 a 3.5.</span><span class="sxs-lookup"><span data-stu-id="bbbde-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="bbbde-134">Hostování</span><span class="sxs-lookup"><span data-stu-id="bbbde-134">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="bbbde-135">Zavádí hostování v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bbbde-135">Introduces hosting in the .NET Framework.</span></span>
