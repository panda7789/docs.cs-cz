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
ms.openlocfilehash: 680d9c959c57620ff38f8e785c670b451e5805b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741229"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="46576-102">Funkce CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="46576-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="46576-103">Uvolní prostředky přidělené [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="46576-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46576-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46576-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46576-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46576-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="46576-106">[out v] Informace stamper čas uvolnit.</span><span class="sxs-lookup"><span data-stu-id="46576-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="46576-107">Zobrazit [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="46576-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46576-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="46576-108">Return Value</span></span>  
 <span data-ttu-id="46576-109">`S_OK` Pokud je funkce úspěšná.</span><span class="sxs-lookup"><span data-stu-id="46576-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="46576-110">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="46576-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46576-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46576-111">See also</span></span>

- [<span data-ttu-id="46576-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="46576-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
