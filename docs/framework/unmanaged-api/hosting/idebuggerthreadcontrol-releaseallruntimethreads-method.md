---
title: IDebuggerThreadControl::ReleaseAllRuntimeThreads – metoda
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
ms.openlocfilehash: 50ffb33456f942a71089f9bc44daa07f6b77ab21
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805290"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="78daf-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="78daf-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="78daf-103">Upozorňuje hostitele, že se chystá ladicí služby uvolnit všechna blokovaná vlákna.</span><span class="sxs-lookup"><span data-stu-id="78daf-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78daf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78daf-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="78daf-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78daf-105">Remarks</span></span>  
 <span data-ttu-id="78daf-106">`ReleaseAllRuntimeThreads`Metoda nebude nikdy volána ve vlákně modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="78daf-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="78daf-107">Pokud má hostitel běhové vlákno, je třeba ho uvolnit hned.</span><span class="sxs-lookup"><span data-stu-id="78daf-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78daf-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78daf-108">Requirements</span></span>  
 <span data-ttu-id="78daf-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78daf-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78daf-110">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="78daf-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78daf-111">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="78daf-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78daf-112">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78daf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78daf-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="78daf-113">See also</span></span>

- [<span data-ttu-id="78daf-114">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78daf-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
