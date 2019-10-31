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
ms.openlocfilehash: 6737b953f39c1087d01f3fb864d84340a6968aba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129358"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="74c95-102">ICLRDebugManager::SetSymbolReadingPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="74c95-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="74c95-103">Nastaví zásadu pro soubory databáze programu pro čtení.</span><span class="sxs-lookup"><span data-stu-id="74c95-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="74c95-104">Tato zásada určuje, zda jsou do zásobníků volání zahrnuty informace o číslech řádků a souborech.</span><span class="sxs-lookup"><span data-stu-id="74c95-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74c95-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74c95-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74c95-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="74c95-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="74c95-107">pro Člen výčtu [ESymbolReadingPolicy –](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="74c95-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74c95-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="74c95-108">Return Value</span></span>  
  
|<span data-ttu-id="74c95-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74c95-109">HRESULT</span></span>|<span data-ttu-id="74c95-110">Popis</span><span class="sxs-lookup"><span data-stu-id="74c95-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74c95-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="74c95-111">S_OK</span></span>|<span data-ttu-id="74c95-112">`SetSymbolReadingPolicy` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="74c95-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="74c95-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="74c95-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="74c95-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="74c95-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="74c95-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="74c95-115">E_FAIL</span></span>|<span data-ttu-id="74c95-116">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="74c95-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="74c95-117">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="74c95-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="74c95-118">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="74c95-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74c95-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74c95-119">Requirements</span></span>  
 <span data-ttu-id="74c95-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74c95-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74c95-121">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="74c95-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="74c95-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="74c95-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74c95-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74c95-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74c95-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74c95-124">See also</span></span>

- [<span data-ttu-id="74c95-125">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74c95-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
