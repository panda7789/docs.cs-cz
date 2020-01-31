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
ms.openlocfilehash: 9fb849c78636d5e29f58a70f59aa4cb3cd22df40
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784741"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="2bd39-102">ICorDebugAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bd39-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="2bd39-103">Poskytuje metodu `Next`, která vrací zadaný počet `ICorDebugAppDomainEnum` hodnot od dalšího umístění ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="2bd39-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="2bd39-104">Toto rozhraní je podtřídou třídy "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="2bd39-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2bd39-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2bd39-105">Methods</span></span>  
  
|<span data-ttu-id="2bd39-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="2bd39-106">Method</span></span>|<span data-ttu-id="2bd39-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2bd39-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2bd39-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="2bd39-108">Next Method</span></span>](icordebugappdomainenum-next-method.md)|<span data-ttu-id="2bd39-109">Načte zadaný počet aplikačních domén z kolekce počínaje aktuální pozicí kurzoru.</span><span class="sxs-lookup"><span data-stu-id="2bd39-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bd39-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2bd39-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2bd39-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="2bd39-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bd39-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2bd39-112">Requirements</span></span>  
 <span data-ttu-id="2bd39-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bd39-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bd39-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2bd39-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2bd39-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2bd39-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bd39-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bd39-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bd39-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2bd39-117">See also</span></span>

- [<span data-ttu-id="2bd39-118">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bd39-118">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="2bd39-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2bd39-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
