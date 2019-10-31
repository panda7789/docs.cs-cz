---
title: ICorDebugThreadEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum::Next
helpviewer_keywords:
- ICorDebugThreadEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: f967c93d-9a7f-4aaf-99a1-a1317899ff3f
topic_type:
- apiref
ms.openlocfilehash: 0c455706b0d644d2444e9fbdf49c5a5d4f5295a9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122393"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="39778-102">ICorDebugThreadEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="39778-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="39778-103">Získá počet zadaných instancí ICorDebugThread z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="39778-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39778-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39778-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39778-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="39778-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="39778-106">pro Počet instancí `ICorDebugThread`, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="39778-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="39778-107">mimo Pole ukazatelů, z nichž každý odkazuje na objekt `ICorDebugThread`, který představuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="39778-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="39778-108">mimo Ukazatel na počet skutečně vrácených instancí `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="39778-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="39778-109">Tato hodnota může být null, pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="39778-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39778-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="39778-110">Requirements</span></span>  
 <span data-ttu-id="39778-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39778-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39778-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="39778-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39778-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="39778-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39778-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39778-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
