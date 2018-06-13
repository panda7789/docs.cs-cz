---
title: ICorDebugObjectValue Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ddf3b60ed595aff8bc81d0bb59675fd1db12f7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422410"
---
# <a name="icordebugobjectvalue-interface1"></a><span data-ttu-id="d30a2-102">ICorDebugObjectValue Interface1</span><span class="sxs-lookup"><span data-stu-id="d30a2-102">ICorDebugObjectValue Interface1</span></span>
<span data-ttu-id="d30a2-103">Podtřídou třídy "ICorDebugValue", který představuje hodnotu, která obsahuje objekt.</span><span class="sxs-lookup"><span data-stu-id="d30a2-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d30a2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d30a2-104">Methods</span></span>  
  
|<span data-ttu-id="d30a2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d30a2-105">Method</span></span>|<span data-ttu-id="d30a2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d30a2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d30a2-107">GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="d30a2-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="d30a2-108">Získá ukazatele rozhraní do common language runtime (CLR) <xref:System.Type> objektu, který tato `ICorDebugObjectValue` odkazy.</span><span class="sxs-lookup"><span data-stu-id="d30a2-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="d30a2-109">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="d30a2-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="d30a2-110">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="d30a2-110">Not implemented.</span></span>|  
|[<span data-ttu-id="d30a2-111">GetFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="d30a2-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="d30a2-112">Získá ukazatele rozhraní k [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) představující hodnotu zadaného pole pro zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="d30a2-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="d30a2-113">GetManagedCopy – metoda</span><span class="sxs-lookup"><span data-stu-id="d30a2-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="d30a2-114">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="d30a2-114">Obsolete.</span></span> <span data-ttu-id="d30a2-115">Tato metoda není volána.</span><span class="sxs-lookup"><span data-stu-id="d30a2-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="d30a2-116">GetVirtualMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="d30a2-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="d30a2-117">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="d30a2-117">Not implemented.</span></span>|  
|[<span data-ttu-id="d30a2-118">IsValueClass – metoda</span><span class="sxs-lookup"><span data-stu-id="d30a2-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="d30a2-119">Získá hodnotu, která určuje, zda objekt odkazuje toto `ICorDebugObjectValue` je typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d30a2-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="d30a2-120">SetFromManagedCopy – metoda</span><span class="sxs-lookup"><span data-stu-id="d30a2-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="d30a2-121">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="d30a2-121">Obsolete.</span></span> <span data-ttu-id="d30a2-122">Tato metoda není volána.</span><span class="sxs-lookup"><span data-stu-id="d30a2-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d30a2-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d30a2-123">Remarks</span></span>  
 <span data-ttu-id="d30a2-124">`ICorDebugObjectValue` Zůstane platná, dokud proces laděné pokračuje.</span><span class="sxs-lookup"><span data-stu-id="d30a2-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d30a2-125">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="d30a2-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d30a2-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d30a2-126">Requirements</span></span>  
 <span data-ttu-id="d30a2-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d30a2-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d30a2-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d30a2-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d30a2-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d30a2-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d30a2-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d30a2-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d30a2-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="d30a2-131">See Also</span></span>  
 [<span data-ttu-id="d30a2-132">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d30a2-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 
