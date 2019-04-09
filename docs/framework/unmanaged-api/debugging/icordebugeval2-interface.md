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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3767368c9da8c97cd081787c0945a15552a1da46
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092666"
---
# <a name="icordebugeval2-interface"></a><span data-ttu-id="7ca15-102">ICorDebugEval2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ca15-102">ICorDebugEval2 Interface</span></span>

<span data-ttu-id="7ca15-103">Rozšiřuje "ICorDebugEval" k poskytování podpory pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="7ca15-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ca15-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7ca15-104">Methods</span></span>  
  
|<span data-ttu-id="7ca15-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7ca15-105">Method</span></span>|<span data-ttu-id="7ca15-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7ca15-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ca15-107">CallParameterizedFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="7ca15-107">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="7ca15-108">Nastavuje volání zadaného "ICorDebugFunction", které mohou být vnořené uvnitř typu, jejíž konstruktor přijímá parametry typu nebo samotné trvat parametry typu.</span><span class="sxs-lookup"><span data-stu-id="7ca15-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="7ca15-109">CreateValueForType – metoda</span><span class="sxs-lookup"><span data-stu-id="7ca15-109">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="7ca15-110">Získá ukazatel na novou "ICorDebugValue" zadaného typu, s počáteční hodnotou null nebo nula.</span><span class="sxs-lookup"><span data-stu-id="7ca15-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="7ca15-111">NewParameterizedArray – metoda</span><span class="sxs-lookup"><span data-stu-id="7ca15-111">NewParameterizedArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="7ca15-112">Přidělí nové pole typu zadaného elementu a dimenze.</span><span class="sxs-lookup"><span data-stu-id="7ca15-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="7ca15-113">NewParameterizedObject – metoda</span><span class="sxs-lookup"><span data-stu-id="7ca15-113">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="7ca15-114">Vytvoří nový objekt typ s parametry a volání metody konstruktoru objektu.</span><span class="sxs-lookup"><span data-stu-id="7ca15-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="7ca15-115">NewParameterizedObjectNoConstructor – metoda</span><span class="sxs-lookup"><span data-stu-id="7ca15-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="7ca15-116">Vytvoří nový objekt typ s parametry ze zadané třídy bez pokusu o volání metody konstruktoru</span><span class="sxs-lookup"><span data-stu-id="7ca15-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="7ca15-117">NewStringWithLength – metoda</span><span class="sxs-lookup"><span data-stu-id="7ca15-117">NewStringWithLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="7ca15-118">Vytvoří nového řetězce zadané délky se zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="7ca15-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="7ca15-119">RudeAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="7ca15-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|<span data-ttu-id="7ca15-120">Zruší výpočet, který tato `ICorDebugEval2` v tuto chvíli provádí.</span><span class="sxs-lookup"><span data-stu-id="7ca15-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ca15-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ca15-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ca15-122">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="7ca15-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ca15-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ca15-123">Requirements</span></span>  
 <span data-ttu-id="7ca15-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ca15-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ca15-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ca15-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ca15-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ca15-126">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7ca15-127">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7ca15-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7ca15-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ca15-128">See also</span></span>

- [<span data-ttu-id="7ca15-129">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ca15-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
