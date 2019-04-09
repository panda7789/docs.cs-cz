---
title: ICorDebugCodeEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5db87cd4ad965654b63a68828cd088b8d2f7d07c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113045"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="c6ce7-102">ICorDebugCodeEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="c6ce7-102">ICorDebugCodeEnum::Next Method</span></span>
<span data-ttu-id="c6ce7-103">Získá zadaný počet instancí "ICorDebugCode" z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="c6ce7-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6ce7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6ce7-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugCode *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6ce7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6ce7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c6ce7-106">[in] Počet `ICorDebugCode` instancí, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="c6ce7-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="c6ce7-107">[out] Pole ukazatelů, každý z nich odkazuje na `ICorDebugCode` objektu.</span><span class="sxs-lookup"><span data-stu-id="c6ce7-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c6ce7-108">[out] Ukazatel na počet `ICorDebugCode` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="c6ce7-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="c6ce7-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="c6ce7-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6ce7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6ce7-110">Requirements</span></span>  
 <span data-ttu-id="c6ce7-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6ce7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6ce7-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6ce7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6ce7-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6ce7-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c6ce7-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c6ce7-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c6ce7-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6ce7-115">See also</span></span>
