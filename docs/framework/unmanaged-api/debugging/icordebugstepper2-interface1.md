---
title: ICorDebugStepper2 – rozhraní 1
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2
helpviewer_keywords:
- ICorDebugStepper2 interface [.NET Framework debugging]
ms.assetid: 7a191c2a-95ea-4d47-83b0-44de2b632d63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b7e91430b970e8a14e0c126b1b7ae2cb123d4eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712873"
---
# <a name="icordebugstepper2-interface1"></a><span data-ttu-id="564b4-102">ICorDebugStepper2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="564b4-102">ICorDebugStepper2 Interface1</span></span>
<span data-ttu-id="564b4-103">Poskytuje podporu pro pouze můj kód (JMC) ladění.</span><span class="sxs-lookup"><span data-stu-id="564b4-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="564b4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="564b4-104">Methods</span></span>  
  
|<span data-ttu-id="564b4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="564b4-105">Method</span></span>|<span data-ttu-id="564b4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="564b4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="564b4-107">SetJMC – metoda</span><span class="sxs-lookup"><span data-stu-id="564b4-107">SetJMC Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-setjmc-method.md)|<span data-ttu-id="564b4-108">Nastaví hodnotu, která určuje, zda tento icordebugstepper – provede pouze kód, který je vytvořený vývojářem aplikace.</span><span class="sxs-lookup"><span data-stu-id="564b4-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="564b4-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="564b4-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="564b4-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="564b4-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="564b4-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="564b4-111">Requirements</span></span>  
 <span data-ttu-id="564b4-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="564b4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="564b4-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="564b4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="564b4-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="564b4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="564b4-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="564b4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="564b4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="564b4-116">See also</span></span>
- [<span data-ttu-id="564b4-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="564b4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
