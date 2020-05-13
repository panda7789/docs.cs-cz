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
ms.openlocfilehash: 16aafa439fc81c3606f98ca2ba860316ec46e0db
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379741"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="42beb-102">ICorDebugThread::GetHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="42beb-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="42beb-103">Získá aktuální popisovač pro aktivní část tohoto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="42beb-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42beb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42beb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42beb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42beb-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="42beb-106">mimo Ukazatel na HTHREAD, který je popisovačem aktivní části tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="42beb-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42beb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42beb-107">Remarks</span></span>  
 <span data-ttu-id="42beb-108">Popisovač se může změnit, protože se spustí proces a může se lišit pro různé části vlákna.</span><span class="sxs-lookup"><span data-stu-id="42beb-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="42beb-109">Tento popisovač je vlastněn rozhraním API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="42beb-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="42beb-110">Ladicí program by ho měl před použitím duplikovat.</span><span class="sxs-lookup"><span data-stu-id="42beb-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42beb-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42beb-111">Requirements</span></span>  
 <span data-ttu-id="42beb-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42beb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42beb-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="42beb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42beb-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="42beb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42beb-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42beb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
