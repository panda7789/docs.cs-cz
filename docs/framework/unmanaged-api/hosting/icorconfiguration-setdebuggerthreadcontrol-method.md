---
title: ICorConfiguration::SetDebuggerThreadControl – metoda
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetDebuggerThreadControl
helpviewer_keywords:
- SetDebuggerThreadControl method [.NET Framework hosting]
- ICorConfiguration::SetDebuggerThreadControl method [.NET Framework hosting]
ms.assetid: 1ded7639-dacb-4db1-961c-d1ceaec01959
topic_type:
- apiref
ms.openlocfilehash: d02b834b22ba7897e4939de88bc3c61c62ac2b0e
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762406"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="49b31-102">ICorConfiguration::SetDebuggerThreadControl – metoda</span><span class="sxs-lookup"><span data-stu-id="49b31-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>
<span data-ttu-id="49b31-103">Nastaví rozhraní zpětného volání, které budou služby ladění volat jako vlákna modulu CLR (Common Language Runtime), jsou blokována a odblokována pro ladění.</span><span class="sxs-lookup"><span data-stu-id="49b31-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49b31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49b31-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49b31-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49b31-105">Parameters</span></span>  
 `pDebuggerThreadControl`  
 <span data-ttu-id="49b31-106">pro Ukazatel na objekt [IDebuggerThreadControl](idebuggerthreadcontrol-interface.md) , který upozorní hostitele na blokování a odblokování vláken pomocí služby ladění.</span><span class="sxs-lookup"><span data-stu-id="49b31-106">[in] A pointer to an [IDebuggerThreadControl](idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49b31-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49b31-107">Requirements</span></span>  
 <span data-ttu-id="49b31-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49b31-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49b31-109">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="49b31-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49b31-110">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="49b31-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49b31-111">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49b31-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49b31-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="49b31-112">See also</span></span>

- [<span data-ttu-id="49b31-113">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="49b31-113">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
