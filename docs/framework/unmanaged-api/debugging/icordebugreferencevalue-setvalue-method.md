---
title: "ICorDebugReferenceValue::SetValue – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugReferenceValue.SetValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugReferenceValue::SetValue
helpviewer_keywords:
- SetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::SetValue method [.NET Framework debugging]
ms.assetid: 3d3f6eec-d772-401f-a028-1a2ecdc31e95
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71250155d0c71b9b8f9cddad57d0c74b4ffc7991
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="97fba-102">ICorDebugReferenceValue::SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="97fba-102">ICorDebugReferenceValue::SetValue Method</span></span>
<span data-ttu-id="97fba-103">Nastaví adresu zadanou paměti.</span><span class="sxs-lookup"><span data-stu-id="97fba-103">Sets the specified memory address.</span></span> <span data-ttu-id="97fba-104">To znamená tato metoda nastaví tento ICorDebugReferenceValue tak, aby odkazoval na objekt.</span><span class="sxs-lookup"><span data-stu-id="97fba-104">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97fba-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97fba-105">Syntax</span></span>  
  
```  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97fba-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="97fba-106">Parameters</span></span>  
 `value`  
 <span data-ttu-id="97fba-107">[v] A `CORDB_ADDRESS` hodnotu, která určuje adresu objektu, ke kterému tato `ICorDebugReferenceValue` body.</span><span class="sxs-lookup"><span data-stu-id="97fba-107">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97fba-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97fba-108">Requirements</span></span>  
 <span data-ttu-id="97fba-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97fba-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97fba-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97fba-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97fba-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97fba-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97fba-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97fba-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
