---
title: ICorDebugValue3::GetSize64 – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
ms.openlocfilehash: 6eb26de83a6cdce47477e6cb3dffd6a94d889975
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397029"
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="afd60-102">ICorDebugValue3::GetSize64 – metoda</span><span class="sxs-lookup"><span data-stu-id="afd60-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="afd60-103">Získá velikost objektu [ICorDebugValue3 –](icordebugvalue3-interface.md) v bajtech.</span><span class="sxs-lookup"><span data-stu-id="afd60-103">Gets the size, in bytes, of this [ICorDebugValue3](icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afd60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afd60-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afd60-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="afd60-105">Parameters</span></span>  
 <span data-ttu-id="afd60-106">pSize</span><span class="sxs-lookup"><span data-stu-id="afd60-106">pSize</span></span>  
 <span data-ttu-id="afd60-107">mimo Ukazatel na velikost (v bajtech) tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="afd60-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afd60-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="afd60-108">Remarks</span></span>  
 <span data-ttu-id="afd60-109">Pokud je typ této hodnoty odkazový typ, vrátí tato metoda velikost ukazatele, nikoli velikost objektu.</span><span class="sxs-lookup"><span data-stu-id="afd60-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="afd60-110">`ICorDebugValue3::GetSize`Metoda se liší od metody [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md) v typu jeho výstupního parametru.</span><span class="sxs-lookup"><span data-stu-id="afd60-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="afd60-111">V [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md)je výstupní parametr a `ULONG32` ; v `ICorDebugValue3::GetSize` , je `ULONG64` .</span><span class="sxs-lookup"><span data-stu-id="afd60-111">In [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="afd60-112">To umožňuje, aby rozhraní [ICorDebugValue3 –](icordebugvalue3-interface.md) nahlásilo velikost polí, která překračují 2 GB.</span><span class="sxs-lookup"><span data-stu-id="afd60-112">This enables the [ICorDebugValue3](icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afd60-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="afd60-113">Requirements</span></span>  
 <span data-ttu-id="afd60-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afd60-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afd60-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="afd60-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="afd60-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="afd60-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afd60-117">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afd60-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afd60-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="afd60-118">See also</span></span>

- [<span data-ttu-id="afd60-119">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="afd60-119">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="afd60-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="afd60-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
