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
ms.openlocfilehash: af90886390b59932d3ae146a70fc2901ec1c378d
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894668"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="6e0ab-102">ICorDebugBreakpointEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="6e0ab-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="6e0ab-103">Získá zadaný počet instancí ICorDebugBreakpoint z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="6e0ab-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e0ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e0ab-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e0ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e0ab-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6e0ab-106">pro Počet `ICorDebugBreakpoint` instancí, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="6e0ab-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="6e0ab-107">mimo Pole ukazatelů, z nichž každý odkazuje na `ICorDebugBreakpoint` objekt, který představuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="6e0ab-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6e0ab-108">mimo Ukazatel na počet skutečně vrácených `ICorDebugBreakpoint` instancí.</span><span class="sxs-lookup"><span data-stu-id="6e0ab-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="6e0ab-109">Tato hodnota může být null, `celt` Pokud je jedna.</span><span class="sxs-lookup"><span data-stu-id="6e0ab-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e0ab-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e0ab-110">Requirements</span></span>  
 <span data-ttu-id="6e0ab-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e0ab-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e0ab-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6e0ab-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e0ab-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6e0ab-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e0ab-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e0ab-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
