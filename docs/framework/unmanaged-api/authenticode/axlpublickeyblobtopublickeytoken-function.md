---
title: Funkce _AxlPublicKeyBlobToPublicKeyToken
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56333165d179abd79e82f1416342a2700029eb12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401671"
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="50f05-102">Funkce _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="50f05-102">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="50f05-103">Vypočítá silným názvem token veřejného klíče z formátu CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="50f05-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50f05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50f05-104">Syntax</span></span>  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50f05-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50f05-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="50f05-106">[v] Zprostředkovatel kryptografických služeb veřejného klíče objektu blob.</span><span class="sxs-lookup"><span data-stu-id="50f05-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="50f05-107">[out] Ukazatel na WCHAR \* přijímat kódováním šestnáctkově hodnota hash veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="50f05-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50f05-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="50f05-108">Return Value</span></span>  
 <span data-ttu-id="50f05-109">`S_OK` Pokud funkci úspěšně. v opačném případě `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="50f05-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f05-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="50f05-110">See Also</span></span>  
 [<span data-ttu-id="50f05-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="50f05-111">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
