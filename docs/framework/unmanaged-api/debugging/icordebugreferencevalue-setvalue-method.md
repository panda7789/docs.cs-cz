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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782925"
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="c9338-102">ICorDebugReferenceValue::SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c9338-102">ICorDebugReferenceValue::SetValue Method</span></span>
<span data-ttu-id="c9338-103">Nastaví adresu zadané paměti.</span><span class="sxs-lookup"><span data-stu-id="c9338-103">Sets the specified memory address.</span></span> <span data-ttu-id="c9338-104">To znamená tato metoda nastaví tento ICorDebugReferenceValue tak, aby odkazoval na objekt.</span><span class="sxs-lookup"><span data-stu-id="c9338-104">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9338-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9338-105">Syntax</span></span>  
  
```  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9338-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9338-106">Parameters</span></span>  
 `value`  
 <span data-ttu-id="c9338-107">[in] A `CORDB_ADDRESS` hodnota, která určuje adresu objektu, ke kterému je tento `ICorDebugReferenceValue` body.</span><span class="sxs-lookup"><span data-stu-id="c9338-107">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9338-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9338-108">Requirements</span></span>  
 <span data-ttu-id="c9338-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9338-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9338-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9338-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9338-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9338-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9338-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9338-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
