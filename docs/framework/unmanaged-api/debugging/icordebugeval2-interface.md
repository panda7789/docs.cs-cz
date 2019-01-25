---
title: ICorDebugEval2 – rozhraní 1
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
ms.openlocfilehash: 7c50dc8e40b6565ae1bf3a5d83f4deb80d2bf0a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712980"
---
# <a name="icordebugeval2-interface1"></a><span data-ttu-id="1e1c2-102">ICorDebugEval2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="1e1c2-102">ICorDebugEval2 Interface1</span></span>
<span data-ttu-id="1e1c2-103">Rozšiřuje "ICorDebugEval" k poskytování podpory pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="1e1c2-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1e1c2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1e1c2-104">Methods</span></span>  
  
|<span data-ttu-id="1e1c2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1e1c2-105">Method</span></span>|<span data-ttu-id="1e1c2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1e1c2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e1c2-107">CallParameterizedFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="1e1c2-107">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="1e1c2-108">Nastavuje volání zadaného "ICorDebugFunction", které mohou být vnořené uvnitř typu, jejíž konstruktor přijímá parametry typu nebo samotné trvat parametry typu.</span><span class="sxs-lookup"><span data-stu-id="1e1c2-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="1e1c2-109">CreateValueForType – metoda</span><span class="sxs-lookup"><span data-stu-id="1e1c2-109">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="1e1c2-110">Získá ukazatel na novou "ICorDebugValue" zadaného typu, s počáteční hodnotou null nebo nula.</span><span class="sxs-lookup"><span data-stu-id="1e1c2-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="1e1c2-111">NewParameterizedArray – metoda</span><span class="sxs-lookup"><span data-stu-id="1e1c2-111">NewParameterizedArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="1e1c2-112">Přidělí nové pole typu zadaného elementu a dimenze.</span><span class="sxs-lookup"><span data-stu-id="1e1c2-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="1e1c2-113">NewParameterizedObject – metoda</span><span class="sxs-lookup"><span data-stu-id="1e1c2-113">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="1e1c2-114">Vytvoří nový objekt typ s parametry a volání metody konstruktoru objektu.</span><span class="sxs-lookup"><span data-stu-id="1e1c2-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="1e1c2-115">NewParameterizedObjectNoConstructor – metoda</span><span class="sxs-lookup"><span data-stu-id="1e1c2-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="1e1c2-116">Vytvoří nový objekt typ s parametry ze zadané třídy bez pokusu o volání metody konstruktoru</span><span class="sxs-lookup"><span data-stu-id="1e1c2-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="1e1c2-117">NewStringWithLength – metoda</span><span class="sxs-lookup"><span data-stu-id="1e1c2-117">NewStringWithLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="1e1c2-118">Vytvoří nového řetězce zadané délky se zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="1e1c2-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="1e1c2-119">RudeAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="1e1c2-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|<span data-ttu-id="1e1c2-120">Zruší výpočet, který tato `ICorDebugEval2` v tuto chvíli provádí.</span><span class="sxs-lookup"><span data-stu-id="1e1c2-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e1c2-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1e1c2-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e1c2-122">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="1e1c2-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e1c2-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1e1c2-123">Requirements</span></span>  
 <span data-ttu-id="1e1c2-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e1c2-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e1c2-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e1c2-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e1c2-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e1c2-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e1c2-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e1c2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e1c2-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e1c2-128">See also</span></span>
- [<span data-ttu-id="1e1c2-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="1e1c2-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
