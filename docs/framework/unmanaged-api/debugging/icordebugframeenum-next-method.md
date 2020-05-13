---
title: ICorDebugFrameEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
ms.openlocfilehash: 4652e4b34d614ad3b7b852925fcc63309bdd1498
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209458"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="156f9-102">ICorDebugFrameEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="156f9-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="156f9-103">Získá zadaný počet instancí ICorDebugFrame od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="156f9-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="156f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="156f9-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="156f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="156f9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="156f9-106">pro Počet instancí, `ICorDebugFrame` které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="156f9-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="156f9-107">mimo Pole ukazatelů, z nichž každý odkazuje na `ICorDebugFrame` objekt.</span><span class="sxs-lookup"><span data-stu-id="156f9-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="156f9-108">mimo Ukazatel na počet `ICorDebugFrame` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="156f9-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="156f9-109">Tato hodnota může být null `celt` , pokud je jedna.</span><span class="sxs-lookup"><span data-stu-id="156f9-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="156f9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="156f9-110">Requirements</span></span>  
 <span data-ttu-id="156f9-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="156f9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="156f9-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="156f9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="156f9-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="156f9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="156f9-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="156f9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
