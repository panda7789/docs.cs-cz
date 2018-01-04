---
title: "GetAppIdAuthority – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type: COM
f1_keywords: GetAppIdAuthority
helpviewer_keywords: GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e89624feb04050534b917b865d5cb53b8c4cf58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getappidauthority-function"></a><span data-ttu-id="b29e4-102">GetAppIdAuthority – funkce</span><span class="sxs-lookup"><span data-stu-id="b29e4-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="b29e4-103">Získá odkazy [iappidauthority –](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instanci, která spravuje klíče pro identity aplikace a odkazy.</span><span class="sxs-lookup"><span data-stu-id="b29e4-103">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b29e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b29e4-104">Syntax</span></span>  
  
```  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b29e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b29e4-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="b29e4-106">[out] Vrácený `IAppIdAuthority` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="b29e4-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b29e4-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b29e4-107">Requirements</span></span>  
 <span data-ttu-id="b29e4-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b29e4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b29e4-109">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="b29e4-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="b29e4-110">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b29e4-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b29e4-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b29e4-111">See Also</span></span>  
 [<span data-ttu-id="b29e4-112">IAppIdAuthority – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b29e4-112">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 [<span data-ttu-id="b29e4-113">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="b29e4-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
