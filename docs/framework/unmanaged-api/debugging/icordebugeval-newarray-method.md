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
ms.openlocfilehash: 38b00d903fdd7301415a8df7642e12366178fd10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413937"
---
# <a name="icordebugevalnewarray-method"></a><span data-ttu-id="36676-102">ICorDebugEval::NewArray – metoda</span><span class="sxs-lookup"><span data-stu-id="36676-102">ICorDebugEval::NewArray Method</span></span>
<span data-ttu-id="36676-103">Přiděluje nový pole typu zadaného elementu a dimenze.</span><span class="sxs-lookup"><span data-stu-id="36676-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
 <span data-ttu-id="36676-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="36676-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="36676-105">Použití [icordebugeval2::newparameterizedarray –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) místo.</span><span class="sxs-lookup"><span data-stu-id="36676-105">Use [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36676-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36676-106">Syntax</span></span>  
  
```  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36676-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="36676-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="36676-108">[v] Hodnota CorElementType – výčet, který určuje typ elementu pole.</span><span class="sxs-lookup"><span data-stu-id="36676-108">[in] A value of the CorElementType enumeration that specifies the element type of the array.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="36676-109">[v] Ukazatel na ICorDebugClass objekt, který určuje třída elementu.</span><span class="sxs-lookup"><span data-stu-id="36676-109">[in] A pointer to a ICorDebugClass object that specifies the class of the element.</span></span> <span data-ttu-id="36676-110">Tato hodnota může mít hodnotu null, pokud je typ elementu primitivního typu.</span><span class="sxs-lookup"><span data-stu-id="36676-110">This value may be null if the element type is a primitive type.</span></span>  
  
 `rank`  
 <span data-ttu-id="36676-111">[v] Počet rozměrů pole.</span><span class="sxs-lookup"><span data-stu-id="36676-111">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="36676-112">V rozhraní .NET Framework 2.0 tato hodnota musí být 1.</span><span class="sxs-lookup"><span data-stu-id="36676-112">In the .NET Framework 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="36676-113">[v] Velikost v bajtech, každá dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="36676-113">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="36676-114">[v] Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="36676-114">[in] Optional.</span></span> <span data-ttu-id="36676-115">Dolní mez Každá dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="36676-115">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="36676-116">Pokud tato hodnota je vynechán, předpokládá se, že dolní mez 0 je pro každou dimenzi.</span><span class="sxs-lookup"><span data-stu-id="36676-116">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36676-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36676-117">Remarks</span></span>  
 <span data-ttu-id="36676-118">Toto pole je vytvořen vždy v doméně aplikace, ve kterém je aktuálně spuštěných vlákno.</span><span class="sxs-lookup"><span data-stu-id="36676-118">The array is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36676-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36676-119">Requirements</span></span>  
 <span data-ttu-id="36676-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36676-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36676-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36676-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36676-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36676-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36676-123">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="36676-123">**.NET Framework Versions:** 1.1, 1.0</span></span>
