---
title: "ICorDebugThread::GetDebugState – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetDebugState
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4e66cc976be59c519e48d7ef9285963e5109d848
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="76eea-102">ICorDebugThread::GetDebugState – metoda</span><span class="sxs-lookup"><span data-stu-id="76eea-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="76eea-103">Získá aktuální stav tohoto objektu ICorDebugThread ladění.</span><span class="sxs-lookup"><span data-stu-id="76eea-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76eea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76eea-104">Syntax</span></span>  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76eea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76eea-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="76eea-106">[out] Ukazatel na bitovou kombinaci CorDebugThreadState – výčet hodnot, které popisují aktuální stav ladění tohoto podprocesu.</span><span class="sxs-lookup"><span data-stu-id="76eea-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76eea-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76eea-107">Remarks</span></span>  
 <span data-ttu-id="76eea-108">Pokud tento proces je nyní zastavena, `pState` představuje stav ladění, které by existovat pro tento přístup z více vláken, pokud proces dál, nikoli skutečné aktuální stav tohoto podprocesu.</span><span class="sxs-lookup"><span data-stu-id="76eea-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76eea-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="76eea-109">Requirements</span></span>  
 <span data-ttu-id="76eea-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76eea-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76eea-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76eea-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76eea-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76eea-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76eea-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76eea-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
