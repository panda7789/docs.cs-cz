---
title: "ICorDebugCode::IsIL – metoda"
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
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3530b5a7a747816a12e76d00fa7c299acf7657c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="b12b4-102">ICorDebugCode::IsIL – metoda</span><span class="sxs-lookup"><span data-stu-id="b12b4-102">ICorDebugCode::IsIL Method</span></span>
<span data-ttu-id="b12b4-103">Získá hodnotu, která určuje, zda tato "ICorDebugCode" představuje kód, který byl sestaven v Microsoft (MSIL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="b12b4-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b12b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b12b4-104">Syntax</span></span>  
  
```  
HRESULT IsIL (  
    [out] BOOL       *pbIL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b12b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b12b4-105">Parameters</span></span>  
 `pbIL`  
 <span data-ttu-id="b12b4-106">[out] `true` Pokud `ICorDebugCode` představuje kód, který byl kompilované v MSIL, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="b12b4-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b12b4-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b12b4-107">Requirements</span></span>  
 <span data-ttu-id="b12b4-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b12b4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b12b4-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b12b4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b12b4-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b12b4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b12b4-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b12b4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b12b4-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="b12b4-112">See Also</span></span>  
 
