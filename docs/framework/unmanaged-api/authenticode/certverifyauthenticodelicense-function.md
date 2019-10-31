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
ms.openlocfilehash: 7cd25a24533b04dc45ee734f9e9639391311405a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099732"
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="19dd3-102">Funkce CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="19dd3-102">CertVerifyAuthenticodeLicense Function</span></span>
<span data-ttu-id="19dd3-103">Ověřuje platnost licence na technologii Authenticode pro technologii Authenticode.</span><span class="sxs-lookup"><span data-stu-id="19dd3-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19dd3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19dd3-104">Syntax</span></span>  
  
```cpp  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19dd3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19dd3-105">Parameters</span></span>  
 `pLicenseBlob`  
 <span data-ttu-id="19dd3-106">pro Licence Authenticode pro technologii Authenticode, která se má ověřit.</span><span class="sxs-lookup"><span data-stu-id="19dd3-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="19dd3-107">Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="19dd3-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="19dd3-108">pro Volitelné.</span><span class="sxs-lookup"><span data-stu-id="19dd3-108">[in] Optional.</span></span> <span data-ttu-id="19dd3-109">Kombinace následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="19dd3-109">A combination of following values:</span></span>  
  
- <span data-ttu-id="19dd3-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="19dd3-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
- <span data-ttu-id="19dd3-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="19dd3-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
- <span data-ttu-id="19dd3-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="19dd3-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
- <span data-ttu-id="19dd3-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="19dd3-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
- <span data-ttu-id="19dd3-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="19dd3-114">AXL_LIFETIME_SIGNING</span></span>  
  
- <span data-ttu-id="19dd3-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="19dd3-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="19dd3-116">mimo Pro získání informací o podepisující osobě.</span><span class="sxs-lookup"><span data-stu-id="19dd3-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="19dd3-117">Pokud licence není podepsaná, `dwError` je nastavená na TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="19dd3-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="19dd3-118">Je zodpovědností volajícího uvolnit prostředky pomocí funkce [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) po použití.</span><span class="sxs-lookup"><span data-stu-id="19dd3-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="19dd3-119">Viz [Struktura AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="19dd3-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="19dd3-120">mimo Pro získání informací o časovém razítku, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="19dd3-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="19dd3-121">Pokud licence nebyla označena časovým razítkem, `dwError` je nastavená na TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="19dd3-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="19dd3-122">Je zodpovědností volajícího uvolnit prostředky pomocí funkce [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) po použití.</span><span class="sxs-lookup"><span data-stu-id="19dd3-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="19dd3-123">Viz [Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="19dd3-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19dd3-124">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="19dd3-124">Return Value</span></span>  
 <span data-ttu-id="19dd3-125">Pokud je úspěšná, vrátí `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="19dd3-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="19dd3-126">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="19dd3-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19dd3-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19dd3-127">See also</span></span>

- [<span data-ttu-id="19dd3-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="19dd3-128">Authenticode</span></span>](index.md)
- [<span data-ttu-id="19dd3-129">GetHashFromHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="19dd3-129">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="19dd3-130">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19dd3-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
