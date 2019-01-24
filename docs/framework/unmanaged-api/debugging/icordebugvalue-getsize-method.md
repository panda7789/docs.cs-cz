---
title: ICorDebugValue::GetSize – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb0030a25dd48ab4236ec2b51891e0ac41aac902
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612616"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="62b58-102">ICorDebugValue::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="62b58-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="62b58-103">Získá velikost v bajtech tohoto objektu "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="62b58-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62b58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62b58-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62b58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62b58-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="62b58-106">[out] Velikost v bajtech, tento objekt hodnotu.</span><span class="sxs-lookup"><span data-stu-id="62b58-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62b58-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62b58-107">Remarks</span></span>  
 <span data-ttu-id="62b58-108">Pokud typ hodnoty je odkazový typ, vrátí tato metoda velikosti ukazatele, nikoli velikost objektu.</span><span class="sxs-lookup"><span data-stu-id="62b58-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="62b58-109">`ICorDebugValue::GetSize` Vrátí metoda `COR_E_OVERFLOW` pro objekty, které jsou větší než 4 GB na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="62b58-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="62b58-110">Použití [icordebugvalue3::getsize64 –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) metoda místo pro objekty, které jsou větší než 4 GB.</span><span class="sxs-lookup"><span data-stu-id="62b58-110">Use the [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62b58-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62b58-111">Requirements</span></span>  
 <span data-ttu-id="62b58-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62b58-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62b58-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62b58-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62b58-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62b58-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62b58-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62b58-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62b58-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62b58-116">See also</span></span>

- [<span data-ttu-id="62b58-117">GetSize64 – metoda</span><span class="sxs-lookup"><span data-stu-id="62b58-117">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
