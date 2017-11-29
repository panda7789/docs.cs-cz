---
title: "ICorRuntimeHost::CloseEnum – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CloseEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b44797f6efaf8904e3df876e9278a977c912ac6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="1ec10-102">ICorRuntimeHost::CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="1ec10-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="1ec10-103">Obnoví enumerátor domény zpět na začátek seznamu domény.</span><span class="sxs-lookup"><span data-stu-id="1ec10-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ec10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ec10-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ec10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ec10-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="1ec10-106">[v] Enumerátor resetovat.</span><span class="sxs-lookup"><span data-stu-id="1ec10-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ec10-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1ec10-107">Return Value</span></span>  
  
|<span data-ttu-id="1ec10-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ec10-108">HRESULT</span></span>|<span data-ttu-id="1ec10-109">Popis</span><span class="sxs-lookup"><span data-stu-id="1ec10-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ec10-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ec10-110">S_OK</span></span>|<span data-ttu-id="1ec10-111">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="1ec10-111">The operation was successful.</span></span>|  
|<span data-ttu-id="1ec10-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1ec10-112">S_FALSE</span></span>|<span data-ttu-id="1ec10-113">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="1ec10-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1ec10-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1ec10-114">E_FAIL</span></span>|<span data-ttu-id="1ec10-115">Došlo k neznámé, závažnou chybu.</span><span class="sxs-lookup"><span data-stu-id="1ec10-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1ec10-116">Pokud metoda vrátí E_FAIL, modul CLR (CLR) již není použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="1ec10-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1ec10-117">Následující volání žádné hostování rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1ec10-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1ec10-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1ec10-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1ec10-119">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="1ec10-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ec10-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1ec10-120">Requirements</span></span>  
 <span data-ttu-id="1ec10-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ec10-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ec10-122">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1ec10-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ec10-123">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ec10-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ec10-124">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="1ec10-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ec10-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ec10-125">See Also</span></span>  
 [<span data-ttu-id="1ec10-126">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="1ec10-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="1ec10-127">Icorruntimehost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ec10-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
