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
ms.workload: dotnet
ms.openlocfilehash: 25bb63f1b1fa759cd6d61a71682b803e3320f22d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="7d75c-102">ICorDebugDebugEvent::GetEventKind – metoda</span><span class="sxs-lookup"><span data-stu-id="7d75c-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="7d75c-103">Určuje, jaký druh událostí to `ICorDebugDebugEvent` objekt představuje.</span><span class="sxs-lookup"><span data-stu-id="7d75c-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d75c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d75c-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d75c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d75c-105">Parameters</span></span>  
 <span data-ttu-id="7d75c-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="7d75c-106">pDebugEventKind</span></span>  
 <span data-ttu-id="7d75c-107">Ukazatel [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) člen výčtu, která určuje typ události.</span><span class="sxs-lookup"><span data-stu-id="7d75c-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d75c-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d75c-108">Remarks</span></span>  
 <span data-ttu-id="7d75c-109">Na základě hodnoty z `pDebugEventKind`, můžete volat `QueryInterface` získat přesnější rozhraní ladění události, která obsahuje další data.</span><span class="sxs-lookup"><span data-stu-id="7d75c-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d75c-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="7d75c-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d75c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d75c-111">Requirements</span></span>  
 <span data-ttu-id="7d75c-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d75c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d75c-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d75c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d75c-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d75c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d75c-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d75c-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d75c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d75c-116">See Also</span></span>  
 [<span data-ttu-id="7d75c-117">ICorDebugDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d75c-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="7d75c-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7d75c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
