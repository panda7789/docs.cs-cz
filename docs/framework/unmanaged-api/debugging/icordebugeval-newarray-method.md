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
ms.openlocfilehash: ca0844e4d2b1cad65266d58c6cda74de203d1758
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137662"
---
# <a name="icordebugevalnewarray-method"></a><span data-ttu-id="de44e-102">ICorDebugEval::NewArray – metoda</span><span class="sxs-lookup"><span data-stu-id="de44e-102">ICorDebugEval::NewArray Method</span></span>
<span data-ttu-id="de44e-103">Přidělí nové pole zadaného typu a dimenzí prvku.</span><span class="sxs-lookup"><span data-stu-id="de44e-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
 <span data-ttu-id="de44e-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="de44e-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="de44e-105">Místo toho použijte [ICorDebugEval2:: newparameterizedarray –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) .</span><span class="sxs-lookup"><span data-stu-id="de44e-105">Use [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de44e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de44e-106">Syntax</span></span>  
  
```cpp  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de44e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="de44e-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="de44e-108">pro Hodnota výčtu CorElementType –, která určuje typ prvku pole.</span><span class="sxs-lookup"><span data-stu-id="de44e-108">[in] A value of the CorElementType enumeration that specifies the element type of the array.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="de44e-109">pro Ukazatel na objekt ICorDebugClass, který určuje třídu prvku.</span><span class="sxs-lookup"><span data-stu-id="de44e-109">[in] A pointer to a ICorDebugClass object that specifies the class of the element.</span></span> <span data-ttu-id="de44e-110">Tato hodnota může být null, pokud je typ prvku primitivní typ.</span><span class="sxs-lookup"><span data-stu-id="de44e-110">This value may be null if the element type is a primitive type.</span></span>  
  
 `rank`  
 <span data-ttu-id="de44e-111">pro Počet rozměrů pole.</span><span class="sxs-lookup"><span data-stu-id="de44e-111">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="de44e-112">V .NET Framework 2,0 musí být tato hodnota 1.</span><span class="sxs-lookup"><span data-stu-id="de44e-112">In the .NET Framework 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="de44e-113">pro Velikost každého rozměru pole v bajtech.</span><span class="sxs-lookup"><span data-stu-id="de44e-113">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="de44e-114">pro Volitelné.</span><span class="sxs-lookup"><span data-stu-id="de44e-114">[in] Optional.</span></span> <span data-ttu-id="de44e-115">Dolní mez každého rozměru pole.</span><span class="sxs-lookup"><span data-stu-id="de44e-115">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="de44e-116">Pokud je tato hodnota vynechána, předpokládá se pro každou dimenzi spodní mez nula.</span><span class="sxs-lookup"><span data-stu-id="de44e-116">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de44e-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de44e-117">Remarks</span></span>  
 <span data-ttu-id="de44e-118">Pole je vždy vytvořeno v doméně aplikace, ve které je vlákno aktuálně prováděno.</span><span class="sxs-lookup"><span data-stu-id="de44e-118">The array is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de44e-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de44e-119">Requirements</span></span>  
 <span data-ttu-id="de44e-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de44e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de44e-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="de44e-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de44e-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="de44e-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de44e-123">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="de44e-123">**.NET Framework Versions:** 1.1, 1.0</span></span>
