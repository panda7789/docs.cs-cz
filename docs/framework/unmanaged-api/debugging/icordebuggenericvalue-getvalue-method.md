---
title: ICorDebugGenericValue::GetValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e2fc054e42c34b13051e2125f8e18adc3029633
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755561"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="2a7b4-102">ICorDebugGenericValue::GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="2a7b4-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="2a7b4-103">Hodnota tomto obecný zkopíruje do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2a7b4-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a7b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a7b4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a7b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a7b4-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="2a7b4-106">[out] Ukazatel na hodnotu, která je reprezentována tímto objektem icordebuggenericvalue –.</span><span class="sxs-lookup"><span data-stu-id="2a7b4-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="2a7b4-107">Hodnota může být jednoduchý typ. nebo typ odkazu (to znamená, že ukazatele).</span><span class="sxs-lookup"><span data-stu-id="2a7b4-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a7b4-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2a7b4-108">Requirements</span></span>  
 <span data-ttu-id="2a7b4-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a7b4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a7b4-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a7b4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a7b4-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a7b4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a7b4-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a7b4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
