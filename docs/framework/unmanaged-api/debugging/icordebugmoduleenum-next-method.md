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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7624a22e5d65ae94797779a0b8cfa70f226450ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418981"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="09e1f-102">ICorDebugModuleEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="09e1f-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="09e1f-103">Získá počet instancí "ICorDebugModule" určeného `celt` z výčtu, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="09e1f-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09e1f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09e1f-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09e1f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09e1f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="09e1f-106">[v] Počet `ICorDebugModule` instancí, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="09e1f-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="09e1f-107">[out] Ukazatele, každý z nich odkazuje na pole `ICorDebugModule` objektu.</span><span class="sxs-lookup"><span data-stu-id="09e1f-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="09e1f-108">[out] Ukazatel na počet `ICorDebugModule` instancí vrácených ve skutečnosti.</span><span class="sxs-lookup"><span data-stu-id="09e1f-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="09e1f-109">Tato hodnota může být null. Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="09e1f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09e1f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="09e1f-110">Requirements</span></span>  
 <span data-ttu-id="09e1f-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09e1f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09e1f-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09e1f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09e1f-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09e1f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09e1f-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09e1f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e1f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="09e1f-115">See Also</span></span>  
 
