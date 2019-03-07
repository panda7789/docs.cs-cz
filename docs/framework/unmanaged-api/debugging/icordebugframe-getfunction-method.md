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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a48396f8ef668cfe7755b2718180317b465793b6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475279"
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="25768-102">ICorDebugFrame::GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="25768-102">ICorDebugFrame::GetFunction Method</span></span>
<span data-ttu-id="25768-103">Získá funkce, která obsahuje kód spojený s rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="25768-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25768-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25768-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25768-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25768-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="25768-106">[out] Ukazatel na adresu ICorDebugFunction objekt, který představuje funkci obsahující kód spojený s rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="25768-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25768-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25768-107">Remarks</span></span>  
 <span data-ttu-id="25768-108">`GetFunction` Metoda může selhat, pokud rámec není přidružen k žádné konkrétní funkce.</span><span class="sxs-lookup"><span data-stu-id="25768-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25768-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25768-109">Requirements</span></span>  
 <span data-ttu-id="25768-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25768-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25768-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25768-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25768-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25768-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25768-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25768-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
