---
title: ICorDebugProcess6::ProcessStateChanged – metoda
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 6be216741e902b15efc3a3ece95cb4a4229960e3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212841"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="28fb7-102">ICorDebugProcess6::ProcessStateChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="28fb7-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="28fb7-103">Upozorní [ICorDebug](icordebug-interface.md) , že proces běží.</span><span class="sxs-lookup"><span data-stu-id="28fb7-103">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28fb7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28fb7-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28fb7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28fb7-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="28fb7-106">pro Člen výčtu [ProcessStateChanged –](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="28fb7-106">[in] A member of the [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28fb7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28fb7-107">Remarks</span></span>  
 <span data-ttu-id="28fb7-108">Ladicí program volá tuto metodu pro oznamování [ICorDebug](icordebug-interface.md) , že proces běží.</span><span class="sxs-lookup"><span data-stu-id="28fb7-108">The debugger calls this method to notify [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28fb7-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28fb7-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28fb7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28fb7-110">Requirements</span></span>  
 <span data-ttu-id="28fb7-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28fb7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28fb7-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="28fb7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28fb7-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="28fb7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28fb7-114">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28fb7-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28fb7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="28fb7-115">See also</span></span>

- [<span data-ttu-id="28fb7-116">Rozhraní ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="28fb7-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="28fb7-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28fb7-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
