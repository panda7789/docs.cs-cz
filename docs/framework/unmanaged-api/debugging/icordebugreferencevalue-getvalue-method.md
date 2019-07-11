---
title: ICorDebugReferenceValue::GetValue – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5542cf5895bc60c5880f2f082a9c14d722e02478
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744920"
---
# <a name="icordebugreferencevaluegetvalue-method"></a><span data-ttu-id="26c8d-102">ICorDebugReferenceValue::GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="26c8d-102">ICorDebugReferenceValue::GetValue Method</span></span>
<span data-ttu-id="26c8d-103">Získá aktuální adresu paměti odkazovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="26c8d-103">Gets the current memory address of the referenced object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26c8d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26c8d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] CORDB_ADDRESS   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26c8d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26c8d-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="26c8d-106">[out] Ukazatel `CORDB_ADDRESS` hodnota, která určuje adresu objektu, na kterou odkazuje tento objekt ICorDebugReferenceValue.</span><span class="sxs-lookup"><span data-stu-id="26c8d-106">[out] A pointer to a `CORDB_ADDRESS` value that specifies the address of the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26c8d-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26c8d-107">Requirements</span></span>  
 <span data-ttu-id="26c8d-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26c8d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26c8d-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26c8d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26c8d-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26c8d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26c8d-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26c8d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
