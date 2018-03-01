---
title: ICorDebugAppDomainEnum Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e5d3d11e3897ff56ffcd475eb363405651578c1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainenum-interface1"></a><span data-ttu-id="190f4-102">ICorDebugAppDomainEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="190f4-102">ICorDebugAppDomainEnum Interface1</span></span>
<span data-ttu-id="190f4-103">Poskytuje `Next` metoda, která vrátí zadaný počet `ICorDebugAppDomainEnum` hodnot počínaje na další umístění ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="190f4-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="190f4-104">Toto rozhraní je podtřídou třídy "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="190f4-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="190f4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="190f4-105">Methods</span></span>  
  
|<span data-ttu-id="190f4-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="190f4-106">Method</span></span>|<span data-ttu-id="190f4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="190f4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="190f4-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="190f4-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="190f4-109">Získá zadaný počet domén aplikací z kolekce, počínaje na aktuální pozici kurzoru.</span><span class="sxs-lookup"><span data-stu-id="190f4-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="190f4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="190f4-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="190f4-111">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="190f4-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="190f4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="190f4-112">Requirements</span></span>  
 <span data-ttu-id="190f4-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="190f4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="190f4-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="190f4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="190f4-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="190f4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="190f4-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="190f4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="190f4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="190f4-117">See Also</span></span>  
 [<span data-ttu-id="190f4-118">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="190f4-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="190f4-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="190f4-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
