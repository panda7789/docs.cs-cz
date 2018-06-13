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
ms.openlocfilehash: b197aa539e60a9dbcee55cf190c44b45da3a5fb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402012"
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="55242-102">Funkce _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="55242-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="55242-103">Načte hodnotu hash SHA-1 veřejný klíč přidružený privátní klíč, který se používá k podepisování zadaný certifikát.</span><span class="sxs-lookup"><span data-stu-id="55242-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55242-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55242-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55242-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55242-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="55242-106">[v] Zprostředkovatel kryptografických služeb veřejného klíče objektu blob.</span><span class="sxs-lookup"><span data-stu-id="55242-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="55242-107">Najdete v článku [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="55242-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="55242-108">[out] Ukazatel na WCHAR \* přijímat kódováním šestnáctkově token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="55242-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55242-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="55242-109">Return Value</span></span>  
 <span data-ttu-id="55242-110">`S_OK` Pokud funkci úspěšně. v opačném případě `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="55242-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55242-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="55242-111">See Also</span></span>  
 [<span data-ttu-id="55242-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="55242-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
