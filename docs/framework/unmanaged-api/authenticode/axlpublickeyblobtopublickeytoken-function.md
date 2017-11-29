---
title: Funkce _AxlPublicKeyBlobToPublicKeyToken
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _AxlPublicKeyBlobToPublicKeyToken
api_location: clr.dll
api_type: DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25a6a78fad95b894e82a75159458f25264f0ee0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="79ee9-102">Funkce _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="79ee9-102">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="79ee9-103">Vypočítá silným názvem token veřejného klíče z formátu CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="79ee9-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79ee9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79ee9-104">Syntax</span></span>  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79ee9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="79ee9-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="79ee9-106">[v] Zprostředkovatel kryptografických služeb veřejného klíče objektu blob.</span><span class="sxs-lookup"><span data-stu-id="79ee9-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="79ee9-107">[out] Ukazatel na WCHAR * přijímat kódováním šestnáctkově hodnota hash veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="79ee9-107">[out] A pointer to WCHAR * to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79ee9-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="79ee9-108">Return Value</span></span>  
 <span data-ttu-id="79ee9-109">`S_OK`Pokud funkci úspěšně. v opačném případě `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="79ee9-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79ee9-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="79ee9-110">See Also</span></span>  
 [<span data-ttu-id="79ee9-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="79ee9-111">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
