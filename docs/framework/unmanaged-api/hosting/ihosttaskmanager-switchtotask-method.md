---
title: IHostTaskManager::SwitchToTask – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SwitchToTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c4b6780b9784c5d02499224e6787f2cda6cc8e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442835"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="a9730-102">IHostTaskManager::SwitchToTask – metoda</span><span class="sxs-lookup"><span data-stu-id="a9730-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="a9730-103">Upozorní hostitele, musí přepnout na aktuální úlohy.</span><span class="sxs-lookup"><span data-stu-id="a9730-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9730-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9730-104">Syntax</span></span>  
  
```  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9730-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9730-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="a9730-106">[v] Jeden z [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty výčtu, který udává akci hostitele provést, pokud bloky požadovanou operaci.</span><span class="sxs-lookup"><span data-stu-id="a9730-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9730-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a9730-107">Return Value</span></span>  
  
|<span data-ttu-id="a9730-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9730-108">HRESULT</span></span>|<span data-ttu-id="a9730-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a9730-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9730-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9730-110">S_OK</span></span>|<span data-ttu-id="a9730-111">`SwitchToTask` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="a9730-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="a9730-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a9730-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a9730-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a9730-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a9730-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a9730-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a9730-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a9730-115">The call timed out.</span></span>|  
|<span data-ttu-id="a9730-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a9730-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a9730-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="a9730-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a9730-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a9730-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a9730-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="a9730-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a9730-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a9730-120">E_FAIL</span></span>|<span data-ttu-id="a9730-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="a9730-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a9730-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="a9730-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a9730-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a9730-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9730-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9730-124">Remarks</span></span>  
 <span data-ttu-id="a9730-125">Přepnout hostitele v jiné úloze jako požadovaný nebo potřebné.</span><span class="sxs-lookup"><span data-stu-id="a9730-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9730-126">`SwitchToTask` neurčuje který úkol hostitele by měl přepínače. Určuje pouze úloha, která by měla přejít z.</span><span class="sxs-lookup"><span data-stu-id="a9730-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9730-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9730-127">Requirements</span></span>  
 <span data-ttu-id="a9730-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9730-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9730-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a9730-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9730-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9730-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9730-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9730-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9730-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9730-132">See Also</span></span>  
 [<span data-ttu-id="a9730-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9730-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="a9730-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9730-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="a9730-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9730-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="a9730-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9730-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
