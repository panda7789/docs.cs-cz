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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26df40297d080d1ccc9464f7b09e7731f135e270
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989232"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="89c81-102">ICorDebugChainEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="89c81-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="89c81-103">Získá zadaný počet instancí icordebugchain – z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="89c81-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89c81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89c81-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89c81-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89c81-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="89c81-106">[in] Počet `ICorDebugChain` instancí, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="89c81-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="89c81-107">[out] Pole ukazatelů, každý z nich odkazuje na `ICorDebugChain` objekt, který reprezentuje řetězce.</span><span class="sxs-lookup"><span data-stu-id="89c81-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="89c81-108">[out] Ukazatel na počet `ICorDebugChain` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="89c81-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="89c81-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="89c81-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89c81-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89c81-110">Requirements</span></span>  
 <span data-ttu-id="89c81-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89c81-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89c81-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89c81-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89c81-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89c81-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89c81-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89c81-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
