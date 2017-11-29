---
title: "IHostTaskManager::EnterRuntime – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.EnterRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a4c0304047246c912be965d80a26b26ec2344ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="98e5e-102">IHostTaskManager::EnterRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="98e5e-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="98e5e-103">Upozorní hostitele, že volání pro metodu nespravované, jako je platforma vyvolání metody vrací řízení provádění do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="98e5e-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98e5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98e5e-104">Syntax</span></span>  
  
```  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="98e5e-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="98e5e-105">Return Value</span></span>  
  
|<span data-ttu-id="98e5e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98e5e-106">HRESULT</span></span>|<span data-ttu-id="98e5e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="98e5e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98e5e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="98e5e-108">S_OK</span></span>|<span data-ttu-id="98e5e-109">`EnterRuntime`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="98e5e-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="98e5e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="98e5e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="98e5e-111">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="98e5e-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="98e5e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="98e5e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="98e5e-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="98e5e-113">The call timed out.</span></span>|  
|<span data-ttu-id="98e5e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="98e5e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="98e5e-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="98e5e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="98e5e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="98e5e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="98e5e-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="98e5e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="98e5e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="98e5e-118">E_FAIL</span></span>|<span data-ttu-id="98e5e-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="98e5e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="98e5e-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="98e5e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="98e5e-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="98e5e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="98e5e-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="98e5e-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="98e5e-123">Nedostatek paměti nebylo k dispozici k dokončení požadované přidělení.</span><span class="sxs-lookup"><span data-stu-id="98e5e-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98e5e-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98e5e-124">Remarks</span></span>  
 <span data-ttu-id="98e5e-125">`EnterRuntime`je volána oznámit hostitele, nespravované funkce, pro který starší volání [leaveruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) metoda byl proveden, byl dokončen a vrací řízení provádění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="98e5e-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98e5e-126">[Reverseenterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) nazývá oznámit hostitele, nespravované funkce, pro kterou starší volání `LeaveRuntime` byl proveden, je vytvořit volání do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="98e5e-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98e5e-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98e5e-127">Requirements</span></span>  
 <span data-ttu-id="98e5e-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98e5e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98e5e-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="98e5e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98e5e-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="98e5e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98e5e-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98e5e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e5e-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="98e5e-132">See Also</span></span>  
 [<span data-ttu-id="98e5e-133">Interoperabilita modelů COM Upřesnit</span><span class="sxs-lookup"><span data-stu-id="98e5e-133">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="98e5e-134">Postupy: volání nativních knihoven DLL ze spravovaného kódu pomocí služby PInvoke</span><span class="sxs-lookup"><span data-stu-id="98e5e-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)  
 [<span data-ttu-id="98e5e-135">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="98e5e-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="98e5e-136">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="98e5e-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="98e5e-137">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="98e5e-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="98e5e-138">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="98e5e-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="98e5e-139">Leaveruntime – metoda</span><span class="sxs-lookup"><span data-stu-id="98e5e-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
