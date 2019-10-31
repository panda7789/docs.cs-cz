---
title: ICorDebugHeapValue::IsValid – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
ms.openlocfilehash: 7edf0065fa7eb39dada167a682f2b634a438f1f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138401"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="423ad-102">ICorDebugHeapValue::IsValid – metoda</span><span class="sxs-lookup"><span data-stu-id="423ad-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="423ad-103">Získá hodnotu, která označuje, zda je objekt reprezentovaný tímto ICorDebugHeapValue platný.</span><span class="sxs-lookup"><span data-stu-id="423ad-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="423ad-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="423ad-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="423ad-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="423ad-105">Syntax</span></span>  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="423ad-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="423ad-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="423ad-107">mimo Ukazatel na logickou hodnotu, která označuje, zda je tato hodnota na haldě platná.</span><span class="sxs-lookup"><span data-stu-id="423ad-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="423ad-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="423ad-108">Remarks</span></span>  
 <span data-ttu-id="423ad-109">Hodnota je neplatná, pokud byla uvolněna systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="423ad-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="423ad-110">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="423ad-110">This method has been deprecated.</span></span> <span data-ttu-id="423ad-111">V .NET Framework 2,0 jsou všechny hodnoty platné, dokud je volána metoda [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , v níž je čas zrušení platnosti hodnot.</span><span class="sxs-lookup"><span data-stu-id="423ad-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="423ad-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="423ad-112">Requirements</span></span>  
 <span data-ttu-id="423ad-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="423ad-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="423ad-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="423ad-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="423ad-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="423ad-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="423ad-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="423ad-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
