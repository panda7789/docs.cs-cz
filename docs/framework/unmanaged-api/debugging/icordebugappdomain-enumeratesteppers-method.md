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
ms.openlocfilehash: 7bf3aa6d883dffece6ba89d41005499cc6206906
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401288"
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="c7a4e-102">ICorDebugAppDomain::EnumerateSteppers – metoda</span><span class="sxs-lookup"><span data-stu-id="c7a4e-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>
<span data-ttu-id="c7a4e-103">Získá enumerátor pro všechny aktivní steppers v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="c7a4e-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7a4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7a4e-104">Syntax</span></span>  
  
```  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7a4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7a4e-105">Parameters</span></span>  
 `ppSteppers`  
 <span data-ttu-id="c7a4e-106">[out] Ukazatel na adresu ICorDebugStepperEnum objekt, který je enumerátor pro všechny aktivní steppers v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="c7a4e-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7a4e-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7a4e-107">Requirements</span></span>  
 <span data-ttu-id="c7a4e-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7a4e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7a4e-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7a4e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7a4e-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7a4e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7a4e-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7a4e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
