---
title: ICorDebugAppDomain – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
ms.openlocfilehash: 140e67417f4fad552f972a93bc8c620b440b2370
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895176"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="527bb-102">ICorDebugAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="527bb-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="527bb-103">Poskytuje metody pro ladění domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="527bb-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="527bb-104">Toto rozhraní je podtřídou třídy ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="527bb-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="527bb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="527bb-105">Methods</span></span>  
  
|<span data-ttu-id="527bb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="527bb-106">Method</span></span>|<span data-ttu-id="527bb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="527bb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="527bb-108">Attach – metoda</span><span class="sxs-lookup"><span data-stu-id="527bb-108">Attach Method</span></span>](icordebugappdomain-attach-method.md)|<span data-ttu-id="527bb-109">Připojí ladicí program k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="527bb-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="527bb-110">EnumerateAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="527bb-110">EnumerateAssemblies Method</span></span>](icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="527bb-111">Získá enumerátor pro sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="527bb-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="527bb-112">EnumerateBreakpoints – metoda</span><span class="sxs-lookup"><span data-stu-id="527bb-112">EnumerateBreakpoints Method</span></span>](icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="527bb-113">Získá enumerátor pro všechny aktivní zarážky v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="527bb-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="527bb-114">EnumerateSteppers – metoda</span><span class="sxs-lookup"><span data-stu-id="527bb-114">EnumerateSteppers Method</span></span>](icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="527bb-115">Získá enumerátor pro všechny aktivní prvky krokování v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="527bb-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="527bb-116">Metoda getId –</span><span class="sxs-lookup"><span data-stu-id="527bb-116">GetId Method</span></span>](icordebugappdomain-getid-method.md)|<span data-ttu-id="527bb-117">Získá jedinečné ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="527bb-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="527bb-118">GetModuleFromMetaDataInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="527bb-118">GetModuleFromMetaDataInterface Method</span></span>](icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="527bb-119">Získá objekt ICorDebugModule se zadaným rozhraním metadat.</span><span class="sxs-lookup"><span data-stu-id="527bb-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="527bb-120">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="527bb-120">GetName Method</span></span>](icordebugappdomain-getname-method.md)|<span data-ttu-id="527bb-121">Získá název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="527bb-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="527bb-122">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="527bb-122">GetObject Method</span></span>](icordebugappdomain-getobject-method.md)|<span data-ttu-id="527bb-123">Načte ukazatel rozhraní do aplikační domény modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="527bb-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="527bb-124">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="527bb-124">GetProcess Method</span></span>](icordebugappdomain-getprocess-method.md)|<span data-ttu-id="527bb-125">Získá proces obsahující doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="527bb-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="527bb-126">IsAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="527bb-126">IsAttached Method</span></span>](icordebugappdomain-isattached-method.md)|<span data-ttu-id="527bb-127">Určuje, zda je ladicí program připojen k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="527bb-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="527bb-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="527bb-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="527bb-129">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="527bb-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="527bb-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="527bb-130">Requirements</span></span>  
 <span data-ttu-id="527bb-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="527bb-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="527bb-132">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="527bb-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="527bb-133">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="527bb-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="527bb-134">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="527bb-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="527bb-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="527bb-135">See also</span></span>

- [<span data-ttu-id="527bb-136">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="527bb-136">Debugging Interfaces</span></span>](debugging-interfaces.md)
