---
title: Funkce _AxlRSAKeyValueToPublicKeyToken
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e09391af9b5d71cfa423b3bf1a2b307117d0dee1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385884"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="3f440-102">\_AxlRSAKeyValueToPublicKeyToken – funkce</span><span class="sxs-lookup"><span data-stu-id="3f440-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="3f440-103">Převede operace modulo a Exponent token veřejného klíče silného názvu.</span><span class="sxs-lookup"><span data-stu-id="3f440-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f440-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f440-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
### <a name="parameters"></a><span data-ttu-id="3f440-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f440-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="3f440-106">[in] Tento objekt blob s kódováním base64 numerického zbytku (z \<numerického zbytku > element).</span><span class="sxs-lookup"><span data-stu-id="3f440-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="3f440-107">Zobrazit [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="3f440-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="3f440-108">[in] Exponent blob s kódováním base64 (z \<Exponent > element).</span><span class="sxs-lookup"><span data-stu-id="3f440-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="3f440-109">Zobrazit [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="3f440-109">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="3f440-110">[out] Ukazatel na WCHAR \* pro příjem šestnáctkově zakódovaného token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="3f440-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f440-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3f440-111">Return Value</span></span>  
 <span data-ttu-id="3f440-112">`S_OK` Pokud je funkce úspěšná.</span><span class="sxs-lookup"><span data-stu-id="3f440-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="3f440-113">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="3f440-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f440-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f440-114">See Also</span></span>  
 [<span data-ttu-id="3f440-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="3f440-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
