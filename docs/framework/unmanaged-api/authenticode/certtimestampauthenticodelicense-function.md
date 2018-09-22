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
ms.openlocfilehash: fd77a8a81718837d55f3018564d0f4ba8fdc95ee
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46695895"
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="a4a69-102">Funkce CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="a4a69-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="a4a69-103">Časová razítka na Authenticode XrML licence.</span><span class="sxs-lookup"><span data-stu-id="a4a69-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4a69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4a69-104">Syntax</span></span>  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4a69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4a69-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="a4a69-106">[in] Podepsané Authenticode XrML licenci, která má být opatřená časovým razítkem.</span><span class="sxs-lookup"><span data-stu-id="a4a69-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="a4a69-107">Zobrazit [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="a4a69-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="a4a69-108">[in] Identifikátor URI serveru časového razítka.</span><span class="sxs-lookup"><span data-stu-id="a4a69-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="a4a69-109">[out] Ukazatel na CRYPT_DATA_BLOB přijímat časové razítko podpis s kódováním base64.</span><span class="sxs-lookup"><span data-stu-id="a4a69-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="a4a69-110">Je odpovědností volajícího uvolnit `pTimestampSignatureBlob` -> `pbData` s `HepFree()` po použití.</span><span class="sxs-lookup"><span data-stu-id="a4a69-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="a4a69-111">Zobrazit [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="a4a69-111">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4a69-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4a69-112">Remarks</span></span>  
 <span data-ttu-id="a4a69-113">Podpis časového razítka je ve skutečnosti zprávu PKCS #7 SignedData jehož obsah je binární forma SignatureValue z podpisu licence.</span><span class="sxs-lookup"><span data-stu-id="a4a69-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="a4a69-114">V podstatě slouží jako protipodpisu licence.</span><span class="sxs-lookup"><span data-stu-id="a4a69-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4a69-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a4a69-115">Return Value</span></span>  
 <span data-ttu-id="a4a69-116">`S_OK` Pokud je funkce úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a4a69-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="a4a69-117">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a4a69-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a69-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4a69-118">See Also</span></span>  
 [<span data-ttu-id="a4a69-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="a4a69-119">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
