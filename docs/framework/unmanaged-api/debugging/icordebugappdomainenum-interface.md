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
ms.openlocfilehash: c48c222a34e2e78f29c33e49da331d97d409bae1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949749"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="2a9e4-102">ICorDebugAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a9e4-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="2a9e4-103">Poskytuje metodu, která vrací zadaný `ICorDebugAppDomainEnum` počet hodnot od dalšího umístění ve výčtu. `Next`</span><span class="sxs-lookup"><span data-stu-id="2a9e4-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="2a9e4-104">Toto rozhraní je podtřídou třídy "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="2a9e4-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a9e4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2a9e4-105">Methods</span></span>  
  
|<span data-ttu-id="2a9e4-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="2a9e4-106">Method</span></span>|<span data-ttu-id="2a9e4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2a9e4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a9e4-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="2a9e4-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="2a9e4-109">Načte zadaný počet aplikačních domén z kolekce počínaje aktuální pozicí kurzoru.</span><span class="sxs-lookup"><span data-stu-id="2a9e4-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a9e4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2a9e4-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a9e4-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="2a9e4-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a9e4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2a9e4-112">Requirements</span></span>  
 <span data-ttu-id="2a9e4-113">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a9e4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a9e4-114">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2a9e4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a9e4-115">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a9e4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a9e4-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a9e4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a9e4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a9e4-117">See also</span></span>

- [<span data-ttu-id="2a9e4-118">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a9e4-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="2a9e4-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2a9e4-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
