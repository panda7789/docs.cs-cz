---
title: "Rozhraní ICorDebugProcess6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 222007d03d8ace00f97c01cf2a02f0dc293bbf78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="b7b1e-102">Rozhraní ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="b7b1e-102">ICorDebugProcess6 Interface</span></span>
<span data-ttu-id="b7b1e-103">Logicky rozšiřuje rozhraní ICorDebugProcess k povolení funkcí, jako je například dekódování spravované ladění události, které jsou v událostí výjimek na nativní ladění a rozdělení virtuální modulu kódování.</span><span class="sxs-lookup"><span data-stu-id="b7b1e-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7b1e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b7b1e-104">Methods</span></span>  
  
|<span data-ttu-id="b7b1e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b7b1e-105">Method</span></span>|<span data-ttu-id="b7b1e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b7b1e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7b1e-107">Metoda DecodeEvent</span><span class="sxs-lookup"><span data-stu-id="b7b1e-107">DecodeEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="b7b1e-108">Dekóduje spravované ladění události, které byly zapouzdřené v datové části události ladění speciálního nativní výjimky.</span><span class="sxs-lookup"><span data-stu-id="b7b1e-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="b7b1e-109">Metoda EnableVirtualModuleSplitting</span><span class="sxs-lookup"><span data-stu-id="b7b1e-109">EnableVirtualModuleSplitting Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="b7b1e-110">Povolí nebo zakáže virtuální modulu rozdělení.</span><span class="sxs-lookup"><span data-stu-id="b7b1e-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="b7b1e-111">Getcode – metoda</span><span class="sxs-lookup"><span data-stu-id="b7b1e-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|<span data-ttu-id="b7b1e-112">Získá informace o spravovaného kódu na adrese konkrétního kódu.</span><span class="sxs-lookup"><span data-stu-id="b7b1e-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="b7b1e-113">Metoda GetExportStepInfo</span><span class="sxs-lookup"><span data-stu-id="b7b1e-113">GetExportStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="b7b1e-114">Obsahuje informace o modulu runtime exportované funkce, které umožňují krok prostřednictvím spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="b7b1e-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="b7b1e-115">Metoda MarkDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="b7b1e-115">MarkDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="b7b1e-116">Změní vnitřní stav debugee tak, aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> vrátí metoda v knihovně tříd rozhraní .NET Framework `true`.</span><span class="sxs-lookup"><span data-stu-id="b7b1e-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="b7b1e-117">Metoda ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="b7b1e-117">ProcessStateChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="b7b1e-118">Upozorní [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) kterém proces běží.</span><span class="sxs-lookup"><span data-stu-id="b7b1e-118">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7b1e-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7b1e-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7b1e-120">Rozhraní je k dispozici s .NET Native pouze.</span><span class="sxs-lookup"><span data-stu-id="b7b1e-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="b7b1e-121">Probíhá pokus o volání `QueryInterface` načíst ukazatele rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b7b1e-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7b1e-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7b1e-122">Requirements</span></span>  
 <span data-ttu-id="b7b1e-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7b1e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7b1e-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7b1e-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7b1e-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7b1e-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7b1e-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7b1e-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b1e-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7b1e-127">See Also</span></span>  
 [<span data-ttu-id="b7b1e-128">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7b1e-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b7b1e-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="b7b1e-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
