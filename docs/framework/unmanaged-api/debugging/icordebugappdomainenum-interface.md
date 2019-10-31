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
ms.openlocfilehash: 6cc3ec1c802c28b74248380aa7f686e675a92f1d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088845"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="65238-102">ICorDebugAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65238-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="65238-103">Poskytuje metodu `Next`, která vrací zadaný počet `ICorDebugAppDomainEnum` hodnot od dalšího umístění ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="65238-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="65238-104">Toto rozhraní je podtřídou třídy "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="65238-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="65238-105">Metody</span><span class="sxs-lookup"><span data-stu-id="65238-105">Methods</span></span>  
  
|<span data-ttu-id="65238-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="65238-106">Method</span></span>|<span data-ttu-id="65238-107">Popis</span><span class="sxs-lookup"><span data-stu-id="65238-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="65238-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="65238-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="65238-109">Načte zadaný počet aplikačních domén z kolekce počínaje aktuální pozicí kurzoru.</span><span class="sxs-lookup"><span data-stu-id="65238-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65238-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65238-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65238-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="65238-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65238-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65238-112">Requirements</span></span>  
 <span data-ttu-id="65238-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65238-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65238-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="65238-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65238-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="65238-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65238-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65238-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65238-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65238-117">See also</span></span>

- [<span data-ttu-id="65238-118">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65238-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="65238-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="65238-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
