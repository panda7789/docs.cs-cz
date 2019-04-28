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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18b65eb3e733fa7970e4c0e7de09755598eaf149
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645341"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="f5bdc-102">ICorDebugBreakpointEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="f5bdc-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="f5bdc-103">Získá zadaný počet instancí ICorDebugBreakpoint z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5bdc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5bdc-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5bdc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5bdc-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f5bdc-106">[in] Počet `ICorDebugBreakpoint` instancí, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="f5bdc-107">[out] Pole ukazatelů, každý z nich odkazuje na `ICorDebugBreakpoint` objekt, který představuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f5bdc-108">[out] Ukazatel na počet `ICorDebugBreakpoint` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="f5bdc-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5bdc-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5bdc-110">Requirements</span></span>  
 <span data-ttu-id="f5bdc-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5bdc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5bdc-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5bdc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5bdc-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5bdc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5bdc-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5bdc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
