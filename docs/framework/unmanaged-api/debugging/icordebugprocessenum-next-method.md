---
title: "ICorDebugProcessEnum::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcessEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2628a6d2a93c66531acfbc20acff560f623854fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="a59c5-102">ICorDebugProcessEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="a59c5-102">ICorDebugProcessEnum::Next Method</span></span>
<span data-ttu-id="a59c5-103">Získá zadaný počet instancí ICorDebugProcess z výčtu, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="a59c5-103">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a59c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a59c5-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a59c5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a59c5-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a59c5-106">[v] Počet `ICorDebugProcess` instancí, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="a59c5-106">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processess`  
 <span data-ttu-id="a59c5-107">[out] Ukazatele, každý z nich odkazuje na pole `ICorDebugProcess` objekt, který představuje proces.</span><span class="sxs-lookup"><span data-stu-id="a59c5-107">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a59c5-108">[out] Ukazatel na počet `ICorDebugProcess` instancí vrácených ve skutečnosti.</span><span class="sxs-lookup"><span data-stu-id="a59c5-108">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="a59c5-109">Tato hodnota může být null. Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="a59c5-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a59c5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a59c5-110">Requirements</span></span>  
 <span data-ttu-id="a59c5-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a59c5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a59c5-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a59c5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a59c5-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a59c5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a59c5-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a59c5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
