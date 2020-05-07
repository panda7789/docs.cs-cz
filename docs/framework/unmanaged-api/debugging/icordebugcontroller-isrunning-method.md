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
ms.openlocfilehash: 89ea9f221ad55063e4186cc27cc8038334d800d4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892866"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="3fb80-102">ICorDebugController::IsRunning – metoda</span><span class="sxs-lookup"><span data-stu-id="3fb80-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="3fb80-103">Získá hodnotu, která označuje, zda jsou vlákna v procesu aktuálně spuštěna volně.</span><span class="sxs-lookup"><span data-stu-id="3fb80-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fb80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fb80-104">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fb80-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3fb80-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="3fb80-106">mimo Ukazatel na hodnotu, která je `true` v případě, že vlákna v procesu jsou spuštěna volně; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="3fb80-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fb80-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3fb80-107">Requirements</span></span>  
 <span data-ttu-id="3fb80-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fb80-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fb80-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3fb80-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fb80-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3fb80-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fb80-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fb80-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb80-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="3fb80-112">See also</span></span>
