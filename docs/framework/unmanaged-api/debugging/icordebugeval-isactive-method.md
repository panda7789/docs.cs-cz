---
title: ICorDebugEval::IsActive – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::IsActive method [.NET Framework debugging]
ms.assetid: bf2bba24-d278-43bd-b1c5-35680e748d3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fe29b3e35d2fbd42fac2d9ec1d1c594abe1239c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411155"
---
# <a name="icordebugevalisactive-method"></a><span data-ttu-id="0588e-102">ICorDebugEval::IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="0588e-102">ICorDebugEval::IsActive Method</span></span>
<span data-ttu-id="0588e-103">Získá hodnotu, která určuje, zda tento objekt ICorDebugEval právě probíhá.</span><span class="sxs-lookup"><span data-stu-id="0588e-103">Gets a value that indicates whether this ICorDebugEval object is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0588e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0588e-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL              *pbActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0588e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0588e-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="0588e-106">[out] Ukazatel na hodnotu, která určuje, zda toto testování je aktivní.</span><span class="sxs-lookup"><span data-stu-id="0588e-106">[out] Pointer to a value that indicates whether this evaluation is active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0588e-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0588e-107">Requirements</span></span>  
 <span data-ttu-id="0588e-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0588e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0588e-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0588e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0588e-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0588e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0588e-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0588e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
