---
title: "ICorDebugArrayValue::GetRank – metoda"
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
- ICorDebugArrayValue.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetRank
helpviewer_keywords:
- ICorDebugArrayValue::GetRank method [.NET Framework debugging]
- GetRank method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 5e83c82c-593d-4691-90b0-383d218b415e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b821e23b9b45932fb9296e0d4dac81d2b8c06135
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvaluegetrank-method"></a><span data-ttu-id="9c048-102">ICorDebugArrayValue::GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="9c048-102">ICorDebugArrayValue::GetRank Method</span></span>
<span data-ttu-id="9c048-103">Získá počet dimenzí v poli.</span><span class="sxs-lookup"><span data-stu-id="9c048-103">Gets the number of dimensions in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c048-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c048-104">Syntax</span></span>  
  
```  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c048-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c048-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="9c048-106">[out] Ukazatel na počet dimenzí v tomto `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="9c048-106">[out] A pointer to the number of dimensions in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c048-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c048-107">Requirements</span></span>  
 <span data-ttu-id="9c048-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c048-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c048-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c048-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c048-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c048-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c048-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c048-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
