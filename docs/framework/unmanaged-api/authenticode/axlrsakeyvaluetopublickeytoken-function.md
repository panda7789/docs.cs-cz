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
ms.openlocfilehash: 7ef73f0f7599fdff887437756a5995591fd8ec89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402406"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="4593f-102">Funkce _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="4593f-102">_AxlRSAKeyValueToPublicKeyToken Function</span></span>
<span data-ttu-id="4593f-103">Převede Exponent a Modulus silný název tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="4593f-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4593f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4593f-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4593f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4593f-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="4593f-106">[v] Objekt blob kódováním base64 numerického zbytku (z \<numerického zbytku > elementu).</span><span class="sxs-lookup"><span data-stu-id="4593f-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="4593f-107">Najdete v článku [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="4593f-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="4593f-108">[v] Objekt blob Exponent kódováním base64 (z \<Exponent > elementu).</span><span class="sxs-lookup"><span data-stu-id="4593f-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="4593f-109">Najdete v článku [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="4593f-109">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="4593f-110">[out] Ukazatel na WCHAR \* přijímat kódováním šestnáctkově token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="4593f-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4593f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4593f-111">Return Value</span></span>  
 <span data-ttu-id="4593f-112">`S_OK` Pokud funkci se zdaří.</span><span class="sxs-lookup"><span data-stu-id="4593f-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="4593f-113">Jinak vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="4593f-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4593f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="4593f-114">See Also</span></span>  
 [<span data-ttu-id="4593f-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="4593f-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
