---
title: Rozhraní ICorDebugProcess6
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: 4ad350e36ee15d7c1781e03698fbee3fd40c4c12
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212864"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="6f282-102">Rozhraní ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="6f282-102">ICorDebugProcess6 Interface</span></span>
<span data-ttu-id="6f282-103">Logicky rozšiřuje rozhraní ICorDebugProcess a povoluje funkce jako dekódování spravovaných událostí ladění, které jsou zakódované v nativních událostech ladění výjimek a rozdělování virtuálních modulů.</span><span class="sxs-lookup"><span data-stu-id="6f282-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f282-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6f282-104">Methods</span></span>  
  
|<span data-ttu-id="6f282-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6f282-105">Method</span></span>|<span data-ttu-id="6f282-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6f282-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f282-107">DecodeEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="6f282-107">DecodeEvent Method</span></span>](icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="6f282-108">Dekóduje spravované události ladění, které byly zapouzdřeny v datové části speciálně vytvořené nativní výjimky ladění.</span><span class="sxs-lookup"><span data-stu-id="6f282-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="6f282-109">EnableVirtualModuleSplitting – metoda</span><span class="sxs-lookup"><span data-stu-id="6f282-109">EnableVirtualModuleSplitting Method</span></span>](icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="6f282-110">Povolí nebo zakáže rozdělení virtuálního modulu.</span><span class="sxs-lookup"><span data-stu-id="6f282-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="6f282-111">GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="6f282-111">GetCode Method</span></span>](icordebugprocess6-getcode-method.md)|<span data-ttu-id="6f282-112">Načte informace o spravovaném kódu na konkrétní kódové adrese.</span><span class="sxs-lookup"><span data-stu-id="6f282-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="6f282-113">GetExportStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="6f282-113">GetExportStepInfo Method</span></span>](icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="6f282-114">Poskytuje informace o exportovaných funkcích modulu runtime, které vám pomůžou krokovat se spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="6f282-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="6f282-115">MarkDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="6f282-115">MarkDebuggerAttached Method</span></span>](icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="6f282-116">Změní vnitřní stav laděného objektu tak, že <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda v knihovně třídy .NET Framework vrátí `true` .</span><span class="sxs-lookup"><span data-stu-id="6f282-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="6f282-117">Metoda ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="6f282-117">ProcessStateChanged Method</span></span>](icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="6f282-118">Upozorní [ICorDebug](icordebug-interface.md) , že proces běží.</span><span class="sxs-lookup"><span data-stu-id="6f282-118">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f282-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6f282-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f282-120">Rozhraní je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6f282-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="6f282-121">Pokus o volání metody `QueryInterface` načtení ukazatele rozhraní `E_NOINTERFACE` pro ICorDebug scénáře mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6f282-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f282-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f282-122">Requirements</span></span>  
 <span data-ttu-id="6f282-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f282-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f282-124">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6f282-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f282-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6f282-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f282-126">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f282-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f282-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f282-127">See also</span></span>

- [<span data-ttu-id="6f282-128">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f282-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6f282-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="6f282-129">Debugging</span></span>](index.md)
