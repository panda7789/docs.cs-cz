---
title: Funkce CertFreeAuthenticodeSignerInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertFreeAuthenticodeSignerInfo
api_location: clr.dll
api_type: DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f922cdba8bcfce6c9ff4543f6aea5bacfdc60ab0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="166a5-102">Funkce CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="166a5-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="166a5-103">Uvolní prostředky přidělené [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="166a5-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="166a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="166a5-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="166a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="166a5-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="166a5-106">[ve out] Informace o podepisující osoba k uvolnění.</span><span class="sxs-lookup"><span data-stu-id="166a5-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="166a5-107">Najdete v článku [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="166a5-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="166a5-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="166a5-108">Return Value</span></span>  
 <span data-ttu-id="166a5-109">`S_OK`Pokud funkci se zdaří.</span><span class="sxs-lookup"><span data-stu-id="166a5-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="166a5-110">Jinak vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="166a5-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="166a5-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="166a5-111">See Also</span></span>  
 [<span data-ttu-id="166a5-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="166a5-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
