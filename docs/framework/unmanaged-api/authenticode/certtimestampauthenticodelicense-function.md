---
title: Funkce CertTimestampAuthenticodeLicense
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 53241a459f561bdfd8fc5cb077cb8384f1d906b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="492e9-102">Funkce CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="492e9-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="492e9-103">Časová razítka na Authenticode XrML licence.</span><span class="sxs-lookup"><span data-stu-id="492e9-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="492e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="492e9-104">Syntax</span></span>  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="492e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="492e9-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="492e9-106">[v] Podepsaný licence Authenticode XrML být časovým razítkem.</span><span class="sxs-lookup"><span data-stu-id="492e9-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="492e9-107">Najdete v článku [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="492e9-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="492e9-108">[v] Identifikátor URI serveru časového razítka.</span><span class="sxs-lookup"><span data-stu-id="492e9-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="492e9-109">[out] Ukazatel na CRYPT_DATA_BLOB přijímat časové razítko podpis kódováním base64.</span><span class="sxs-lookup"><span data-stu-id="492e9-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="492e9-110">Je zodpovědností volajícího k bezplatným `pTimestampSignatureBlob` -> `pbData` s `HepFree()` po použití.</span><span class="sxs-lookup"><span data-stu-id="492e9-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="492e9-111">Najdete v článku [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="492e9-111">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="492e9-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="492e9-112">Remarks</span></span>  
 <span data-ttu-id="492e9-113">Podpis časové razítko je ve skutečnosti PKCS #7 SignedData zpráva, jejíž obsah je binární formu SignatureValue z podpisu s licencí.</span><span class="sxs-lookup"><span data-stu-id="492e9-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="492e9-114">V podstatě to funguje jako kontrolní podpis licence.</span><span class="sxs-lookup"><span data-stu-id="492e9-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="492e9-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="492e9-115">Return Value</span></span>  
 <span data-ttu-id="492e9-116">`S_OK`Pokud funkci se zdaří.</span><span class="sxs-lookup"><span data-stu-id="492e9-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="492e9-117">Jinak vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="492e9-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="492e9-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="492e9-118">See Also</span></span>  
 [<span data-ttu-id="492e9-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="492e9-119">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
