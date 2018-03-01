---
title: "ICorDebugEval2::NewParameterizedArray – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a605276fac66e395d5663bacff727c235981a868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="e3de6-102">ICorDebugEval2::NewParameterizedArray – metoda</span><span class="sxs-lookup"><span data-stu-id="e3de6-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="e3de6-103">Přiděluje nový pole typu zadaného elementu a dimenze.</span><span class="sxs-lookup"><span data-stu-id="e3de6-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3de6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3de6-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3de6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3de6-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="e3de6-106">[v] Ukazatel na ICorDebugType objekt, který představuje typ elementu uložené v poli.</span><span class="sxs-lookup"><span data-stu-id="e3de6-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="e3de6-107">[v] Počet rozměrů pole.</span><span class="sxs-lookup"><span data-stu-id="e3de6-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="e3de6-108">V rozhraní .NET Framework verze 2.0 tato hodnota musí být 1.</span><span class="sxs-lookup"><span data-stu-id="e3de6-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="e3de6-109">[v] Velikost v bajtech, každá dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="e3de6-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="e3de6-110">[v] Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="e3de6-110">[in] Optional.</span></span> <span data-ttu-id="e3de6-111">Dolní mez Každá dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="e3de6-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="e3de6-112">Pokud tato hodnota je vynechán, předpokládá se, že dolní mez 0 je pro každou dimenzi.</span><span class="sxs-lookup"><span data-stu-id="e3de6-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3de6-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3de6-113">Remarks</span></span>  
 <span data-ttu-id="e3de6-114">Elementy pole může být instance obecného typu.</span><span class="sxs-lookup"><span data-stu-id="e3de6-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="e3de6-115">Toto pole je vytvořen vždy v doméně aplikace, ve které je aktuálně spuštěný vlákno.</span><span class="sxs-lookup"><span data-stu-id="e3de6-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="e3de6-116">V rozhraní .NET Framework 2.0, hodnota `rank` musí být 1.</span><span class="sxs-lookup"><span data-stu-id="e3de6-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3de6-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e3de6-117">Requirements</span></span>  
 <span data-ttu-id="e3de6-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3de6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3de6-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3de6-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3de6-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3de6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3de6-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3de6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
