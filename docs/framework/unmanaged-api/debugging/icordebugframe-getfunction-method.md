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
ms.openlocfilehash: 39175e338e4fd98dd4af1325138da732ed81c764
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137924"
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="7c275-102">ICorDebugFrame::GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="7c275-102">ICorDebugFrame::GetFunction Method</span></span>
<span data-ttu-id="7c275-103">Získá funkci, která obsahuje kód spojený s tímto rámcem zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7c275-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c275-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c275-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c275-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c275-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="7c275-106">mimo Ukazatel na adresu objektu ICorDebugFunction, který představuje funkci obsahující kód spojený s tímto rámcem zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7c275-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c275-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c275-107">Remarks</span></span>  
 <span data-ttu-id="7c275-108">Metoda `GetFunction` může selhat, pokud rámec není přidružen k žádné konkrétní funkci.</span><span class="sxs-lookup"><span data-stu-id="7c275-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c275-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c275-109">Requirements</span></span>  
 <span data-ttu-id="7c275-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c275-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c275-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7c275-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c275-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7c275-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c275-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c275-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
