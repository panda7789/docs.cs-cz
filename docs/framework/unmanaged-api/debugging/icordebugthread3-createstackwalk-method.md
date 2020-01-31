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
ms.openlocfilehash: 64f6bc9abb8105cdfa942c2aaca71994e8a91765
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791418"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="2d789-102">ICorDebugThread3::CreateStackWalk – metoda</span><span class="sxs-lookup"><span data-stu-id="2d789-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="2d789-103">Vytvoří objekt [ICorDebugStackWalk](icordebugstackwalk-interface.md) pro vlákno, jehož zásobník chcete vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="2d789-103">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d789-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d789-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d789-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d789-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="2d789-106">mimo Ukazatel na adresu objektu [ICorDebugStackWalk](icordebugstackwalk-interface.md) pro vlákno, jehož zásobník chcete vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="2d789-106">[out] A pointer to address of the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d789-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2d789-107">Return Value</span></span>  
 <span data-ttu-id="2d789-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="2d789-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2d789-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d789-109">HRESULT</span></span>|<span data-ttu-id="2d789-110">Popis</span><span class="sxs-lookup"><span data-stu-id="2d789-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d789-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d789-111">S_OK</span></span>|<span data-ttu-id="2d789-112">Objekt `ICorDebugStackWalk` byl úspěšně vytvořen.</span><span class="sxs-lookup"><span data-stu-id="2d789-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="2d789-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2d789-113">E_FAIL</span></span>|<span data-ttu-id="2d789-114">Objekt `ICorDebugStackWalk` nebyl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="2d789-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="2d789-115">Výjimky</span><span class="sxs-lookup"><span data-stu-id="2d789-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d789-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d789-116">Remarks</span></span>  
 <span data-ttu-id="2d789-117">Pokud je metoda `CreateStackWalk` úspěšná, vrácený kontext objektu `ICorDebugStackWalk` je nastaven na aktuální kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="2d789-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d789-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d789-118">Requirements</span></span>  
 <span data-ttu-id="2d789-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d789-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d789-120">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2d789-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d789-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2d789-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d789-122">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d789-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d789-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d789-123">See also</span></span>

- [<span data-ttu-id="2d789-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2d789-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2d789-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="2d789-125">Debugging</span></span>](index.md)
