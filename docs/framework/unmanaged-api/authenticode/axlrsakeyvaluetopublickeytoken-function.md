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
ms.openlocfilehash: 49476a4417e5431842f8e2ba0371c53c5c9f03e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948890"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="74a30-102">\_AxlRSAKeyValueToPublicKeyToken – funkce</span><span class="sxs-lookup"><span data-stu-id="74a30-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="74a30-103">Převede operace modulo a Exponent token veřejného klíče silného názvu.</span><span class="sxs-lookup"><span data-stu-id="74a30-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74a30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74a30-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74a30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="74a30-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="74a30-106">[in] Tento objekt blob s kódováním base64 numerického zbytku (z \<numerického zbytku > element).</span><span class="sxs-lookup"><span data-stu-id="74a30-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="74a30-107">Zobrazit [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="74a30-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="74a30-108">[in] Exponent blob s kódováním base64 (z \<Exponent > element).</span><span class="sxs-lookup"><span data-stu-id="74a30-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="74a30-109">Zobrazit [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.</span><span class="sxs-lookup"><span data-stu-id="74a30-109">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="74a30-110">[out] Ukazatel na WCHAR \* pro příjem šestnáctkově zakódovaného token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="74a30-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74a30-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="74a30-111">Return Value</span></span>  
 <span data-ttu-id="74a30-112">`S_OK` Pokud je funkce úspěšná.</span><span class="sxs-lookup"><span data-stu-id="74a30-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="74a30-113">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="74a30-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a30-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74a30-114">See also</span></span>

- [<span data-ttu-id="74a30-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="74a30-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
