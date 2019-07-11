---
title: ICorDebugAppDomain::EnumerateSteppers – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateSteppers
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateSteppers
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateSteppers method [.NET Framework debugging]
- EnumerateSteppers method [.NET Framework debugging]
ms.assetid: 3f3c4503-570e-44c1-ae6a-a3c6b840c732
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea2c72a91aaa09d1c2d0e0944b73beb9ea313d0a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738026"
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="3db44-102">ICorDebugAppDomain::EnumerateSteppers – metoda</span><span class="sxs-lookup"><span data-stu-id="3db44-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>
<span data-ttu-id="3db44-103">Získá enumerátor pro všechny aktivní prvky krokování v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="3db44-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3db44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3db44-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3db44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3db44-105">Parameters</span></span>  
 `ppSteppers`  
 <span data-ttu-id="3db44-106">[out] Ukazatel na adresu icordebugstepperenum – objekt, který je enumerátor pro všechny aktivní prvky krokování v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="3db44-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3db44-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3db44-107">Requirements</span></span>  
 <span data-ttu-id="3db44-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3db44-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3db44-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3db44-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3db44-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3db44-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3db44-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3db44-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
