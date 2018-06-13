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
ms.openlocfilehash: ddf8db3b02ba4766d046fc549eec8add31f51069
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407917"
---
# <a name="icordebugappdomainenum-interface1"></a><span data-ttu-id="b30ec-102">ICorDebugAppDomainEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="b30ec-102">ICorDebugAppDomainEnum Interface1</span></span>
<span data-ttu-id="b30ec-103">Poskytuje `Next` metoda, která vrátí zadaný počet `ICorDebugAppDomainEnum` hodnot počínaje na další umístění ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="b30ec-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="b30ec-104">Toto rozhraní je podtřídou třídy "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="b30ec-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b30ec-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b30ec-105">Methods</span></span>  
  
|<span data-ttu-id="b30ec-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b30ec-106">Method</span></span>|<span data-ttu-id="b30ec-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b30ec-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b30ec-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="b30ec-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="b30ec-109">Získá zadaný počet domén aplikací z kolekce, počínaje na aktuální pozici kurzoru.</span><span class="sxs-lookup"><span data-stu-id="b30ec-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b30ec-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b30ec-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b30ec-111">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="b30ec-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b30ec-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b30ec-112">Requirements</span></span>  
 <span data-ttu-id="b30ec-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b30ec-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b30ec-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b30ec-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b30ec-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b30ec-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b30ec-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b30ec-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b30ec-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="b30ec-117">See Also</span></span>  
 [<span data-ttu-id="b30ec-118">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b30ec-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="b30ec-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b30ec-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
