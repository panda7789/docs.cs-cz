---
title: GetAppIdAuthority – funkce
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 274b91793cd51348c42661bf12a4e4385e17f630
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093966"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="b07b0-102">GetAppIdAuthority – funkce</span><span class="sxs-lookup"><span data-stu-id="b07b0-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="b07b0-103">Získá ukazatel [iappidauthority –](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance, která spravuje klíče pro identity aplikací a odkazy.</span><span class="sxs-lookup"><span data-stu-id="b07b0-103">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b07b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b07b0-104">Syntax</span></span>  
  
```  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b07b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b07b0-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="b07b0-106">[out] Vrácený `IAppIdAuthority` ukazatele.</span><span class="sxs-lookup"><span data-stu-id="b07b0-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b07b0-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b07b0-107">Requirements</span></span>  
 <span data-ttu-id="b07b0-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b07b0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b07b0-109">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="b07b0-109">**Header:** Isolation.h</span></span>  
  
 **<span data-ttu-id="b07b0-110">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b07b0-110">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b07b0-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b07b0-111">See also</span></span>

- [<span data-ttu-id="b07b0-112">IAppIdAuthority – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b07b0-112">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)
- [<span data-ttu-id="b07b0-113">Fúze globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="b07b0-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
