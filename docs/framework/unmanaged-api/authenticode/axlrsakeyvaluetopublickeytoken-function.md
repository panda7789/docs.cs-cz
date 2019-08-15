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
ms.openlocfilehash: eca6c5fc61d4f7e80046102a560d228fc01e5292
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038413"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="36919-102">\_AxlRSAKeyValueToPublicKeyToken – funkce</span><span class="sxs-lookup"><span data-stu-id="36919-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="36919-103">Převede zbytek a exponent na token veřejného klíče silného názvu.</span><span class="sxs-lookup"><span data-stu-id="36919-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36919-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36919-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36919-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36919-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="36919-106">pro Objekt BLOB s kódováním Base64 (z \<modulu > prvku).</span><span class="sxs-lookup"><span data-stu-id="36919-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="36919-107">Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="36919-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="36919-108">pro Objekt BLOB exponentem kódovaný ve formátu Base64 ( \<z > elementu exponent).</span><span class="sxs-lookup"><span data-stu-id="36919-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="36919-109">Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="36919-109">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="36919-110">mimo Ukazatel na WCHAR \* pro příjem šestnáctkově zakódovaného tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="36919-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36919-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="36919-111">Return Value</span></span>  
 <span data-ttu-id="36919-112">`S_OK`Pokud je funkce úspěšná.</span><span class="sxs-lookup"><span data-stu-id="36919-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="36919-113">V opačném případě vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="36919-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36919-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36919-114">See also</span></span>

- [<span data-ttu-id="36919-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="36919-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
