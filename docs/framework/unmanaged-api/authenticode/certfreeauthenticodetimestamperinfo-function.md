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
ms.openlocfilehash: 9c37a9af6a1532d03fa04ca151605cef7ab5244e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401765"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="83624-102">Funkce CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="83624-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="83624-103">Uvolní prostředky přidělené [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="83624-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83624-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83624-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83624-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83624-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="83624-106">[ve out] Informace stamper čas k uvolnění.</span><span class="sxs-lookup"><span data-stu-id="83624-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="83624-107">Najdete v článku [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="83624-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83624-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="83624-108">Return Value</span></span>  
 <span data-ttu-id="83624-109">`S_OK` Pokud funkci se zdaří.</span><span class="sxs-lookup"><span data-stu-id="83624-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="83624-110">Jinak vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="83624-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83624-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="83624-111">See Also</span></span>  
 [<span data-ttu-id="83624-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="83624-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
