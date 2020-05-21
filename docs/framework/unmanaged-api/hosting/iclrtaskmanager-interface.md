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
ms.openlocfilehash: 9e26071181e8e0712c753fa03d5e16eb85e5ee68
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762824"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="5832a-102">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5832a-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="5832a-103">Poskytuje metody, které umožňují hostiteli explicitně požádat, aby modul CLR (Common Language Runtime) vytvořil nový úkol, získal aktuálně spuštěnou úlohu a pro úkol nastavil geografickou jazyk a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="5832a-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5832a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5832a-104">Methods</span></span>  
  
|<span data-ttu-id="5832a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5832a-105">Method</span></span>|<span data-ttu-id="5832a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5832a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5832a-107">CreateTask – metoda</span><span class="sxs-lookup"><span data-stu-id="5832a-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="5832a-108">Požadavky explicitně, aby CLR vytvořil novou instanci [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5832a-108">Requests explicitly that the CLR create a new [ICLRTask](iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="5832a-109">GetCurrentTask – metoda</span><span class="sxs-lookup"><span data-stu-id="5832a-109">GetCurrentTask Method</span></span>](iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="5832a-110">Načte `ICLRTask` instanci, která představuje aktuálně prováděnou úlohu.</span><span class="sxs-lookup"><span data-stu-id="5832a-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="5832a-111">GetCurrentTaskType – metoda</span><span class="sxs-lookup"><span data-stu-id="5832a-111">GetCurrentTaskType Method</span></span>](iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="5832a-112">Získá typ úlohy, která je právě prováděna.</span><span class="sxs-lookup"><span data-stu-id="5832a-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="5832a-113">SetLocale – metoda</span><span class="sxs-lookup"><span data-stu-id="5832a-113">SetLocale Method</span></span>](iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="5832a-114">Upozorní CLR, že hostitel změnil identifikátor národního prostředí v aktuálně spuštěné úloze.</span><span class="sxs-lookup"><span data-stu-id="5832a-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="5832a-115">SetUILocale – metoda</span><span class="sxs-lookup"><span data-stu-id="5832a-115">SetUILocale Method</span></span>](iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="5832a-116">Upozorní modul CLR (Common Language Runtime), že hostitel změnil identifikátor národního prostředí uživatelského rozhraní v aktuálně spuštěné úloze.</span><span class="sxs-lookup"><span data-stu-id="5832a-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5832a-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5832a-117">Remarks</span></span>  
 <span data-ttu-id="5832a-118">Každý úkol, který běží v hostovaném prostředí, má znázornění na straně hostitele (instance [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) a na straně CLR (instance [ICLRTask](iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="5832a-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](iclrtask-interface.md)).</span></span> <span data-ttu-id="5832a-119">Hostitel nebo modul CLR může iniciovat vytvoření úlohy, ale reprezentace na straně hostitele musí být přidružena k odpovídajícímu vyjádření na straně CLR, aby bylo zajištěno úspěšné propojení mezi hostitelem a modulem CLR týkajícím se úlohy.</span><span class="sxs-lookup"><span data-stu-id="5832a-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="5832a-120">Aby bylo možné spustit spravovaný kód ve vlákně operačního systému, je třeba vytvořit tyto dva objekty a vytvořit jejich instanci.</span><span class="sxs-lookup"><span data-stu-id="5832a-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5832a-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5832a-121">Requirements</span></span>  
 <span data-ttu-id="5832a-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5832a-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5832a-123">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5832a-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5832a-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5832a-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5832a-125">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5832a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5832a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="5832a-126">See also</span></span>

- [<span data-ttu-id="5832a-127">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5832a-127">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="5832a-128">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5832a-128">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="5832a-129">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5832a-129">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="5832a-130">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="5832a-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
