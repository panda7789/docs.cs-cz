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
ms.openlocfilehash: f054f8f2bd7c322e722a1e17290ba6fbad9e37b0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133510"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="08c32-102">ICorDebugThread::GetDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="08c32-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="08c32-103">Získá aktuální stav ladění tohoto objektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="08c32-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08c32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08c32-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08c32-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08c32-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="08c32-106">mimo Ukazatel na bitovou kombinaci hodnot výčtu CorDebugThreadState –, které popisují aktuální stav ladění tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="08c32-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08c32-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="08c32-107">Remarks</span></span>  
 <span data-ttu-id="08c32-108">Pokud je proces aktuálně zastaven, `pState` představuje stav ladění, který by existoval pro toto vlákno, pokud by proces pokračoval, nikoli skutečný aktuální stav tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="08c32-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08c32-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08c32-109">Requirements</span></span>  
 <span data-ttu-id="08c32-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08c32-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08c32-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="08c32-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08c32-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="08c32-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08c32-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08c32-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
