---
title: "ICorDebugController::IsRunning – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.IsRunning
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57621c0097c63ee9caca0a3fc4d5e95666b4e5b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="c5a0c-102">ICorDebugController::IsRunning – metoda</span><span class="sxs-lookup"><span data-stu-id="c5a0c-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="c5a0c-103">Získá hodnotu, která určuje, zda vláken v procesu jsou aktuálně spuštěny volně.</span><span class="sxs-lookup"><span data-stu-id="c5a0c-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5a0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5a0c-104">Syntax</span></span>  
  
```  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5a0c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5a0c-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="c5a0c-106">[out] Ukazatel na hodnotu, která je `true` Pokud vláken v procesu běží volně; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="c5a0c-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5a0c-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5a0c-107">Requirements</span></span>  
 <span data-ttu-id="c5a0c-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5a0c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5a0c-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5a0c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5a0c-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5a0c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5a0c-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5a0c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5a0c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5a0c-112">See Also</span></span>  
 
