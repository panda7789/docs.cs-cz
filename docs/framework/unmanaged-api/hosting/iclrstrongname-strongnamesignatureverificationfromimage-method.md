---
title: "ICLRStrongName::StrongNameSignatureVerificationFromImage – metoda"
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
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 57c8422d59a07de9ad045f2043594cb8d01f2f74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="2b0a4-102">ICLRStrongName::StrongNameSignatureVerificationFromImage – metoda</span><span class="sxs-lookup"><span data-stu-id="2b0a4-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="2b0a4-103">Ověřuje, že je sestavení, které už je namapovaný na paměť pro přidružené veřejný klíč platný.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b0a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b0a4-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b0a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b0a4-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="2b0a4-106">[v] Relativní virtuální adresa manifest namapované sestavení.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2b0a4-107">[v] Velikost v bajtech, namapované bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="2b0a4-108">[v] Příznaky, které ovlivňují chování ověření.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="2b0a4-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="2b0a4-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="2b0a4-110">`SN_INFLAG_FORCE_VER`(0x00000001) - vynutí ověření i v případě, že je nutné přepsat nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="2b0a4-111">`SN_INFLAG_INSTALL`(0x00000002) - určuje, že se jedná o první ověření provést na tuto bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   <span data-ttu-id="2b0a4-112">`SN_INFLAG_ADMIN_ACCESS`(0x00000004). - Určuje, že mezipaměť povolí přístup pouze uživatelům, kteří mají oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="2b0a4-113">`SN_INFLAG_USER_ACCESS`(0x00000008) - určuje, že sestavení budou přístupné pouze pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="2b0a4-114">`SN_INFLAG_ALL_ACCESS`(0x00000010) - určuje, že mezipaměti bude poskytovat žádné záruky omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="2b0a4-115">`SN_INFLAG_RUNTIME`(0x80000000) - vyhrazená pro interní ladění.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="2b0a4-116">[out] Příznak pro další výstupní informace.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="2b0a4-117">Je podporován následující hodnotu:</span><span class="sxs-lookup"><span data-stu-id="2b0a4-117">The following value is supported:</span></span>  
  
-   <span data-ttu-id="2b0a4-118">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001) – Tato hodnota nastavena na `false` k určení, že ověření proběhlo úspěšně z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b0a4-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2b0a4-119">Return Value</span></span>  
 <span data-ttu-id="2b0a4-120">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="2b0a4-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b0a4-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b0a4-121">Requirements</span></span>  
 <span data-ttu-id="2b0a4-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b0a4-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b0a4-123">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2b0a4-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2b0a4-124">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2b0a4-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b0a4-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b0a4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b0a4-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b0a4-126">See Also</span></span>  
 [<span data-ttu-id="2b0a4-127">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b0a4-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
