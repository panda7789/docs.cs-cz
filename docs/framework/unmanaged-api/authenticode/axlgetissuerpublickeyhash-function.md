---
title: Funkce _AxlGetIssuerPublicKeyHash
ms.date: 03/30/2017
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408b71bf38427d12418e05f8b509fe841bc95ef1
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752268"
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="db98b-102">Funkce _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="db98b-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="db98b-103">Načte hodnotu hash SHA-1 veřejný klíč přidružený privátní klíč, který se používá k podepsání zadaný certifikát.</span><span class="sxs-lookup"><span data-stu-id="db98b-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db98b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db98b-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db98b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db98b-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="db98b-106">[in] Zprostředkovatel kryptografických služeb blob veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="db98b-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="db98b-107">Zobrazit [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="db98b-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="db98b-108">[out] Ukazatel na WCHAR \* pro příjem šestnáctkově zakódovaného token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="db98b-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db98b-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="db98b-109">Return Value</span></span>  
 <span data-ttu-id="db98b-110">`S_OK` Pokud je funkce úspěšná; v opačném případě `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="db98b-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db98b-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="db98b-111">See Also</span></span>  
 [<span data-ttu-id="db98b-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="db98b-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
