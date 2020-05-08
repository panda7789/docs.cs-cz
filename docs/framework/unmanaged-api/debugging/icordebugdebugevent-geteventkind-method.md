---
title: ICorDebugDebugEvent::GetEventKind – metoda
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 6e3ebdcb5b3e85f6f5a329ed249aa58be903e30f
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976392"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="a793b-102">ICorDebugDebugEvent::GetEventKind – metoda</span><span class="sxs-lookup"><span data-stu-id="a793b-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="a793b-103">Určuje, jaký druh události tento `ICorDebugDebugEvent` objekt představuje.</span><span class="sxs-lookup"><span data-stu-id="a793b-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a793b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a793b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a793b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a793b-105">Parameters</span></span>  
 <span data-ttu-id="a793b-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="a793b-106">pDebugEventKind</span></span>  
 <span data-ttu-id="a793b-107">Ukazatel na člen výčtu [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) , který určuje typ události.</span><span class="sxs-lookup"><span data-stu-id="a793b-107">A pointer to a [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a793b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a793b-108">Remarks</span></span>  
 <span data-ttu-id="a793b-109">Na základě hodnoty `pDebugEventKind`můžete zavolat `QueryInterface` pro získání přesnější rozhraní události ladění, které má další data.</span><span class="sxs-lookup"><span data-stu-id="a793b-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a793b-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a793b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a793b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a793b-111">Requirements</span></span>  
 <span data-ttu-id="a793b-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a793b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a793b-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a793b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a793b-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a793b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a793b-115">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a793b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a793b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a793b-116">See also</span></span>

- [<span data-ttu-id="a793b-117">Rozhraní ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="a793b-117">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="a793b-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a793b-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
