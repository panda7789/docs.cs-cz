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
ms.openlocfilehash: e9bddaa25ba83570389a9d70ac1a9f60357f533c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432219"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="0faef-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets – metoda</span><span class="sxs-lookup"><span data-stu-id="0faef-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="0faef-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="0faef-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0faef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0faef-104">Syntax</span></span>  
  
```  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0faef-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0faef-105">Return Value</span></span>  
  
|<span data-ttu-id="0faef-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0faef-106">HRESULT</span></span>|<span data-ttu-id="0faef-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0faef-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0faef-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0faef-108">S_OK</span></span>|<span data-ttu-id="0faef-109">`SetEagerSerializeGrantSets` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="0faef-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="0faef-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0faef-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0faef-111">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0faef-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0faef-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0faef-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0faef-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0faef-113">The call timed out.</span></span>|  
|<span data-ttu-id="0faef-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0faef-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0faef-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="0faef-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0faef-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0faef-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0faef-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="0faef-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0faef-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0faef-118">E_FAIL</span></span>|<span data-ttu-id="0faef-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="0faef-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0faef-120">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="0faef-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0faef-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0faef-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0faef-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0faef-122">Requirements</span></span>  
 <span data-ttu-id="0faef-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0faef-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0faef-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0faef-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0faef-125">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0faef-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0faef-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0faef-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0faef-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="0faef-127">See Also</span></span>  
 [<span data-ttu-id="0faef-128">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0faef-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="0faef-129">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0faef-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
