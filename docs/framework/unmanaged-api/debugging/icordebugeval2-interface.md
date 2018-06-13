---
title: ICorDebugEval2 Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da4364e132e2a9d578a761eea77d0dfc8d0b92aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418233"
---
# <a name="icordebugeval2-interface1"></a><span data-ttu-id="9a918-102">ICorDebugEval2 Interface1</span><span class="sxs-lookup"><span data-stu-id="9a918-102">ICorDebugEval2 Interface1</span></span>
<span data-ttu-id="9a918-103">Rozšiřuje "ICorDebugEval" kvůli zajištění podpory pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="9a918-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9a918-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9a918-104">Methods</span></span>  
  
|<span data-ttu-id="9a918-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9a918-105">Method</span></span>|<span data-ttu-id="9a918-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9a918-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9a918-107">CallParameterizedFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="9a918-107">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="9a918-108">Nastaví volání zadaný "ICorDebugFunction", který může být vnořena ve typu jehož konstruktor přijímá parametry typu nebo sám přijmout parametry typu.</span><span class="sxs-lookup"><span data-stu-id="9a918-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="9a918-109">CreateValueForType – metoda</span><span class="sxs-lookup"><span data-stu-id="9a918-109">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="9a918-110">Získá ukazatel nové "ICorDebugValue" zadaného typu, s počáteční hodnotou null nebo nula.</span><span class="sxs-lookup"><span data-stu-id="9a918-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="9a918-111">NewParameterizedArray – metoda</span><span class="sxs-lookup"><span data-stu-id="9a918-111">NewParameterizedArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="9a918-112">Přiděluje nový pole typu zadaného elementu a dimenze.</span><span class="sxs-lookup"><span data-stu-id="9a918-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="9a918-113">NewParameterizedObject – metoda</span><span class="sxs-lookup"><span data-stu-id="9a918-113">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="9a918-114">Vytvoří nový objekt parametrizované typu a volá konstruktor metodu objektu.</span><span class="sxs-lookup"><span data-stu-id="9a918-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="9a918-115">NewParameterizedObjectNoConstructor – metoda</span><span class="sxs-lookup"><span data-stu-id="9a918-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="9a918-116">Vytvoří nový objekt parametrizované typ zadané třídy bez pokus o volání metody konstruktoru</span><span class="sxs-lookup"><span data-stu-id="9a918-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="9a918-117">NewStringWithLength – metoda</span><span class="sxs-lookup"><span data-stu-id="9a918-117">NewStringWithLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="9a918-118">Vytvoří nový řetězec určené délky zadaný obsah.</span><span class="sxs-lookup"><span data-stu-id="9a918-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="9a918-119">RudeAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="9a918-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|<span data-ttu-id="9a918-120">Zruší výpočet které tento `ICorDebugEval2` právě provádí.</span><span class="sxs-lookup"><span data-stu-id="9a918-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a918-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a918-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a918-122">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="9a918-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a918-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9a918-123">Requirements</span></span>  
 <span data-ttu-id="9a918-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a918-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a918-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a918-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a918-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a918-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a918-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a918-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a918-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a918-128">See Also</span></span>  
 [<span data-ttu-id="9a918-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9a918-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
