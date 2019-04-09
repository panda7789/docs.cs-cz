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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7613bc744ad4c2e172fc4f6dd7bf282fb3d9072c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179748"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="5a3e7-102">IGCThreadControl::SuspensionStarting – metoda</span><span class="sxs-lookup"><span data-stu-id="5a3e7-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="5a3e7-103">Upozorňuje hostitele, že modul runtime zahajuje pozastavení vláken pro uvolnění paměti nebo jiných pozastavení.</span><span class="sxs-lookup"><span data-stu-id="5a3e7-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a3e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a3e7-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="5a3e7-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a3e7-105">Remarks</span></span>  
 <span data-ttu-id="5a3e7-106">Nelze změnit plán žádného vlákna během `SuspensionStarting` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="5a3e7-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a3e7-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a3e7-107">Requirements</span></span>  
 <span data-ttu-id="5a3e7-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a3e7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a3e7-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5a3e7-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a3e7-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5a3e7-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5a3e7-111">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5a3e7-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5a3e7-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a3e7-112">See also</span></span>

- [<span data-ttu-id="5a3e7-113">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a3e7-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
