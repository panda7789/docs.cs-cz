---
title: ICorDebugThread::GetObject – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetObject method [.NET Framework debugging]
ms.assetid: 1590febe-96c2-4046-97db-d81d81d67e01
topic_type:
- apiref
ms.openlocfilehash: 5cb95fb7cf70dbf7616e9bc59ebf44de090de883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133434"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="df699-102">ICorDebugThread::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="df699-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="df699-103">Načte ukazatel rozhraní do vlákna modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="df699-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df699-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df699-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df699-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df699-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="df699-106">mimo Ukazatel na adresu objektu rozhraní ICorDebugValue, který představuje vlákno CLR.</span><span class="sxs-lookup"><span data-stu-id="df699-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df699-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df699-107">Requirements</span></span>  
 <span data-ttu-id="df699-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df699-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df699-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="df699-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df699-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="df699-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df699-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df699-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df699-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df699-112">See also</span></span>

- <xref:System.Threading.Thread>
