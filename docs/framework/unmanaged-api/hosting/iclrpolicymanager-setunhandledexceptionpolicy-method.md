---
title: "ICLRPolicyManager::SetUnhandledExceptionPolicy – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 59ff5cfd93d8077388694ee2e155133a88319c47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="6cdac-102">ICLRPolicyManager::SetUnhandledExceptionPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="6cdac-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="6cdac-103">Určuje chování common language runtime (CLR), když dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="6cdac-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cdac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cdac-104">Syntax</span></span>  
  
```  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6cdac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6cdac-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="6cdac-106">[v] Jeden z [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) hodnoty, která určuje, zda je nastaven chování modulu CLR nebo hostitele.</span><span class="sxs-lookup"><span data-stu-id="6cdac-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cdac-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6cdac-107">Return Value</span></span>  
  
|<span data-ttu-id="6cdac-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6cdac-108">HRESULT</span></span>|<span data-ttu-id="6cdac-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6cdac-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6cdac-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6cdac-110">S_OK</span></span>|<span data-ttu-id="6cdac-111">`SetUnhandledExceptionPolicy`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="6cdac-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="6cdac-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6cdac-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6cdac-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6cdac-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6cdac-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6cdac-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6cdac-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6cdac-115">The call timed out.</span></span>|  
|<span data-ttu-id="6cdac-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6cdac-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6cdac-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="6cdac-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6cdac-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6cdac-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6cdac-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="6cdac-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6cdac-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6cdac-120">E_FAIL</span></span>|<span data-ttu-id="6cdac-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="6cdac-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6cdac-122">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="6cdac-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6cdac-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6cdac-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cdac-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cdac-124">Remarks</span></span>  
 <span data-ttu-id="6cdac-125">Ve výchozím modulu CLR je poslední obslužné rutiny pro všechny neošetřené výjimky a jeho výchozí chování je přerušit proces.</span><span class="sxs-lookup"><span data-stu-id="6cdac-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="6cdac-126">Hostitel může toto chování změnit v nastavení `policy` hodnotu eHostDeterminedPolicy.</span><span class="sxs-lookup"><span data-stu-id="6cdac-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="6cdac-127">Tato hodnota umožňuje hostiteli implementovat vlastní výchozí chování, stejně jako u starších verzí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6cdac-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cdac-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6cdac-128">Requirements</span></span>  
 <span data-ttu-id="6cdac-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cdac-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cdac-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6cdac-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cdac-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6cdac-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cdac-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cdac-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cdac-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cdac-133">See Also</span></span>  
 [<span data-ttu-id="6cdac-134">EClrUnhandledException – výčet</span><span class="sxs-lookup"><span data-stu-id="6cdac-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)  
 [<span data-ttu-id="6cdac-135">Iclrcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cdac-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="6cdac-136">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cdac-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="6cdac-137">Ihostpolicymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cdac-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
