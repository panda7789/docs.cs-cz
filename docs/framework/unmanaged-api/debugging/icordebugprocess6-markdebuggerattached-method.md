---
title: ICorDebugProcess6::MarkDebuggerAttached – metoda
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63300f65a811b80132e6569a599044ff2d480acd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471573"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="9e10a-102">ICorDebugProcess6::MarkDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="9e10a-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="9e10a-103">Vnitřní stav laděného objektu se změní tak, aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> vrátí metoda v knihovně tříd rozhraní .NET Framework `true`.</span><span class="sxs-lookup"><span data-stu-id="9e10a-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e10a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e10a-104">Syntax</span></span>  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e10a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e10a-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="9e10a-106">`true` Pokud <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda měl označovat, že je připojen ladicí program; `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="9e10a-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e10a-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9e10a-107">Return Value</span></span>  
 <span data-ttu-id="9e10a-108">Metoda může vrátit hodnoty uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="9e10a-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="9e10a-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9e10a-109">Return value</span></span>|<span data-ttu-id="9e10a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="9e10a-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="9e10a-111">Laděný proces byl úspěšně aktualizován.</span><span class="sxs-lookup"><span data-stu-id="9e10a-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="9e10a-112">Sestavení obsahující <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda nebyla načtena, nebo některé jiné chyby, jako je například chybějící metadata, brání to bude rozpoznán.</span><span class="sxs-lookup"><span data-stu-id="9e10a-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="9e10a-113">Tato chyba je běžné a neškodné.</span><span class="sxs-lookup"><span data-stu-id="9e10a-113">This error is common and benign.</span></span> <span data-ttu-id="9e10a-114">Metoda by měla volat znovu, když načíst další sestavení.</span><span class="sxs-lookup"><span data-stu-id="9e10a-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="9e10a-115">Další selhání `HRESULT` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9e10a-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="9e10a-116">Jiné hodnoty může znamenat identifikovala ladicího programu nebo komponenty kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="9e10a-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e10a-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e10a-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e10a-118">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9e10a-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e10a-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e10a-119">Requirements</span></span>  
 <span data-ttu-id="9e10a-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e10a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e10a-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e10a-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e10a-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e10a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e10a-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e10a-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e10a-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e10a-124">See also</span></span>
- [<span data-ttu-id="9e10a-125">ICorDebugProcess6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e10a-125">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="9e10a-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9e10a-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
