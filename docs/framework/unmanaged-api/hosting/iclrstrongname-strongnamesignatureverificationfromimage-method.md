---
title: ICLRStrongName::StrongNameSignatureVerificationFromImage – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7e09ac96a8803f41d78b532c9da67315e5dd6b4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113734"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="50a3e-102">ICLRStrongName::StrongNameSignatureVerificationFromImage – metoda</span><span class="sxs-lookup"><span data-stu-id="50a3e-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="50a3e-103">Ověřuje, že je platný pro přidružené veřejný klíč sestavení, které je již namapováno na paměť.</span><span class="sxs-lookup"><span data-stu-id="50a3e-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50a3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50a3e-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50a3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50a3e-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="50a3e-106">[in] Relativní virtuální adresu z namapované sestavení manifestu.</span><span class="sxs-lookup"><span data-stu-id="50a3e-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="50a3e-107">[in] Velikost v bajtech, z namapované bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="50a3e-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="50a3e-108">[in] Příznaky, které ovlivňují chování ověřování.</span><span class="sxs-lookup"><span data-stu-id="50a3e-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="50a3e-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="50a3e-109">The following values are supported:</span></span>  
  
-   `SN_INFLAG_FORCE_VER` <span data-ttu-id="50a3e-110">(0x00000001) – vynutí ověření i v případě, že je potřeba přepsat nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="50a3e-110">(0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   `SN_INFLAG_INSTALL` <span data-ttu-id="50a3e-111">(0x00000002) - určuje, že se jedná o první ověřování prováděné na tomto obrázku.</span><span class="sxs-lookup"><span data-stu-id="50a3e-111">(0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   `SN_INFLAG_ADMIN_ACCESS` <span data-ttu-id="50a3e-112">(0x00000004) - určuje, že mezipaměť bude umožňovat přístup pouze uživatelům, kteří mají oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="50a3e-112">(0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   `SN_INFLAG_USER_ACCESS` <span data-ttu-id="50a3e-113">(0x00000008) - určuje, zda sestavení přístupné pouze pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="50a3e-113">(0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   `SN_INFLAG_ALL_ACCESS` <span data-ttu-id="50a3e-114">(0x00000010) - určuje, že mezipaměť bude poskytovat žádné záruky omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="50a3e-114">(0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   `SN_INFLAG_RUNTIME` <span data-ttu-id="50a3e-115">(0x80000000) – vyhrazené pro interní ladění.</span><span class="sxs-lookup"><span data-stu-id="50a3e-115">(0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="50a3e-116">[out] Příznak pro další výstupní informace.</span><span class="sxs-lookup"><span data-stu-id="50a3e-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="50a3e-117">Je podporován následující hodnotu:</span><span class="sxs-lookup"><span data-stu-id="50a3e-117">The following value is supported:</span></span>  
  
-   `SN_OUTFLAG_WAS_VERIFIED` <span data-ttu-id="50a3e-118">(0x00000001) – Tato hodnota nastavená na `false` k určení, že ověření proběhlo úspěšně z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="50a3e-118">(0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50a3e-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="50a3e-119">Return Value</span></span>  
 `S_OK` <span data-ttu-id="50a3e-120">Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="50a3e-120">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50a3e-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50a3e-121">Requirements</span></span>  
 <span data-ttu-id="50a3e-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50a3e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50a3e-123">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="50a3e-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="50a3e-124">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50a3e-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="50a3e-125">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="50a3e-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="50a3e-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50a3e-126">See also</span></span>

- [<span data-ttu-id="50a3e-127">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50a3e-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
