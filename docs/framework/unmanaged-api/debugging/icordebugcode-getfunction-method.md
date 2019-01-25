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
ms.openlocfilehash: dd544619f9e5fb85a0b08b91ead8231ea25743cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651225"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="1291b-102">ICorDebugCode::GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="1291b-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="1291b-103">Získá "ICorDebugFunction" přidružené k této "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="1291b-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1291b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1291b-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1291b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1291b-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="1291b-106">[out] Ukazatel na adresu funkce.</span><span class="sxs-lookup"><span data-stu-id="1291b-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1291b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1291b-107">Remarks</span></span>  
 <span data-ttu-id="1291b-108">`ICorDebugCode` a `ICorDebugFunction` udržovat relaci.</span><span class="sxs-lookup"><span data-stu-id="1291b-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1291b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1291b-109">Requirements</span></span>  
 <span data-ttu-id="1291b-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1291b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1291b-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1291b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1291b-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1291b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1291b-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1291b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1291b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1291b-114">See also</span></span>

