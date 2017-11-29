---
title: "ICLRDebugManager::SetSymbolReadingPolicy – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.SetSymbolReadingPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::SetSymbolReadingPolicy
helpviewer_keywords:
- ICLRDebugManager, SetSymbolREadingPolicy method
- SetSymbolReadingPolicy method [.NET Framework hosting]
- ICLRDebugManager::SetSymbolReadingPolicy method [.NET Framework hosting]
ms.assetid: bd921fa2-d377-4d79-acfc-64c38d4dcae9
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d116883c39b4400451ede07df83ac77893ce285c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="3039e-102">ICLRDebugManager::SetSymbolReadingPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="3039e-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="3039e-103">Nastavení zásad pro soubory databáze (PDB) program pro čtení.</span><span class="sxs-lookup"><span data-stu-id="3039e-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="3039e-104">Zásady určuje, zda je informace o čísla řádků a soubory součástí zásobníky volání.</span><span class="sxs-lookup"><span data-stu-id="3039e-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3039e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3039e-105">Syntax</span></span>  
  
```  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3039e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3039e-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="3039e-107">[v] Člen [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="3039e-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3039e-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3039e-108">Return Value</span></span>  
  
|<span data-ttu-id="3039e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3039e-109">HRESULT</span></span>|<span data-ttu-id="3039e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="3039e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3039e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3039e-111">S_OK</span></span>|<span data-ttu-id="3039e-112">`SetSymbolReadingPolicy`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="3039e-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="3039e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3039e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3039e-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3039e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3039e-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3039e-115">E_FAIL</span></span>|<span data-ttu-id="3039e-116">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="3039e-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3039e-117">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="3039e-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3039e-118">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3039e-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3039e-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3039e-119">Requirements</span></span>  
 <span data-ttu-id="3039e-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3039e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3039e-121">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3039e-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3039e-122">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3039e-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3039e-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3039e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3039e-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="3039e-124">See Also</span></span>  
 [<span data-ttu-id="3039e-125">Iclrdebugmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3039e-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
