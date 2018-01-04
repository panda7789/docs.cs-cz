---
title: "ICLRPolicyManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager
helpviewer_keywords: ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce37f9beb0901eaf1bc98f5af3f8f99a7fedf1c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="77b76-102">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77b76-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="77b76-103">Poskytuje metody, které umožňují na hostiteli a poté zadejte akce zásad pro případ selhání a vypršení časových limitů.</span><span class="sxs-lookup"><span data-stu-id="77b76-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="77b76-104">Metody</span><span class="sxs-lookup"><span data-stu-id="77b76-104">Methods</span></span>  
  
|<span data-ttu-id="77b76-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="77b76-105">Method</span></span>|<span data-ttu-id="77b76-106">Popis</span><span class="sxs-lookup"><span data-stu-id="77b76-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="77b76-107">SetActionOnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="77b76-107">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="77b76-108">Určuje akci zásady, které modul CLR (CLR) má provést, pokud dojde k selhání zadané.</span><span class="sxs-lookup"><span data-stu-id="77b76-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="77b76-109">SetActionOnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="77b76-109">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="77b76-110">Určuje akci zásady, kterou modulu CLR by měla provést, pokud zadaná operace vyprší časový limit.</span><span class="sxs-lookup"><span data-stu-id="77b76-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="77b76-111">SetDefaultAction – metoda</span><span class="sxs-lookup"><span data-stu-id="77b76-111">SetDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="77b76-112">Určuje akci zásady, kterou modulu CLR má provést, když dojde k zadanou operaci.</span><span class="sxs-lookup"><span data-stu-id="77b76-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="77b76-113">SetTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="77b76-113">SetTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="77b76-114">Nastaví hodnotu časového limitu pro danou operaci.</span><span class="sxs-lookup"><span data-stu-id="77b76-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="77b76-115">SetTimeoutAndAction – metoda</span><span class="sxs-lookup"><span data-stu-id="77b76-115">SetTimeoutAndAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="77b76-116">Nastaví hodnotu časového limitu pro zadanou operaci a určí zásad akci, kterou modulu CLR by měla provést, když dojde k operaci.</span><span class="sxs-lookup"><span data-stu-id="77b76-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="77b76-117">SetUnhandledExceptionPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="77b76-117">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="77b76-118">Určuje chování modulu CLR, když dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="77b76-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="77b76-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77b76-119">Requirements</span></span>  
 <span data-ttu-id="77b76-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77b76-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77b76-121">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="77b76-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77b76-122">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77b76-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77b76-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77b76-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77b76-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="77b76-124">See Also</span></span>  
 [<span data-ttu-id="77b76-125">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="77b76-125">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="77b76-126">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="77b76-126">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="77b76-127">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="77b76-127">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="77b76-128">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77b76-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
