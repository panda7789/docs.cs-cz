---
title: ICorDebugAssemblyEnum::Next – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 155354b335caf83c466c8d9d6711f36c7efc9298
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894815"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="33416-102">ICorDebugAssemblyEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="33416-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="33416-103">Získá zadaný počet sestavení z kolekce počínaje aktuální pozicí kurzoru.</span><span class="sxs-lookup"><span data-stu-id="33416-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33416-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33416-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33416-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33416-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="33416-106">pro Počet sestavení, která mají být načtena.</span><span class="sxs-lookup"><span data-stu-id="33416-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="33416-107">mimo Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugAssembly, který představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="33416-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="33416-108">mimo Ukazatel na počet skutečně vrácených sestavení.</span><span class="sxs-lookup"><span data-stu-id="33416-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="33416-109">Tato hodnota může být null, `celt` Pokud je jedna.</span><span class="sxs-lookup"><span data-stu-id="33416-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33416-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33416-110">Requirements</span></span>  
 <span data-ttu-id="33416-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33416-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33416-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="33416-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33416-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="33416-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33416-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33416-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
