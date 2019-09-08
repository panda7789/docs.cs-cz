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
ms.openlocfilehash: aaf76d4c3d0f5fb59aeb35fae7a7020ee97b74d6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776487"
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="a8dab-102">Funkce CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="a8dab-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="a8dab-103">Časová razítka licence XrML technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="a8dab-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8dab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8dab-104">Syntax</span></span>  
  
```cpp  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8dab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8dab-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="a8dab-106">pro Podepsaná licence technologie Authenticode pro technologii Authenticode, která bude označená časovým razítkem</span><span class="sxs-lookup"><span data-stu-id="a8dab-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="a8dab-107">Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="a8dab-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="a8dab-108">pro Identifikátor URI serveru časového razítka.</span><span class="sxs-lookup"><span data-stu-id="a8dab-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="a8dab-109">mimo Ukazatel na CRYPT_DATA_BLOB pro příjem signatury časového razítka kódovaného ve formátu base64.</span><span class="sxs-lookup"><span data-stu-id="a8dab-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="a8dab-110">Je zodpovědností volajícího, `pTimestampSignatureBlob` aby `HepFree()` po použití zadarmo ->. `pbData`</span><span class="sxs-lookup"><span data-stu-id="a8dab-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="a8dab-111">Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="a8dab-111">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8dab-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8dab-112">Remarks</span></span>  
 <span data-ttu-id="a8dab-113">Podpisem časového razítka je ve skutečnosti zpráva typu PKCS #7 SignedData, jejíž obsah je binární forma SignatureValue z podpisu licence.</span><span class="sxs-lookup"><span data-stu-id="a8dab-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="a8dab-114">V podstatě to funguje jako počítadlo signatury licence.</span><span class="sxs-lookup"><span data-stu-id="a8dab-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8dab-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a8dab-115">Return Value</span></span>  
 <span data-ttu-id="a8dab-116">`S_OK`Pokud je funkce úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a8dab-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="a8dab-117">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a8dab-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8dab-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8dab-118">See also</span></span>

- [<span data-ttu-id="a8dab-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="a8dab-119">Authenticode</span></span>](index.md)
