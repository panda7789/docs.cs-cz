---
title: IHostTask::Start – metoda
ms.date: 03/30/2017
api_name:
- IHostTask.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d45c5b09358430535438734b38e5dce5d1bcdd3e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101624"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="85d84-102">IHostTask::Start – metoda</span><span class="sxs-lookup"><span data-stu-id="85d84-102">IHostTask::Start Method</span></span>
<span data-ttu-id="85d84-103">Požadavky, že hostitel move – úloha reprezentované aktuální [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instancí z pozastavené do živé stavu, ve kterém lze kód spustit.</span><span class="sxs-lookup"><span data-stu-id="85d84-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85d84-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85d84-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="85d84-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="85d84-105">Return Value</span></span>  
  
|<span data-ttu-id="85d84-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85d84-106">HRESULT</span></span>|<span data-ttu-id="85d84-107">Popis</span><span class="sxs-lookup"><span data-stu-id="85d84-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85d84-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="85d84-108">S_OK</span></span>|<span data-ttu-id="85d84-109">Spuštění bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="85d84-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="85d84-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="85d84-110">E_FAIL</span></span>|<span data-ttu-id="85d84-111">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="85d84-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="85d84-112">Po návratu metody E_FAIL, modul CLR (CLR) už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="85d84-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="85d84-113">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="85d84-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85d84-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="85d84-114">Remarks</span></span>  
 <span data-ttu-id="85d84-115">`Start` vždy vrátí hodnotu HRESULT S_OK, s výjimkou v případech, kdy došlo k závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="85d84-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85d84-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85d84-116">Requirements</span></span>  
 <span data-ttu-id="85d84-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85d84-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85d84-118">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="85d84-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="85d84-119">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="85d84-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85d84-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85d84-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85d84-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85d84-121">See also</span></span>

- [<span data-ttu-id="85d84-122">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85d84-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="85d84-123">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85d84-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="85d84-124">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85d84-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="85d84-125">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85d84-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
