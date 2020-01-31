---
title: ICorDebugDebugEvent::GetEventKind – metoda
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 0c67f8bdce49b4e9200b501aaf00ae293cced7d7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783416"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="84b61-102">ICorDebugDebugEvent::GetEventKind – metoda</span><span class="sxs-lookup"><span data-stu-id="84b61-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="84b61-103">Určuje, jaký typ události tento objekt `ICorDebugDebugEvent` představuje.</span><span class="sxs-lookup"><span data-stu-id="84b61-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84b61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84b61-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84b61-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84b61-105">Parameters</span></span>  
 <span data-ttu-id="84b61-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="84b61-106">pDebugEventKind</span></span>  
 <span data-ttu-id="84b61-107">Ukazatel na člen výčtu [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) , který určuje typ události.</span><span class="sxs-lookup"><span data-stu-id="84b61-107">A pointer to a [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84b61-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84b61-108">Remarks</span></span>  
 <span data-ttu-id="84b61-109">Na základě hodnoty `pDebugEventKind`můžete volat `QueryInterface` a získat tak přesnější rozhraní události ladění, které obsahuje další data.</span><span class="sxs-lookup"><span data-stu-id="84b61-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84b61-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="84b61-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84b61-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84b61-111">Requirements</span></span>  
 <span data-ttu-id="84b61-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84b61-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84b61-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="84b61-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84b61-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="84b61-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84b61-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84b61-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b61-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84b61-116">See also</span></span>

- [<span data-ttu-id="84b61-117">ICorDebugDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="84b61-117">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="84b61-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="84b61-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
