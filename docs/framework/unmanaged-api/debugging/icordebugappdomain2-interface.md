---
title: "Icordebugappdomain2 – Interface1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain2
helpviewer_keywords: ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ebd1e504cbf2f74ad82e7fea6b6c3f355a1bda34
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain2-interface1"></a><span data-ttu-id="5fd2c-102">Icordebugappdomain2 – Interface1</span><span class="sxs-lookup"><span data-stu-id="5fd2c-102">ICorDebugAppDomain2 Interface1</span></span>
<span data-ttu-id="5fd2c-103">Poskytuje metody pro práci s pole, ukazatelů, ukazatelů na funkce a odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="5fd2c-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="5fd2c-104">Toto rozhraní je rozšíření rozhraní ICorDebugAppDomain.</span><span class="sxs-lookup"><span data-stu-id="5fd2c-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5fd2c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5fd2c-105">Methods</span></span>  
  
|<span data-ttu-id="5fd2c-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5fd2c-106">Method</span></span>|<span data-ttu-id="5fd2c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5fd2c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5fd2c-108">Getarrayorpointertype – metoda</span><span class="sxs-lookup"><span data-stu-id="5fd2c-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="5fd2c-109">Získá zadaný typ, nebo ukazatel nebo odkaz na zadaný typ pole.</span><span class="sxs-lookup"><span data-stu-id="5fd2c-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="5fd2c-110">Getfunctionpointertype –</span><span class="sxs-lookup"><span data-stu-id="5fd2c-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="5fd2c-111">Získá ukazatel na funkci, která má daný podpis.</span><span class="sxs-lookup"><span data-stu-id="5fd2c-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fd2c-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5fd2c-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fd2c-113">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="5fd2c-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fd2c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5fd2c-114">Requirements</span></span>  
 <span data-ttu-id="5fd2c-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fd2c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fd2c-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fd2c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fd2c-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fd2c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fd2c-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fd2c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fd2c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="5fd2c-119">See Also</span></span>  
 [<span data-ttu-id="5fd2c-120">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="5fd2c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
