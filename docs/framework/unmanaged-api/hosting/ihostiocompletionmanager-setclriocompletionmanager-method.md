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
ms.openlocfilehash: 1a190041cacb635f1ad6703a634923e0bb9ddb3f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484261"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="8bf01-102">IHostIoCompletionManager::SetCLRIoCompletionManager – metoda</span><span class="sxs-lookup"><span data-stu-id="8bf01-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="8bf01-103">Poskytuje ukazatel rozhraní na hostiteli [iclriocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implementován modulem common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="8bf01-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bf01-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bf01-104">Syntax</span></span>  
  
```  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bf01-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bf01-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="8bf01-106">[in] Ukazatel rozhraní k `ICLRIoCompletionManager` instance k dispozici modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="8bf01-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8bf01-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8bf01-107">Return Value</span></span>  
  
|<span data-ttu-id="8bf01-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8bf01-108">HRESULT</span></span>|<span data-ttu-id="8bf01-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8bf01-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8bf01-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8bf01-110">S_OK</span></span>|<span data-ttu-id="8bf01-111">`SetCLRIoCompletionManager` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8bf01-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="8bf01-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8bf01-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8bf01-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8bf01-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8bf01-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8bf01-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8bf01-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8bf01-115">The call timed out.</span></span>|  
|<span data-ttu-id="8bf01-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8bf01-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8bf01-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="8bf01-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8bf01-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8bf01-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8bf01-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="8bf01-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8bf01-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8bf01-120">E_FAIL</span></span>|<span data-ttu-id="8bf01-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="8bf01-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8bf01-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="8bf01-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8bf01-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8bf01-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bf01-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8bf01-124">Remarks</span></span>  
 <span data-ttu-id="8bf01-125">Po CLR volal `SetCLRIoCompletionManager`, hostitel musí volat [iclriocompletionmanager::onComplete –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) upozornit modul CLR, požadavek na vstupně-výstupní operace byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="8bf01-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bf01-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8bf01-126">Requirements</span></span>  
 <span data-ttu-id="8bf01-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bf01-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bf01-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8bf01-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8bf01-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8bf01-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8bf01-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bf01-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf01-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8bf01-131">See also</span></span>
- [<span data-ttu-id="8bf01-132">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bf01-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="8bf01-133">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bf01-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
