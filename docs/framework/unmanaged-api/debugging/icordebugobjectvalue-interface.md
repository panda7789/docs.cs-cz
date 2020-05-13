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
ms.openlocfilehash: 603ab20b57dc4ba736b0342797d0be649a5bebc4
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207482"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="8e408-102">ICorDebugObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e408-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="8e408-103">Podtřída "ICorDebugValue", která představuje hodnotu, která obsahuje objekt.</span><span class="sxs-lookup"><span data-stu-id="8e408-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8e408-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8e408-104">Methods</span></span>  
  
|<span data-ttu-id="8e408-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8e408-105">Method</span></span>|<span data-ttu-id="8e408-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8e408-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8e408-107">GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="8e408-107">GetClass Method</span></span>](icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="8e408-108">Získá ukazatel rozhraní modulu CLR (Common Language Runtime) <xref:System.Type> objektu, na který `ICorDebugObjectValue` odkazují.</span><span class="sxs-lookup"><span data-stu-id="8e408-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="8e408-109">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="8e408-109">GetContext Method</span></span>](icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="8e408-110">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="8e408-110">Not implemented.</span></span>|  
|[<span data-ttu-id="8e408-111">GetFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="8e408-111">GetFieldValue Method</span></span>](icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="8e408-112">Získá ukazatel rozhraní na [ICorDebugValue](icordebugvalue-interface.md) , který představuje hodnotu zadaného pole zadané třídy.</span><span class="sxs-lookup"><span data-stu-id="8e408-112">Gets an interface pointer to an [ICorDebugValue](icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="8e408-113">GetManagedCopy – metoda</span><span class="sxs-lookup"><span data-stu-id="8e408-113">GetManagedCopy Method</span></span>](icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="8e408-114">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="8e408-114">Obsolete.</span></span> <span data-ttu-id="8e408-115">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="8e408-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="8e408-116">GetVirtualMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="8e408-116">GetVirtualMethod Method</span></span>](icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="8e408-117">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="8e408-117">Not implemented.</span></span>|  
|[<span data-ttu-id="8e408-118">IsValueClass – metoda</span><span class="sxs-lookup"><span data-stu-id="8e408-118">IsValueClass Method</span></span>](icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="8e408-119">Získá hodnotu, která označuje, zda je objekt, na který odkazuje, `ICorDebugObjectValue` typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8e408-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="8e408-120">SetFromManagedCopy – metoda</span><span class="sxs-lookup"><span data-stu-id="8e408-120">SetFromManagedCopy Method</span></span>](icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="8e408-121">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="8e408-121">Obsolete.</span></span> <span data-ttu-id="8e408-122">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="8e408-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e408-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e408-123">Remarks</span></span>  
 <span data-ttu-id="8e408-124">`ICorDebugObjectValue`Zůstane platná, dokud se proces, který se právě ladí, nepokračuje.</span><span class="sxs-lookup"><span data-stu-id="8e408-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e408-125">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="8e408-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e408-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8e408-126">Requirements</span></span>  
 <span data-ttu-id="8e408-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e408-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e408-128">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8e408-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e408-129">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8e408-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e408-130">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e408-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e408-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e408-131">See also</span></span>

- [<span data-ttu-id="8e408-132">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e408-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
