---
title: ICorDebugController::IsRunning – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.IsRunning
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5eae9e14bcd0ca430f03a873818246896438463
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227090"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="90e5a-102">ICorDebugController::IsRunning – metoda</span><span class="sxs-lookup"><span data-stu-id="90e5a-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="90e5a-103">Získá hodnotu, která označuje, zda vlákna v procesu jsou aktuálně spuštěna bez omezení.</span><span class="sxs-lookup"><span data-stu-id="90e5a-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90e5a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90e5a-104">Syntax</span></span>  
  
```  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90e5a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90e5a-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="90e5a-106">[out] Ukazatel na hodnotu, která je `true` Pokud vlákna v procesu systém volně; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="90e5a-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90e5a-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90e5a-107">Requirements</span></span>  
 <span data-ttu-id="90e5a-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90e5a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90e5a-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90e5a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90e5a-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90e5a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90e5a-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90e5a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e5a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90e5a-112">See also</span></span>
