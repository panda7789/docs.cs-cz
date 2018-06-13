---
title: ICorDebugFrameEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f049a7cadf1857495e49b9bdc2fecd1b49103af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415480"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="eba10-102">ICorDebugFrameEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="eba10-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="eba10-103">Získá zadaný počet instancí ICorDebugFrame, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="eba10-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eba10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eba10-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eba10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eba10-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="eba10-106">[v] Počet `ICorDebugFrame` instancí, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="eba10-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="eba10-107">[out] Ukazatele, každý z nich odkazuje na pole `ICorDebugFrame` objektu.</span><span class="sxs-lookup"><span data-stu-id="eba10-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="eba10-108">[out] Ukazatel na počet `ICorDebugFrame` instancí vrácených ve skutečnosti.</span><span class="sxs-lookup"><span data-stu-id="eba10-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="eba10-109">Tato hodnota může být null. Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="eba10-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eba10-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eba10-110">Requirements</span></span>  
 <span data-ttu-id="eba10-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eba10-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eba10-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eba10-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eba10-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eba10-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eba10-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eba10-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
