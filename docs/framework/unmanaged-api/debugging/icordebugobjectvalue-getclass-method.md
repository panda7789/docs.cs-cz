---
title: ICorDebugObjectValue::GetClass – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type:
- apiref
ms.openlocfilehash: b0e8fd162ccc1cfc944fb870f493febfe2e5ef42
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207686"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="6d259-102">ICorDebugObjectValue::GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="6d259-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="6d259-103">Získá třídu této hodnoty objektu.</span><span class="sxs-lookup"><span data-stu-id="6d259-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d259-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d259-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d259-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d259-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="6d259-106">mimo Ukazatel na adresu objektu "ICorDebugClass", který představuje třídu hodnoty objektu reprezentované tímto objektem "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="6d259-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d259-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d259-107">Remarks</span></span>  
 <span data-ttu-id="6d259-108">`GetClass`Metody a [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) vrátí informace o typu hodnoty. obě jsou nahrazeny obecnými [ICorDebugValue2:: GetExactType –](icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="6d259-108">The `GetClass` and [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d259-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d259-109">Requirements</span></span>  
 <span data-ttu-id="6d259-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d259-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d259-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6d259-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d259-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6d259-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d259-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d259-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d259-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d259-114">See also</span></span>
