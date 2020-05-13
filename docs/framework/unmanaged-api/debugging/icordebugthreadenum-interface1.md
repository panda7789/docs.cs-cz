---
title: ICorDebugThreadEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum
helpviewer_keywords:
- ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: 796de687-7dd4-4b7b-a10b-8bf22dc7779f
topic_type:
- apiref
ms.openlocfilehash: 82a7689bb1848d89f5dee4482d8dc7685c9c5b5c
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378327"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="6b52c-102">ICorDebugThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b52c-102">ICorDebugThreadEnum Interface</span></span>
<span data-ttu-id="6b52c-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="6b52c-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6b52c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6b52c-104">Methods</span></span>  
  
|<span data-ttu-id="6b52c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6b52c-105">Method</span></span>|<span data-ttu-id="6b52c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6b52c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6b52c-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="6b52c-107">Next Method</span></span>](icordebugthreadenum-next-method.md)|<span data-ttu-id="6b52c-108">Získá zadaný počet `ICorDebugThread` instancí z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="6b52c-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b52c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b52c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b52c-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="6b52c-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b52c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b52c-111">Requirements</span></span>  
 <span data-ttu-id="6b52c-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b52c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b52c-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6b52c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b52c-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6b52c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b52c-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b52c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b52c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b52c-116">See also</span></span>

- [<span data-ttu-id="6b52c-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b52c-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
