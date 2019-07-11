---
title: Funkce CertVerifyAuthenticodeLicense
ms.date: 03/30/2017
api_name:
- CertVerifyAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf7e997282351cc10dd6da1fc405366ea67c7307
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741094"
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="a0123-102">Funkce CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="a0123-102">CertVerifyAuthenticodeLicense Function</span></span>
<span data-ttu-id="a0123-103">Ověří platnost licence k Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="a0123-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0123-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0123-104">Syntax</span></span>  
  
```cpp  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0123-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0123-105">Parameters</span></span>  
 `pLicenseBlob`  
 <span data-ttu-id="a0123-106">[in] Licence technologie Authenticode XrML ověření.</span><span class="sxs-lookup"><span data-stu-id="a0123-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="a0123-107">Zobrazit [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="a0123-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a0123-108">[in] Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a0123-108">[in] Optional.</span></span> <span data-ttu-id="a0123-109">Kombinací těchto hodnot:</span><span class="sxs-lookup"><span data-stu-id="a0123-109">A combination of following values:</span></span>  
  
- <span data-ttu-id="a0123-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="a0123-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
- <span data-ttu-id="a0123-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="a0123-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
- <span data-ttu-id="a0123-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="a0123-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
- <span data-ttu-id="a0123-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="a0123-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
- <span data-ttu-id="a0123-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="a0123-114">AXL_LIFETIME_SIGNING</span></span>  
  
- <span data-ttu-id="a0123-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="a0123-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="a0123-116">[out] Získat informace podepisující osoby.</span><span class="sxs-lookup"><span data-stu-id="a0123-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="a0123-117">Pokud nebyla podepsána licence, `dwError` je nastavena na TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="a0123-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="a0123-118">Je odpovědností volajícího k uvolnění prostředků s použitím [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) funkce po použití.</span><span class="sxs-lookup"><span data-stu-id="a0123-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="a0123-119">Zobrazit [struktura AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="a0123-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="a0123-120">[out] Získat čas stamper informace, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a0123-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="a0123-121">Pokud licence nebyla časovým razítkem, `dwError` je nastavena na TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="a0123-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="a0123-122">Je odpovědností volajícího k uvolnění prostředků s použitím [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) funkce po použití.</span><span class="sxs-lookup"><span data-stu-id="a0123-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="a0123-123">Zobrazit [struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="a0123-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0123-124">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a0123-124">Return Value</span></span>  
 <span data-ttu-id="a0123-125">Vrátí `S_OK` v případě úspěšného ověření.</span><span class="sxs-lookup"><span data-stu-id="a0123-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="a0123-126">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a0123-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0123-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0123-127">See also</span></span>

- [<span data-ttu-id="a0123-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="a0123-128">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
- [<span data-ttu-id="a0123-129">GetHashFromHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="a0123-129">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="a0123-130">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0123-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
