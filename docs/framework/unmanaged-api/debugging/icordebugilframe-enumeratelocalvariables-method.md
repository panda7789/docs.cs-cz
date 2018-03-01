---
title: "ICorDebugILFrame::EnumerateLocalVariables – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3a1b53dbefefcea6003ec4a61c8169ed96bac701
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="ab506-102">ICorDebugILFrame::EnumerateLocalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="ab506-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="ab506-103">Získá enumerátor pro místní proměnné do tohoto rámce.</span><span class="sxs-lookup"><span data-stu-id="ab506-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab506-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab506-104">Syntax</span></span>  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab506-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab506-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="ab506-106">[out] Ukazatel na adresu ICorDebugValueEnum objekt, který je enumerátor pro místní proměnné do tohoto rámce.</span><span class="sxs-lookup"><span data-stu-id="ab506-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab506-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab506-107">Remarks</span></span>  
 <span data-ttu-id="ab506-108">`EnumerateLocalVariables`Získá enumerátor, který může být uveden lokální proměnné, které jsou k dispozici v rámci volání, která je reprezentována tento objekt ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="ab506-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="ab506-109">V seznamu nemusí zahrnovat všechny lokální proměnné ve funkci spuštěné, protože některé z nich nemusí být aktivní.</span><span class="sxs-lookup"><span data-stu-id="ab506-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab506-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab506-110">Requirements</span></span>  
 <span data-ttu-id="ab506-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab506-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab506-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab506-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab506-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab506-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab506-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab506-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
