---
title: ITypeName::GetTypeArguments – metoda
ms.date: 03/30/2017
api_name:
- ITypeName.GetTypeArguments
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeArguments
helpviewer_keywords:
- ITypeName::GetTypeArguments method [.NET Framework hosting]
- GetTypeArguments method [.NET Framework hosting]
ms.assetid: 638d77df-ff9c-40d9-88ee-930f5f87ada1
topic_type:
- apiref
ms.openlocfilehash: ac835459f88655377d96699e6aea0e877218c8fb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125276"
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="3a9f1-102">ITypeName::GetTypeArguments – metoda</span><span class="sxs-lookup"><span data-stu-id="3a9f1-102">ITypeName::GetTypeArguments Method</span></span>
<span data-ttu-id="3a9f1-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="3a9f1-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a9f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a9f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3a9f1-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a9f1-105">Requirements</span></span>  
 <span data-ttu-id="3a9f1-106">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a9f1-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a9f1-107">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3a9f1-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a9f1-108">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3a9f1-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a9f1-109">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a9f1-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a9f1-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a9f1-110">See also</span></span>

- [<span data-ttu-id="3a9f1-111">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="3a9f1-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
