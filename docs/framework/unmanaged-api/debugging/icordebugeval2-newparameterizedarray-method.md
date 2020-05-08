---
title: ICorDebugEval2::NewParameterizedArray – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
ms.openlocfilehash: 9d589bfc3093d03d87acb47ade0fc6c972bcd335
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976106"
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="31e75-102">ICorDebugEval2::NewParameterizedArray – metoda</span><span class="sxs-lookup"><span data-stu-id="31e75-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="31e75-103">Přidělí nové pole zadaného typu a dimenzí prvku.</span><span class="sxs-lookup"><span data-stu-id="31e75-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31e75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31e75-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31e75-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31e75-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="31e75-106">pro Ukazatel na objekt ICorDebugType, který představuje typ elementu uloženého v poli.</span><span class="sxs-lookup"><span data-stu-id="31e75-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="31e75-107">pro Počet rozměrů pole.</span><span class="sxs-lookup"><span data-stu-id="31e75-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="31e75-108">V .NET Framework verze 2,0 musí být tato hodnota 1.</span><span class="sxs-lookup"><span data-stu-id="31e75-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="31e75-109">pro Velikost každého rozměru pole v bajtech.</span><span class="sxs-lookup"><span data-stu-id="31e75-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="31e75-110">pro Volitelné.</span><span class="sxs-lookup"><span data-stu-id="31e75-110">[in] Optional.</span></span> <span data-ttu-id="31e75-111">Dolní mez každého rozměru pole.</span><span class="sxs-lookup"><span data-stu-id="31e75-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="31e75-112">Pokud je tato hodnota vynechána, předpokládá se pro každou dimenzi spodní mez nula.</span><span class="sxs-lookup"><span data-stu-id="31e75-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31e75-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31e75-113">Remarks</span></span>  
 <span data-ttu-id="31e75-114">Prvky pole mohou být instancemi obecného typu.</span><span class="sxs-lookup"><span data-stu-id="31e75-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="31e75-115">Pole je vždy vytvořeno v doméně aplikace, ve které je vlákno aktuálně spuštěno.</span><span class="sxs-lookup"><span data-stu-id="31e75-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="31e75-116">V .NET Framework 2,0 hodnota `rank` musí být 1.</span><span class="sxs-lookup"><span data-stu-id="31e75-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31e75-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="31e75-117">Requirements</span></span>  
 <span data-ttu-id="31e75-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31e75-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31e75-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="31e75-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31e75-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="31e75-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31e75-121">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31e75-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
