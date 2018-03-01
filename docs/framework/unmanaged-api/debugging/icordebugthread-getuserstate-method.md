---
title: "ICorDebugThread::GetUserState – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThread.GetUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9af89f355916f01fad118a4b63b57b23b2671f54
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="74400-102">ICorDebugThread::GetUserState – metoda</span><span class="sxs-lookup"><span data-stu-id="74400-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="74400-103">Získá aktuální stav této ICorDebugThread uživatele.</span><span class="sxs-lookup"><span data-stu-id="74400-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74400-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74400-104">Syntax</span></span>  
  
```  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74400-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="74400-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="74400-106">[out] Ukazatel na bitové kombinace hodnot výčtu CorDebugUserState, které popisují aktuální stav uživatele z tohoto podprocesu.</span><span class="sxs-lookup"><span data-stu-id="74400-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74400-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74400-107">Remarks</span></span>  
 <span data-ttu-id="74400-108">Stav uživatele vlákno je stav vlákno při kontrole programem, který je právě laděn.</span><span class="sxs-lookup"><span data-stu-id="74400-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="74400-109">Vlákno může mít několik sadu bitů stavu.</span><span class="sxs-lookup"><span data-stu-id="74400-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74400-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74400-110">Requirements</span></span>  
 <span data-ttu-id="74400-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74400-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74400-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74400-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74400-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74400-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74400-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74400-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
