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
ms.workload: dotnet
ms.openlocfilehash: b1380f658d9c154d9ea41228cace5f9a3eed39b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="d3c26-102">Funkce _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="d3c26-102">_AxlRSAKeyValueToPublicKeyToken Function</span></span>
<span data-ttu-id="d3c26-103">Převede Exponent a Modulus silný název tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="d3c26-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3c26-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3c26-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3c26-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3c26-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="d3c26-106">[v] Objekt blob kódováním base64 numerického zbytku (z \<numerického zbytku > elementu).</span><span class="sxs-lookup"><span data-stu-id="d3c26-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="d3c26-107">Najdete v článku [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="d3c26-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="d3c26-108">[v] Objekt blob Exponent kódováním base64 (z \<Exponent > elementu).</span><span class="sxs-lookup"><span data-stu-id="d3c26-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="d3c26-109">Najdete v článku [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="d3c26-109">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="d3c26-110">[out] Ukazatel na WCHAR * přijímat kódováním šestnáctkově token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="d3c26-110">[out] A pointer to WCHAR * to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3c26-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d3c26-111">Return Value</span></span>  
 <span data-ttu-id="d3c26-112">`S_OK`Pokud funkci se zdaří.</span><span class="sxs-lookup"><span data-stu-id="d3c26-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="d3c26-113">Jinak vrátí kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d3c26-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3c26-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3c26-114">See Also</span></span>  
 [<span data-ttu-id="d3c26-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="d3c26-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
