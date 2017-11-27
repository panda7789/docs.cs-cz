---
title: "IGCThreadControl::SuspensionStarting – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCThreadControl.SuspensionStarting
api_location: mscoree.dll
api_type: COM
f1_keywords: SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9d5f403c2880d0079a89c6de5c2ad9aa4f8d9fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="b9eda-102">IGCThreadControl::SuspensionStarting – metoda</span><span class="sxs-lookup"><span data-stu-id="b9eda-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="b9eda-103">Aby modul runtime zahajuje pozastavení vláken pro uvolnění paměti nebo jiných pozastavení upozorní hostitele.</span><span class="sxs-lookup"><span data-stu-id="b9eda-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9eda-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9eda-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="b9eda-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9eda-105">Remarks</span></span>  
 <span data-ttu-id="b9eda-106">Není změnit plán žádné podprocesy během `SuspensionStarting` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="b9eda-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9eda-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9eda-107">Requirements</span></span>  
 <span data-ttu-id="b9eda-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9eda-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9eda-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b9eda-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9eda-110">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b9eda-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9eda-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9eda-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9eda-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9eda-112">See Also</span></span>  
 [<span data-ttu-id="b9eda-113">Igcthreadcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9eda-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
