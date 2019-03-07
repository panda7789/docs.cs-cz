---
title: ICorDebugThread::GetDebugState – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68df19120f2e0b45e73f9d5e137afc8a5e7ac513
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489888"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="8ded3-102">ICorDebugThread::GetDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="8ded3-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="8ded3-103">Získá aktuální stav ladění tohoto objektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="8ded3-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ded3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ded3-104">Syntax</span></span>  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ded3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ded3-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="8ded3-106">[out] Ukazatel na bitová kombinace hodnot cordebugthreadstate – výčet popisující aktuální stav ladění tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="8ded3-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ded3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ded3-107">Remarks</span></span>  
 <span data-ttu-id="8ded3-108">Pokud je aktuálně zastavený proces, `pState` představuje stav ladění, která by existovala pro toto vlákno, pokud proces pokračuje, nikoli skutečné aktuální stav tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="8ded3-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ded3-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ded3-109">Requirements</span></span>  
 <span data-ttu-id="8ded3-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ded3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ded3-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ded3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ded3-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ded3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ded3-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ded3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
