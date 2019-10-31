---
title: ICorDebugModuleEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
ms.openlocfilehash: 6c4262c18e4efcbbca1b3e2a327fec7d4b609a31
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096929"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="a75da-102">ICorDebugModuleEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="a75da-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="a75da-103">Získá počet instancí "ICorDebugModule" určených `celt` z výčtu, počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="a75da-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a75da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a75da-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a75da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a75da-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a75da-106">pro Počet instancí `ICorDebugModule`, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="a75da-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="a75da-107">mimo Pole ukazatelů, z nichž každý odkazuje na objekt `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="a75da-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a75da-108">mimo Ukazatel na počet skutečně vrácených instancí `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="a75da-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="a75da-109">Tato hodnota může být null, pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="a75da-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a75da-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a75da-110">Requirements</span></span>  
 <span data-ttu-id="a75da-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a75da-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a75da-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a75da-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a75da-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a75da-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a75da-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a75da-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a75da-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a75da-115">See also</span></span>
