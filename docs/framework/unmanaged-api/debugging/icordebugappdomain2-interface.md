---
title: ICorDebugAppDomain2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2
helpviewer_keywords:
- ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c6ef901f43cd6568f17657ed8e58bc2cc2cc0a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922262"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="b4728-102">ICorDebugAppDomain2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4728-102">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="b4728-103">Poskytuje metody pro práci s pole, odkazy, ukazatele na funkce a typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="b4728-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="b4728-104">Toto rozhraní je rozšířením icordebugappdomain – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b4728-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4728-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b4728-105">Methods</span></span>  
  
|<span data-ttu-id="b4728-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b4728-106">Method</span></span>|<span data-ttu-id="b4728-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b4728-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4728-108">GetArrayOrPointerType – metoda</span><span class="sxs-lookup"><span data-stu-id="b4728-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="b4728-109">Získá pole objektů zadaného typu nebo ukazatel nebo odkaz na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="b4728-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="b4728-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="b4728-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="b4728-111">Získá ukazatel na funkci, která má daným podpisem.</span><span class="sxs-lookup"><span data-stu-id="b4728-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4728-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4728-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4728-113">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="b4728-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4728-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4728-114">Requirements</span></span>  
 <span data-ttu-id="b4728-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4728-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4728-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4728-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4728-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4728-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4728-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4728-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4728-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4728-119">See also</span></span>

- [<span data-ttu-id="b4728-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b4728-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
