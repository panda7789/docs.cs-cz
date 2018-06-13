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
ms.openlocfilehash: 95d9696e29bc1b460c94d7f4d8afd3de82653333
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419627"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="44b60-102">ICorDebugThread::GetDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="44b60-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="44b60-103">Získá aktuální stav tohoto objektu ICorDebugThread ladění.</span><span class="sxs-lookup"><span data-stu-id="44b60-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44b60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44b60-104">Syntax</span></span>  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44b60-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44b60-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="44b60-106">[out] Ukazatel na bitovou kombinaci CorDebugThreadState – výčet hodnot, které popisují aktuální stav ladění tohoto podprocesu.</span><span class="sxs-lookup"><span data-stu-id="44b60-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44b60-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44b60-107">Remarks</span></span>  
 <span data-ttu-id="44b60-108">Pokud tento proces je nyní zastavena, `pState` představuje stav ladění, které by existovat pro tento přístup z více vláken, pokud proces dál, nikoli skutečné aktuální stav tohoto podprocesu.</span><span class="sxs-lookup"><span data-stu-id="44b60-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44b60-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44b60-109">Requirements</span></span>  
 <span data-ttu-id="44b60-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44b60-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44b60-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44b60-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44b60-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44b60-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44b60-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44b60-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
