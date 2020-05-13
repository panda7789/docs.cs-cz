---
title: ICorDebugThread::CreateStepper – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
ms.openlocfilehash: a74d32478bc88ee634fa5ff9b61ac2059bc8e302
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379721"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="17765-102">ICorDebugThread::CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="17765-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="17765-103">Vytvoří objekt ICorDebugStepper, který umožňuje krokování skrze aktivní rámec tohoto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="17765-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17765-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17765-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17765-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17765-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="17765-106">mimo Ukazatel na adresu `ICorDebugStepper` objektu, který umožňuje krokování skrze aktivní rámec tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="17765-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17765-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17765-107">Remarks</span></span>  
 <span data-ttu-id="17765-108">Aktivní rámec může být nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="17765-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="17765-109">`ICorDebugStepper`K provedení samotného krokování je nutné použít rozhraní.</span><span class="sxs-lookup"><span data-stu-id="17765-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17765-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17765-110">Requirements</span></span>  
 <span data-ttu-id="17765-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17765-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17765-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="17765-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17765-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="17765-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17765-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17765-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
