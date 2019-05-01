---
title: IHostCrst::Enter – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c772f67b8ac09e2383aff335d9f164c2e048cbd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984396"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="fe9fd-102">IHostCrst::Enter – metoda</span><span class="sxs-lookup"><span data-stu-id="fe9fd-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="fe9fd-103">Zadá kritický oddíl, která je reprezentována aktuální [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="fe9fd-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe9fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe9fd-104">Syntax</span></span>  
  
```  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe9fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe9fd-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="fe9fd-106">[in] Jeden z [wait_option –](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty označující, jaká akce by hostitele zabrat Pokud operace bloky.</span><span class="sxs-lookup"><span data-stu-id="fe9fd-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe9fd-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fe9fd-107">Return Value</span></span>  
  
|<span data-ttu-id="fe9fd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fe9fd-108">HRESULT</span></span>|<span data-ttu-id="fe9fd-109">Popis</span><span class="sxs-lookup"><span data-stu-id="fe9fd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fe9fd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fe9fd-110">S_OK</span></span>|<span data-ttu-id="fe9fd-111">`Enter` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="fe9fd-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="fe9fd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fe9fd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fe9fd-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="fe9fd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fe9fd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fe9fd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fe9fd-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="fe9fd-115">The call timed out.</span></span>|  
|<span data-ttu-id="fe9fd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fe9fd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fe9fd-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="fe9fd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fe9fd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fe9fd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fe9fd-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="fe9fd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fe9fd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fe9fd-120">E_FAIL</span></span>|<span data-ttu-id="fe9fd-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="fe9fd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fe9fd-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="fe9fd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fe9fd-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fe9fd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe9fd-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe9fd-124">Remarks</span></span>  
 <span data-ttu-id="fe9fd-125">`Enter` odráží Win32 `EnterCriticalSection` funkce.</span><span class="sxs-lookup"><span data-stu-id="fe9fd-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe9fd-126">Tato metoda nevrátí, dokud nebude zadán kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="fe9fd-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe9fd-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe9fd-127">Requirements</span></span>  
 <span data-ttu-id="fe9fd-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe9fd-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe9fd-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fe9fd-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe9fd-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fe9fd-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe9fd-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe9fd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe9fd-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe9fd-132">See also</span></span>

- [<span data-ttu-id="fe9fd-133">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe9fd-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="fe9fd-134">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe9fd-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="fe9fd-135">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe9fd-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
