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
ms.openlocfilehash: 68098895b2ad7f5c08d30f222777e52d4ee3f063
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995797"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="03dae-102">ICorDebugFrameEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="03dae-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="03dae-103">Získá zadaný počet instancí ICorDebugFrame od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="03dae-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03dae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03dae-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03dae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03dae-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="03dae-106">[in] Počet `ICorDebugFrame` instancí, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="03dae-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="03dae-107">[out] Pole ukazatelů, každý z nich odkazuje na `ICorDebugFrame` objektu.</span><span class="sxs-lookup"><span data-stu-id="03dae-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="03dae-108">[out] Ukazatel na počet `ICorDebugFrame` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="03dae-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="03dae-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="03dae-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03dae-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03dae-110">Requirements</span></span>  
 <span data-ttu-id="03dae-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03dae-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03dae-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03dae-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03dae-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03dae-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03dae-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03dae-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
