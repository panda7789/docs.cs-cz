---
title: ICorDebugCode::GetAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetAddress
helpviewer_keywords:
- GetAddress method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetAddress method [.NET Framework debugging]
ms.assetid: cc507cb0-df2e-49c2-b32e-0c3271a8df9a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 229bf968d21516d48468610c8f47367324fb6b13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695514"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="a3cc9-102">ICorDebugCode::GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="a3cc9-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="a3cc9-103">Získá relativní virtuální adresu (RVA) segmentu kódu, který představuje toto rozhraní "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="a3cc9-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3cc9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3cc9-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3cc9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3cc9-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="a3cc9-106">[out] Ukazatel na adresu RVA segmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="a3cc9-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3cc9-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a3cc9-107">Requirements</span></span>  
 <span data-ttu-id="a3cc9-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3cc9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3cc9-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3cc9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3cc9-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3cc9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3cc9-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3cc9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3cc9-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3cc9-112">See also</span></span>

