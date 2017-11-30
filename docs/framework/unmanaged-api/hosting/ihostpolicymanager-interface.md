---
title: "IHostPolicyManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostPolicyManager
helpviewer_keywords: IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8f49474f1a75af91ac5296be866914e05732e755
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="0e8aa-102">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e8aa-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="0e8aa-103">Poskytuje metody, které hostitele akce, které provádí common language runtime (CLR) pro zrušení, překročení časového limitu nebo chyby.</span><span class="sxs-lookup"><span data-stu-id="0e8aa-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0e8aa-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0e8aa-104">Methods</span></span>  
  
|<span data-ttu-id="0e8aa-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0e8aa-105">Method</span></span>|<span data-ttu-id="0e8aa-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0e8aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0e8aa-107">Ondefaultaction – metoda</span><span class="sxs-lookup"><span data-stu-id="0e8aa-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="0e8aa-108">Upozorní hostitele, který modulu CLR se chystáte udělat výchozí akci určenou volání [iclrpolicymanager::setdefaultaction –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) v reakci na vlákno k přerušení nebo <xref:System.AppDomain> uvolnit.</span><span class="sxs-lookup"><span data-stu-id="0e8aa-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="0e8aa-109">OnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="0e8aa-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="0e8aa-110">Upozorní na hostitele, modul CLR se chystá provést akci určenou volání [iclrpolicymanager::setactiononfailure –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) v reakci na selhání přidělení nebo recyklaci prostředku.</span><span class="sxs-lookup"><span data-stu-id="0e8aa-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="0e8aa-111">Ontimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="0e8aa-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="0e8aa-112">Upozorní na hostitele, modul CLR se chystá provést akci určenou volání [iclrpolicymanager::setactionontimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) v reakci na vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="0e8aa-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e8aa-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e8aa-113">Requirements</span></span>  
 <span data-ttu-id="0e8aa-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e8aa-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e8aa-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0e8aa-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e8aa-116">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0e8aa-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e8aa-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e8aa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e8aa-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e8aa-118">See Also</span></span>  
 [<span data-ttu-id="0e8aa-119">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="0e8aa-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="0e8aa-120">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="0e8aa-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="0e8aa-121">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="0e8aa-121">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="0e8aa-122">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e8aa-122">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="0e8aa-123">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="0e8aa-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
