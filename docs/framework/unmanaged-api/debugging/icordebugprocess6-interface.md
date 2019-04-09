---
title: Rozhraní ICorDebugProcess6
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 518c6ec99e4062bf8432809d3472baa395017da3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147261"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="2a0dc-102">Rozhraní ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="2a0dc-102">ICorDebugProcess6 Interface</span></span>
<span data-ttu-id="2a0dc-103">Logicky rozšiřuje icordebugprocess – rozhraní k povolení funkcí, jako je například dekódování spravované ladění události, které jsou zakódovány nativní výjimka ladění událostí a rozdělení virtuální modulu.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a0dc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2a0dc-104">Methods</span></span>  
  
|<span data-ttu-id="2a0dc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2a0dc-105">Method</span></span>|<span data-ttu-id="2a0dc-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2a0dc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a0dc-107">DecodeEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="2a0dc-107">DecodeEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="2a0dc-108">Dekóduje spravované ladění události, které byly zapouzdřené v datové části události speciálně nativní výjimka ladění.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="2a0dc-109">EnableVirtualModuleSplitting – metoda</span><span class="sxs-lookup"><span data-stu-id="2a0dc-109">EnableVirtualModuleSplitting Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="2a0dc-110">Povolí nebo zakáže virtuální modulu rozdělení.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="2a0dc-111">GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="2a0dc-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|<span data-ttu-id="2a0dc-112">Získá informace o spravovaném kódu na adrese konkrétního kódu.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="2a0dc-113">GetExportStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="2a0dc-113">GetExportStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="2a0dc-114">Obsahuje informace o modulu runtime exportované funkce, které umožňují krokovat spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="2a0dc-115">MarkDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="2a0dc-115">MarkDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="2a0dc-116">Vnitřní stav laděného objektu se změní tak, aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> vrátí metoda v knihovně tříd rozhraní .NET Framework `true`.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="2a0dc-117">ProcessStateChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="2a0dc-117">ProcessStateChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="2a0dc-118">Upozorní [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , který je proces spuštěn.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-118">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a0dc-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2a0dc-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a0dc-120">Rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="2a0dc-121">Pokus o volání `QueryInterface` načíst ukazatel rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a0dc-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2a0dc-122">Requirements</span></span>  
 <span data-ttu-id="2a0dc-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a0dc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a0dc-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a0dc-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a0dc-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a0dc-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2a0dc-126">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2a0dc-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2a0dc-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a0dc-127">See also</span></span>

- [<span data-ttu-id="2a0dc-128">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a0dc-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2a0dc-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="2a0dc-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
