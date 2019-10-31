---
title: ICLRTaskManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
ms.openlocfilehash: e25a6a03a836b8b4964b8260c974c8e8d8d9998d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092191"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="b654f-102">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b654f-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="b654f-103">Poskytuje metody, které umožňují hostiteli explicitně požádat, aby modul CLR (Common Language Runtime) vytvořil nový úkol, získal aktuálně spuštěnou úlohu a pro úkol nastavil geografickou jazyk a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="b654f-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b654f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b654f-104">Methods</span></span>  
  
|<span data-ttu-id="b654f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b654f-105">Method</span></span>|<span data-ttu-id="b654f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b654f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b654f-107">CreateTask – metoda</span><span class="sxs-lookup"><span data-stu-id="b654f-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="b654f-108">Požadavky explicitně, aby CLR vytvořil novou instanci [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b654f-108">Requests explicitly that the CLR create a new [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="b654f-109">GetCurrentTask – metoda</span><span class="sxs-lookup"><span data-stu-id="b654f-109">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="b654f-110">Získá instanci `ICLRTask`, která představuje aktuálně prováděnou úlohu.</span><span class="sxs-lookup"><span data-stu-id="b654f-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="b654f-111">GetCurrentTaskType – metoda</span><span class="sxs-lookup"><span data-stu-id="b654f-111">GetCurrentTaskType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="b654f-112">Získá typ úlohy, která je právě prováděna.</span><span class="sxs-lookup"><span data-stu-id="b654f-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="b654f-113">SetLocale – metoda</span><span class="sxs-lookup"><span data-stu-id="b654f-113">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="b654f-114">Upozorní CLR, že hostitel změnil identifikátor národního prostředí v aktuálně spuštěné úloze.</span><span class="sxs-lookup"><span data-stu-id="b654f-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="b654f-115">SetUILocale – metoda</span><span class="sxs-lookup"><span data-stu-id="b654f-115">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="b654f-116">Upozorní modul CLR (Common Language Runtime), že hostitel změnil identifikátor národního prostředí uživatelského rozhraní v aktuálně spuštěné úloze.</span><span class="sxs-lookup"><span data-stu-id="b654f-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b654f-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b654f-117">Remarks</span></span>  
 <span data-ttu-id="b654f-118">Každý úkol, který běží v hostovaném prostředí, má znázornění na straně hostitele (instance [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) a na straně CLR (instance [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="b654f-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span></span> <span data-ttu-id="b654f-119">Hostitel nebo modul CLR může iniciovat vytvoření úlohy, ale reprezentace na straně hostitele musí být přidružena k odpovídajícímu vyjádření na straně CLR, aby bylo zajištěno úspěšné propojení mezi hostitelem a modulem CLR týkajícím se úlohy.</span><span class="sxs-lookup"><span data-stu-id="b654f-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="b654f-120">Aby bylo možné spustit spravovaný kód ve vlákně operačního systému, je třeba vytvořit tyto dva objekty a vytvořit jejich instanci.</span><span class="sxs-lookup"><span data-stu-id="b654f-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b654f-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b654f-121">Requirements</span></span>  
 <span data-ttu-id="b654f-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b654f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b654f-123">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b654f-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b654f-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b654f-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b654f-125">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b654f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b654f-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b654f-126">See also</span></span>

- [<span data-ttu-id="b654f-127">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b654f-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b654f-128">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b654f-128">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b654f-129">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b654f-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="b654f-130">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="b654f-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
