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
ms.openlocfilehash: 1cfc2f5cde22bf63275dd4bdc65857ac1d51b3fe
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038421"
---
# <a name="_axlgetissuerpublickeyhash-function"></a><span data-ttu-id="9ba90-102">\_AxlGetIssuerPublicKeyHash – funkce</span><span class="sxs-lookup"><span data-stu-id="9ba90-102">\_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="9ba90-103">Načte hodnotu hash SHA-1 veřejného klíče přidruženého k privátnímu klíči, který se používá k podepsání zadaného certifikátu.</span><span class="sxs-lookup"><span data-stu-id="9ba90-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ba90-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ba90-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ba90-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ba90-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="9ba90-106">pro Objekt blob veřejného klíče CSP</span><span class="sxs-lookup"><span data-stu-id="9ba90-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="9ba90-107">Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="9ba90-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="9ba90-108">mimo Ukazatel na WCHAR \* pro příjem šestnáctkově zakódovaného tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="9ba90-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ba90-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9ba90-109">Return Value</span></span>  
 <span data-ttu-id="9ba90-110">`S_OK`Pokud je funkce úspěšná; v `S_FALSE`opačném případě.</span><span class="sxs-lookup"><span data-stu-id="9ba90-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba90-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ba90-111">See also</span></span>

- [<span data-ttu-id="9ba90-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="9ba90-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
