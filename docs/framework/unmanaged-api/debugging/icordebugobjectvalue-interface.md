---
title: ICorDebugObjectValue – rozhraní
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
ms.openlocfilehash: a4ca59aac075a42294026ad54c5d5dd4dbf7fda4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943339"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="c820e-102">ICorDebugObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c820e-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="c820e-103">Podtřída "ICorDebugValue", která představuje hodnotu, která obsahuje objekt.</span><span class="sxs-lookup"><span data-stu-id="c820e-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c820e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c820e-104">Methods</span></span>  
  
|<span data-ttu-id="c820e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c820e-105">Method</span></span>|<span data-ttu-id="c820e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c820e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c820e-107">GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="c820e-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="c820e-108">Získá ukazatel rozhraní modulu CLR (Common Language Runtime) <xref:System.Type> objektu `ICorDebugObjectValue` , na který odkazují.</span><span class="sxs-lookup"><span data-stu-id="c820e-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="c820e-109">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="c820e-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="c820e-110">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="c820e-110">Not implemented.</span></span>|  
|[<span data-ttu-id="c820e-111">GetFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c820e-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="c820e-112">Získá ukazatel rozhraní na [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) , který představuje hodnotu zadaného pole zadané třídy.</span><span class="sxs-lookup"><span data-stu-id="c820e-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="c820e-113">GetManagedCopy – metoda</span><span class="sxs-lookup"><span data-stu-id="c820e-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="c820e-114">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="c820e-114">Obsolete.</span></span> <span data-ttu-id="c820e-115">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="c820e-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="c820e-116">GetVirtualMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="c820e-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="c820e-117">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="c820e-117">Not implemented.</span></span>|  
|[<span data-ttu-id="c820e-118">IsValueClass – metoda</span><span class="sxs-lookup"><span data-stu-id="c820e-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="c820e-119">Získá hodnotu, která označuje, zda `ICorDebugObjectValue` je objekt, na který odkazuje, typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c820e-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="c820e-120">SetFromManagedCopy – metoda</span><span class="sxs-lookup"><span data-stu-id="c820e-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="c820e-121">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="c820e-121">Obsolete.</span></span> <span data-ttu-id="c820e-122">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="c820e-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c820e-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c820e-123">Remarks</span></span>  
 <span data-ttu-id="c820e-124">`ICorDebugObjectValue` Zůstane platná, dokud se proces, který se právě ladí, nepokračuje.</span><span class="sxs-lookup"><span data-stu-id="c820e-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c820e-125">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="c820e-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c820e-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c820e-126">Requirements</span></span>  
 <span data-ttu-id="c820e-127">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c820e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c820e-128">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c820e-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c820e-129">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c820e-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c820e-130">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c820e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c820e-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c820e-131">See also</span></span>

- [<span data-ttu-id="c820e-132">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c820e-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
