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
ms.openlocfilehash: 2acabe66e3b6b5652df20e31a9d2294c2396b54b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805098"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="0d6ec-102">IGCThreadControl::SuspensionStarting – metoda</span><span class="sxs-lookup"><span data-stu-id="0d6ec-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="0d6ec-103">Upozorňuje hostitele, že modul runtime zahajuje pozastavení vlákna pro uvolňování paměti nebo jiné pozastavení.</span><span class="sxs-lookup"><span data-stu-id="0d6ec-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d6ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d6ec-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="0d6ec-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d6ec-105">Remarks</span></span>  
 <span data-ttu-id="0d6ec-106">Neprovádějte přeplánování všech vláken během `SuspensionStarting` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="0d6ec-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d6ec-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d6ec-107">Requirements</span></span>  
 <span data-ttu-id="0d6ec-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d6ec-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d6ec-109">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0d6ec-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d6ec-110">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0d6ec-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d6ec-111">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d6ec-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d6ec-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d6ec-112">See also</span></span>

- [<span data-ttu-id="0d6ec-113">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d6ec-113">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
