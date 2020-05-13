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
ms.openlocfilehash: 13b100012215a7c2cee51ad5af39ec1447ab4e5b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207517"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="42800-102">ICorDebugObjectValue::IsValueClass – metoda</span><span class="sxs-lookup"><span data-stu-id="42800-102">ICorDebugObjectValue::IsValueClass Method</span></span>
<span data-ttu-id="42800-103">Získá hodnotu, která označuje, zda je hodnota tohoto objektu typem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="42800-103">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42800-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42800-104">Syntax</span></span>  
  
```cpp  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42800-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42800-105">Parameters</span></span>  
 `pbIsValueClass`  
 <span data-ttu-id="42800-106">mimo Ukazatel na logickou hodnotu, která je `true` v případě, že hodnota objektu reprezentovaná tímto "ICorDebugObjectValue" je typ hodnoty, nikoli odkazový typ. v opačném případě `pbIsValueClass` je `false` .</span><span class="sxs-lookup"><span data-stu-id="42800-106">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42800-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42800-107">Requirements</span></span>  
 <span data-ttu-id="42800-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42800-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42800-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="42800-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42800-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="42800-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42800-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42800-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42800-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="42800-112">See also</span></span>
