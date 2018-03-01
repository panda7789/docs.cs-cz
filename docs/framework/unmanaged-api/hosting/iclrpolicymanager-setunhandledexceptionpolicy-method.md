---
title: "ICLRPolicyManager::SetUnhandledExceptionPolicy – metoda"
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
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9ad287fedbc06768dd683c254292e0c28760d59a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="83751-102">ICLRPolicyManager::SetUnhandledExceptionPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="83751-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="83751-103">Určuje chování common language runtime (CLR), když dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="83751-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83751-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83751-104">Syntax</span></span>  
  
```  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83751-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83751-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="83751-106">[v] Jeden z [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) hodnoty, která určuje, zda je nastaven chování modulu CLR nebo hostitele.</span><span class="sxs-lookup"><span data-stu-id="83751-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83751-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="83751-107">Return Value</span></span>  
  
|<span data-ttu-id="83751-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83751-108">HRESULT</span></span>|<span data-ttu-id="83751-109">Popis</span><span class="sxs-lookup"><span data-stu-id="83751-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83751-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="83751-110">S_OK</span></span>|<span data-ttu-id="83751-111">`SetUnhandledExceptionPolicy`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="83751-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="83751-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="83751-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="83751-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="83751-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="83751-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="83751-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="83751-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="83751-115">The call timed out.</span></span>|  
|<span data-ttu-id="83751-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="83751-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="83751-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="83751-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="83751-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="83751-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="83751-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="83751-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="83751-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="83751-120">E_FAIL</span></span>|<span data-ttu-id="83751-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="83751-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="83751-122">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="83751-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="83751-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="83751-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83751-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83751-124">Remarks</span></span>  
 <span data-ttu-id="83751-125">Ve výchozím modulu CLR je poslední obslužné rutiny pro všechny neošetřené výjimky a jeho výchozí chování je přerušit proces.</span><span class="sxs-lookup"><span data-stu-id="83751-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="83751-126">Hostitel může toto chování změnit v nastavení `policy` hodnotu eHostDeterminedPolicy.</span><span class="sxs-lookup"><span data-stu-id="83751-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="83751-127">Tato hodnota umožňuje hostiteli implementovat vlastní výchozí chování, stejně jako u starších verzí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="83751-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83751-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83751-128">Requirements</span></span>  
 <span data-ttu-id="83751-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83751-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83751-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83751-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83751-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83751-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83751-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83751-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83751-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="83751-133">See Also</span></span>  
 [<span data-ttu-id="83751-134">EClrUnhandledException – výčet</span><span class="sxs-lookup"><span data-stu-id="83751-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)  
 [<span data-ttu-id="83751-135">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="83751-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="83751-136">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="83751-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="83751-137">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="83751-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
