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
ms.openlocfilehash: d1ff3427feb5dc8395bbb2fda78e3e93e1a1a8f0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378847"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="95e30-102">ICorDebugThread::GetUserState – metoda</span><span class="sxs-lookup"><span data-stu-id="95e30-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="95e30-103">Načte aktuální stav uživatele tohoto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="95e30-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95e30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95e30-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95e30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95e30-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="95e30-106">mimo Ukazatel na bitovou kombinaci hodnot výčtu CorDebugUserState –, které popisují aktuální stav uživatele tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="95e30-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95e30-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95e30-107">Remarks</span></span>  
 <span data-ttu-id="95e30-108">Stav uživatele vlákna je stav vlákna, když je testován program, který je právě laděn.</span><span class="sxs-lookup"><span data-stu-id="95e30-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="95e30-109">Vlákno může mít několik sad bitů stavu.</span><span class="sxs-lookup"><span data-stu-id="95e30-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95e30-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95e30-110">Requirements</span></span>  
 <span data-ttu-id="95e30-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95e30-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95e30-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="95e30-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95e30-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="95e30-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95e30-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95e30-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
