---
title: ICorDebugBreakpointEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBreakpointEnum interface [.NET Framework debugging]
- ICorDebugBreakpointEnum::Next method [.NET Framework debugging]
ms.assetid: 2e6bbaea-79ba-448c-a0e3-7c90fc7c2939
topic_type:
- apiref
ms.openlocfilehash: d29576c6f073f1d0e8e0aea417fc38c09a8327c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122749"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="7c6fc-102">ICorDebugBreakpointEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="7c6fc-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="7c6fc-103">Získá zadaný počet instancí ICorDebugBreakpoint z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="7c6fc-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c6fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c6fc-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c6fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c6fc-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7c6fc-106">pro Počet instancí `ICorDebugBreakpoint`, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="7c6fc-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="7c6fc-107">mimo Pole ukazatelů, z nichž každý odkazuje na objekt `ICorDebugBreakpoint`, který představuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="7c6fc-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7c6fc-108">mimo Ukazatel na počet skutečně vrácených instancí `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="7c6fc-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="7c6fc-109">Tato hodnota může být null, pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="7c6fc-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c6fc-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c6fc-110">Requirements</span></span>  
 <span data-ttu-id="7c6fc-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c6fc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c6fc-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7c6fc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c6fc-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7c6fc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c6fc-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c6fc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
