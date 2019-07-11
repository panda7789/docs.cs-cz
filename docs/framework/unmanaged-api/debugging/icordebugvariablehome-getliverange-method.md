---
title: IcorDebugVariableHome::GetLiveRange – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLiveRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLiveRange
helpviewer_keywords:
- ICorDebugVariableHome::GetLiveRange method [.NET Framework debugging]
- GetLiveRange method, ICorDebugVariableFrame interface [.NET Framework debugging]
ms.assetid: 87277e1a-1595-4729-9e25-d1c3ac18ce5f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b293a3e166bb2614b5d0b064485178f5a569db48
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774139"
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="ac237-102">IcorDebugVariableHome::GetLiveRange – metoda</span><span class="sxs-lookup"><span data-stu-id="ac237-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="ac237-103">Získá nativní rozsah nad tím, které tato proměnná je v provozu.</span><span class="sxs-lookup"><span data-stu-id="ac237-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac237-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac237-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac237-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac237-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="ac237-106">[out] Logický posun jakou proměnná je první za provozu.</span><span class="sxs-lookup"><span data-stu-id="ac237-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="ac237-107">[out] Logický posun hned od chvíle, kdy je proměnná poslední za provozu.</span><span class="sxs-lookup"><span data-stu-id="ac237-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac237-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac237-108">Requirements</span></span>  
 <span data-ttu-id="ac237-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac237-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac237-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac237-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac237-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac237-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac237-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac237-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac237-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac237-113">See also</span></span>

- [<span data-ttu-id="ac237-114">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac237-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
