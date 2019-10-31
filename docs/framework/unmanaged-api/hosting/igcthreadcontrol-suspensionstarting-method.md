---
title: IGCThreadControl::SuspensionStarting – metoda
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type:
- apiref
ms.openlocfilehash: 1e1d63ab28276f69e5b3a762520db8f8300d05bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134765"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="97571-102">IGCThreadControl::SuspensionStarting – metoda</span><span class="sxs-lookup"><span data-stu-id="97571-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="97571-103">Upozorňuje hostitele, že modul runtime zahajuje pozastavení vlákna pro uvolňování paměti nebo jiné pozastavení.</span><span class="sxs-lookup"><span data-stu-id="97571-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97571-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97571-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="97571-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97571-105">Remarks</span></span>  
 <span data-ttu-id="97571-106">Během zpětného volání `SuspensionStarting` neplánujte žádná vlákna.</span><span class="sxs-lookup"><span data-stu-id="97571-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97571-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97571-107">Requirements</span></span>  
 <span data-ttu-id="97571-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97571-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97571-109">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="97571-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97571-110">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="97571-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97571-111">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97571-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97571-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97571-112">See also</span></span>

- [<span data-ttu-id="97571-113">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="97571-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
