---
title: IHostIoCompletionManager::SetCLRIoCompletionManager – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd48664c78e3f5772cdfa655ebbc7cfa716f4950
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796827"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="c66d7-102">IHostIoCompletionManager::SetCLRIoCompletionManager – metoda</span><span class="sxs-lookup"><span data-stu-id="c66d7-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="c66d7-103">Poskytuje ukazatel rozhraní na hostiteli [iclriocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implementován modulem common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c66d7-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c66d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c66d7-104">Syntax</span></span>  
  
```  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c66d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c66d7-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="c66d7-106">[in] Ukazatel rozhraní k `ICLRIoCompletionManager` instance k dispozici modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="c66d7-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c66d7-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c66d7-107">Return Value</span></span>  
  
|<span data-ttu-id="c66d7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c66d7-108">HRESULT</span></span>|<span data-ttu-id="c66d7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c66d7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c66d7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c66d7-110">S_OK</span></span>|<span data-ttu-id="c66d7-111">`SetCLRIoCompletionManager` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c66d7-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="c66d7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c66d7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c66d7-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c66d7-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c66d7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c66d7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c66d7-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c66d7-115">The call timed out.</span></span>|  
|<span data-ttu-id="c66d7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c66d7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c66d7-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="c66d7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c66d7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c66d7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c66d7-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="c66d7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c66d7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c66d7-120">E_FAIL</span></span>|<span data-ttu-id="c66d7-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="c66d7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c66d7-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c66d7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c66d7-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c66d7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c66d7-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c66d7-124">Remarks</span></span>  
 <span data-ttu-id="c66d7-125">Po CLR volal `SetCLRIoCompletionManager`, hostitel musí volat [iclriocompletionmanager::onComplete –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) upozornit modul CLR, požadavek na vstupně-výstupní operace byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="c66d7-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c66d7-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c66d7-126">Requirements</span></span>  
 <span data-ttu-id="c66d7-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c66d7-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c66d7-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c66d7-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c66d7-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c66d7-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c66d7-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c66d7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c66d7-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c66d7-131">See also</span></span>

- [<span data-ttu-id="c66d7-132">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c66d7-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="c66d7-133">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c66d7-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
