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
ms.openlocfilehash: 6c2bb6f0324c461f59bd98a70333b176e79a16a6
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039595"
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="609f3-102">Funkce CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="609f3-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="609f3-103">Časová razítka licence XrML technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="609f3-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="609f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="609f3-104">Syntax</span></span>  
  
```cpp  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="609f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="609f3-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="609f3-106">pro Podepsaná licence technologie Authenticode pro technologii Authenticode, která bude označená časovým razítkem</span><span class="sxs-lookup"><span data-stu-id="609f3-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="609f3-107">Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="609f3-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="609f3-108">pro Identifikátor URI serveru časového razítka.</span><span class="sxs-lookup"><span data-stu-id="609f3-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="609f3-109">mimo Ukazatel na CRYPT_DATA_BLOB pro příjem signatury časového razítka kódovaného ve formátu base64.</span><span class="sxs-lookup"><span data-stu-id="609f3-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="609f3-110">Je zodpovědností volajícího, `pTimestampSignatureBlob` aby `HepFree()` po použití zadarmo ->. `pbData`</span><span class="sxs-lookup"><span data-stu-id="609f3-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="609f3-111">Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="609f3-111">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="609f3-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="609f3-112">Remarks</span></span>  
 <span data-ttu-id="609f3-113">Podpisem časového razítka je ve skutečnosti zpráva typu PKCS #7 SignedData, jejíž obsah je binární forma SignatureValue z podpisu licence.</span><span class="sxs-lookup"><span data-stu-id="609f3-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="609f3-114">V podstatě to funguje jako počítadlo signatury licence.</span><span class="sxs-lookup"><span data-stu-id="609f3-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="609f3-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="609f3-115">Return Value</span></span>  
 <span data-ttu-id="609f3-116">`S_OK`Pokud je funkce úspěšná.</span><span class="sxs-lookup"><span data-stu-id="609f3-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="609f3-117">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="609f3-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="609f3-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="609f3-118">See also</span></span>

- [<span data-ttu-id="609f3-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="609f3-119">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
