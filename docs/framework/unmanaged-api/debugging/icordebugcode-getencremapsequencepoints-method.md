---
title: ICorDebugCode::GetEnCRemapSequencePoints – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetEnCRemapSequencePoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetEnCRemapSequencePoints
helpviewer_keywords:
- GetEnCRemapSequencePoints method [.NET Framework debugging]
- ICorDebugCode::GetEnCRemapSequencePoints method [.NET Framework debugging]
ms.assetid: 8463a98a-de4a-418e-beb0-9611885ae6b0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 422c5eab896833b2bab8daf0c854c05c252b9ee6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747478"
---
# <a name="icordebugcodegetencremapsequencepoints-method"></a><span data-ttu-id="4f85e-102">ICorDebugCode::GetEnCRemapSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="4f85e-102">ICorDebugCode::GetEnCRemapSequencePoints Method</span></span>
<span data-ttu-id="4f85e-103">Tato metoda není implementována v aktuální verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f85e-103">This method is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f85e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f85e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEnCRemapSequencePoints(  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        ULONG32 offsets[]  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f85e-105">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f85e-105">See also</span></span>
