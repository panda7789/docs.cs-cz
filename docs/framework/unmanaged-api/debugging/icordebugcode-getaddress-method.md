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
ms.openlocfilehash: 11ced90b88f083eb69b06d197d64a8ef4252f9d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141490"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="8475f-102">ICorDebugCode::GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="8475f-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="8475f-103">Získá relativní virtuální adresu (RVA) segmentu kódu, který představuje toto rozhraní "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="8475f-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8475f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8475f-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8475f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8475f-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="8475f-106">[out] Ukazatel na adresu RVA segmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="8475f-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8475f-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8475f-107">Requirements</span></span>  
 <span data-ttu-id="8475f-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8475f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8475f-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8475f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8475f-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8475f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8475f-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8475f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8475f-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8475f-112">See also</span></span>
