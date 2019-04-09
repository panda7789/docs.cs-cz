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
ms.openlocfilehash: be1ba87ae979911dd21647569725eafa2c80ffa6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080720"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="2e6c6-102">ICorDebugVariableHomeEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="2e6c6-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="2e6c6-103">Získá zadaný počet [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instancí, které obsahují informace o lokálních proměnných a argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="2e6c6-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e6c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e6c6-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e6c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e6c6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="2e6c6-106">[in] Počet objektů, které se mají načíst.</span><span class="sxs-lookup"><span data-stu-id="2e6c6-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="2e6c6-107">Pole ukazatelů, každý z nich odkazuje [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objekt, který poskytuje informace o místní proměnné nebo argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="2e6c6-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="2e6c6-108">[out] Počet instancí, které skutečně vrácených objektů.</span><span class="sxs-lookup"><span data-stu-id="2e6c6-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e6c6-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2e6c6-109">Return Value</span></span>  
 <span data-ttu-id="2e6c6-110">Metoda vrátí následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2e6c6-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="2e6c6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e6c6-111">HRESULT</span></span>|<span data-ttu-id="2e6c6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2e6c6-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2e6c6-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="2e6c6-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2e6c6-114">Načíst skutečný počet instancí, jak jsou uvedeny v `pceltFetched`, je menší než počet instancí požadavku.</span><span class="sxs-lookup"><span data-stu-id="2e6c6-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e6c6-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e6c6-115">Remarks</span></span>  
 <span data-ttu-id="2e6c6-116">[ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) metoda načte maximálně `celt` objekty od aktuální pozice čítače výčtu.</span><span class="sxs-lookup"><span data-stu-id="2e6c6-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="2e6c6-117">Po návratu metody `pceltFetched` obsahuje skutečný počet objektů, které jsou načteny.</span><span class="sxs-lookup"><span data-stu-id="2e6c6-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e6c6-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e6c6-118">Requirements</span></span>  
 <span data-ttu-id="2e6c6-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e6c6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e6c6-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e6c6-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e6c6-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e6c6-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2e6c6-122">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2e6c6-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2e6c6-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e6c6-123">See also</span></span>

- [<span data-ttu-id="2e6c6-124">ICorDebugVariableHomeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e6c6-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
- [<span data-ttu-id="2e6c6-125">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e6c6-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
