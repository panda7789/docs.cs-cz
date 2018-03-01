---
title: "ICLRMetaHostPolicy – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cd9b8d6aef2289833a0bd192b838e6f70ea8c0ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="6c7b6-102">ICLRMetaHostPolicy – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c7b6-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="6c7b6-103">Poskytuje [getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metodu, která vrací ukazatel na společné rozhraní language runtime (CLR) na základě zásad kritérií, spravované sestavení, verzi a konfiguračnímu souboru.</span><span class="sxs-lookup"><span data-stu-id="6c7b6-103">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c7b6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6c7b6-104">Methods</span></span>  
  
|<span data-ttu-id="6c7b6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6c7b6-105">Method</span></span>|<span data-ttu-id="6c7b6-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6c7b6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c7b6-107">GetRequestedRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="6c7b6-107">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="6c7b6-108">Poskytuje upřednostňované CLR rozhraní na základě zásad kritérií, spravované sestavení, verzi a konfiguračnímu souboru.</span><span class="sxs-lookup"><span data-stu-id="6c7b6-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c7b6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c7b6-109">Remarks</span></span>  
 <span data-ttu-id="6c7b6-110">Odkaz na tohoto rozhraní můžete získat voláním [clrcreateinstance –](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) fungovat, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="6c7b6-110">You can get a reference to this interface by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  <span data-ttu-id="6c7b6-111">Toto rozhraní není ve skutečnosti načíst nebo aktivace CLR, ale jednoduše vrátí upřednostňovaný verze CLR, závisí na dostupných verzí, které jsou nainstalovány nebo načíst.</span><span class="sxs-lookup"><span data-stu-id="6c7b6-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="6c7b6-112">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Hostující rozhraní API konsoliduje zásady tak, aby hostiteli s potřeb může používat základní funkce aniž by docházelo k neúmyslnému postihy.</span><span class="sxs-lookup"><span data-stu-id="6c7b6-112">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="6c7b6-113">Například mnoho exporty MSCorEE.dll vytvoří vazbu k určité CLR, i když metody nemusejí být nutné logicky ho.</span><span class="sxs-lookup"><span data-stu-id="6c7b6-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="6c7b6-114">[METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) výčtu poskytuje vazby zásady, které jsou společné pro většinu hostitelů.</span><span class="sxs-lookup"><span data-stu-id="6c7b6-114">The [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c7b6-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c7b6-115">Requirements</span></span>  
 <span data-ttu-id="6c7b6-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c7b6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c7b6-117">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6c7b6-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6c7b6-118">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c7b6-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c7b6-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c7b6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c7b6-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c7b6-120">See Also</span></span>  
 [<span data-ttu-id="6c7b6-121">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="6c7b6-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="6c7b6-122">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="6c7b6-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="6c7b6-123">Hostování</span><span class="sxs-lookup"><span data-stu-id="6c7b6-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
