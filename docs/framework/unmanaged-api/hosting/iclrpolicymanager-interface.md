---
title: ICLRPolicyManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
ms.openlocfilehash: 59aa904d4c67326b60381d3476eaab179d7fa42b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140801"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="4d7b1-102">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d7b1-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="4d7b1-103">Poskytuje metody, které umožňují hostiteli určit akce zásad, které mají být provedeny v případě selhání a časových limitů.</span><span class="sxs-lookup"><span data-stu-id="4d7b1-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d7b1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4d7b1-104">Methods</span></span>  
  
|<span data-ttu-id="4d7b1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4d7b1-105">Method</span></span>|<span data-ttu-id="4d7b1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4d7b1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d7b1-107">SetActionOnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="4d7b1-107">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="4d7b1-108">Určuje akci zásad, kterou by modul CLR (Common Language Runtime) měl provést při výskytu zadaného selhání.</span><span class="sxs-lookup"><span data-stu-id="4d7b1-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="4d7b1-109">SetActionOnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="4d7b1-109">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="4d7b1-110">Určuje akci zásad, kterou by měl modul CLR provést po vypršení časového limitu zadané operace.</span><span class="sxs-lookup"><span data-stu-id="4d7b1-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="4d7b1-111">SetDefaultAction – metoda</span><span class="sxs-lookup"><span data-stu-id="4d7b1-111">SetDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="4d7b1-112">Určuje akci zásad, kterou by měl CLR provést, když dojde k zadané operaci.</span><span class="sxs-lookup"><span data-stu-id="4d7b1-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="4d7b1-113">SetTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="4d7b1-113">SetTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="4d7b1-114">Nastaví hodnotu časového limitu pro zadanou operaci.</span><span class="sxs-lookup"><span data-stu-id="4d7b1-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="4d7b1-115">SetTimeoutAndAction – metoda</span><span class="sxs-lookup"><span data-stu-id="4d7b1-115">SetTimeoutAndAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="4d7b1-116">Nastaví hodnotu časového limitu pro zadanou operaci a určuje akci zásad, kterou by měl CLR provést při výskytu operace.</span><span class="sxs-lookup"><span data-stu-id="4d7b1-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="4d7b1-117">SetUnhandledExceptionPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="4d7b1-117">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="4d7b1-118">Určuje chování modulu CLR, pokud dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="4d7b1-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d7b1-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d7b1-119">Requirements</span></span>  
 <span data-ttu-id="4d7b1-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d7b1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d7b1-121">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4d7b1-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4d7b1-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4d7b1-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d7b1-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d7b1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d7b1-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d7b1-124">See also</span></span>

- [<span data-ttu-id="4d7b1-125">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="4d7b1-125">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="4d7b1-126">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="4d7b1-126">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="4d7b1-127">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="4d7b1-127">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="4d7b1-128">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d7b1-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
