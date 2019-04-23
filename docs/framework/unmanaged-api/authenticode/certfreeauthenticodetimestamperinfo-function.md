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
ms.openlocfilehash: 355e6c7b1cd77936d5ccfa5ccff7312c8e35ac63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220396"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="2eeec-102">Funkce CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="2eeec-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="2eeec-103">Uvolní prostředky přidělené [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="2eeec-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eeec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2eeec-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2eeec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2eeec-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="2eeec-106">[out v] Informace stamper čas uvolnit.</span><span class="sxs-lookup"><span data-stu-id="2eeec-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="2eeec-107">Zobrazit [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="2eeec-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2eeec-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2eeec-108">Return Value</span></span>  
 <span data-ttu-id="2eeec-109">`S_OK` Pokud je funkce úspěšná.</span><span class="sxs-lookup"><span data-stu-id="2eeec-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="2eeec-110">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="2eeec-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eeec-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2eeec-111">See also</span></span>

- [<span data-ttu-id="2eeec-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="2eeec-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
