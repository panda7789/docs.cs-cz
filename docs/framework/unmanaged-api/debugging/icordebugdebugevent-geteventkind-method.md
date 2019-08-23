---
title: ICorDebugDebugEvent::GetEventKind – metoda
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a87dda8d8a263df1989a685d94c5163212f41382
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911343"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="dd6d3-102">ICorDebugDebugEvent::GetEventKind – metoda</span><span class="sxs-lookup"><span data-stu-id="dd6d3-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="dd6d3-103">Určuje, jaký druh události tento `ICorDebugDebugEvent` objekt představuje.</span><span class="sxs-lookup"><span data-stu-id="dd6d3-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd6d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd6d3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd6d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd6d3-105">Parameters</span></span>  
 <span data-ttu-id="dd6d3-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="dd6d3-106">pDebugEventKind</span></span>  
 <span data-ttu-id="dd6d3-107">Ukazatel na člen výčtu [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) , který určuje typ události.</span><span class="sxs-lookup"><span data-stu-id="dd6d3-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd6d3-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd6d3-108">Remarks</span></span>  
 <span data-ttu-id="dd6d3-109">Na základě hodnoty `pDebugEventKind`můžete zavolat `QueryInterface` pro získání přesnější rozhraní události ladění, které má další data.</span><span class="sxs-lookup"><span data-stu-id="dd6d3-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd6d3-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dd6d3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd6d3-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd6d3-111">Requirements</span></span>  
 <span data-ttu-id="dd6d3-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd6d3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd6d3-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dd6d3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd6d3-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd6d3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd6d3-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd6d3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd6d3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd6d3-116">See also</span></span>

- [<span data-ttu-id="dd6d3-117">ICorDebugDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd6d3-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="dd6d3-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dd6d3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
