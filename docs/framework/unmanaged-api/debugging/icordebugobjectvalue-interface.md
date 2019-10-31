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
ms.openlocfilehash: b782207503a2c3f739a30f68d509e6b481d2b6a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129756"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="b14d9-102">ICorDebugObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b14d9-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="b14d9-103">Podtřída "ICorDebugValue", která představuje hodnotu, která obsahuje objekt.</span><span class="sxs-lookup"><span data-stu-id="b14d9-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b14d9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b14d9-104">Methods</span></span>  
  
|<span data-ttu-id="b14d9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b14d9-105">Method</span></span>|<span data-ttu-id="b14d9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b14d9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b14d9-107">GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="b14d9-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="b14d9-108">Získá ukazatel rozhraní modulu CLR (Common Language Runtime) <xref:System.Type> objektu, na který odkazuje tento `ICorDebugObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="b14d9-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="b14d9-109">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="b14d9-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="b14d9-110">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="b14d9-110">Not implemented.</span></span>|  
|[<span data-ttu-id="b14d9-111">GetFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="b14d9-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="b14d9-112">Získá ukazatel rozhraní na [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) , který představuje hodnotu zadaného pole zadané třídy.</span><span class="sxs-lookup"><span data-stu-id="b14d9-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="b14d9-113">GetManagedCopy – metoda</span><span class="sxs-lookup"><span data-stu-id="b14d9-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="b14d9-114">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="b14d9-114">Obsolete.</span></span> <span data-ttu-id="b14d9-115">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="b14d9-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="b14d9-116">GetVirtualMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="b14d9-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="b14d9-117">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="b14d9-117">Not implemented.</span></span>|  
|[<span data-ttu-id="b14d9-118">IsValueClass – metoda</span><span class="sxs-lookup"><span data-stu-id="b14d9-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="b14d9-119">Získá hodnotu, která označuje, zda je objekt, na který odkazuje tento `ICorDebugObjectValue` hodnotový typ.</span><span class="sxs-lookup"><span data-stu-id="b14d9-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="b14d9-120">SetFromManagedCopy – metoda</span><span class="sxs-lookup"><span data-stu-id="b14d9-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="b14d9-121">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="b14d9-121">Obsolete.</span></span> <span data-ttu-id="b14d9-122">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="b14d9-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b14d9-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b14d9-123">Remarks</span></span>  
 <span data-ttu-id="b14d9-124">`ICorDebugObjectValue` zůstává platný, dokud proces, který se právě ladí, nebude pokračovat.</span><span class="sxs-lookup"><span data-stu-id="b14d9-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b14d9-125">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="b14d9-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b14d9-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b14d9-126">Requirements</span></span>  
 <span data-ttu-id="b14d9-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b14d9-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b14d9-128">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b14d9-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b14d9-129">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b14d9-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b14d9-130">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b14d9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b14d9-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b14d9-131">See also</span></span>

- [<span data-ttu-id="b14d9-132">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b14d9-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
