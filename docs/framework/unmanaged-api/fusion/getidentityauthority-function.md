---
title: GetIdentityAuthority – funkce
ms.date: 03/30/2017
api_name:
- GetIdentityAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetIdentityAuthority
helpviewer_keywords:
- GetIdentityAuthority function [.NET Framework fusion]
ms.assetid: 843cd5ab-d2b7-4ff6-86bd-e68c7a91c098
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09d6284d7042dfebee004c4cb18d8ef3752c325c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496986"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="aca4c-102">GetIdentityAuthority – funkce</span><span class="sxs-lookup"><span data-stu-id="aca4c-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="aca4c-103">Získá ukazatel [iidentityauthority –](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance, která spravuje klíče pro objekty kódu.</span><span class="sxs-lookup"><span data-stu-id="aca4c-103">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aca4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aca4c-104">Syntax</span></span>  
  
```  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="aca4c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aca4c-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="aca4c-106">[out] Vrácený `IIdentityAuthority` ukazatele.</span><span class="sxs-lookup"><span data-stu-id="aca4c-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aca4c-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aca4c-107">Requirements</span></span>  
 <span data-ttu-id="aca4c-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aca4c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aca4c-109">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="aca4c-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="aca4c-110">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aca4c-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca4c-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aca4c-111">See also</span></span>
- [<span data-ttu-id="aca4c-112">IIdentityAuthority – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aca4c-112">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)
- [<span data-ttu-id="aca4c-113">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="aca4c-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
