---
title: "ICorDebugAppDomain::EnumerateSteppers – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b410eabee546307488449e577d9e102ac6a210b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="263d6-102">ICorDebugAppDomain::EnumerateSteppers – metoda</span><span class="sxs-lookup"><span data-stu-id="263d6-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>
<span data-ttu-id="263d6-103">Získá enumerátor pro všechny aktivní steppers v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="263d6-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="263d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="263d6-104">Syntax</span></span>  
  
```  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="263d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="263d6-105">Parameters</span></span>  
 `ppSteppers`  
 <span data-ttu-id="263d6-106">[out] Ukazatel na adresu ICorDebugStepperEnum objekt, který je enumerátor pro všechny aktivní steppers v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="263d6-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="263d6-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="263d6-107">Requirements</span></span>  
 <span data-ttu-id="263d6-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="263d6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="263d6-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="263d6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="263d6-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="263d6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="263d6-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="263d6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
