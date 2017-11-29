---
title: Funkce _AxlRSAKeyValueToPublicKeyToken
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _AxlRSAKeyValueToPublicKeyToken
api_location: clr.dll
api_type: DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4af27a2abf1a0bcf4d79eda389c5f79f0ecb1eef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="3198b-102">Funkce _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="3198b-102">_AxlRSAKeyValueToPublicKeyToken Function</span></span>
<span data-ttu-id="3198b-103">Převede Exponent a Modulus silný název tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="3198b-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3198b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3198b-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3198b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3198b-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="3198b-106">[v] Objekt blob kódováním base64 numerického zbytku (z \<numerického zbytku > elementu).</span><span class="sxs-lookup"><span data-stu-id="3198b-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="3198b-107">Najdete v článku [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="3198b-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="3198b-108">[v] Objekt blob Exponent kódováním base64 (z \<Exponent > elementu).</span><span class="sxs-lookup"><span data-stu-id="3198b-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="3198b-109">Najdete v článku [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="3198b-109">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="3198b-110">[out] Ukazatel na WCHAR * přijímat kódováním šestnáctkově token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="3198b-110">[out] A pointer to WCHAR * to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3198b-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3198b-111">Return Value</span></span>  
 <span data-ttu-id="3198b-112">`S_OK`Pokud funkci se zdaří.</span><span class="sxs-lookup"><span data-stu-id="3198b-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="3198b-113">Jinak vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="3198b-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3198b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="3198b-114">See Also</span></span>  
 [<span data-ttu-id="3198b-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="3198b-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
