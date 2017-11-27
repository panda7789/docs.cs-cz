---
title: "ICorDebugDebugEvent::GetEventKind – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf3296eafb3e3ff933092240f8f353b2b69a89c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="963e0-102">ICorDebugDebugEvent::GetEventKind – metoda</span><span class="sxs-lookup"><span data-stu-id="963e0-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="963e0-103">Určuje, jaký druh událostí to `ICorDebugDebugEvent` objekt představuje.</span><span class="sxs-lookup"><span data-stu-id="963e0-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="963e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="963e0-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="963e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="963e0-105">Parameters</span></span>  
 <span data-ttu-id="963e0-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="963e0-106">pDebugEventKind</span></span>  
 <span data-ttu-id="963e0-107">Ukazatel [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) člen výčtu, která určuje typ události.</span><span class="sxs-lookup"><span data-stu-id="963e0-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="963e0-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="963e0-108">Remarks</span></span>  
 <span data-ttu-id="963e0-109">Na základě hodnoty z `pDebugEventKind`, můžete volat `QueryInterface` získat přesnější rozhraní ladění události, která obsahuje další data.</span><span class="sxs-lookup"><span data-stu-id="963e0-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="963e0-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="963e0-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="963e0-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="963e0-111">Requirements</span></span>  
 <span data-ttu-id="963e0-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="963e0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="963e0-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="963e0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="963e0-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="963e0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="963e0-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="963e0-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="963e0-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="963e0-116">See Also</span></span>  
 [<span data-ttu-id="963e0-117">Rozhraní ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="963e0-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="963e0-118">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="963e0-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
