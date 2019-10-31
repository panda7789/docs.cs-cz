---
title: ICorDebugThread::GetHandle – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
ms.openlocfilehash: 33219d9a67379244e23da49c13617a4c4a2fa66d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133455"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="9e22c-102">ICorDebugThread::GetHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="9e22c-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="9e22c-103">Získá aktuální popisovač pro aktivní část tohoto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="9e22c-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e22c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e22c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e22c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e22c-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="9e22c-106">mimo Ukazatel na HTHREAD, který je popisovačem aktivní části tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="9e22c-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e22c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e22c-107">Remarks</span></span>  
 <span data-ttu-id="9e22c-108">Popisovač se může změnit, protože se spustí proces a může se lišit pro různé části vlákna.</span><span class="sxs-lookup"><span data-stu-id="9e22c-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="9e22c-109">Tento popisovač je vlastněn rozhraním API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="9e22c-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="9e22c-110">Ladicí program by ho měl před použitím duplikovat.</span><span class="sxs-lookup"><span data-stu-id="9e22c-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e22c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e22c-111">Requirements</span></span>  
 <span data-ttu-id="9e22c-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e22c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e22c-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9e22c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e22c-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9e22c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e22c-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e22c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
