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
ms.openlocfilehash: 33b8f47813a3bf43bd69741c9febb150fa3a92e3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099897"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="0bf06-102">\_funkce AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="0bf06-102">\_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="0bf06-103">Vypočítá token veřejného klíče se silným názvem z formátu PublicKeyBlob – CSP.</span><span class="sxs-lookup"><span data-stu-id="0bf06-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bf06-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bf06-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bf06-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bf06-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="0bf06-106">pro Objekt blob veřejného klíče CSP</span><span class="sxs-lookup"><span data-stu-id="0bf06-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="0bf06-107">mimo Ukazatel na WCHAR \* pro příjem šestnáctkově zakódované hodnoty hash veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="0bf06-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0bf06-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0bf06-108">Return Value</span></span>  
 <span data-ttu-id="0bf06-109">`S_OK`, zda je funkce úspěšná; jinak `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="0bf06-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bf06-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0bf06-110">See also</span></span>

- [<span data-ttu-id="0bf06-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="0bf06-111">Authenticode</span></span>](index.md)
