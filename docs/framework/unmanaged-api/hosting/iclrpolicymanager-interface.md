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
ms.openlocfilehash: 631301a10aee96bb00aeda6b0b8695f0aea186a8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703473"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="5f94c-102">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f94c-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="5f94c-103">Poskytuje metody, které umožňují hostiteli určit akce zásad, které mají být provedeny v případě selhání a časových limitů.</span><span class="sxs-lookup"><span data-stu-id="5f94c-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f94c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5f94c-104">Methods</span></span>  
  
|<span data-ttu-id="5f94c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5f94c-105">Method</span></span>|<span data-ttu-id="5f94c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5f94c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f94c-107">SetActionOnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="5f94c-107">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="5f94c-108">Určuje akci zásad, kterou by modul CLR (Common Language Runtime) měl provést při výskytu zadaného selhání.</span><span class="sxs-lookup"><span data-stu-id="5f94c-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="5f94c-109">SetActionOnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="5f94c-109">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="5f94c-110">Určuje akci zásad, kterou by měl modul CLR provést po vypršení časového limitu zadané operace.</span><span class="sxs-lookup"><span data-stu-id="5f94c-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="5f94c-111">SetDefaultAction – metoda</span><span class="sxs-lookup"><span data-stu-id="5f94c-111">SetDefaultAction Method</span></span>](iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="5f94c-112">Určuje akci zásad, kterou by měl CLR provést, když dojde k zadané operaci.</span><span class="sxs-lookup"><span data-stu-id="5f94c-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="5f94c-113">SetTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="5f94c-113">SetTimeout Method</span></span>](iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="5f94c-114">Nastaví hodnotu časového limitu pro zadanou operaci.</span><span class="sxs-lookup"><span data-stu-id="5f94c-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="5f94c-115">SetTimeoutAndAction – metoda</span><span class="sxs-lookup"><span data-stu-id="5f94c-115">SetTimeoutAndAction Method</span></span>](iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="5f94c-116">Nastaví hodnotu časového limitu pro zadanou operaci a určuje akci zásad, kterou by měl CLR provést při výskytu operace.</span><span class="sxs-lookup"><span data-stu-id="5f94c-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="5f94c-117">SetUnhandledExceptionPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="5f94c-117">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="5f94c-118">Určuje chování modulu CLR, pokud dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="5f94c-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5f94c-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f94c-119">Requirements</span></span>  
 <span data-ttu-id="5f94c-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f94c-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f94c-121">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5f94c-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f94c-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5f94c-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f94c-123">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f94c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f94c-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f94c-124">See also</span></span>

- [<span data-ttu-id="5f94c-125">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="5f94c-125">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="5f94c-126">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="5f94c-126">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="5f94c-127">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="5f94c-127">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="5f94c-128">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f94c-128">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
