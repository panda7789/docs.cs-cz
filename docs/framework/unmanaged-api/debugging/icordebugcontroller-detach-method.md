---
title: ICorDebugController::Detach – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f2dae147f8667a73036dbcf873e2082996b2755
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666982"
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="ba572-102">ICorDebugController::Detach – metoda</span><span class="sxs-lookup"><span data-stu-id="ba572-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="ba572-103">Odpojí ladicí program z domény, procesu nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="ba572-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba572-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba572-104">Syntax</span></span>  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ba572-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba572-105">Remarks</span></span>  
 <span data-ttu-id="ba572-106">Domény aplikace nebo proces pokračuje v provádění kódu za normálních okolností, ale "ICorDebugProcess" nebo "ICorDebugAppDomain" objekt již není platný a bude probíhat žádná další zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="ba572-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="ba572-107">V rozhraní .NET Framework verze 2.0 Pokud je povoleno ladění nespravovaného kódu, tato metoda selže z důvodu omezení operačního systému.</span><span class="sxs-lookup"><span data-stu-id="ba572-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba572-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba572-108">Requirements</span></span>  
 <span data-ttu-id="ba572-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba572-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba572-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba572-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba572-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba572-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba572-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba572-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba572-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba572-113">See also</span></span>

