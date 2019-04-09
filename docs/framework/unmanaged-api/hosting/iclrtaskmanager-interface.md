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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19ef7cb78791496de76e5741f8254ee88563c776
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134651"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="9b9d9-102">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b9d9-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="9b9d9-103">Poskytuje metody, které umožňují common language runtime (CLR) hostitele tak, aby požadavku explicitně, který vytvoří nový úkol, získat právě prováděnou úlohu a nastavit geografické jazyk a jazykovou verzi pro úlohu.</span><span class="sxs-lookup"><span data-stu-id="9b9d9-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9b9d9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9b9d9-104">Methods</span></span>  
  
|<span data-ttu-id="9b9d9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9b9d9-105">Method</span></span>|<span data-ttu-id="9b9d9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9b9d9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9b9d9-107">CreateTask – metoda</span><span class="sxs-lookup"><span data-stu-id="9b9d9-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="9b9d9-108">Explicitně požaduje, aby vytvořil nový modul CLR [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="9b9d9-108">Requests explicitly that the CLR create a new [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="9b9d9-109">GetCurrentTask – metoda</span><span class="sxs-lookup"><span data-stu-id="9b9d9-109">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="9b9d9-110">Získá `ICLRTask` instanci, která představuje úkol, který aktuálně spouští.</span><span class="sxs-lookup"><span data-stu-id="9b9d9-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="9b9d9-111">GetCurrentTaskType – metoda</span><span class="sxs-lookup"><span data-stu-id="9b9d9-111">GetCurrentTaskType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="9b9d9-112">Získá typ úkolu, který aktuálně spouští.</span><span class="sxs-lookup"><span data-stu-id="9b9d9-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="9b9d9-113">SetLocale – metoda</span><span class="sxs-lookup"><span data-stu-id="9b9d9-113">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="9b9d9-114">Upozorní CLR, že hostitel změnil identifikátor národního prostředí na právě prováděnou úlohu.</span><span class="sxs-lookup"><span data-stu-id="9b9d9-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="9b9d9-115">SetUILocale – metoda</span><span class="sxs-lookup"><span data-stu-id="9b9d9-115">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="9b9d9-116">Upozorní modul common language runtime, že hostitel změnil identifikátor národního prostředí uživatelského rozhraní na právě prováděnou úlohu.</span><span class="sxs-lookup"><span data-stu-id="9b9d9-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b9d9-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b9d9-117">Remarks</span></span>  
 <span data-ttu-id="9b9d9-118">Každý úkol, na kterém běží v hostovaném prostředí má reprezentace i na straně hostitele (instance [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) a na straně modulu CLR (instance [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="9b9d9-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span></span> <span data-ttu-id="9b9d9-119">CLR nebo hostitele můžete zahájit vytvořením úlohy, ale na straně hostitele vyjádření musí být přidružen odpovídající reprezentaci straně CLR k zajištění úspěšné komunikaci mezi hostitelem a CLR týkající se úloha.</span><span class="sxs-lookup"><span data-stu-id="9b9d9-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="9b9d9-120">Dva objekty musí být vytvořené a vytvořit instanci před spravovaný kód může provádět na vlákna operačního systému.</span><span class="sxs-lookup"><span data-stu-id="9b9d9-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b9d9-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b9d9-121">Requirements</span></span>  
 <span data-ttu-id="9b9d9-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b9d9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b9d9-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9b9d9-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b9d9-124">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9b9d9-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9b9d9-125">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9b9d9-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9b9d9-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b9d9-126">See also</span></span>

- [<span data-ttu-id="9b9d9-127">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b9d9-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="9b9d9-128">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b9d9-128">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="9b9d9-129">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b9d9-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="9b9d9-130">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="9b9d9-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
