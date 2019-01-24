---
title: ICorDebugVariableHomeEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d383d4bf0f3d203c331ff00981885cbc6c0c35d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519200"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="5abf0-102">ICorDebugVariableHomeEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="5abf0-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="5abf0-103">Získá zadaný počet [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instancí, které obsahují informace o lokálních proměnných a argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="5abf0-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5abf0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5abf0-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5abf0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5abf0-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5abf0-106">[in] Počet objektů, které se mají načíst.</span><span class="sxs-lookup"><span data-stu-id="5abf0-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="5abf0-107">Pole ukazatelů, každý z nich odkazuje [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objekt, který poskytuje informace o místní proměnné nebo argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="5abf0-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="5abf0-108">[out] Počet instancí, které skutečně vrácených objektů.</span><span class="sxs-lookup"><span data-stu-id="5abf0-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5abf0-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5abf0-109">Return Value</span></span>  
 <span data-ttu-id="5abf0-110">Metoda vrátí následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5abf0-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="5abf0-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5abf0-111">HRESULT</span></span>|<span data-ttu-id="5abf0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5abf0-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5abf0-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="5abf0-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5abf0-114">Načíst skutečný počet instancí, jak jsou uvedeny v `pceltFetched`, je menší než počet instancí požadavku.</span><span class="sxs-lookup"><span data-stu-id="5abf0-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5abf0-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5abf0-115">Remarks</span></span>  
 <span data-ttu-id="5abf0-116">[ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) metoda načte maximálně `celt` objekty od aktuální pozice čítače výčtu.</span><span class="sxs-lookup"><span data-stu-id="5abf0-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="5abf0-117">Po návratu metody `pceltFetched` obsahuje skutečný počet objektů, které jsou načteny.</span><span class="sxs-lookup"><span data-stu-id="5abf0-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5abf0-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5abf0-118">Requirements</span></span>  
 <span data-ttu-id="5abf0-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5abf0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5abf0-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5abf0-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5abf0-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5abf0-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5abf0-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5abf0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5abf0-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5abf0-123">See also</span></span>
- [<span data-ttu-id="5abf0-124">ICorDebugVariableHomeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5abf0-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
- [<span data-ttu-id="5abf0-125">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5abf0-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
