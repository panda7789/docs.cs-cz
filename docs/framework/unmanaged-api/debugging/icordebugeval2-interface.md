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
ms.openlocfilehash: e69b32430651edd0222db874e2659bd959f89549
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788713"
---
# <a name="icordebugeval2-interface"></a><span data-ttu-id="dd4b7-102">ICorDebugEval2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd4b7-102">ICorDebugEval2 Interface</span></span>

<span data-ttu-id="dd4b7-103">Rozšiřuje "ICorDebugEval", aby poskytovala podporu pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="dd4b7-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dd4b7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dd4b7-104">Methods</span></span>  
  
|<span data-ttu-id="dd4b7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dd4b7-105">Method</span></span>|<span data-ttu-id="dd4b7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="dd4b7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dd4b7-107">CallParameterizedFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="dd4b7-107">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="dd4b7-108">Nastaví volání zadaného "ICorDebugFunction", která může být vnořena do typu, jehož konstruktor přijímá parametry typu, nebo může sám převzít parametry typu.</span><span class="sxs-lookup"><span data-stu-id="dd4b7-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="dd4b7-109">CreateValueForType – metoda</span><span class="sxs-lookup"><span data-stu-id="dd4b7-109">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="dd4b7-110">Získá ukazatel na nový "ICorDebugValue" zadaného typu s počáteční hodnotou null nebo nula.</span><span class="sxs-lookup"><span data-stu-id="dd4b7-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="dd4b7-111">NewParameterizedArray – metoda</span><span class="sxs-lookup"><span data-stu-id="dd4b7-111">NewParameterizedArray Method</span></span>](icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="dd4b7-112">Přidělí nové pole zadaného typu a dimenzí prvku.</span><span class="sxs-lookup"><span data-stu-id="dd4b7-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="dd4b7-113">NewParameterizedObject – metoda</span><span class="sxs-lookup"><span data-stu-id="dd4b7-113">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="dd4b7-114">Vytvoří instanci nového parametrizovaného typu objektu a zavolá metodu konstruktoru objektu.</span><span class="sxs-lookup"><span data-stu-id="dd4b7-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="dd4b7-115">NewParameterizedObjectNoConstructor – metoda</span><span class="sxs-lookup"><span data-stu-id="dd4b7-115">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="dd4b7-116">Vytvoří instanci nového parametrizovaného typu objektu zadané třídy bez pokusu o volání metody konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="dd4b7-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="dd4b7-117">NewStringWithLength – metoda</span><span class="sxs-lookup"><span data-stu-id="dd4b7-117">NewStringWithLength Method</span></span>](icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="dd4b7-118">Vytvoří nový řetězec o zadané délce se zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="dd4b7-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="dd4b7-119">RudeAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="dd4b7-119">RudeAbort Method</span></span>](icordebugeval2-rudeabort-method.md)|<span data-ttu-id="dd4b7-120">Přeruší výpočet, který tato `ICorDebugEval2` v tuto chvíli provádí.</span><span class="sxs-lookup"><span data-stu-id="dd4b7-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd4b7-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd4b7-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd4b7-122">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="dd4b7-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd4b7-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd4b7-123">Requirements</span></span>  
 <span data-ttu-id="dd4b7-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd4b7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd4b7-125">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dd4b7-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd4b7-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dd4b7-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd4b7-127">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd4b7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd4b7-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd4b7-128">See also</span></span>

- [<span data-ttu-id="dd4b7-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dd4b7-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
