---
title: "ITypeName::GetNames – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ITypeName.GetNames
api_location: mscoree.dll
api_type: COM
f1_keywords: GetNames
helpviewer_keywords:
- ITypeName::GetNames method [.NET Framework hosting]
- GetNames method [.NET Framework hosting]
ms.assetid: e2a3637b-d1e9-4d93-9e9b-0555fbff793d
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62635531149f90a499b4809869ed2a2efded58a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="itypenamegetnames-method"></a><span data-ttu-id="d954e-102">ITypeName::GetNames – metoda</span><span class="sxs-lookup"><span data-stu-id="d954e-102">ITypeName::GetNames Method</span></span>
<span data-ttu-id="d954e-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="d954e-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d954e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d954e-104">Syntax</span></span>  
  
```  
HRESULT GetNames (  
    [in] DWORD           count,  
    [out] BSTR*          rgbszNames,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d954e-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d954e-105">Requirements</span></span>  
 <span data-ttu-id="d954e-106">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d954e-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d954e-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d954e-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d954e-108">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d954e-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d954e-109">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d954e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d954e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d954e-110">See Also</span></span>  
 [<span data-ttu-id="d954e-111">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="d954e-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
