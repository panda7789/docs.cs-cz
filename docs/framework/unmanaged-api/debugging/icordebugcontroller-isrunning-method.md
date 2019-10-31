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
ms.openlocfilehash: f24c07a654dc2345cb65226463573576a6fb3658
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125343"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="d2c14-102">ICorDebugController::IsRunning – metoda</span><span class="sxs-lookup"><span data-stu-id="d2c14-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="d2c14-103">Získá hodnotu, která označuje, zda jsou vlákna v procesu aktuálně spuštěna volně.</span><span class="sxs-lookup"><span data-stu-id="d2c14-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2c14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2c14-104">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2c14-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2c14-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="d2c14-106">mimo Ukazatel na hodnotu, která je `true`, pokud jsou vlákna v procesu volně spuštěná; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="d2c14-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2c14-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2c14-107">Requirements</span></span>  
 <span data-ttu-id="d2c14-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2c14-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2c14-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d2c14-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2c14-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d2c14-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2c14-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2c14-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c14-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2c14-112">See also</span></span>
