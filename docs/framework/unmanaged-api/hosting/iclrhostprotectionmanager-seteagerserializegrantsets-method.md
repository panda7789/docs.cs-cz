---
title: "ICLRHostProtectionManager::SetEagerSerializeGrantSets – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager.SetEagerSerializeGrantSets
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager::SetEagerSerializeGrantSets
helpviewer_keywords:
- SetEagerSerializeGrantSets method [.NET Framework hosting]
- ICLRHostProtectionManager::SetEagerSerializeGrantSets method [.NET Framework hosting]
ms.assetid: d6158360-22b1-4ace-ad85-d830b9964783
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a9b1e314f7af6edf3d8db00780105dff95868a6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="833a9-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets – metoda</span><span class="sxs-lookup"><span data-stu-id="833a9-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="833a9-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="833a9-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="833a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="833a9-104">Syntax</span></span>  
  
```  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="833a9-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="833a9-105">Return Value</span></span>  
  
|<span data-ttu-id="833a9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="833a9-106">HRESULT</span></span>|<span data-ttu-id="833a9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="833a9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="833a9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="833a9-108">S_OK</span></span>|<span data-ttu-id="833a9-109">`SetEagerSerializeGrantSets`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="833a9-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="833a9-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="833a9-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="833a9-111">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="833a9-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="833a9-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="833a9-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="833a9-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="833a9-113">The call timed out.</span></span>|  
|<span data-ttu-id="833a9-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="833a9-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="833a9-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="833a9-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="833a9-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="833a9-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="833a9-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="833a9-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="833a9-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="833a9-118">E_FAIL</span></span>|<span data-ttu-id="833a9-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="833a9-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="833a9-120">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="833a9-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="833a9-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="833a9-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="833a9-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="833a9-122">Requirements</span></span>  
 <span data-ttu-id="833a9-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="833a9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="833a9-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="833a9-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="833a9-125">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="833a9-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="833a9-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="833a9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="833a9-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="833a9-127">See Also</span></span>  
 [<span data-ttu-id="833a9-128">Iclrcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="833a9-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="833a9-129">Iclrhostprotectionmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="833a9-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
