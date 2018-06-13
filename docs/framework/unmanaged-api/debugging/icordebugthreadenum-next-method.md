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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 050bfb08dfd95e29b6534f69dbd35400d59e6099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419601"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="21977-102">ICorDebugThreadEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="21977-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="21977-103">Získá počet instancí ICorDebugThread zadaný z výčtu, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="21977-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21977-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21977-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21977-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21977-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="21977-106">[v] Počet `ICorDebugThread` instancí, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="21977-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="21977-107">[out] Ukazatele, každý z nich odkazuje na pole `ICorDebugThread` objekt, který reprezentuje vlákna.</span><span class="sxs-lookup"><span data-stu-id="21977-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="21977-108">[out] Ukazatel na počet `ICorDebugThread` instancí vrácených ve skutečnosti.</span><span class="sxs-lookup"><span data-stu-id="21977-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="21977-109">Tato hodnota může být null. Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="21977-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21977-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21977-110">Requirements</span></span>  
 <span data-ttu-id="21977-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21977-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21977-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21977-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21977-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21977-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21977-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21977-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
