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
ms.openlocfilehash: 764b99b5687c171b0dcdbc7f8ca15493c182ff7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="33b0d-102">ICorDebugReferenceValue::SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="33b0d-102">ICorDebugReferenceValue::SetValue Method</span></span>
<span data-ttu-id="33b0d-103">Nastaví adresu zadanou paměti.</span><span class="sxs-lookup"><span data-stu-id="33b0d-103">Sets the specified memory address.</span></span> <span data-ttu-id="33b0d-104">To znamená tato metoda nastaví tento ICorDebugReferenceValue tak, aby odkazoval na objekt.</span><span class="sxs-lookup"><span data-stu-id="33b0d-104">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33b0d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33b0d-105">Syntax</span></span>  
  
```  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33b0d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="33b0d-106">Parameters</span></span>  
 `value`  
 <span data-ttu-id="33b0d-107">[v] A `CORDB_ADDRESS` hodnotu, která určuje adresu objektu, ke kterému tato `ICorDebugReferenceValue` body.</span><span class="sxs-lookup"><span data-stu-id="33b0d-107">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33b0d-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33b0d-108">Requirements</span></span>  
 <span data-ttu-id="33b0d-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33b0d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33b0d-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33b0d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33b0d-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33b0d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33b0d-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33b0d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
