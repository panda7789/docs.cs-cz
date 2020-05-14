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
ms.openlocfilehash: 83adea3d659eea6d4af9ae364aad18df67e69c03
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396625"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="c0ae2-102">ICorDebugTypeEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="c0ae2-102">ICorDebugTypeEnum::Next Method</span></span>
<span data-ttu-id="c0ae2-103">Získá počet instancí "ICorDebugType" určených `celt` od výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="c0ae2-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0ae2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0ae2-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0ae2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0ae2-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c0ae2-106">pro Počet instancí, `ICorDebugType` které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="c0ae2-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="c0ae2-107">mimo Pole ukazatelů, z nichž každý odkazuje na `ICorDebugType` objekt.</span><span class="sxs-lookup"><span data-stu-id="c0ae2-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c0ae2-108">mimo Ukazatel na počet `ICorDebugType` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="c0ae2-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="c0ae2-109">Tato hodnota může být null `celt` , pokud je jedna.</span><span class="sxs-lookup"><span data-stu-id="c0ae2-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0ae2-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c0ae2-110">Requirements</span></span>  
 <span data-ttu-id="c0ae2-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0ae2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0ae2-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c0ae2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0ae2-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c0ae2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0ae2-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0ae2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0ae2-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0ae2-115">See also</span></span>
