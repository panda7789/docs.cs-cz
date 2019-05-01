---
title: ICorDebugDebugEvent::GetEventKind – metoda
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62eede48eea01563dbc3e170720694a24343d0a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964759"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="8011a-102">ICorDebugDebugEvent::GetEventKind – metoda</span><span class="sxs-lookup"><span data-stu-id="8011a-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="8011a-103">Jaký druh událostí označuje to `ICorDebugDebugEvent` objekt představuje.</span><span class="sxs-lookup"><span data-stu-id="8011a-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8011a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8011a-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8011a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8011a-105">Parameters</span></span>  
 <span data-ttu-id="8011a-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="8011a-106">pDebugEventKind</span></span>  
 <span data-ttu-id="8011a-107">Ukazatel [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) člen výčtu, která určuje typ události.</span><span class="sxs-lookup"><span data-stu-id="8011a-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8011a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8011a-108">Remarks</span></span>  
 <span data-ttu-id="8011a-109">Na základě hodnoty z `pDebugEventKind`, můžete volat `QueryInterface` získat přesnější rozhraní události ladění, který obsahuje další data.</span><span class="sxs-lookup"><span data-stu-id="8011a-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8011a-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8011a-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8011a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8011a-111">Requirements</span></span>  
 <span data-ttu-id="8011a-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8011a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8011a-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8011a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8011a-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8011a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8011a-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8011a-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8011a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8011a-116">See also</span></span>

- [<span data-ttu-id="8011a-117">ICorDebugDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8011a-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="8011a-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8011a-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
