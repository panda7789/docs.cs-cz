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
ms.openlocfilehash: d00a5f71ac7e47d78deebca0e46350e465964c72
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210095"
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="f317f-102">ICorDebugProcessEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="f317f-102">ICorDebugProcessEnum::Next Method</span></span>
<span data-ttu-id="f317f-103">Získá zadaný počet instancí ICorDebugProcess z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="f317f-103">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f317f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f317f-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f317f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f317f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f317f-106">pro Počet instancí, `ICorDebugProcess` které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="f317f-106">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processes`  
 <span data-ttu-id="f317f-107">mimo Pole ukazatelů, z nichž každý odkazuje na `ICorDebugProcess` objekt, který představuje proces.</span><span class="sxs-lookup"><span data-stu-id="f317f-107">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f317f-108">mimo Ukazatel na počet `ICorDebugProcess` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="f317f-108">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="f317f-109">Tato hodnota může být null `celt` , pokud je jedna.</span><span class="sxs-lookup"><span data-stu-id="f317f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f317f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f317f-110">Requirements</span></span>  
 <span data-ttu-id="f317f-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f317f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f317f-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f317f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f317f-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f317f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f317f-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f317f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
