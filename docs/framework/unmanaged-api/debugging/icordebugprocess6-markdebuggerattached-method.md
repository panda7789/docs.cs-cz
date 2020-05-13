---
title: ICorDebugProcess6::MarkDebuggerAttached – metoda
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
ms.openlocfilehash: c83d6e892b89e6e50779abf9a71a2cbe9093af2c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212842"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="2995a-102">ICorDebugProcess6::MarkDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="2995a-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="2995a-103">Změní vnitřní stav laděného objektu tak, že <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda v knihovně třídy .NET Framework vrátí `true` .</span><span class="sxs-lookup"><span data-stu-id="2995a-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2995a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2995a-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2995a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2995a-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="2995a-106">`true`Pokud <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> by metoda měla označovat, že je připojen ladicí program. `false` v opačném případě.</span><span class="sxs-lookup"><span data-stu-id="2995a-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2995a-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2995a-107">Return Value</span></span>  
 <span data-ttu-id="2995a-108">Metoda může vracet hodnoty uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="2995a-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="2995a-109">Vrácená hodnota</span><span class="sxs-lookup"><span data-stu-id="2995a-109">Return value</span></span>|<span data-ttu-id="2995a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="2995a-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="2995a-111">Laděného procesu se úspěšně aktualizoval.</span><span class="sxs-lookup"><span data-stu-id="2995a-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="2995a-112">Sestavení, které obsahuje metodu, není <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> načteno nebo došlo k nějaké jiné chybě, například chybějící metadata, brání jejímu rozpoznání.</span><span class="sxs-lookup"><span data-stu-id="2995a-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="2995a-113">Tato chyba je běžná a neškodná.</span><span class="sxs-lookup"><span data-stu-id="2995a-113">This error is common and benign.</span></span> <span data-ttu-id="2995a-114">Metodu byste měli zavolat znovu, až se načtou další sestavení.</span><span class="sxs-lookup"><span data-stu-id="2995a-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="2995a-115">Jiné neúspěšné `HRESULT` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2995a-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="2995a-116">Jiné hodnoty nejspíš naznačují, že se nechovají ladicí program nebo komponenty kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="2995a-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2995a-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2995a-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2995a-118">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2995a-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2995a-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2995a-119">Requirements</span></span>  
 <span data-ttu-id="2995a-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2995a-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2995a-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2995a-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2995a-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2995a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2995a-123">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2995a-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2995a-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="2995a-124">See also</span></span>

- [<span data-ttu-id="2995a-125">Rozhraní ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="2995a-125">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="2995a-126">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2995a-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
