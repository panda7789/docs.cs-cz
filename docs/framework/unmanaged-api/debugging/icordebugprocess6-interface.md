---
title: Rozhraní ICorDebugProcess6
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d180d57431e34d872ff077e6bc597175029688e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962710"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="0de1c-102">Rozhraní ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="0de1c-102">ICorDebugProcess6 Interface</span></span>
<span data-ttu-id="0de1c-103">Logicky rozšiřuje rozhraní ICorDebugProcess a povoluje funkce jako dekódování spravovaných událostí ladění, které jsou zakódované v nativních událostech ladění výjimek a rozdělování virtuálních modulů.</span><span class="sxs-lookup"><span data-stu-id="0de1c-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0de1c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0de1c-104">Methods</span></span>  
  
|<span data-ttu-id="0de1c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0de1c-105">Method</span></span>|<span data-ttu-id="0de1c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0de1c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0de1c-107">DecodeEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="0de1c-107">DecodeEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="0de1c-108">Dekóduje spravované události ladění, které byly zapouzdřeny v datové části speciálně vytvořené nativní výjimky ladění.</span><span class="sxs-lookup"><span data-stu-id="0de1c-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="0de1c-109">EnableVirtualModuleSplitting – metoda</span><span class="sxs-lookup"><span data-stu-id="0de1c-109">EnableVirtualModuleSplitting Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="0de1c-110">Povolí nebo zakáže rozdělení virtuálního modulu.</span><span class="sxs-lookup"><span data-stu-id="0de1c-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="0de1c-111">GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="0de1c-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|<span data-ttu-id="0de1c-112">Načte informace o spravovaném kódu na konkrétní kódové adrese.</span><span class="sxs-lookup"><span data-stu-id="0de1c-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="0de1c-113">GetExportStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="0de1c-113">GetExportStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="0de1c-114">Poskytuje informace o exportovaných funkcích modulu runtime, které vám pomůžou krokovat se spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="0de1c-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="0de1c-115">MarkDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="0de1c-115">MarkDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="0de1c-116">Změní vnitřní stav laděného objektu tak, že <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda v knihovně třídy .NET Framework vrátí. `true`</span><span class="sxs-lookup"><span data-stu-id="0de1c-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="0de1c-117">ProcessStateChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="0de1c-117">ProcessStateChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="0de1c-118">Upozorní [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , že proces běží.</span><span class="sxs-lookup"><span data-stu-id="0de1c-118">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0de1c-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0de1c-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0de1c-120">Rozhraní je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0de1c-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="0de1c-121">Pokus o volání metody `QueryInterface` načtení `E_NOINTERFACE` ukazatele rozhraní pro ICorDebug scénáře mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0de1c-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0de1c-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0de1c-122">Requirements</span></span>  
 <span data-ttu-id="0de1c-123">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0de1c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0de1c-124">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0de1c-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0de1c-125">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0de1c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0de1c-126">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0de1c-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0de1c-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0de1c-127">See also</span></span>

- [<span data-ttu-id="0de1c-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0de1c-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0de1c-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="0de1c-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
