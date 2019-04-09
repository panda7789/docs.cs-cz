---
title: ICorDebugDebugEvent::GetEventKind – metoda
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62eede48eea01563dbc3e170720694a24343d0a5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150524"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="e656e-102">ICorDebugDebugEvent::GetEventKind – metoda</span><span class="sxs-lookup"><span data-stu-id="e656e-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="e656e-103">Jaký druh událostí označuje to `ICorDebugDebugEvent` objekt představuje.</span><span class="sxs-lookup"><span data-stu-id="e656e-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e656e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e656e-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e656e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e656e-105">Parameters</span></span>  
 <span data-ttu-id="e656e-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="e656e-106">pDebugEventKind</span></span>  
 <span data-ttu-id="e656e-107">Ukazatel [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) člen výčtu, která určuje typ události.</span><span class="sxs-lookup"><span data-stu-id="e656e-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e656e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e656e-108">Remarks</span></span>  
 <span data-ttu-id="e656e-109">Na základě hodnoty z `pDebugEventKind`, můžete volat `QueryInterface` získat přesnější rozhraní události ladění, který obsahuje další data.</span><span class="sxs-lookup"><span data-stu-id="e656e-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e656e-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e656e-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e656e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e656e-111">Requirements</span></span>  
 <span data-ttu-id="e656e-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e656e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e656e-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e656e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e656e-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e656e-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e656e-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e656e-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e656e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e656e-116">See also</span></span>

- [<span data-ttu-id="e656e-117">Rozhraní ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="e656e-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="e656e-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e656e-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
