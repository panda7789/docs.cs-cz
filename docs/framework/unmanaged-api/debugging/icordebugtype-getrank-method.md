---
title: "ICorDebugType::GetRank – metoda"
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
- ICorDebugType.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetRank
helpviewer_keywords:
- GetRank method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetRank method [.NET Framework debugging]
ms.assetid: 72d3d927-f590-4f2d-8f60-448f3dfb96af
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: af481f01202d8a864c5258720f06e67d0bbd1e2b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="a3acc-102">ICorDebugType::GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="a3acc-102">ICorDebugType::GetRank Method</span></span>
<span data-ttu-id="a3acc-103">Získá počet dimenzí v typu pole.</span><span class="sxs-lookup"><span data-stu-id="a3acc-103">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3acc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3acc-104">Syntax</span></span>  
  
```  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3acc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3acc-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="a3acc-106">[out] Ukazatel na počet dimenzí.</span><span class="sxs-lookup"><span data-stu-id="a3acc-106">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3acc-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a3acc-107">Requirements</span></span>  
 <span data-ttu-id="a3acc-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3acc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3acc-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3acc-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3acc-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3acc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3acc-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3acc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
