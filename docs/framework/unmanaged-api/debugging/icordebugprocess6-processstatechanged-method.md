---
title: ICorDebugProcess6::ProcessStateChanged – metoda
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: b6665df550a2d07a3fa84c3f2b6bf07f459cd713
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792206"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="a00c3-102">ICorDebugProcess6::ProcessStateChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="a00c3-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="a00c3-103">Upozorní [ICorDebug](icordebug-interface.md) , že proces běží.</span><span class="sxs-lookup"><span data-stu-id="a00c3-103">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a00c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a00c3-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a00c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a00c3-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="a00c3-106">pro Člen výčtu [ProcessStateChanged –](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="a00c3-106">[in] A member of the [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a00c3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a00c3-107">Remarks</span></span>  
 <span data-ttu-id="a00c3-108">Ladicí program volá tuto metodu pro oznamování [ICorDebug](icordebug-interface.md) , že proces běží.</span><span class="sxs-lookup"><span data-stu-id="a00c3-108">The debugger calls this method to notify [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a00c3-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a00c3-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a00c3-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a00c3-110">Requirements</span></span>  
 <span data-ttu-id="a00c3-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a00c3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a00c3-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a00c3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a00c3-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a00c3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a00c3-114">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a00c3-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a00c3-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a00c3-115">See also</span></span>

- [<span data-ttu-id="a00c3-116">ICorDebugProcess6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a00c3-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="a00c3-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a00c3-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
