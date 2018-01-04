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
ms.workload: dotnet
ms.openlocfilehash: f1d2bb2ecc4ae7edb4edbaa3ff36650c70c82daf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="a25e3-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets – metoda</span><span class="sxs-lookup"><span data-stu-id="a25e3-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="a25e3-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="a25e3-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a25e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a25e3-104">Syntax</span></span>  
  
```  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a25e3-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a25e3-105">Return Value</span></span>  
  
|<span data-ttu-id="a25e3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a25e3-106">HRESULT</span></span>|<span data-ttu-id="a25e3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a25e3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a25e3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a25e3-108">S_OK</span></span>|<span data-ttu-id="a25e3-109">`SetEagerSerializeGrantSets`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="a25e3-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="a25e3-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a25e3-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a25e3-111">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a25e3-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a25e3-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a25e3-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a25e3-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a25e3-113">The call timed out.</span></span>|  
|<span data-ttu-id="a25e3-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a25e3-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a25e3-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="a25e3-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a25e3-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a25e3-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a25e3-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="a25e3-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a25e3-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a25e3-118">E_FAIL</span></span>|<span data-ttu-id="a25e3-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="a25e3-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a25e3-120">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="a25e3-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a25e3-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a25e3-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a25e3-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a25e3-122">Requirements</span></span>  
 <span data-ttu-id="a25e3-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a25e3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a25e3-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a25e3-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a25e3-125">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a25e3-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a25e3-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a25e3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a25e3-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="a25e3-127">See Also</span></span>  
 [<span data-ttu-id="a25e3-128">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a25e3-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="a25e3-129">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a25e3-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
