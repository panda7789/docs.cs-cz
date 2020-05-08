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
ms.openlocfilehash: 480fec4897dac73594515ba8bc0f0e96ceb79ace
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892905"
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="88a39-102">ICorDebugController::Detach – metoda</span><span class="sxs-lookup"><span data-stu-id="88a39-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="88a39-103">Odpojí ladicí program od domény procesu nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="88a39-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88a39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88a39-104">Syntax</span></span>  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="88a39-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88a39-105">Remarks</span></span>  
 <span data-ttu-id="88a39-106">Proces nebo aplikační doména pokračuje v normálním provádění, ale objekt "ICorDebugProcess" nebo "ICorDebugAppDomain" již není platný a žádné další zpětné volání nebudou provedeny.</span><span class="sxs-lookup"><span data-stu-id="88a39-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="88a39-107">Pokud je v .NET Framework verze 2,0, pokud je povoleno ladění nespravovaného kódu, nebude tato metoda v důsledku omezení operačního systému úspěšná.</span><span class="sxs-lookup"><span data-stu-id="88a39-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88a39-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88a39-108">Requirements</span></span>  
 <span data-ttu-id="88a39-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88a39-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88a39-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="88a39-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88a39-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="88a39-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88a39-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88a39-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88a39-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="88a39-113">See also</span></span>
