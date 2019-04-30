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
ms.openlocfilehash: 1b2535441da173ee13653c68f25039fd1431261a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948951"
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="d4956-102">Funkce _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="d4956-102">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="d4956-103">Vypočítá silným názvem token veřejného klíče z CSP publickeyblob – formátu.</span><span class="sxs-lookup"><span data-stu-id="d4956-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4956-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4956-104">Syntax</span></span>  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4956-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4956-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="d4956-106">[in] Zprostředkovatel kryptografických služeb blob veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="d4956-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="d4956-107">[out] Ukazatel na WCHAR \* pro příjem hexadecimální zakódovaná hodnota hash veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="d4956-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4956-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d4956-108">Return Value</span></span>  
 <span data-ttu-id="d4956-109">`S_OK` Pokud je funkce úspěšná; v opačném případě `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="d4956-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4956-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4956-110">See also</span></span>

- [<span data-ttu-id="d4956-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="d4956-111">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
