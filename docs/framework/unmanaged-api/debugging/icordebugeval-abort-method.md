---
title: "ICorDebugEval::Abort – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.Abort
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::Abort
helpviewer_keywords:
- Abort method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::Abort method [.NET Framework debugging]
ms.assetid: 7070b6d0-f2e0-44ff-b124-0944cd807e69
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 064febeec32e5c43b6b73ef2b3a44625f151eb48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="f830c-102">ICorDebugEval::Abort – metoda</span><span class="sxs-lookup"><span data-stu-id="f830c-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="f830c-103">Zruší, které tento objekt ICorDebugEval právě provádí výpočet.</span><span class="sxs-lookup"><span data-stu-id="f830c-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f830c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f830c-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f830c-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f830c-105">Remarks</span></span>  
 <span data-ttu-id="f830c-106">Pokud je vnořený vyhodnocení a není tu poslední `Abort` metoda může selhat.</span><span class="sxs-lookup"><span data-stu-id="f830c-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f830c-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f830c-107">Requirements</span></span>  
 <span data-ttu-id="f830c-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f830c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f830c-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f830c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f830c-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f830c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f830c-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f830c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
