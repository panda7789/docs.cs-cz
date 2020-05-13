---
title: ICorDebugFrame::GetFunction – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type:
- apiref
ms.openlocfilehash: 7bf73266f0269cfcd5371c5155856800036cc066
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209835"
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="c7548-102">ICorDebugFrame::GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="c7548-102">ICorDebugFrame::GetFunction Method</span></span>
<span data-ttu-id="c7548-103">Získá funkci, která obsahuje kód spojený s tímto rámcem zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c7548-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7548-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7548-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7548-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7548-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="c7548-106">mimo Ukazatel na adresu objektu ICorDebugFunction, který představuje funkci obsahující kód spojený s tímto rámcem zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c7548-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7548-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7548-107">Remarks</span></span>  
 <span data-ttu-id="c7548-108">`GetFunction`Metoda může selhat, pokud rámec není přidružen k žádné konkrétní funkci.</span><span class="sxs-lookup"><span data-stu-id="c7548-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7548-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7548-109">Requirements</span></span>  
 <span data-ttu-id="c7548-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7548-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7548-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c7548-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7548-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c7548-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7548-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7548-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
