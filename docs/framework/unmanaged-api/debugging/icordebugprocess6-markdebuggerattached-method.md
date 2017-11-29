---
title: "ICorDebugProcess6::MarkDebuggerAttached – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f6d219e298e04157ea0670681c7550bd920bd284
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="f4ba2-102">ICorDebugProcess6::MarkDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="f4ba2-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="f4ba2-103">Změní vnitřní stav debugee tak, aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> vrátí metoda v knihovně tříd rozhraní .NET Framework `true`.</span><span class="sxs-lookup"><span data-stu-id="f4ba2-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4ba2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4ba2-104">Syntax</span></span>  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4ba2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4ba2-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="f4ba2-106">`true`Pokud <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda by měl znamenat, že je připojen ladicí program; `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="f4ba2-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4ba2-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f4ba2-107">Return Value</span></span>  
 <span data-ttu-id="f4ba2-108">Metoda může vrátit hodnoty uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="f4ba2-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="f4ba2-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f4ba2-109">Return value</span></span>|<span data-ttu-id="f4ba2-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f4ba2-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="f4ba2-111">Ladění byla úspěšně aktualizována.</span><span class="sxs-lookup"><span data-stu-id="f4ba2-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="f4ba2-112">Sestavení, které obsahuje <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda není načten nebo některé jiné chyby, jako je například chybí metadata, znemožňuje ho bude rozpoznán.</span><span class="sxs-lookup"><span data-stu-id="f4ba2-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="f4ba2-113">Tato chyba je běžné a neškodné.</span><span class="sxs-lookup"><span data-stu-id="f4ba2-113">This error is common and benign.</span></span> <span data-ttu-id="f4ba2-114">Při spouštění dalších sestavení by měl znovu volejte metodu.</span><span class="sxs-lookup"><span data-stu-id="f4ba2-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="f4ba2-115">Další selhání `HRESULT` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f4ba2-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="f4ba2-116">Ostatní hodnoty pravděpodobně znamenat identifikovala ladicí program nebo kompilátoru součásti.</span><span class="sxs-lookup"><span data-stu-id="f4ba2-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4ba2-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f4ba2-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4ba2-118">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="f4ba2-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4ba2-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4ba2-119">Requirements</span></span>  
 <span data-ttu-id="f4ba2-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4ba2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4ba2-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4ba2-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4ba2-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4ba2-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4ba2-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4ba2-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4ba2-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4ba2-124">See Also</span></span>  
 [<span data-ttu-id="f4ba2-125">Rozhraní ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="f4ba2-125">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="f4ba2-126">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4ba2-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
