---
title: ICorDebugValueEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
ms.openlocfilehash: db1721fed6414310556ceac493275e069a781ac8
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397134"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="9ca89-102">ICorDebugValueEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="9ca89-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="9ca89-103">Získá zadaný počet instancí "ICorDebugValue" z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="9ca89-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ca89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ca89-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ca89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ca89-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9ca89-106">pro Počet instancí, `ICorDebugValue` které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="9ca89-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="9ca89-107">mimo Pole ukazatelů, z nichž každý odkazuje na `ICorDebugValue` objekt.</span><span class="sxs-lookup"><span data-stu-id="9ca89-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9ca89-108">mimo Ukazatel na počet `ICorDebugValue` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="9ca89-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="9ca89-109">Tato hodnota může být null `celt` , pokud je jedna.</span><span class="sxs-lookup"><span data-stu-id="9ca89-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ca89-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ca89-110">Requirements</span></span>  
 <span data-ttu-id="9ca89-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ca89-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ca89-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9ca89-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ca89-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9ca89-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ca89-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ca89-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca89-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ca89-115">See also</span></span>
