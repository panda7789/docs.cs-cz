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
ms.openlocfilehash: 37957931f9d1e2f8da44f70e5b99d3544bf0ae4f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497493"
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="079a9-102">Funkce _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="079a9-102">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="079a9-103">Vypočítá silným názvem token veřejného klíče z CSP publickeyblob – formátu.</span><span class="sxs-lookup"><span data-stu-id="079a9-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="079a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="079a9-104">Syntax</span></span>  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="079a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="079a9-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="079a9-106">[in] Zprostředkovatel kryptografických služeb blob veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="079a9-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="079a9-107">[out] Ukazatel na WCHAR \* pro příjem hexadecimální zakódovaná hodnota hash veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="079a9-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="079a9-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="079a9-108">Return Value</span></span>  
 <span data-ttu-id="079a9-109">`S_OK` Pokud je funkce úspěšná; v opačném případě `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="079a9-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="079a9-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="079a9-110">See also</span></span>
- [<span data-ttu-id="079a9-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="079a9-111">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
