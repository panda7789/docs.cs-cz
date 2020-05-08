---
title: ICorDebugDebugEvent::GetThread – metoda
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: acce18517c105739417fc734b49ff004ca9546dc
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976375"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="068aa-102">ICorDebugDebugEvent::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="068aa-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="068aa-103">Získá vlákno, ve kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="068aa-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="068aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="068aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="068aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="068aa-105">Parameters</span></span>  
 <span data-ttu-id="068aa-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="068aa-106">ppThread</span></span>  
 <span data-ttu-id="068aa-107">mimo Ukazatel na adresu objektu ICorDebugThread, který představuje vlákno, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="068aa-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="068aa-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="068aa-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="068aa-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="068aa-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="068aa-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="068aa-110">Requirements</span></span>  
 <span data-ttu-id="068aa-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="068aa-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="068aa-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="068aa-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="068aa-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="068aa-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="068aa-114">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="068aa-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="068aa-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="068aa-115">See also</span></span>

- [<span data-ttu-id="068aa-116">Rozhraní ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="068aa-116">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="068aa-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="068aa-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
