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
ms.openlocfilehash: e059cdddef7926c1359a83bc562146203724aa60
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842101"
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="d6196-102">ITypeName::GetTypeArguments – metoda</span><span class="sxs-lookup"><span data-stu-id="d6196-102">ITypeName::GetTypeArguments Method</span></span>
<span data-ttu-id="d6196-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="d6196-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6196-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6196-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d6196-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6196-105">Requirements</span></span>  
 <span data-ttu-id="d6196-106">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6196-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6196-107">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d6196-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6196-108">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d6196-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6196-109">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6196-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6196-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6196-110">See also</span></span>

- [<span data-ttu-id="d6196-111">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="d6196-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
