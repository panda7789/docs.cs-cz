---
title: "ICorDebugAssemblyEnum::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAssemblyEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum::Next method
helpviewer_keywords:
- ICorDebugAssemblyEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: b3e7d0c2-3baa-4ef8-8e3f-b865cf252940
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69f43a24caff7e67f307bbf4521094e8ebfd98cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="66d31-102">ICorDebugAssemblyEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="66d31-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="66d31-103">Získá zadaný počet sestavení z kolekce, počínaje na aktuální pozici kurzoru.</span><span class="sxs-lookup"><span data-stu-id="66d31-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66d31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66d31-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66d31-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66d31-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="66d31-106">[v] Číslo sestavení, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="66d31-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="66d31-107">[out] Pole ukazatele, každý z nich odkazuje na objekt ICorDebugAssembly, který představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="66d31-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="66d31-108">[out] Ukazatel na číslo sestavení, ve skutečnosti vrátila.</span><span class="sxs-lookup"><span data-stu-id="66d31-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="66d31-109">Tato hodnota může být null. Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="66d31-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66d31-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66d31-110">Requirements</span></span>  
 <span data-ttu-id="66d31-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66d31-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66d31-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66d31-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66d31-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66d31-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66d31-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66d31-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
