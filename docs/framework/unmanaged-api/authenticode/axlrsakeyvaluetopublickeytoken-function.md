---
title: _AxlRSAKeyValueToPublicKeyToken – funkce
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
ms.openlocfilehash: 690035ffe0724d3987a198c78bf14e668527b98a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787023"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="6d0f1-102">\_AxlRSAKeyValueToPublicKeyToken – funkce</span><span class="sxs-lookup"><span data-stu-id="6d0f1-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="6d0f1-103">Převede zbytek a exponent na token veřejného klíče silného názvu.</span><span class="sxs-lookup"><span data-stu-id="6d0f1-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d0f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d0f1-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d0f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d0f1-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="6d0f1-106">pro Objekt BLOB s kódováním Base64 (z \<modulu > prvku).</span><span class="sxs-lookup"><span data-stu-id="6d0f1-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="6d0f1-107">Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="6d0f1-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="6d0f1-108">pro Objekt BLOB exponentem kódovaný ve formátu Base64 ( \<z > elementu exponent).</span><span class="sxs-lookup"><span data-stu-id="6d0f1-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="6d0f1-109">Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="6d0f1-109">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="6d0f1-110">mimo Ukazatel na WCHAR \* pro příjem šestnáctkově zakódovaného tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="6d0f1-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d0f1-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6d0f1-111">Return Value</span></span>  
 <span data-ttu-id="6d0f1-112">`S_OK`Pokud je funkce úspěšná.</span><span class="sxs-lookup"><span data-stu-id="6d0f1-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="6d0f1-113">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="6d0f1-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d0f1-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d0f1-114">See also</span></span>

- [<span data-ttu-id="6d0f1-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="6d0f1-115">Authenticode</span></span>](index.md)
