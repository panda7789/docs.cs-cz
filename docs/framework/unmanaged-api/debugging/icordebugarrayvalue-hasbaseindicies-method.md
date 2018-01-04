---
title: "ICorDebugArrayValue::HasBaseIndicies – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.HasBaseIndicies
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1aa7e263c4e6b1460e327869c0c6945cba65328
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="450a7-102">ICorDebugArrayValue::HasBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="450a7-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="450a7-103">Získá hodnotu, která určuje, zda mají všechny dimenze toto pole základní index nulová.</span><span class="sxs-lookup"><span data-stu-id="450a7-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="450a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="450a7-104">Syntax</span></span>  
  
```  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="450a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="450a7-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="450a7-106">[out] Ukazatel na logickou hodnotu, která je `true` Pokud jeden nebo více dimenzí tohoto `ICorDebugArrayValue` objekt mají základní index nulová, jinak je logická hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="450a7-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="450a7-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="450a7-107">Requirements</span></span>  
 <span data-ttu-id="450a7-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="450a7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="450a7-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="450a7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="450a7-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="450a7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="450a7-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="450a7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
