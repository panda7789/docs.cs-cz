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
ms.openlocfilehash: be59acea8eadb0da9e3cd26cf17eb9e1617c3575
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141062"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="17fcb-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets – metoda</span><span class="sxs-lookup"><span data-stu-id="17fcb-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="17fcb-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="17fcb-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17fcb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17fcb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="17fcb-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="17fcb-105">Return Value</span></span>  
  
|<span data-ttu-id="17fcb-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="17fcb-106">HRESULT</span></span>|<span data-ttu-id="17fcb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="17fcb-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17fcb-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="17fcb-108">S_OK</span></span>|<span data-ttu-id="17fcb-109">`SetEagerSerializeGrantSets` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="17fcb-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="17fcb-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="17fcb-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="17fcb-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="17fcb-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="17fcb-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="17fcb-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="17fcb-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="17fcb-113">The call timed out.</span></span>|  
|<span data-ttu-id="17fcb-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="17fcb-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="17fcb-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="17fcb-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="17fcb-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="17fcb-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="17fcb-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="17fcb-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="17fcb-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="17fcb-118">E_FAIL</span></span>|<span data-ttu-id="17fcb-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="17fcb-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="17fcb-120">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="17fcb-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="17fcb-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="17fcb-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="17fcb-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17fcb-122">Requirements</span></span>  
 <span data-ttu-id="17fcb-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17fcb-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17fcb-124">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="17fcb-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17fcb-125">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="17fcb-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17fcb-126">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17fcb-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17fcb-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17fcb-127">See also</span></span>

- [<span data-ttu-id="17fcb-128">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17fcb-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="17fcb-129">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17fcb-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
