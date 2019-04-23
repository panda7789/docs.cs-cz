---
title: ICLRHostProtectionManager::SetEagerSerializeGrantSets – metoda
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetEagerSerializeGrantSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetEagerSerializeGrantSets
helpviewer_keywords:
- SetEagerSerializeGrantSets method [.NET Framework hosting]
- ICLRHostProtectionManager::SetEagerSerializeGrantSets method [.NET Framework hosting]
ms.assetid: d6158360-22b1-4ace-ad85-d830b9964783
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 160e31859e3d58812861d4462e77d68fa18d6186
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079653"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="243f0-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets – metoda</span><span class="sxs-lookup"><span data-stu-id="243f0-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="243f0-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="243f0-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="243f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="243f0-104">Syntax</span></span>  
  
```  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="243f0-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="243f0-105">Return Value</span></span>  
  
|<span data-ttu-id="243f0-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="243f0-106">HRESULT</span></span>|<span data-ttu-id="243f0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="243f0-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="243f0-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="243f0-108">S_OK</span></span>|<span data-ttu-id="243f0-109">`SetEagerSerializeGrantSets` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="243f0-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="243f0-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="243f0-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="243f0-111">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="243f0-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="243f0-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="243f0-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="243f0-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="243f0-113">The call timed out.</span></span>|  
|<span data-ttu-id="243f0-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="243f0-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="243f0-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="243f0-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="243f0-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="243f0-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="243f0-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="243f0-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="243f0-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="243f0-118">E_FAIL</span></span>|<span data-ttu-id="243f0-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="243f0-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="243f0-120">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="243f0-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="243f0-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="243f0-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="243f0-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="243f0-122">Requirements</span></span>  
 <span data-ttu-id="243f0-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="243f0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="243f0-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="243f0-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="243f0-125">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="243f0-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="243f0-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="243f0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="243f0-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="243f0-127">See also</span></span>

- [<span data-ttu-id="243f0-128">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="243f0-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="243f0-129">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="243f0-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
