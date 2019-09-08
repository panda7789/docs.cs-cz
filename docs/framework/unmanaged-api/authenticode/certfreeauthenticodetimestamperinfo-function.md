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
ms.openlocfilehash: a8ecada29528b065ddad0abc80a850ee0f347f6b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787001"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="00386-102">Funkce CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="00386-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="00386-103">Uvolní prostředky přidělené pro strukturu [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="00386-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00386-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00386-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00386-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00386-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="00386-106">[in, out] Informace o časovém razítku, které se mají uvolnit</span><span class="sxs-lookup"><span data-stu-id="00386-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="00386-107">Podívejte se na strukturu [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="00386-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00386-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="00386-108">Return Value</span></span>  
 <span data-ttu-id="00386-109">`S_OK`Pokud je funkce úspěšná.</span><span class="sxs-lookup"><span data-stu-id="00386-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="00386-110">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="00386-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00386-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00386-111">See also</span></span>

- [<span data-ttu-id="00386-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="00386-112">Authenticode</span></span>](index.md)
