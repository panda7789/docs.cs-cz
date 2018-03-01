---
title: "ICorDebugCode::GetEnCRemapSequencePoints – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 508979a63c2ab25ee3478dde490a5c3f7df14c73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodegetencremapsequencepoints-method"></a><span data-ttu-id="16be8-102">ICorDebugCode::GetEnCRemapSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="16be8-102">ICorDebugCode::GetEnCRemapSequencePoints Method</span></span>
<span data-ttu-id="16be8-103">Tato metoda není implementována v aktuální verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16be8-103">This method is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16be8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16be8-104">Syntax</span></span>  
  
```  
HRESULT GetEnCRemapSequencePoints(  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        ULONG32 offsets[]  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="16be8-105">Viz také</span><span class="sxs-lookup"><span data-stu-id="16be8-105">See Also</span></span>  
 
