---
title: ICorDebugBreakpoint::IsActive – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::IsActive
helpviewer_keywords:
- ICorDebugBreakpoint::IsActive method [.NET Framework debugging]
- IsActive method, ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: 06e583d6-d88a-4ff5-bb95-5c48618a461c
topic_type:
- apiref
ms.openlocfilehash: 8df4e1df7836f340bb04fc47d1ca55e0fb7c9f0e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122771"
---
# <a name="icordebugbreakpointisactive-method"></a><span data-ttu-id="c4fcb-102">ICorDebugBreakpoint::IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="c4fcb-102">ICorDebugBreakpoint::IsActive Method</span></span>
<span data-ttu-id="c4fcb-103">Získá hodnotu, která označuje, zda je tato `ICorDebugBreakpoint` aktivní.</span><span class="sxs-lookup"><span data-stu-id="c4fcb-103">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4fcb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4fcb-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4fcb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4fcb-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="c4fcb-106">[out] `true`, pokud je tato zarážka aktivní; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="c4fcb-106">[out] `true` if this breakpoint is active; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4fcb-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4fcb-107">Requirements</span></span>  
 <span data-ttu-id="c4fcb-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4fcb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4fcb-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c4fcb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4fcb-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c4fcb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4fcb-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4fcb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
