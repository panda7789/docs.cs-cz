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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 900fece1dd29f73f77b85ff08e4deff1396f8aaf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994016"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="95a08-102">ICorDebugThread::GetHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="95a08-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="95a08-103">Získá aktuální popisovač pro aktivní část této ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="95a08-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95a08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95a08-104">Syntax</span></span>  
  
```  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95a08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95a08-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="95a08-106">[out] Ukazatel na HTHREAD, který popisovač aktivní součást toto vlákno.</span><span class="sxs-lookup"><span data-stu-id="95a08-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95a08-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95a08-107">Remarks</span></span>  
 <span data-ttu-id="95a08-108">Popisovač můžou změnit, protože proces spustí a může lišit pro různé části vlákna.</span><span class="sxs-lookup"><span data-stu-id="95a08-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="95a08-109">Tento popisovač vlastní rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="95a08-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="95a08-110">Ladicí program by měl duplikovat před jeho použitím.</span><span class="sxs-lookup"><span data-stu-id="95a08-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95a08-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95a08-111">Requirements</span></span>  
 <span data-ttu-id="95a08-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95a08-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95a08-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95a08-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95a08-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95a08-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95a08-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95a08-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
