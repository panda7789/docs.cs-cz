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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 973f975885bbbf5cbed74adef7b9f4f423c42583
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753652"
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="38bb1-102">ICorDebugEval2::NewParameterizedArray – metoda</span><span class="sxs-lookup"><span data-stu-id="38bb1-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="38bb1-103">Přidělí nové pole typu zadaného elementu a dimenze.</span><span class="sxs-lookup"><span data-stu-id="38bb1-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38bb1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38bb1-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38bb1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38bb1-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="38bb1-106">[in] Ukazatel na objekt ICorDebugType, který představuje typ prvků uložených v poli.</span><span class="sxs-lookup"><span data-stu-id="38bb1-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="38bb1-107">[in] Počet rozměrů pole.</span><span class="sxs-lookup"><span data-stu-id="38bb1-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="38bb1-108">V rozhraní .NET Framework verze 2.0 tato hodnota musí být 1.</span><span class="sxs-lookup"><span data-stu-id="38bb1-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="38bb1-109">[in] Velikost v bajtech každého rozměru pole.</span><span class="sxs-lookup"><span data-stu-id="38bb1-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="38bb1-110">[in] Volitelné.</span><span class="sxs-lookup"><span data-stu-id="38bb1-110">[in] Optional.</span></span> <span data-ttu-id="38bb1-111">Dolní mez každé dimenze matice.</span><span class="sxs-lookup"><span data-stu-id="38bb1-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="38bb1-112">Pokud je tato hodnota vynechána, předpokládá se pro jednotlivé rozměry dolní mez nula.</span><span class="sxs-lookup"><span data-stu-id="38bb1-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38bb1-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38bb1-113">Remarks</span></span>  
 <span data-ttu-id="38bb1-114">Prvky pole mohou být instancí obecného typu.</span><span class="sxs-lookup"><span data-stu-id="38bb1-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="38bb1-115">Pole je vytvořen vždy v aplikační doméně, ve kterém je spuštěn podproces.</span><span class="sxs-lookup"><span data-stu-id="38bb1-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="38bb1-116">V rozhraní .NET Framework 2.0, hodnota `rank` musí být 1.</span><span class="sxs-lookup"><span data-stu-id="38bb1-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38bb1-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38bb1-117">Requirements</span></span>  
 <span data-ttu-id="38bb1-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38bb1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38bb1-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38bb1-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38bb1-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38bb1-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38bb1-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38bb1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
