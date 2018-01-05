---
title: ICorDebugEval2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2
helpviewer_keywords: ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac816d2b2dce6c9c76813bf4247bac7ca40da5f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2-interface1"></a><span data-ttu-id="0429d-102">ICorDebugEval2 Interface1</span><span class="sxs-lookup"><span data-stu-id="0429d-102">ICorDebugEval2 Interface1</span></span>
<span data-ttu-id="0429d-103">Rozšiřuje "ICorDebugEval" kvůli zajištění podpory pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="0429d-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0429d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0429d-104">Methods</span></span>  
  
|<span data-ttu-id="0429d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0429d-105">Method</span></span>|<span data-ttu-id="0429d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0429d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0429d-107">CallParameterizedFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="0429d-107">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="0429d-108">Nastaví volání zadaný "ICorDebugFunction", který může být vnořena ve typu jehož konstruktor přijímá parametry typu nebo sám přijmout parametry typu.</span><span class="sxs-lookup"><span data-stu-id="0429d-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="0429d-109">CreateValueForType – metoda</span><span class="sxs-lookup"><span data-stu-id="0429d-109">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="0429d-110">Získá ukazatel nové "ICorDebugValue" zadaného typu, s počáteční hodnotou null nebo nula.</span><span class="sxs-lookup"><span data-stu-id="0429d-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="0429d-111">NewParameterizedArray – metoda</span><span class="sxs-lookup"><span data-stu-id="0429d-111">NewParameterizedArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="0429d-112">Přiděluje nový pole typu zadaného elementu a dimenze.</span><span class="sxs-lookup"><span data-stu-id="0429d-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="0429d-113">NewParameterizedObject – metoda</span><span class="sxs-lookup"><span data-stu-id="0429d-113">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="0429d-114">Vytvoří nový objekt parametrizované typu a volá konstruktor metodu objektu.</span><span class="sxs-lookup"><span data-stu-id="0429d-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="0429d-115">NewParameterizedObjectNoConstructor – metoda</span><span class="sxs-lookup"><span data-stu-id="0429d-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="0429d-116">Vytvoří nový objekt parametrizované typ zadané třídy bez pokus o volání metody konstruktoru</span><span class="sxs-lookup"><span data-stu-id="0429d-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="0429d-117">NewStringWithLength – metoda</span><span class="sxs-lookup"><span data-stu-id="0429d-117">NewStringWithLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="0429d-118">Vytvoří nový řetězec určené délky zadaný obsah.</span><span class="sxs-lookup"><span data-stu-id="0429d-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="0429d-119">RudeAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="0429d-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|<span data-ttu-id="0429d-120">Zruší výpočet které tento `ICorDebugEval2` právě provádí.</span><span class="sxs-lookup"><span data-stu-id="0429d-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0429d-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0429d-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0429d-122">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="0429d-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0429d-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0429d-123">Requirements</span></span>  
 <span data-ttu-id="0429d-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0429d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0429d-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0429d-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0429d-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0429d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0429d-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0429d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0429d-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="0429d-128">See Also</span></span>  
 [<span data-ttu-id="0429d-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0429d-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
