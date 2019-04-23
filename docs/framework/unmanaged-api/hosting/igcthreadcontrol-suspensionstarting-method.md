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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179748"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="e09db-102">IGCThreadControl::SuspensionStarting – metoda</span><span class="sxs-lookup"><span data-stu-id="e09db-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="e09db-103">Upozorňuje hostitele, že modul runtime zahajuje pozastavení vláken pro uvolnění paměti nebo jiných pozastavení.</span><span class="sxs-lookup"><span data-stu-id="e09db-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e09db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e09db-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="e09db-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e09db-105">Remarks</span></span>  
 <span data-ttu-id="e09db-106">Nelze změnit plán žádného vlákna během `SuspensionStarting` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="e09db-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e09db-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e09db-107">Requirements</span></span>  
 <span data-ttu-id="e09db-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e09db-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e09db-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e09db-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e09db-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e09db-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e09db-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e09db-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e09db-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e09db-112">See also</span></span>

- [<span data-ttu-id="e09db-113">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e09db-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
