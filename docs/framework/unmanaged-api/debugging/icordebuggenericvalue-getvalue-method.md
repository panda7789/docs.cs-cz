---
title: "ICorDebugGenericValue::GetValue – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGenericValue.GetValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ebb681d32c3ba805fd2e413ceeb007cb2cee57f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="00898-102">ICorDebugGenericValue::GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="00898-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="00898-103">Hodnota tomto obecný zkopíruje do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="00898-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00898-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00898-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00898-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00898-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="00898-106">[out] Ukazatel na hodnotu, která je reprezentována tento objekt ICorDebugGenericValue.</span><span class="sxs-lookup"><span data-stu-id="00898-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="00898-107">Hodnota může být jednoduchého typu nebo typu odkazu (tedy ukazatel).</span><span class="sxs-lookup"><span data-stu-id="00898-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00898-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00898-108">Requirements</span></span>  
 <span data-ttu-id="00898-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00898-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00898-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00898-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00898-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00898-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00898-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00898-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
