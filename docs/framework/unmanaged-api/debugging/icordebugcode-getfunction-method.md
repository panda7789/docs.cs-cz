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
ms.openlocfilehash: 10ab92c660353bea85bbd0918a25f716898ef837
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747533"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="a0458-102">ICorDebugCode::GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="a0458-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="a0458-103">Získá "ICorDebugFunction" přidružené k této "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="a0458-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0458-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0458-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0458-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0458-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="a0458-106">[out] Ukazatel na adresu funkce.</span><span class="sxs-lookup"><span data-stu-id="a0458-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0458-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0458-107">Remarks</span></span>  
 <span data-ttu-id="a0458-108">`ICorDebugCode` a `ICorDebugFunction` udržovat relaci.</span><span class="sxs-lookup"><span data-stu-id="a0458-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0458-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0458-109">Requirements</span></span>  
 <span data-ttu-id="a0458-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0458-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0458-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0458-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0458-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0458-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0458-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0458-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0458-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0458-114">See also</span></span>
