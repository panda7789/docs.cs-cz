---
title: Funkce CertTimestampAuthenticodeLicense
ms.date: 03/30/2017
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7b336d1372bdbe0d6dbdcf79d94e14c30ad2ebe
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497337"
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="12cae-102">Funkce CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="12cae-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="12cae-103">Časová razítka na Authenticode XrML licence.</span><span class="sxs-lookup"><span data-stu-id="12cae-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12cae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12cae-104">Syntax</span></span>  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12cae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12cae-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="12cae-106">[in] Podepsané Authenticode XrML licenci, která má být opatřená časovým razítkem.</span><span class="sxs-lookup"><span data-stu-id="12cae-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="12cae-107">Zobrazit [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="12cae-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="12cae-108">[in] Identifikátor URI serveru časového razítka.</span><span class="sxs-lookup"><span data-stu-id="12cae-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="12cae-109">[out] Ukazatel na CRYPT_DATA_BLOB přijímat časové razítko podpis s kódováním base64.</span><span class="sxs-lookup"><span data-stu-id="12cae-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="12cae-110">Je odpovědností volajícího uvolnit `pTimestampSignatureBlob` -> `pbData` s `HepFree()` po použití.</span><span class="sxs-lookup"><span data-stu-id="12cae-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="12cae-111">Zobrazit [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="12cae-111">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12cae-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12cae-112">Remarks</span></span>  
 <span data-ttu-id="12cae-113">Podpis časového razítka je ve skutečnosti zprávu PKCS #7 SignedData jehož obsah je binární forma SignatureValue z podpisu licence.</span><span class="sxs-lookup"><span data-stu-id="12cae-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="12cae-114">V podstatě slouží jako protipodpisu licence.</span><span class="sxs-lookup"><span data-stu-id="12cae-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12cae-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="12cae-115">Return Value</span></span>  
 <span data-ttu-id="12cae-116">`S_OK` Pokud je funkce úspěšná.</span><span class="sxs-lookup"><span data-stu-id="12cae-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="12cae-117">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="12cae-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12cae-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12cae-118">See also</span></span>
- [<span data-ttu-id="12cae-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="12cae-119">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
