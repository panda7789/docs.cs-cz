---
title: "ICLRTaskManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager
helpviewer_keywords: ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3144338ddce262aaa6772f588a4f1a652cc57e01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="c0ca3-102">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0ca3-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="c0ca3-103">Poskytuje metody, které umožňují na hostiteli a požadavku explicitně, modul CLR (CLR) vytvořit nový úkol, získat aktuálně spuštěné úlohy a nastavit zeměpisné language a jazykovou verzi pro úlohu.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c0ca3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c0ca3-104">Methods</span></span>  
  
|<span data-ttu-id="c0ca3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c0ca3-105">Method</span></span>|<span data-ttu-id="c0ca3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c0ca3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c0ca3-107">Createtask – metoda</span><span class="sxs-lookup"><span data-stu-id="c0ca3-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="c0ca3-108">Výslovně požaduje, aby vytvořil novou modulu CLR [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-108">Requests explicitly that the CLR create a new [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="c0ca3-109">Getcurrenttask – metoda</span><span class="sxs-lookup"><span data-stu-id="c0ca3-109">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="c0ca3-110">Získá `ICLRTask` instanci, která představuje úloha, která je aktuálně spuštěné.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="c0ca3-111">Getcurrenttasktype – metoda</span><span class="sxs-lookup"><span data-stu-id="c0ca3-111">GetCurrentTaskType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="c0ca3-112">Získá typ úlohy, který je aktuálně spuštěné.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="c0ca3-113">Setlocale – metoda</span><span class="sxs-lookup"><span data-stu-id="c0ca3-113">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="c0ca3-114">Upozorní modulu CLR, že hostitel změnil identifikátor národního prostředí na aktuálně spuštěné úlohy.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="c0ca3-115">Setuilocale – metoda</span><span class="sxs-lookup"><span data-stu-id="c0ca3-115">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="c0ca3-116">Upozorní modul common language runtime, že hostitel změnil identifikátor národního prostředí uživatelského rozhraní na aktuálně spuštěné úlohy.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0ca3-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0ca3-117">Remarks</span></span>  
 <span data-ttu-id="c0ca3-118">Každý úkol, který běží v hostovaném prostředí má reprezentace i na straně hostitele (instance [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) a na straně CLR (instance [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="c0ca3-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span></span> <span data-ttu-id="c0ca3-119">Hostitele nebo modulu CLR může spustit vytvoření úlohy, avšak reprezentace straně hostitele musí být přidružen znázornění odpovídající CLR straně zajistit úspěšné komunikaci mezi hostitelem a CLR týkající se úloha.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="c0ca3-120">Tyto dva objekty musí být vytvořen a vytvořit její instanci před spravovaný kód můžete spustit na vláknu operačního systému.</span><span class="sxs-lookup"><span data-stu-id="c0ca3-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0ca3-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c0ca3-121">Requirements</span></span>  
 <span data-ttu-id="c0ca3-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0ca3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0ca3-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c0ca3-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c0ca3-124">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c0ca3-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c0ca3-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0ca3-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0ca3-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0ca3-126">See Also</span></span>  
 [<span data-ttu-id="c0ca3-127">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0ca3-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="c0ca3-128">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0ca3-128">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="c0ca3-129">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0ca3-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="c0ca3-130">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="c0ca3-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
