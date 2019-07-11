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
ms.openlocfilehash: f687e48413cb227ad715720e24bd645065309553
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748840"
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="b7284-102">ICorDebugController::Detach – metoda</span><span class="sxs-lookup"><span data-stu-id="b7284-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="b7284-103">Odpojí ladicí program z domény, procesu nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="b7284-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7284-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7284-104">Syntax</span></span>  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b7284-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7284-105">Remarks</span></span>  
 <span data-ttu-id="b7284-106">Domény aplikace nebo proces pokračuje v provádění kódu za normálních okolností, ale "ICorDebugProcess" nebo "ICorDebugAppDomain" objekt již není platný a bude probíhat žádná další zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="b7284-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="b7284-107">V rozhraní .NET Framework verze 2.0 Pokud je povoleno ladění nespravovaného kódu, tato metoda selže z důvodu omezení operačního systému.</span><span class="sxs-lookup"><span data-stu-id="b7284-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7284-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7284-108">Requirements</span></span>  
 <span data-ttu-id="b7284-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7284-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7284-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7284-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7284-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7284-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7284-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7284-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7284-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7284-113">See also</span></span>
