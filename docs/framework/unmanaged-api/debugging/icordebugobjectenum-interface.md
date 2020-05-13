---
title: ICorDebugObjectEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
ms.openlocfilehash: 0594caf53a889d51ea78e2ee9d6fff4d30f7cff2
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205282"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="050fa-102">ICorDebugObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="050fa-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="050fa-103">Implementuje metody ICorDebugEnum a vytváří výčet polí objektů podle jejich relativních virtuálních adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="050fa-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="050fa-104">Metody</span><span class="sxs-lookup"><span data-stu-id="050fa-104">Methods</span></span>  
  
|<span data-ttu-id="050fa-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="050fa-105">Method</span></span>|<span data-ttu-id="050fa-106">Popis</span><span class="sxs-lookup"><span data-stu-id="050fa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="050fa-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="050fa-107">Next Method</span></span>](icordebugobjectenum-next-method.md)|<span data-ttu-id="050fa-108">Získá RVA zadaného počtu objektů z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="050fa-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="050fa-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="050fa-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="050fa-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="050fa-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="050fa-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="050fa-111">Requirements</span></span>  
 <span data-ttu-id="050fa-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="050fa-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="050fa-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="050fa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="050fa-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="050fa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="050fa-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="050fa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="050fa-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="050fa-116">See also</span></span>

- [<span data-ttu-id="050fa-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="050fa-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
