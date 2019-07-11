---
title: ICorDebugFunctionBreakpoint::GetFunction – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetFunction
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetFunction method [.NET Framework debugging]
- GetFunction method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 2a62dae5-dd8a-4696-b817-0e1e586c24a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4f9ea741e545cc424dff450325c3f8d271c8554
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755574"
---
# <a name="icordebugfunctionbreakpointgetfunction-method"></a><span data-ttu-id="1eadf-102">ICorDebugFunctionBreakpoint::GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="1eadf-102">ICorDebugFunctionBreakpoint::GetFunction Method</span></span>
<span data-ttu-id="1eadf-103">Získá ukazatel rozhraní ICorDebugFunction, který odkazuje na funkci, ve kterém je nastavena zarážka.</span><span class="sxs-lookup"><span data-stu-id="1eadf-103">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1eadf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1eadf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1eadf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1eadf-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="1eadf-106">[out] Ukazatel na adresu funkce, ve kterém je nastavena zarážka.</span><span class="sxs-lookup"><span data-stu-id="1eadf-106">[out] A pointer to the address of the function in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1eadf-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1eadf-107">Requirements</span></span>  
 <span data-ttu-id="1eadf-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1eadf-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1eadf-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1eadf-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1eadf-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1eadf-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1eadf-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1eadf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
