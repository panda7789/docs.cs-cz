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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155191"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="790d9-102">ICorDebugAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="790d9-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="790d9-103">Poskytuje `Next` metodu, která vrací zadaný počet `ICorDebugAppDomainEnum` hodnot počínaje na dalším místě ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="790d9-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="790d9-104">Toto rozhraní je podtřídou třídy "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="790d9-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="790d9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="790d9-105">Methods</span></span>  
  
|<span data-ttu-id="790d9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="790d9-106">Method</span></span>|<span data-ttu-id="790d9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="790d9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="790d9-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="790d9-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="790d9-109">Zadaný počet domén aplikace získá z kolekce, spouští se na aktuální pozici kurzoru.</span><span class="sxs-lookup"><span data-stu-id="790d9-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="790d9-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="790d9-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="790d9-111">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="790d9-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="790d9-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="790d9-112">Requirements</span></span>  
 <span data-ttu-id="790d9-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="790d9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="790d9-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="790d9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="790d9-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="790d9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="790d9-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="790d9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="790d9-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="790d9-117">See also</span></span>

- [<span data-ttu-id="790d9-118">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="790d9-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="790d9-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="790d9-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
