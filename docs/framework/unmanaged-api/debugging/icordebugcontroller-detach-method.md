---
title: "ICorDebugController::Detach – metoda"
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
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 59fe2c4bfbd91afd263a0ada1eb355aaa8914aa2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="b0755-102">ICorDebugController::Detach – metoda</span><span class="sxs-lookup"><span data-stu-id="b0755-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="b0755-103">Umožňuje odpojit ladicí program z domény procesů nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="b0755-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0755-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0755-104">Syntax</span></span>  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b0755-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0755-105">Remarks</span></span>  
 <span data-ttu-id="b0755-106">Domény procesů nebo aplikace pokračuje provádění za normálních okolností, ale objekt "ICorDebugProcess" nebo "ICorDebugAppDomain" již není platný a dojde k žádné další zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="b0755-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="b0755-107">V rozhraní .NET Framework verze 2.0 Pokud je povoleno ladění nespravované, tato metoda selže z důvodu omezení operačního systému.</span><span class="sxs-lookup"><span data-stu-id="b0755-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0755-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0755-108">Requirements</span></span>  
 <span data-ttu-id="b0755-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0755-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0755-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0755-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0755-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0755-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0755-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0755-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0755-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0755-113">See Also</span></span>  
 
