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
ms.openlocfilehash: 7969d8482970b13951938203262f6ce8f9bf574a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993951"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="4be35-102">ICorDebugThread3::CreateStackWalk – metoda</span><span class="sxs-lookup"><span data-stu-id="4be35-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="4be35-103">Vytvoří [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objektu pro vlákno, jehož zásobníku, které chcete vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="4be35-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4be35-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4be35-104">Syntax</span></span>  
  
```  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4be35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4be35-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="4be35-106">[out] Ukazatel na adresu [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objektu pro vlákno, jehož zásobníku, které chcete vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="4be35-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4be35-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4be35-107">Return Value</span></span>  
 <span data-ttu-id="4be35-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="4be35-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4be35-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4be35-109">HRESULT</span></span>|<span data-ttu-id="4be35-110">Popis</span><span class="sxs-lookup"><span data-stu-id="4be35-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4be35-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4be35-111">S_OK</span></span>|<span data-ttu-id="4be35-112">`ICorDebugStackWalk` Objekt byl úspěšně vytvořen.</span><span class="sxs-lookup"><span data-stu-id="4be35-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="4be35-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4be35-113">E_FAIL</span></span>|<span data-ttu-id="4be35-114">`ICorDebugStackWalk` Objekt nebyl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="4be35-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="4be35-115">Výjimky</span><span class="sxs-lookup"><span data-stu-id="4be35-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4be35-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4be35-116">Remarks</span></span>  
 <span data-ttu-id="4be35-117">Pokud `CreateStackWalk` metoda bude úspěšná, vrácený `ICorDebugStackWalk` objektu kontextu je nastavena na aktuální kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="4be35-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4be35-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4be35-118">Requirements</span></span>  
 <span data-ttu-id="4be35-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4be35-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4be35-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4be35-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4be35-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4be35-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4be35-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4be35-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4be35-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4be35-123">See also</span></span>

- [<span data-ttu-id="4be35-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4be35-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="4be35-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="4be35-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
