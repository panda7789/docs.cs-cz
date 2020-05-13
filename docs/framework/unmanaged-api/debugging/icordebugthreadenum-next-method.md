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
ms.openlocfilehash: c025afac1b53b23636a6160a475704011999d434
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379048"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="62c6c-102">ICorDebugThreadEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="62c6c-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="62c6c-103">Získá počet zadaných instancí ICorDebugThread z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="62c6c-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62c6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62c6c-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62c6c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62c6c-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="62c6c-106">pro Počet instancí, `ICorDebugThread` které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="62c6c-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="62c6c-107">mimo Pole ukazatelů, z nichž každý odkazuje na `ICorDebugThread` objekt, který představuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="62c6c-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="62c6c-108">mimo Ukazatel na počet `ICorDebugThread` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="62c6c-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="62c6c-109">Tato hodnota může být null `celt` , pokud je jedna.</span><span class="sxs-lookup"><span data-stu-id="62c6c-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62c6c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62c6c-110">Requirements</span></span>  
 <span data-ttu-id="62c6c-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62c6c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62c6c-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="62c6c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62c6c-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="62c6c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62c6c-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62c6c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
