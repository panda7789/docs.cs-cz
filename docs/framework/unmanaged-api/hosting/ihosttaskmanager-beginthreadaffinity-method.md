---
title: IHostTaskManager::BeginThreadAffinity – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginThreadAffinity
helpviewer_keywords:
- IHostTaskManager::BeginThreadAffinity method [.NET Framework hosting]
- BeginThreadAffinity method [.NET Framework hosting]
ms.assetid: fea3ab88-ce41-4c5a-847b-bb78cd748da6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a94797e6279a1f1d419b977c22d73ca41bbafc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443370"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="3bea1-102">IHostTaskManager::BeginThreadAffinity – metoda</span><span class="sxs-lookup"><span data-stu-id="3bea1-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="3bea1-103">Upozorní, že hostitele, který spravovaný kód je zadání období, ve kterém nesmí být aktuální úlohy přesunout do jiné vlákno operačního systému.</span><span class="sxs-lookup"><span data-stu-id="3bea1-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bea1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bea1-104">Syntax</span></span>  
  
```  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3bea1-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3bea1-105">Return Value</span></span>  
  
|<span data-ttu-id="3bea1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3bea1-106">HRESULT</span></span>|<span data-ttu-id="3bea1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3bea1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3bea1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="3bea1-108">S_OK</span></span>|<span data-ttu-id="3bea1-109">`BeginThreadAffinity` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="3bea1-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="3bea1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3bea1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3bea1-111">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3bea1-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3bea1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3bea1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3bea1-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="3bea1-113">The call timed out.</span></span>|  
|<span data-ttu-id="3bea1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3bea1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3bea1-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="3bea1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3bea1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3bea1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3bea1-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="3bea1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3bea1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3bea1-118">E_FAIL</span></span>|<span data-ttu-id="3bea1-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="3bea1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3bea1-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="3bea1-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3bea1-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3bea1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bea1-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3bea1-122">Remarks</span></span>  
 <span data-ttu-id="3bea1-123">Modul CLR obvykle volá `IHostTaskManager::BeginThreadAffinity` v kontextu volání <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3bea1-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3bea1-124">Aktuální úloha nesmí přeplánovat, dokud odpovídající Přišla žádost o [ihosttaskmanager::endthreadaffinity –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="3bea1-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="3bea1-125">Úlohy je možné přepnout na, ale při přepnutí zpět v, musí být přiřazeni ke stejné vláknu operačního systému, ze kterého byla přepnuta na. Vnořená volání `BeginThreadAffinity` mít žádný vliv, protože volání odkazuje na aktuální úlohy.</span><span class="sxs-lookup"><span data-stu-id="3bea1-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bea1-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3bea1-126">Requirements</span></span>  
 <span data-ttu-id="3bea1-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bea1-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bea1-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3bea1-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3bea1-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3bea1-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3bea1-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bea1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bea1-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="3bea1-131">See Also</span></span>  
 [<span data-ttu-id="3bea1-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3bea1-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="3bea1-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3bea1-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="3bea1-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3bea1-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="3bea1-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3bea1-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
