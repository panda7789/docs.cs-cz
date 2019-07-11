---
title: ICLRDebugManager::SetSymbolReadingPolicy – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetSymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetSymbolReadingPolicy
helpviewer_keywords:
- ICLRDebugManager, SetSymbolREadingPolicy method
- SetSymbolReadingPolicy method [.NET Framework hosting]
- ICLRDebugManager::SetSymbolReadingPolicy method [.NET Framework hosting]
ms.assetid: bd921fa2-d377-4d79-acfc-64c38d4dcae9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2921484cb2baa92593ddb0335cf7b20c5c0f33eb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773018"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="12a36-102">ICLRDebugManager::SetSymbolReadingPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="12a36-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="12a36-103">Nastavit zásady pro čtení souborů databáze (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="12a36-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="12a36-104">Zásady určuje, zda informace o čísla řádků a souborů je součástí zásobníky volání.</span><span class="sxs-lookup"><span data-stu-id="12a36-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12a36-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12a36-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12a36-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="12a36-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="12a36-107">[in] Člen [esymbolreadingpolicy –](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="12a36-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12a36-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="12a36-108">Return Value</span></span>  
  
|<span data-ttu-id="12a36-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="12a36-109">HRESULT</span></span>|<span data-ttu-id="12a36-110">Popis</span><span class="sxs-lookup"><span data-stu-id="12a36-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="12a36-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="12a36-111">S_OK</span></span>|<span data-ttu-id="12a36-112">`SetSymbolReadingPolicy` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="12a36-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="12a36-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="12a36-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="12a36-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="12a36-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="12a36-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="12a36-115">E_FAIL</span></span>|<span data-ttu-id="12a36-116">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="12a36-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="12a36-117">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="12a36-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="12a36-118">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="12a36-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="12a36-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12a36-119">Requirements</span></span>  
 <span data-ttu-id="12a36-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12a36-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12a36-121">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="12a36-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="12a36-122">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="12a36-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12a36-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12a36-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12a36-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12a36-124">See also</span></span>

- [<span data-ttu-id="12a36-125">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12a36-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
