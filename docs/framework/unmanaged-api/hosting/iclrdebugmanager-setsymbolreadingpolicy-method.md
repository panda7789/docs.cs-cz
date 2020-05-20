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
ms.openlocfilehash: f037e902a9f573023022c81503ea3b987cf6d424
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615742"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="f5eca-102">ICLRDebugManager::SetSymbolReadingPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="f5eca-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="f5eca-103">Nastaví zásadu pro soubory databáze programu pro čtení.</span><span class="sxs-lookup"><span data-stu-id="f5eca-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="f5eca-104">Tato zásada určuje, zda jsou do zásobníků volání zahrnuty informace o číslech řádků a souborech.</span><span class="sxs-lookup"><span data-stu-id="f5eca-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5eca-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5eca-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5eca-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5eca-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="f5eca-107">pro Člen výčtu [ESymbolReadingPolicy –](esymbolreadingpolicy-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="f5eca-107">[in] A member of the [ESymbolReadingPolicy](esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5eca-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f5eca-108">Return Value</span></span>  
  
|<span data-ttu-id="f5eca-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5eca-109">HRESULT</span></span>|<span data-ttu-id="f5eca-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f5eca-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5eca-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5eca-111">S_OK</span></span>|<span data-ttu-id="f5eca-112">`SetSymbolReadingPolicy`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f5eca-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="f5eca-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f5eca-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f5eca-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f5eca-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f5eca-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5eca-115">E_FAIL</span></span>|<span data-ttu-id="f5eca-116">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="f5eca-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5eca-117">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="f5eca-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f5eca-118">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f5eca-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5eca-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5eca-119">Requirements</span></span>  
 <span data-ttu-id="f5eca-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5eca-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5eca-121">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f5eca-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5eca-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f5eca-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5eca-123">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5eca-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5eca-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5eca-124">See also</span></span>

- [<span data-ttu-id="f5eca-125">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5eca-125">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
