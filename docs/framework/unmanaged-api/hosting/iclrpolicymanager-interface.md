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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2eeccc4dfd7a7147fe791444eeeca2bd3a844305
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211039"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="be648-102">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be648-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="be648-103">Poskytuje metody, které umožňují hostitele k určení akce zásad, které mají být provedeny v případě selhání a vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="be648-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be648-104">Metody</span><span class="sxs-lookup"><span data-stu-id="be648-104">Methods</span></span>  
  
|<span data-ttu-id="be648-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="be648-105">Method</span></span>|<span data-ttu-id="be648-106">Popis</span><span class="sxs-lookup"><span data-stu-id="be648-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be648-107">SetActionOnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="be648-107">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="be648-108">Určuje akci zásad by měl trvat common language runtime (CLR), když dojde k selhání zadané.</span><span class="sxs-lookup"><span data-stu-id="be648-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="be648-109">SetActionOnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="be648-109">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="be648-110">Určuje akci zásad by měl trvat CLR, když vyprší časový limit operace zadané.</span><span class="sxs-lookup"><span data-stu-id="be648-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="be648-111">SetDefaultAction – metoda</span><span class="sxs-lookup"><span data-stu-id="be648-111">SetDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="be648-112">Určuje akci zásad by měl trvat CLR, když dojde k zadané operace.</span><span class="sxs-lookup"><span data-stu-id="be648-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="be648-113">SetTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="be648-113">SetTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="be648-114">Nastaví hodnotu časového limitu pro danou operaci.</span><span class="sxs-lookup"><span data-stu-id="be648-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="be648-115">SetTimeoutAndAction – metoda</span><span class="sxs-lookup"><span data-stu-id="be648-115">SetTimeoutAndAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="be648-116">Nastaví hodnotu časového limitu pro zadanou operaci a určuje akci zásad by měl trvat CLR, když dojde k operaci.</span><span class="sxs-lookup"><span data-stu-id="be648-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="be648-117">SetUnhandledExceptionPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="be648-117">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="be648-118">Určuje chování modulu CLR, když dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="be648-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be648-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be648-119">Requirements</span></span>  
 <span data-ttu-id="be648-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be648-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be648-121">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="be648-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="be648-122">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="be648-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be648-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be648-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be648-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be648-124">See also</span></span>

- [<span data-ttu-id="be648-125">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="be648-125">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="be648-126">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="be648-126">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="be648-127">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="be648-127">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="be648-128">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be648-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
