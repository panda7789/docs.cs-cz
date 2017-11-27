---
title: "ICLRMetaHostPolicy – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHostPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHostPolicy
helpviewer_keywords: ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type: apiref
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b8cbe1d397e1214cfa4d3f4cbc3d6cdf2d3ccd5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="8f4ee-102">ICLRMetaHostPolicy – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f4ee-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="8f4ee-103">Poskytuje [getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metodu, která vrací ukazatel na společné rozhraní language runtime (CLR) na základě zásad kritérií, spravované sestavení, verzi a konfiguračnímu souboru.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-103">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8f4ee-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8f4ee-104">Methods</span></span>  
  
|<span data-ttu-id="8f4ee-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8f4ee-105">Method</span></span>|<span data-ttu-id="8f4ee-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8f4ee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8f4ee-107">Getrequestedruntime – metoda</span><span class="sxs-lookup"><span data-stu-id="8f4ee-107">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="8f4ee-108">Poskytuje upřednostňované CLR rozhraní na základě zásad kritérií, spravované sestavení, verzi a konfiguračnímu souboru.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f4ee-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f4ee-109">Remarks</span></span>  
 <span data-ttu-id="8f4ee-110">Odkaz na tohoto rozhraní můžete získat voláním [clrcreateinstance –](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) fungovat, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="8f4ee-110">You can get a reference to this interface by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  <span data-ttu-id="8f4ee-111">Toto rozhraní není ve skutečnosti načíst nebo aktivace CLR, ale jednoduše vrátí upřednostňovaný verze CLR, závisí na dostupných verzí, které jsou nainstalovány nebo načíst.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="8f4ee-112">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Hostující rozhraní API konsoliduje zásady tak, aby hostiteli s potřeb může používat základní funkce aniž by docházelo k neúmyslnému postihy.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-112">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="8f4ee-113">Například mnoho exporty MSCorEE.dll vytvoří vazbu k určité CLR, i když metody nemusejí být nutné logicky ho.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="8f4ee-114">[METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) výčtu poskytuje vazby zásady, které jsou společné pro většinu hostitelů.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-114">The [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f4ee-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8f4ee-115">Requirements</span></span>  
 <span data-ttu-id="8f4ee-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f4ee-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f4ee-117">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8f4ee-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8f4ee-118">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8f4ee-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f4ee-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f4ee-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f4ee-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f4ee-120">See Also</span></span>  
 [<span data-ttu-id="8f4ee-121">Rozhraní hostování CLR přidaná v rozhraní .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="8f4ee-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="8f4ee-122">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="8f4ee-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="8f4ee-123">Hostování</span><span class="sxs-lookup"><span data-stu-id="8f4ee-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
