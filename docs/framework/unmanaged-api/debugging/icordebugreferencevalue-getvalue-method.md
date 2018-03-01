---
title: "ICorDebugReferenceValue::GetValue – metoda"
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
- ICorDebugReferenceValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::GetValue method [.NET Framework debugging]
ms.assetid: 5da07f99-6c70-46ec-b997-5ab6fb7106cd
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6d7be70ec41b2044b4af10e102218ce487e4a5e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugreferencevaluegetvalue-method"></a><span data-ttu-id="7dfc3-102">ICorDebugReferenceValue::GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="7dfc3-102">ICorDebugReferenceValue::GetValue Method</span></span>
<span data-ttu-id="7dfc3-103">Získá aktuální adresa paměti odkazovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="7dfc3-103">Gets the current memory address of the referenced object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dfc3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7dfc3-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] CORDB_ADDRESS   *pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7dfc3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7dfc3-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="7dfc3-106">[out] Ukazatel na `CORDB_ADDRESS` hodnotu, která určuje adresu objektu, na kterou odkazuje tento objekt ICorDebugReferenceValue.</span><span class="sxs-lookup"><span data-stu-id="7dfc3-106">[out] A pointer to a `CORDB_ADDRESS` value that specifies the address of the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dfc3-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7dfc3-107">Requirements</span></span>  
 <span data-ttu-id="7dfc3-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dfc3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dfc3-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7dfc3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7dfc3-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7dfc3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7dfc3-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dfc3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
