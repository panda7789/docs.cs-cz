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
ms.openlocfilehash: 892471e7b35b4f4093df3f86d4777947b6e484e0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378308"
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="d35fa-102">ICorDebugReferenceValue::SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="d35fa-102">ICorDebugReferenceValue::SetValue Method</span></span>
<span data-ttu-id="d35fa-103">Nastaví zadanou adresu paměti.</span><span class="sxs-lookup"><span data-stu-id="d35fa-103">Sets the specified memory address.</span></span> <span data-ttu-id="d35fa-104">To znamená, že tato metoda nastaví tento ICorDebugReferenceValue tak, aby odkazoval na objekt.</span><span class="sxs-lookup"><span data-stu-id="d35fa-104">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d35fa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d35fa-105">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d35fa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d35fa-106">Parameters</span></span>  
 `value`  
 <span data-ttu-id="d35fa-107">pro `CORDB_ADDRESS`Hodnota, která určuje adresu objektu, na který tyto `ICorDebugReferenceValue` body odkazují.</span><span class="sxs-lookup"><span data-stu-id="d35fa-107">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d35fa-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d35fa-108">Requirements</span></span>  
 <span data-ttu-id="d35fa-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d35fa-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d35fa-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d35fa-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d35fa-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d35fa-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d35fa-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d35fa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
