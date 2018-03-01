---
title: "ICLRStrongName::StrongNameSignatureVerificationEx – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 047bc2212e1552a52f0eabf86cc0e86a6945ba39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="64de6-102">ICLRStrongName::StrongNameSignatureVerificationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="64de6-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>
<span data-ttu-id="64de6-103">Získá hodnotu, která určuje, zda manifest sestavení v zadaná cesta obsahuje podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="64de6-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64de6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64de6-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64de6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64de6-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="64de6-106">[v] Cesta k přenosné spustitelný soubor (.exe nebo .dll) souboru pro sestavení, které má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="64de6-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="64de6-107">[v] `true` provést ověření, i když je nezbytné pro přepsání nastavení registru; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="64de6-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="64de6-108">[out] `true` Pokud podpis silného názvu byl ověřený, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="64de6-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="64de6-109">`pfWasVerified`je také nastavena na `false` Pokud ověření bylo úspěšné z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="64de6-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64de6-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="64de6-110">Return Value</span></span>  
 <span data-ttu-id="64de6-111">`S_OK`Pokud ověření byla úspěšná. jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="64de6-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64de6-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64de6-112">Remarks</span></span>  
 <span data-ttu-id="64de6-113">[Iclrstrongname::strongnamesignatureverificationex –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) metoda poskytuje podobné funkce [iclrstrongname::strongnamesignatureverification –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="64de6-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="64de6-114">Ale druhý vstupní parametr a výstupní parametr pro [iclrstrongname::strongnamesignatureverificationex –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) typu `BOOLEAN` místo `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="64de6-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64de6-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64de6-115">Requirements</span></span>  
 <span data-ttu-id="64de6-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64de6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64de6-117">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="64de6-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="64de6-118">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="64de6-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64de6-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64de6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64de6-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="64de6-120">See Also</span></span>  
 [<span data-ttu-id="64de6-121">StrongNameSignatureVerification – metoda</span><span class="sxs-lookup"><span data-stu-id="64de6-121">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="64de6-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64de6-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
