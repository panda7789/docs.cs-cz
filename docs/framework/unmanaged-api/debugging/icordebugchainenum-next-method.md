---
title: ICorDebugChainEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type:
- apiref
ms.openlocfilehash: 2d075820df534e08bdf4c2b75d36f6a60f979662
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894098"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="dba8f-102">ICorDebugChainEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="dba8f-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="dba8f-103">Získá zadaný počet instancí ICorDebugChain z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="dba8f-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba8f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dba8f-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dba8f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dba8f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="dba8f-106">pro Počet `ICorDebugChain` instancí, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="dba8f-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="dba8f-107">mimo Pole ukazatelů, z nichž každý odkazuje na `ICorDebugChain` objekt, který představuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="dba8f-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="dba8f-108">mimo Ukazatel na počet skutečně vrácených `ICorDebugChain` instancí.</span><span class="sxs-lookup"><span data-stu-id="dba8f-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="dba8f-109">Tato hodnota může být null, `celt` Pokud je jedna.</span><span class="sxs-lookup"><span data-stu-id="dba8f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dba8f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dba8f-110">Requirements</span></span>  
 <span data-ttu-id="dba8f-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dba8f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dba8f-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dba8f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dba8f-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dba8f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dba8f-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dba8f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
