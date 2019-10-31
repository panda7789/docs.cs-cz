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
ms.openlocfilehash: f3511ff5ee9b9221037c64a5e17d61f6bf52e5f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133417"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="973a7-102">ICorDebugThread::GetUserState – metoda</span><span class="sxs-lookup"><span data-stu-id="973a7-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="973a7-103">Načte aktuální stav uživatele tohoto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="973a7-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="973a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="973a7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="973a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="973a7-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="973a7-106">mimo Ukazatel na bitovou kombinaci hodnot výčtu CorDebugUserState –, které popisují aktuální stav uživatele tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="973a7-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="973a7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="973a7-107">Remarks</span></span>  
 <span data-ttu-id="973a7-108">Stav uživatele vlákna je stav vlákna, když je testován program, který je právě laděn.</span><span class="sxs-lookup"><span data-stu-id="973a7-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="973a7-109">Vlákno může mít několik sad bitů stavu.</span><span class="sxs-lookup"><span data-stu-id="973a7-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="973a7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="973a7-110">Requirements</span></span>  
 <span data-ttu-id="973a7-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="973a7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="973a7-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="973a7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="973a7-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="973a7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="973a7-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="973a7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
