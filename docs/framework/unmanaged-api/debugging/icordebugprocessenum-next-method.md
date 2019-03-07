---
title: ICorDebugProcessEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c298107983f4835569cfee7503537537ad11a165
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493580"
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="a43b9-102">ICorDebugProcessEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="a43b9-102">ICorDebugProcessEnum::Next Method</span></span>
<span data-ttu-id="a43b9-103">Získá zadaný počet instancí ICorDebugProcess z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="a43b9-103">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a43b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a43b9-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a43b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a43b9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a43b9-106">[in] Počet `ICorDebugProcess` instancí, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="a43b9-106">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processess`  
 <span data-ttu-id="a43b9-107">[out] Pole ukazatelů, každý z nich odkazuje na `ICorDebugProcess` objekt, který reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="a43b9-107">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a43b9-108">[out] Ukazatel na počet `ICorDebugProcess` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="a43b9-108">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="a43b9-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="a43b9-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a43b9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a43b9-110">Requirements</span></span>  
 <span data-ttu-id="a43b9-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a43b9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a43b9-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a43b9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a43b9-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a43b9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a43b9-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a43b9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
