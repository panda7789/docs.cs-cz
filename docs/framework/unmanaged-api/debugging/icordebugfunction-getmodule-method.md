---
title: ICorDebugFunction::GetModule – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetModule
helpviewer_keywords:
- ICorDebugFunction::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 5031a5d3-2564-412a-9007-e36d4631308a
topic_type:
- apiref
ms.openlocfilehash: e49bf6a7db9edb9e5ae489cc0655eea54406643d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137883"
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="df50f-102">ICorDebugFunction::GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="df50f-102">ICorDebugFunction::GetModule Method</span></span>
<span data-ttu-id="df50f-103">Získá modul, ve kterém je tato funkce definovaná.</span><span class="sxs-lookup"><span data-stu-id="df50f-103">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df50f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df50f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df50f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df50f-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="df50f-106">mimo Ukazatel na adresu objektu ICorDebugModule, který představuje modul, ve kterém je tato funkce definována.</span><span class="sxs-lookup"><span data-stu-id="df50f-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df50f-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df50f-107">Requirements</span></span>  
 <span data-ttu-id="df50f-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df50f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df50f-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="df50f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df50f-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="df50f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df50f-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df50f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
