---
title: Funkce CertFreeAuthenticodeSignerInfo
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84f15dc49d14e781f69d0f9da8f314eb71d8c034
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401613"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="37161-102">Funkce CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="37161-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="37161-103">Uvolní prostředky přidělené [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="37161-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37161-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37161-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37161-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37161-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="37161-106">[ve out] Informace o podepisující osoba k uvolnění.</span><span class="sxs-lookup"><span data-stu-id="37161-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="37161-107">Najdete v článku [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="37161-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37161-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="37161-108">Return Value</span></span>  
 <span data-ttu-id="37161-109">`S_OK` Pokud funkci se zdaří.</span><span class="sxs-lookup"><span data-stu-id="37161-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="37161-110">Jinak vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="37161-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37161-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="37161-111">See Also</span></span>  
 [<span data-ttu-id="37161-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="37161-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
