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
ms.openlocfilehash: 7eef04dfb305978c81f465ecb37eda75a52f25e4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502946"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="bd4f4-102">ICorDebugController::IsRunning – metoda</span><span class="sxs-lookup"><span data-stu-id="bd4f4-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="bd4f4-103">Získá hodnotu, která označuje, zda vlákna v procesu jsou aktuálně spuštěna bez omezení.</span><span class="sxs-lookup"><span data-stu-id="bd4f4-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd4f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd4f4-104">Syntax</span></span>  
  
```  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd4f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd4f4-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="bd4f4-106">[out] Ukazatel na hodnotu, která je `true` Pokud vlákna v procesu systém volně; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="bd4f4-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd4f4-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd4f4-107">Requirements</span></span>  
 <span data-ttu-id="bd4f4-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd4f4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd4f4-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd4f4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd4f4-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd4f4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd4f4-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd4f4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd4f4-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd4f4-112">See also</span></span>

