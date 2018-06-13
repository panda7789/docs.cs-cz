---
title: ICorDebugThread3::CreateStackWalk – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.CreateStackWalk Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1ae7cdcdc604bef98fdb8a891c9f0118edcffea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421775"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="dc911-102">ICorDebugThread3::CreateStackWalk – metoda</span><span class="sxs-lookup"><span data-stu-id="dc911-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="dc911-103">Vytvoří [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objekt, pro jehož zásobníku chcete unwind vlákno.</span><span class="sxs-lookup"><span data-stu-id="dc911-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc911-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc911-104">Syntax</span></span>  
  
```  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc911-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc911-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="dc911-106">[out] Ukazatel na adresu [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objekt, pro jehož zásobníku chcete unwind vlákno.</span><span class="sxs-lookup"><span data-stu-id="dc911-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc911-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dc911-107">Return Value</span></span>  
 <span data-ttu-id="dc911-108">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="dc911-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="dc911-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc911-109">HRESULT</span></span>|<span data-ttu-id="dc911-110">Popis</span><span class="sxs-lookup"><span data-stu-id="dc911-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc911-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dc911-111">S_OK</span></span>|<span data-ttu-id="dc911-112">`ICorDebugStackWalk` Objekt byl úspěšně vytvořen.</span><span class="sxs-lookup"><span data-stu-id="dc911-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="dc911-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dc911-113">E_FAIL</span></span>|<span data-ttu-id="dc911-114">`ICorDebugStackWalk` Objekt nebyl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="dc911-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="dc911-115">Výjimky</span><span class="sxs-lookup"><span data-stu-id="dc911-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc911-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc911-116">Remarks</span></span>  
 <span data-ttu-id="dc911-117">Pokud `CreateStackWalk` metoda bude úspěšná, vrácený `ICorDebugStackWalk` objektu kontextu je nastaven na aktuální kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="dc911-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc911-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc911-118">Requirements</span></span>  
 <span data-ttu-id="dc911-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc911-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc911-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc911-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc911-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc911-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc911-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc911-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc911-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc911-123">See Also</span></span>  
 [<span data-ttu-id="dc911-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dc911-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="dc911-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="dc911-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
