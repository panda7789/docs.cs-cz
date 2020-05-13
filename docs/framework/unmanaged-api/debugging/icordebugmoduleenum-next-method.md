---
title: ICorDebugModuleEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
ms.openlocfilehash: d7ad4a6b25fe6d53ab0b21066345451ae7c22c16
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213319"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="7d35a-102">ICorDebugModuleEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="7d35a-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="7d35a-103">Získá počet instancí "ICorDebugModule" určených `celt` od výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="7d35a-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d35a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d35a-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d35a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d35a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7d35a-106">pro Počet instancí, `ICorDebugModule` které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="7d35a-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="7d35a-107">mimo Pole ukazatelů, z nichž každý odkazuje na `ICorDebugModule` objekt.</span><span class="sxs-lookup"><span data-stu-id="7d35a-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7d35a-108">mimo Ukazatel na počet `ICorDebugModule` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="7d35a-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="7d35a-109">Tato hodnota může být null `celt` , pokud je jedna.</span><span class="sxs-lookup"><span data-stu-id="7d35a-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d35a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d35a-110">Requirements</span></span>  
 <span data-ttu-id="7d35a-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d35a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d35a-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7d35a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d35a-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7d35a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d35a-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d35a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d35a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d35a-115">See also</span></span>
