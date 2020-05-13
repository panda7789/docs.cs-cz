---
title: ICorDebugThread4 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
ms.openlocfilehash: a0d6f3e109f92ad44eeeb1b1dec05e53015992a6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378363"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="d01ad-102">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d01ad-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="d01ad-103">Poskytuje informace o blokování vlákna.</span><span class="sxs-lookup"><span data-stu-id="d01ad-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d01ad-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d01ad-104">Methods</span></span>  
  
|<span data-ttu-id="d01ad-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d01ad-105">Method</span></span>|<span data-ttu-id="d01ad-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d01ad-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d01ad-107">GetBlockingObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="d01ad-107">GetBlockingObjects Method</span></span>](icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="d01ad-108">Poskytuje seřazený výčet struktur [CorDebugBlockingObject –](cordebugblockingobject-structure.md) , které poskytují informace o blokování vláken.</span><span class="sxs-lookup"><span data-stu-id="d01ad-108">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="d01ad-109">HadUnhandledException – metoda</span><span class="sxs-lookup"><span data-stu-id="d01ad-109">HadUnhandledException Method</span></span>](icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="d01ad-110">Označuje, zda má vlákno někdy neošetřenou výjimku.</span><span class="sxs-lookup"><span data-stu-id="d01ad-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="d01ad-111">GetCurrentCustomDebuggerNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="d01ad-111">GetCurrentCustomDebuggerNotification Method</span></span>](icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="d01ad-112">Získá aktuální objekt [ICorDebugManagedCallback3 –:: CustomNotification –](icordebugmanagedcallback3-customnotification-method.md) v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="d01ad-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d01ad-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d01ad-113">Remarks</span></span>  
 <span data-ttu-id="d01ad-114">Toto rozhraní je logické rozšíření rozhraní ICorDebugThread, ICorDebugThread2 a [ICorDebugThread3](icordebugthread3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d01ad-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d01ad-115">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="d01ad-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d01ad-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d01ad-116">Requirements</span></span>  
 <span data-ttu-id="d01ad-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d01ad-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d01ad-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d01ad-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d01ad-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d01ad-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d01ad-120">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d01ad-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d01ad-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="d01ad-121">See also</span></span>

- [<span data-ttu-id="d01ad-122">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d01ad-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d01ad-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="d01ad-123">Debugging</span></span>](index.md)
