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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4cd4fa8f4ba2bea5a2a853544eae6239bfaaeba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917577"
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="e1bc6-102">ITypeName::GetTypeArguments – metoda</span><span class="sxs-lookup"><span data-stu-id="e1bc6-102">ITypeName::GetTypeArguments Method</span></span>
<span data-ttu-id="e1bc6-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="e1bc6-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1bc6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1bc6-104">Syntax</span></span>  
  
```  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e1bc6-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1bc6-105">Requirements</span></span>  
 <span data-ttu-id="e1bc6-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1bc6-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1bc6-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e1bc6-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e1bc6-108">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e1bc6-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1bc6-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1bc6-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1bc6-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1bc6-110">See also</span></span>

- [<span data-ttu-id="e1bc6-111">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="e1bc6-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
