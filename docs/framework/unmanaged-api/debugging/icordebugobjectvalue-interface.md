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
ms.openlocfilehash: 5cd991049c159b96a0f0717b31d6a2834b250f70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631984"
---
# <a name="icordebugobjectvalue-interface1"></a><span data-ttu-id="8d254-102">ICorDebugObjectValue Interface1</span><span class="sxs-lookup"><span data-stu-id="8d254-102">ICorDebugObjectValue Interface1</span></span>
<span data-ttu-id="8d254-103">Podtřída ICorDebugValue"", který představuje hodnotu, která obsahuje objekt.</span><span class="sxs-lookup"><span data-stu-id="8d254-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8d254-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8d254-104">Methods</span></span>  
  
|<span data-ttu-id="8d254-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8d254-105">Method</span></span>|<span data-ttu-id="8d254-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8d254-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8d254-107">GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="8d254-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="8d254-108">Získá ukazatel rozhraní common language runtime (CLR) <xref:System.Type> objektu, který tato `ICorDebugObjectValue` odkazy.</span><span class="sxs-lookup"><span data-stu-id="8d254-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="8d254-109">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="8d254-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="8d254-110">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="8d254-110">Not implemented.</span></span>|  
|[<span data-ttu-id="8d254-111">GetFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="8d254-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="8d254-112">Získá ukazatel rozhraní k [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) , který představuje hodnotu zadaného pole z dané třídy.</span><span class="sxs-lookup"><span data-stu-id="8d254-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="8d254-113">GetManagedCopy – metoda</span><span class="sxs-lookup"><span data-stu-id="8d254-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="8d254-114">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="8d254-114">Obsolete.</span></span> <span data-ttu-id="8d254-115">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="8d254-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="8d254-116">GetVirtualMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="8d254-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="8d254-117">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="8d254-117">Not implemented.</span></span>|  
|[<span data-ttu-id="8d254-118">IsValueClass – metoda</span><span class="sxs-lookup"><span data-stu-id="8d254-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="8d254-119">Získá hodnotu určující, zda objekt odkazovaný tímto objektem `ICorDebugObjectValue` je typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8d254-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="8d254-120">SetFromManagedCopy – metoda</span><span class="sxs-lookup"><span data-stu-id="8d254-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="8d254-121">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="8d254-121">Obsolete.</span></span> <span data-ttu-id="8d254-122">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="8d254-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d254-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d254-123">Remarks</span></span>  
 <span data-ttu-id="8d254-124">`ICorDebugObjectValue` Zůstává v platnosti, dokud se pokračuje se v laděném procesu.</span><span class="sxs-lookup"><span data-stu-id="8d254-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d254-125">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="8d254-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d254-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d254-126">Requirements</span></span>  
 <span data-ttu-id="8d254-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d254-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d254-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d254-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d254-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d254-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d254-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d254-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d254-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d254-131">See also</span></span>
- [<span data-ttu-id="8d254-132">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8d254-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

