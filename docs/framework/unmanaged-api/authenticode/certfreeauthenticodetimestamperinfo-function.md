---
title: Funkce CertFreeAuthenticodeTimestamperInfo
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 082ed24eb65de12f337ab4a379b088da0f6eea5a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497376"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="e7a65-102">Funkce CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="e7a65-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="e7a65-103">Uvolní prostředky přidělené [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="e7a65-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7a65-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7a65-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7a65-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7a65-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="e7a65-106">[out v] Informace stamper čas uvolnit.</span><span class="sxs-lookup"><span data-stu-id="e7a65-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="e7a65-107">Zobrazit [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="e7a65-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7a65-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e7a65-108">Return Value</span></span>  
 <span data-ttu-id="e7a65-109">`S_OK` Pokud je funkce úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e7a65-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="e7a65-110">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e7a65-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a65-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7a65-111">See also</span></span>
- [<span data-ttu-id="e7a65-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="e7a65-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
