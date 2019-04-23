---
title: ICorDebugCode::GetFunction – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0104a52c3aa206f86daff30d9d16298e6beae324
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099453"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="889ce-102">ICorDebugCode::GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="889ce-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="889ce-103">Získá "ICorDebugFunction" přidružené k této "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="889ce-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="889ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="889ce-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="889ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="889ce-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="889ce-106">[out] Ukazatel na adresu funkce.</span><span class="sxs-lookup"><span data-stu-id="889ce-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="889ce-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="889ce-107">Remarks</span></span>  
 <span data-ttu-id="889ce-108">`ICorDebugCode` a `ICorDebugFunction` udržovat relaci.</span><span class="sxs-lookup"><span data-stu-id="889ce-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="889ce-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="889ce-109">Requirements</span></span>  
 <span data-ttu-id="889ce-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="889ce-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="889ce-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="889ce-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="889ce-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="889ce-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="889ce-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="889ce-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="889ce-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="889ce-114">See also</span></span>
