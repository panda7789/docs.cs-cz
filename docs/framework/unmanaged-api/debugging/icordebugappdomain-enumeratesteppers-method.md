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
ms.openlocfilehash: d326c801ed17fa6fe79f9e464e64844d0016e572
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785150"
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="53e3b-102">ICorDebugAppDomain::EnumerateSteppers – metoda</span><span class="sxs-lookup"><span data-stu-id="53e3b-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>
<span data-ttu-id="53e3b-103">Získá enumerátor pro všechny aktivní prvky krokování v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="53e3b-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53e3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53e3b-104">Syntax</span></span>  
  
```  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53e3b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53e3b-105">Parameters</span></span>  
 `ppSteppers`  
 <span data-ttu-id="53e3b-106">[out] Ukazatel na adresu icordebugstepperenum – objekt, který je enumerátor pro všechny aktivní prvky krokování v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="53e3b-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53e3b-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53e3b-107">Requirements</span></span>  
 <span data-ttu-id="53e3b-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53e3b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53e3b-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53e3b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53e3b-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53e3b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53e3b-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53e3b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
