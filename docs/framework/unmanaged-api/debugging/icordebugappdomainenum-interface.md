---
title: ICorDebugAppDomainEnum Interface1
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3759be77cd6e6265eb8328669c88225067b99bfd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509711"
---
# <a name="icordebugappdomainenum-interface1"></a><span data-ttu-id="a00a0-102">ICorDebugAppDomainEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="a00a0-102">ICorDebugAppDomainEnum Interface1</span></span>
<span data-ttu-id="a00a0-103">Poskytuje `Next` metodu, která vrací zadaný počet `ICorDebugAppDomainEnum` hodnot počínaje na dalším místě ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="a00a0-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="a00a0-104">Toto rozhraní je podtřídou třídy "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="a00a0-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a00a0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a00a0-105">Methods</span></span>  
  
|<span data-ttu-id="a00a0-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a00a0-106">Method</span></span>|<span data-ttu-id="a00a0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a00a0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a00a0-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="a00a0-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="a00a0-109">Zadaný počet domén aplikace získá z kolekce, spouští se na aktuální pozici kurzoru.</span><span class="sxs-lookup"><span data-stu-id="a00a0-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a00a0-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a00a0-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a00a0-111">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="a00a0-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a00a0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a00a0-112">Requirements</span></span>  
 <span data-ttu-id="a00a0-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a00a0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a00a0-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a00a0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a00a0-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a00a0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a00a0-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a00a0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a00a0-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a00a0-117">See also</span></span>
- [<span data-ttu-id="a00a0-118">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a00a0-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="a00a0-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a00a0-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
