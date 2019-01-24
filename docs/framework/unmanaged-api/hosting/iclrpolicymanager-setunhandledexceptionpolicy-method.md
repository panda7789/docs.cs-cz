---
title: ICLRPolicyManager::SetUnhandledExceptionPolicy – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6190d867e86ae7e77f701b8b0bdad9caee4421a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561007"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="215da-102">ICLRPolicyManager::SetUnhandledExceptionPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="215da-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="215da-103">Určuje chování modulu common language runtime (CLR), když dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="215da-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="215da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="215da-104">Syntax</span></span>  
  
```  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="215da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="215da-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="215da-106">[in] Jeden z [eclrunhandledexception –](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) hodnoty, která udává, zda je nastaven chování modulu CLR nebo hostitele.</span><span class="sxs-lookup"><span data-stu-id="215da-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="215da-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="215da-107">Return Value</span></span>  
  
|<span data-ttu-id="215da-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="215da-108">HRESULT</span></span>|<span data-ttu-id="215da-109">Popis</span><span class="sxs-lookup"><span data-stu-id="215da-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="215da-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="215da-110">S_OK</span></span>|<span data-ttu-id="215da-111">`SetUnhandledExceptionPolicy` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="215da-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="215da-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="215da-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="215da-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="215da-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="215da-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="215da-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="215da-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="215da-115">The call timed out.</span></span>|  
|<span data-ttu-id="215da-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="215da-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="215da-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="215da-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="215da-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="215da-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="215da-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="215da-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="215da-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="215da-120">E_FAIL</span></span>|<span data-ttu-id="215da-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="215da-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="215da-122">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="215da-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="215da-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="215da-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="215da-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="215da-124">Remarks</span></span>  
 <span data-ttu-id="215da-125">Ve výchozím nastavení je poslední obslužnou rutinu pro všechny neošetřené výjimky modulu CLR a její výchozí chování je dovolí procesu.</span><span class="sxs-lookup"><span data-stu-id="215da-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="215da-126">Hostitel toto chování můžete změnit tak, že nastavíte `policy` hodnota, která má eHostDeterminedPolicy.</span><span class="sxs-lookup"><span data-stu-id="215da-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="215da-127">Tato hodnota umožňuje hostiteli implementovat vlastní výchozí chování, stejně jako u starších verzí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="215da-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="215da-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="215da-128">Requirements</span></span>  
 <span data-ttu-id="215da-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="215da-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="215da-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="215da-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="215da-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="215da-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="215da-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="215da-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215da-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="215da-133">See also</span></span>
- [<span data-ttu-id="215da-134">EClrUnhandledException – výčet</span><span class="sxs-lookup"><span data-stu-id="215da-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="215da-135">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="215da-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="215da-136">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="215da-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="215da-137">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="215da-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
