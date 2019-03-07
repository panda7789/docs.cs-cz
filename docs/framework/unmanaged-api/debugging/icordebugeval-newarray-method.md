---
title: ICorDebugEval::NewArray – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1abe307e3b9fa607912f98e456a11176eb17c56
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471507"
---
# <a name="icordebugevalnewarray-method"></a><span data-ttu-id="de58d-102">ICorDebugEval::NewArray – metoda</span><span class="sxs-lookup"><span data-stu-id="de58d-102">ICorDebugEval::NewArray Method</span></span>
<span data-ttu-id="de58d-103">Přidělí nové pole typu zadaného elementu a dimenze.</span><span class="sxs-lookup"><span data-stu-id="de58d-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
 <span data-ttu-id="de58d-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="de58d-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="de58d-105">Použití [icordebugeval2::newparameterizedarray –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) místo.</span><span class="sxs-lookup"><span data-stu-id="de58d-105">Use [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de58d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de58d-106">Syntax</span></span>  
  
```  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de58d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="de58d-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="de58d-108">[in] Hodnota corelementtype – výčet, který určuje typ prvku pole.</span><span class="sxs-lookup"><span data-stu-id="de58d-108">[in] A value of the CorElementType enumeration that specifies the element type of the array.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="de58d-109">[in] Ukazatel na ICorDebugClass objekt, který určuje třídu elementu.</span><span class="sxs-lookup"><span data-stu-id="de58d-109">[in] A pointer to a ICorDebugClass object that specifies the class of the element.</span></span> <span data-ttu-id="de58d-110">Tato hodnota může mít hodnotu null, pokud typ prvku je primitivního typu.</span><span class="sxs-lookup"><span data-stu-id="de58d-110">This value may be null if the element type is a primitive type.</span></span>  
  
 `rank`  
 <span data-ttu-id="de58d-111">[in] Počet rozměrů pole.</span><span class="sxs-lookup"><span data-stu-id="de58d-111">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="de58d-112">V rozhraní .NET Framework 2.0 tato hodnota musí být 1.</span><span class="sxs-lookup"><span data-stu-id="de58d-112">In the .NET Framework 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="de58d-113">[in] Velikost v bajtech každého rozměru pole.</span><span class="sxs-lookup"><span data-stu-id="de58d-113">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="de58d-114">[in] Volitelné.</span><span class="sxs-lookup"><span data-stu-id="de58d-114">[in] Optional.</span></span> <span data-ttu-id="de58d-115">Dolní mez každé dimenze matice.</span><span class="sxs-lookup"><span data-stu-id="de58d-115">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="de58d-116">Pokud je tato hodnota vynechána, předpokládá se pro jednotlivé rozměry dolní mez nula.</span><span class="sxs-lookup"><span data-stu-id="de58d-116">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de58d-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de58d-117">Remarks</span></span>  
 <span data-ttu-id="de58d-118">Pole je vytvořen vždy v aplikační doméně, ve které vlákno právě probíhá.</span><span class="sxs-lookup"><span data-stu-id="de58d-118">The array is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de58d-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de58d-119">Requirements</span></span>  
 <span data-ttu-id="de58d-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de58d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de58d-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de58d-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de58d-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de58d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de58d-123">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="de58d-123">**.NET Framework Versions:** 1.1, 1.0</span></span>
