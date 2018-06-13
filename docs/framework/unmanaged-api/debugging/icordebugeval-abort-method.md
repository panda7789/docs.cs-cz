---
title: ICorDebugEval::Abort – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.Abort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::Abort
helpviewer_keywords:
- Abort method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::Abort method [.NET Framework debugging]
ms.assetid: 7070b6d0-f2e0-44ff-b124-0944cd807e69
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 682d6684b6c86485530b9e5283d843f3b2eb7e46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413800"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="13a13-102">ICorDebugEval::Abort – metoda</span><span class="sxs-lookup"><span data-stu-id="13a13-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="13a13-103">Zruší, které tento objekt ICorDebugEval právě provádí výpočet.</span><span class="sxs-lookup"><span data-stu-id="13a13-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13a13-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13a13-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="13a13-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13a13-105">Remarks</span></span>  
 <span data-ttu-id="13a13-106">Pokud je vnořený vyhodnocení a není tu poslední `Abort` metoda může selhat.</span><span class="sxs-lookup"><span data-stu-id="13a13-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13a13-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13a13-107">Requirements</span></span>  
 <span data-ttu-id="13a13-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13a13-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13a13-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13a13-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13a13-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13a13-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13a13-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13a13-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
