---
title: ICorDebugObjectValue::IsValueClass – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.IsValueClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::IsValueClass
helpviewer_keywords:
- ICorDebugObjectValue::IsValueClass method [.NET Framework debugging]
- IsValueClass method [.NET Framework debugging]
ms.assetid: 13d89a4a-5d9d-4a79-9600-5e2a98c3d166
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12ba95eca2a103cffa07247a6ce474263e42e5ad
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487517"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="151c8-102">ICorDebugObjectValue::IsValueClass – metoda</span><span class="sxs-lookup"><span data-stu-id="151c8-102">ICorDebugObjectValue::IsValueClass Method</span></span>
<span data-ttu-id="151c8-103">Získá hodnotu, která určuje, zda je hodnota tohoto objektu typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="151c8-103">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="151c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="151c8-104">Syntax</span></span>  
  
```  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="151c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="151c8-105">Parameters</span></span>  
 `pbIsValueClass`  
 <span data-ttu-id="151c8-106">[out] Ukazatel na logickou hodnotu, která je `true` Pokud hodnoty objektu, která je reprezentována tento "ICorDebugObjectValue", je typ hodnoty místo odkazový typ; v opačném případě `pbIsValueClass` je `false`.</span><span class="sxs-lookup"><span data-stu-id="151c8-106">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="151c8-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="151c8-107">Requirements</span></span>  
 <span data-ttu-id="151c8-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="151c8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="151c8-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="151c8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="151c8-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="151c8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="151c8-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="151c8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="151c8-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="151c8-112">See also</span></span>


