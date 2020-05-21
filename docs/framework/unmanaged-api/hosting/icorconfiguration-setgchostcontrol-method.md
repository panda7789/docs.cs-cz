---
title: ICorConfiguration::SetGCHostControl – metoda
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type:
- apiref
ms.openlocfilehash: e648b36a2b276d9335eefaf71b57ad76f9fe0def
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762380"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="c913f-102">ICorConfiguration::SetGCHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="c913f-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="c913f-103">Nastaví rozhraní zpětného volání, které má systém uvolňování paměti použít k vyžádání hostitele, aby změnil limity virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="c913f-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c913f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c913f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c913f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c913f-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="c913f-106">pro Ukazatel na objekt [IGCHostControl –](igchostcontrol-interface.md) , který umožňuje systému uvolňování paměti požádat hostitele o změnu omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="c913f-106">[in] A pointer to an [IGCHostControl](igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c913f-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c913f-107">Requirements</span></span>  
 <span data-ttu-id="c913f-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c913f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c913f-109">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c913f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c913f-110">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c913f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c913f-111">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c913f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c913f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="c913f-112">See also</span></span>

- [<span data-ttu-id="c913f-113">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c913f-113">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
