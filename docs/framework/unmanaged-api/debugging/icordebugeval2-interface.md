---
title: ICorDebugEval2 – rozhraní
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
ms.openlocfilehash: b597d95b5b25e5ebf04fac48e4f3fda312a9594c
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976119"
---
# <a name="icordebugeval2-interface"></a><span data-ttu-id="6d7d1-102">ICorDebugEval2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6d7d1-102">ICorDebugEval2 Interface</span></span>

<span data-ttu-id="6d7d1-103">Rozšiřuje "ICorDebugEval", aby poskytovala podporu pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="6d7d1-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d7d1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6d7d1-104">Methods</span></span>  
  
|<span data-ttu-id="6d7d1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6d7d1-105">Method</span></span>|<span data-ttu-id="6d7d1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6d7d1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d7d1-107">CallParameterizedFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="6d7d1-107">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="6d7d1-108">Nastaví volání zadaného "ICorDebugFunction", která může být vnořena do typu, jehož konstruktor přijímá parametry typu, nebo může sám převzít parametry typu.</span><span class="sxs-lookup"><span data-stu-id="6d7d1-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="6d7d1-109">CreateValueForType – metoda</span><span class="sxs-lookup"><span data-stu-id="6d7d1-109">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="6d7d1-110">Získá ukazatel na nový "ICorDebugValue" zadaného typu s počáteční hodnotou null nebo nula.</span><span class="sxs-lookup"><span data-stu-id="6d7d1-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="6d7d1-111">NewParameterizedArray – metoda</span><span class="sxs-lookup"><span data-stu-id="6d7d1-111">NewParameterizedArray Method</span></span>](icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="6d7d1-112">Přidělí nové pole zadaného typu a dimenzí prvku.</span><span class="sxs-lookup"><span data-stu-id="6d7d1-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="6d7d1-113">NewParameterizedObject – metoda</span><span class="sxs-lookup"><span data-stu-id="6d7d1-113">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="6d7d1-114">Vytvoří instanci nového parametrizovaného typu objektu a zavolá metodu konstruktoru objektu.</span><span class="sxs-lookup"><span data-stu-id="6d7d1-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="6d7d1-115">NewParameterizedObjectNoConstructor – metoda</span><span class="sxs-lookup"><span data-stu-id="6d7d1-115">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="6d7d1-116">Vytvoří instanci nového parametrizovaného typu objektu zadané třídy bez pokusu o volání metody konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="6d7d1-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="6d7d1-117">NewStringWithLength – metoda</span><span class="sxs-lookup"><span data-stu-id="6d7d1-117">NewStringWithLength Method</span></span>](icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="6d7d1-118">Vytvoří nový řetězec o zadané délce se zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="6d7d1-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="6d7d1-119">RudeAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="6d7d1-119">RudeAbort Method</span></span>](icordebugeval2-rudeabort-method.md)|<span data-ttu-id="6d7d1-120">Přeruší výpočet, který `ICorDebugEval2` právě provádí.</span><span class="sxs-lookup"><span data-stu-id="6d7d1-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d7d1-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d7d1-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d7d1-122">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="6d7d1-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d7d1-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d7d1-123">Requirements</span></span>  
 <span data-ttu-id="6d7d1-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d7d1-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d7d1-125">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6d7d1-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d7d1-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6d7d1-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d7d1-127">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d7d1-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d7d1-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d7d1-128">See also</span></span>

- [<span data-ttu-id="6d7d1-129">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6d7d1-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
