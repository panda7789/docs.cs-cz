---
title: ICorDebugThread::GetUserState – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4deaa3ab4b14fbd32d45841966cfac9e33b9f31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987068"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="148e3-102">ICorDebugThread::GetUserState – metoda</span><span class="sxs-lookup"><span data-stu-id="148e3-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="148e3-103">Získá aktuální stav uživatele v této ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="148e3-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="148e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="148e3-104">Syntax</span></span>  
  
```  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="148e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="148e3-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="148e3-106">[out] Ukazatel na bitové kombinace cordebuguserstate – výčet hodnot, které popisují aktuální stav uživatele z tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="148e3-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="148e3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="148e3-107">Remarks</span></span>  
 <span data-ttu-id="148e3-108">Stav uživatele vlákna je stav vlákna při kontrole programem, který je právě laděna.</span><span class="sxs-lookup"><span data-stu-id="148e3-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="148e3-109">Vlákno může mít více sadu bitů stavu.</span><span class="sxs-lookup"><span data-stu-id="148e3-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="148e3-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="148e3-110">Requirements</span></span>  
 <span data-ttu-id="148e3-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="148e3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="148e3-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="148e3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="148e3-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="148e3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="148e3-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="148e3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
