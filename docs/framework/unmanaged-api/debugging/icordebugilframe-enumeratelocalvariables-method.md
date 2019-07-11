---
title: ICorDebugILFrame::EnumerateLocalVariables – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c18f2fce23e979f27d9116e74b6c6b007cd33bf0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752883"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="028b1-102">ICorDebugILFrame::EnumerateLocalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="028b1-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="028b1-103">Získá enumerátor pro místní proměnné v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="028b1-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="028b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="028b1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="028b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="028b1-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="028b1-106">[out] Ukazatel na adresu icordebugvalueenum – objekt, který je enumerátor pro místní proměnné v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="028b1-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="028b1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="028b1-107">Remarks</span></span>  
 <span data-ttu-id="028b1-108">`EnumerateLocalVariables` Získá enumerátor, který můžete zobrazit seznam dostupných v rámci volání, která je reprezentována tímto objektem ICorDebugILFrame lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="028b1-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="028b1-109">V seznamu nemusí obsahovat celou lokální proměnné ve funkci spuštěné, protože některé z nich nesmí být aktivní.</span><span class="sxs-lookup"><span data-stu-id="028b1-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="028b1-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="028b1-110">Requirements</span></span>  
 <span data-ttu-id="028b1-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="028b1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="028b1-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="028b1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="028b1-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="028b1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="028b1-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="028b1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
