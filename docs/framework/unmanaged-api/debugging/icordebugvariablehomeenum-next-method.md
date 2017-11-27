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
ms.openlocfilehash: 480317a4ec0515411f1ca8156a5bc4d06aa3f38a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="9a041-102">ICorDebugVariableHomeEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="9a041-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="9a041-103">Získá zadaný počet [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instancí, které obsahují informace o místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="9a041-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a041-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a041-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a041-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a041-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9a041-106">[v] Počet objektů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="9a041-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="9a041-107">Ukazatele, každý z nich odkazuje na pole [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objekt, který obsahuje informace o místní proměnné nebo argument funkce.</span><span class="sxs-lookup"><span data-stu-id="9a041-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9a041-108">[out] Počet instancí ve skutečnosti vrácených v objektech.</span><span class="sxs-lookup"><span data-stu-id="9a041-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a041-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9a041-109">Return Value</span></span>  
 <span data-ttu-id="9a041-110">Metoda vrátí následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9a041-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="9a041-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a041-111">HRESULT</span></span>|<span data-ttu-id="9a041-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9a041-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9a041-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="9a041-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9a041-114">Načíst skutečný počet instancí, jak jsou uvedeny v `pceltFetched`, je menší než počet instancí požadovaný.</span><span class="sxs-lookup"><span data-stu-id="9a041-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a041-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a041-115">Remarks</span></span>  
 <span data-ttu-id="9a041-116">[ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) metoda načte maximálně `celt` objekty začínající na aktuální pozici enumerátor.</span><span class="sxs-lookup"><span data-stu-id="9a041-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="9a041-117">Po návratu metody `pceltFetched` obsahuje skutečný počet objektů načíst.</span><span class="sxs-lookup"><span data-stu-id="9a041-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a041-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9a041-118">Requirements</span></span>  
 <span data-ttu-id="9a041-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a041-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a041-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a041-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a041-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a041-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a041-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a041-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a041-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a041-123">See Also</span></span>  
 [<span data-ttu-id="9a041-124">ICorDebugVariableHomeEnum rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a041-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 [<span data-ttu-id="9a041-125">ICorDebugVariableHome rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a041-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
