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
ms.openlocfilehash: 0682c0786182422587adb976ff6bc2455b9e5cdc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128937"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="4904b-102">ICorDebugObjectValue::IsValueClass – metoda</span><span class="sxs-lookup"><span data-stu-id="4904b-102">ICorDebugObjectValue::IsValueClass Method</span></span>
<span data-ttu-id="4904b-103">Získá hodnotu, která označuje, zda je hodnota tohoto objektu typem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4904b-103">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4904b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4904b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4904b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4904b-105">Parameters</span></span>  
 `pbIsValueClass`  
 <span data-ttu-id="4904b-106">mimo Ukazatel na logickou hodnotu, která je `true`, pokud hodnota objektu reprezentovaná tímto "ICorDebugObjectValue" je typ hodnoty spíše než typ odkazu; v opačném případě `pbIsValueClass` `false`.</span><span class="sxs-lookup"><span data-stu-id="4904b-106">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4904b-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4904b-107">Requirements</span></span>  
 <span data-ttu-id="4904b-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4904b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4904b-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4904b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4904b-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4904b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4904b-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4904b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4904b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4904b-112">See also</span></span>
