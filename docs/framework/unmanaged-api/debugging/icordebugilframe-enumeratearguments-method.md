---
title: "ICorDebugILFrame::EnumerateArguments – metoda"
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
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 474118abc505928d16737d792a619e75f1209344
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="92b9e-102">ICorDebugILFrame::EnumerateArguments – metoda</span><span class="sxs-lookup"><span data-stu-id="92b9e-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="92b9e-103">Získá enumerátor pro argumenty do tohoto rámce.</span><span class="sxs-lookup"><span data-stu-id="92b9e-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92b9e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92b9e-104">Syntax</span></span>  
  
```  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92b9e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92b9e-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="92b9e-106">[out] Ukazatel na adresu ICorDebugValueEnum objekt, který je enumerátor pro argumenty do tohoto rámce.</span><span class="sxs-lookup"><span data-stu-id="92b9e-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92b9e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92b9e-107">Remarks</span></span>  
 <span data-ttu-id="92b9e-108">`EnumerateArguments`Získá enumerátor, který můžete zobrazit seznam argumentů, které jsou k dispozici v rámci volání, která je reprezentována tento objekt ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="92b9e-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="92b9e-109">Obsahuje seznam argumentů, které jsou [vararg](/cpp/windows/vararg) (tedy proměnný počet argumentů) a také argumenty, které nejsou `vararg`.</span><span class="sxs-lookup"><span data-stu-id="92b9e-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92b9e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92b9e-110">Requirements</span></span>  
 <span data-ttu-id="92b9e-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92b9e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92b9e-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92b9e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92b9e-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92b9e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92b9e-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92b9e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
