---
title: ICorDebugTypeEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d47f14ff2adb37fca16cf6774a2b80cb2e074b17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157310"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="60f21-102">ICorDebugTypeEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="60f21-102">ICorDebugTypeEnum::Next Method</span></span>
<span data-ttu-id="60f21-103">Získá počet instancí "ICorDebugType" určené `celt` z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="60f21-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60f21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60f21-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60f21-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60f21-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="60f21-106">[in] Počet `ICorDebugType` instancí, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="60f21-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="60f21-107">[out] Pole ukazatelů, každý z nich odkazuje na `ICorDebugType` objektu.</span><span class="sxs-lookup"><span data-stu-id="60f21-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="60f21-108">[out] Ukazatel na počet `ICorDebugType` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="60f21-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="60f21-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="60f21-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60f21-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60f21-110">Requirements</span></span>  
 <span data-ttu-id="60f21-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60f21-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60f21-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60f21-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60f21-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60f21-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="60f21-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="60f21-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="60f21-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60f21-115">See also</span></span>
