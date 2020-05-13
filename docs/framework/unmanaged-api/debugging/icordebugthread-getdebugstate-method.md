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
ms.openlocfilehash: 13125f60f596cb8a80d9c42c51a979f632de494b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379748"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="41ada-102">ICorDebugThread::GetDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="41ada-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="41ada-103">Získá aktuální stav ladění tohoto objektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="41ada-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41ada-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41ada-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41ada-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41ada-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="41ada-106">mimo Ukazatel na bitovou kombinaci hodnot výčtu CorDebugThreadState –, které popisují aktuální stav ladění tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="41ada-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41ada-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41ada-107">Remarks</span></span>  
 <span data-ttu-id="41ada-108">Pokud je proces aktuálně zastaven, `pState` představuje stav ladění, který by existoval pro toto vlákno, pokud by proces pokračoval, nikoli skutečný aktuální stav tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="41ada-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41ada-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41ada-109">Requirements</span></span>  
 <span data-ttu-id="41ada-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41ada-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41ada-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="41ada-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41ada-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="41ada-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41ada-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41ada-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
