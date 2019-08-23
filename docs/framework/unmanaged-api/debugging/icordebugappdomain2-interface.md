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
ms.openlocfilehash: 63772c6642cc6f7f96a375beab4f7ef1b4884139
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959849"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="2b5b6-102">ICorDebugAppDomain2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b5b6-102">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="2b5b6-103">Poskytuje metody pro práci s poli, ukazateli, ukazateli na funkci a typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="2b5b6-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="2b5b6-104">Toto rozhraní je rozšířením rozhraní ICorDebugAppDomain.</span><span class="sxs-lookup"><span data-stu-id="2b5b6-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2b5b6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2b5b6-105">Methods</span></span>  
  
|<span data-ttu-id="2b5b6-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="2b5b6-106">Method</span></span>|<span data-ttu-id="2b5b6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2b5b6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2b5b6-108">GetArrayOrPointerType – metoda</span><span class="sxs-lookup"><span data-stu-id="2b5b6-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="2b5b6-109">Získá pole zadaného typu nebo ukazatel nebo odkaz na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="2b5b6-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="2b5b6-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="2b5b6-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="2b5b6-111">Získá ukazatel na funkci, která má daný podpis.</span><span class="sxs-lookup"><span data-stu-id="2b5b6-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b5b6-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b5b6-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b5b6-113">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="2b5b6-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b5b6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b5b6-114">Requirements</span></span>  
 <span data-ttu-id="2b5b6-115">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b5b6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b5b6-116">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2b5b6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b5b6-117">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b5b6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b5b6-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b5b6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b5b6-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b5b6-119">See also</span></span>

- [<span data-ttu-id="2b5b6-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2b5b6-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
