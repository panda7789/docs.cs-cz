---
title: "IHostCrst::Enter – metoda"
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
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 390f30c85dac494451af1ff82328c913dd9438ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="e31b7-102">IHostCrst::Enter – metoda</span><span class="sxs-lookup"><span data-stu-id="e31b7-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="e31b7-103">Zadá kritické část, která je reprezentována aktuální [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="e31b7-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e31b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e31b7-104">Syntax</span></span>  
  
```  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e31b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e31b7-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="e31b7-106">[v] Jeden z [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty, která určuje, jaké akce hostitele by měla přijmout, pokud operace bloky.</span><span class="sxs-lookup"><span data-stu-id="e31b7-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e31b7-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e31b7-107">Return Value</span></span>  
  
|<span data-ttu-id="e31b7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e31b7-108">HRESULT</span></span>|<span data-ttu-id="e31b7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e31b7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e31b7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e31b7-110">S_OK</span></span>|<span data-ttu-id="e31b7-111">`Enter`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e31b7-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="e31b7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e31b7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e31b7-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e31b7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e31b7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e31b7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e31b7-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e31b7-115">The call timed out.</span></span>|  
|<span data-ttu-id="e31b7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e31b7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e31b7-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="e31b7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e31b7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e31b7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e31b7-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="e31b7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e31b7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e31b7-120">E_FAIL</span></span>|<span data-ttu-id="e31b7-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="e31b7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e31b7-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e31b7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e31b7-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e31b7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e31b7-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e31b7-124">Remarks</span></span>  
 <span data-ttu-id="e31b7-125">`Enter`odpovídá Win32 `EnterCriticalSection` funkce.</span><span class="sxs-lookup"><span data-stu-id="e31b7-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e31b7-126">Tato metoda nevrátí, dokud nebude zadán kritická sekce.</span><span class="sxs-lookup"><span data-stu-id="e31b7-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e31b7-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e31b7-127">Requirements</span></span>  
 <span data-ttu-id="e31b7-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e31b7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e31b7-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e31b7-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e31b7-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e31b7-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e31b7-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e31b7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e31b7-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="e31b7-132">See Also</span></span>  
 [<span data-ttu-id="e31b7-133">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e31b7-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="e31b7-134">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e31b7-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="e31b7-135">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e31b7-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
