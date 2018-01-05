---
title: "ICorDebugVariableHomeEnum::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHomeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3bab158cbbe2eaf6e52ae0df6a0eed86d3d0b8ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="47b5a-102">ICorDebugVariableHomeEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="47b5a-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="47b5a-103">Získá zadaný počet [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instancí, které obsahují informace o místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="47b5a-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47b5a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47b5a-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47b5a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="47b5a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="47b5a-106">[v] Počet objektů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="47b5a-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="47b5a-107">Ukazatele, každý z nich odkazuje na pole [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objekt, který obsahuje informace o místní proměnné nebo argument funkce.</span><span class="sxs-lookup"><span data-stu-id="47b5a-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="47b5a-108">[out] Počet instancí ve skutečnosti vrácených v objektech.</span><span class="sxs-lookup"><span data-stu-id="47b5a-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47b5a-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="47b5a-109">Return Value</span></span>  
 <span data-ttu-id="47b5a-110">Metoda vrátí následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="47b5a-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="47b5a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="47b5a-111">HRESULT</span></span>|<span data-ttu-id="47b5a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="47b5a-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="47b5a-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="47b5a-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="47b5a-114">Načíst skutečný počet instancí, jak jsou uvedeny v `pceltFetched`, je menší než počet instancí požadovaný.</span><span class="sxs-lookup"><span data-stu-id="47b5a-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47b5a-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47b5a-115">Remarks</span></span>  
 <span data-ttu-id="47b5a-116">[ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) metoda načte maximálně `celt` objekty začínající na aktuální pozici enumerátor.</span><span class="sxs-lookup"><span data-stu-id="47b5a-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="47b5a-117">Po návratu metody `pceltFetched` obsahuje skutečný počet objektů načíst.</span><span class="sxs-lookup"><span data-stu-id="47b5a-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47b5a-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47b5a-118">Requirements</span></span>  
 <span data-ttu-id="47b5a-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47b5a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47b5a-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47b5a-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47b5a-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47b5a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47b5a-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47b5a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b5a-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="47b5a-123">See Also</span></span>  
 [<span data-ttu-id="47b5a-124">ICorDebugVariableHomeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47b5a-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 [<span data-ttu-id="47b5a-125">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47b5a-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
