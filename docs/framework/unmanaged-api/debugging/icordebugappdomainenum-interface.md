---
title: ICorDebugAppDomainEnum – rozhraní
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
ms.openlocfilehash: da1fc949109455cf50767191a99a8a727116f77c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989505"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="36de5-102">ICorDebugAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36de5-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="36de5-103">Poskytuje `Next` metodu, která vrací zadaný počet `ICorDebugAppDomainEnum` hodnot počínaje na dalším místě ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="36de5-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="36de5-104">Toto rozhraní je podtřídou třídy "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="36de5-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="36de5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="36de5-105">Methods</span></span>  
  
|<span data-ttu-id="36de5-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="36de5-106">Method</span></span>|<span data-ttu-id="36de5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="36de5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="36de5-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="36de5-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="36de5-109">Zadaný počet domén aplikace získá z kolekce, spouští se na aktuální pozici kurzoru.</span><span class="sxs-lookup"><span data-stu-id="36de5-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36de5-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36de5-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36de5-111">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="36de5-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36de5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36de5-112">Requirements</span></span>  
 <span data-ttu-id="36de5-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36de5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36de5-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36de5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36de5-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36de5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36de5-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36de5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36de5-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36de5-117">See also</span></span>

- [<span data-ttu-id="36de5-118">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36de5-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="36de5-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="36de5-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
