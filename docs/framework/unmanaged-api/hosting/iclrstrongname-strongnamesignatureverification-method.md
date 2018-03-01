---
title: "ICLRStrongName::StrongNameSignatureVerification – metoda"
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
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b1d8cb0ac6c671dae6ca5985e4082e2d3e71d89e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="dc1cb-102">ICLRStrongName::StrongNameSignatureVerification – metoda</span><span class="sxs-lookup"><span data-stu-id="dc1cb-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>
<span data-ttu-id="dc1cb-103">Získá hodnotu, která určuje, zda manifest sestavení v zadaná cesta obsahuje podpis silného názvu, který bude ověřen podle zadaného příznaky.</span><span class="sxs-lookup"><span data-stu-id="dc1cb-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc1cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc1cb-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc1cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc1cb-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="dc1cb-106">[v] Cesta k přenosné spustitelný (.dll nebo .exe) soubor pro ověření sestavení.</span><span class="sxs-lookup"><span data-stu-id="dc1cb-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="dc1cb-107">[v] Příznaky chcete změnit chování ověření.</span><span class="sxs-lookup"><span data-stu-id="dc1cb-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="dc1cb-108">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="dc1cb-108">The following values are supported:</span></span>  
  
-   <span data-ttu-id="dc1cb-109">`SN_INFLAG_FORCE_VER`(0x00000001) - vynutí ověření i v případě, že je nutné přepsat nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="dc1cb-109">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="dc1cb-110">`SN_INFLAG_INSTALL`(0x00000002) - určuje, že to je prvním ověření manifestu.</span><span class="sxs-lookup"><span data-stu-id="dc1cb-110">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
-   <span data-ttu-id="dc1cb-111">`SN_INFLAG_ADMIN_ACCESS`(0x00000004). - Určuje, že mezipaměť povolí přístup pouze uživatelům, kteří mají oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="dc1cb-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="dc1cb-112">`SN_INFLAG_USER_ACCESS`(0x00000008) - určuje, že sestavení budou přístupné pouze pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="dc1cb-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="dc1cb-113">`SN_INFLAG_ALL_ACCESS`(0x00000010) - určuje, že mezipaměti bude poskytovat žádné záruky omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="dc1cb-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="dc1cb-114">`SN_INFLAG_RUNTIME`(0x80000000) - vyhrazená pro interní ladění.</span><span class="sxs-lookup"><span data-stu-id="dc1cb-114">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="dc1cb-115">[out] Příznaky udávající, zda se ověřit podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="dc1cb-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="dc1cb-116">Je podporován následující hodnotu:</span><span class="sxs-lookup"><span data-stu-id="dc1cb-116">The following value is supported:</span></span>  
  
-   <span data-ttu-id="dc1cb-117">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001) – Tato hodnota nastavena na `false` k určení, že ověření proběhlo úspěšně z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="dc1cb-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc1cb-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dc1cb-118">Return Value</span></span>  
 <span data-ttu-id="dc1cb-119">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="dc1cb-119">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc1cb-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc1cb-120">Requirements</span></span>  
 <span data-ttu-id="dc1cb-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc1cb-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc1cb-122">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="dc1cb-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="dc1cb-123">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dc1cb-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc1cb-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc1cb-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc1cb-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc1cb-125">See Also</span></span>  
 [<span data-ttu-id="dc1cb-126">StrongNameSignatureVerificationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="dc1cb-126">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="dc1cb-127">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc1cb-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
