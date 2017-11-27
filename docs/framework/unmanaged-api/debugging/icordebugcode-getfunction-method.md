---
title: "ICorDebugCode::GetFunction – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.GetFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0304eaadec5805b1ded9a4cbfe79959c3e18a344
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="0cd78-102">ICorDebugCode::GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="0cd78-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="0cd78-103">Získá "ICorDebugFunction" přidružené k této "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="0cd78-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cd78-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cd78-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0cd78-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0cd78-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="0cd78-106">[out] Ukazatel na adresu funkce.</span><span class="sxs-lookup"><span data-stu-id="0cd78-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cd78-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0cd78-107">Remarks</span></span>  
 <span data-ttu-id="0cd78-108">`ICorDebugCode`a `ICorDebugFunction` udržovat relaci 1: 1.</span><span class="sxs-lookup"><span data-stu-id="0cd78-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cd78-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0cd78-109">Requirements</span></span>  
 <span data-ttu-id="0cd78-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cd78-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cd78-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0cd78-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0cd78-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cd78-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cd78-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cd78-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cd78-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cd78-114">See Also</span></span>  
 
