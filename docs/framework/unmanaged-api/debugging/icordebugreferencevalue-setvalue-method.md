---
title: ICorDebugReferenceValue::SetValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::SetValue
helpviewer_keywords:
- SetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::SetValue method [.NET Framework debugging]
ms.assetid: 3d3f6eec-d772-401f-a028-1a2ecdc31e95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59ef7bf8f17e79c9ae7b80dd314a5afce7fa9584
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474173"
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="336f5-102">ICorDebugReferenceValue::SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="336f5-102">ICorDebugReferenceValue::SetValue Method</span></span>
<span data-ttu-id="336f5-103">Nastaví adresu zadané paměti.</span><span class="sxs-lookup"><span data-stu-id="336f5-103">Sets the specified memory address.</span></span> <span data-ttu-id="336f5-104">To znamená tato metoda nastaví tento ICorDebugReferenceValue tak, aby odkazoval na objekt.</span><span class="sxs-lookup"><span data-stu-id="336f5-104">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="336f5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="336f5-105">Syntax</span></span>  
  
```  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="336f5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="336f5-106">Parameters</span></span>  
 `value`  
 <span data-ttu-id="336f5-107">[in] A `CORDB_ADDRESS` hodnota, která určuje adresu objektu, ke kterému je tento `ICorDebugReferenceValue` body.</span><span class="sxs-lookup"><span data-stu-id="336f5-107">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="336f5-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="336f5-108">Requirements</span></span>  
 <span data-ttu-id="336f5-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="336f5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="336f5-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="336f5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="336f5-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="336f5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="336f5-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="336f5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
