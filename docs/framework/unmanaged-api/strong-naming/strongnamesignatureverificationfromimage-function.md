---
title: StrongNameSignatureVerificationFromImage – funkce
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9baf207f46082a4bb1ece4dba39c98cdd125d073
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702103"
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="6c9d8-102">StrongNameSignatureVerificationFromImage – funkce</span><span class="sxs-lookup"><span data-stu-id="6c9d8-102">StrongNameSignatureVerificationFromImage Function</span></span>
<span data-ttu-id="6c9d8-103">Ověřuje, že je platný pro přidružené veřejný klíč sestavení, které je již namapováno na paměť.</span><span class="sxs-lookup"><span data-stu-id="6c9d8-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="6c9d8-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="6c9d8-104">This function has been deprecated.</span></span> <span data-ttu-id="6c9d8-105">Použití [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="6c9d8-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c9d8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c9d8-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c9d8-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c9d8-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="6c9d8-108">[in] Relativní virtuální adresu z namapované sestavení manifestu.</span><span class="sxs-lookup"><span data-stu-id="6c9d8-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="6c9d8-109">[in] Velikost v bajtech, z namapované bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="6c9d8-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="6c9d8-110">[in] Příznaky, které ovlivňují chování ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c9d8-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="6c9d8-111">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="6c9d8-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="6c9d8-112">`SN_INFLAG_FORCE_VER` (0x00000001) – vynutí ověření i v případě, že je potřeba přepsat nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="6c9d8-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="6c9d8-113">`SN_INFLAG_INSTALL` (0x00000002) - určuje, že se jedná o první ověřování prováděné na tomto obrázku.</span><span class="sxs-lookup"><span data-stu-id="6c9d8-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   <span data-ttu-id="6c9d8-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - určuje, že mezipaměť bude umožňovat přístup pouze uživatelům, kteří mají oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="6c9d8-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="6c9d8-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - určuje, zda sestavení přístupné pouze pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="6c9d8-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="6c9d8-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - určuje, že mezipaměť bude poskytovat žádné záruky omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="6c9d8-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="6c9d8-117">`SN_INFLAG_RUNTIME` (0x80000000) – vyhrazené pro interní ladění.</span><span class="sxs-lookup"><span data-stu-id="6c9d8-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="6c9d8-118">[out] Příznak pro další výstupní informace.</span><span class="sxs-lookup"><span data-stu-id="6c9d8-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="6c9d8-119">Je podporován následující hodnotu:</span><span class="sxs-lookup"><span data-stu-id="6c9d8-119">The following value is supported:</span></span>  
  
-   <span data-ttu-id="6c9d8-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) – Tato hodnota nastavená na `false` k určení, že ověření proběhlo úspěšně z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="6c9d8-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c9d8-121">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6c9d8-121">Return Value</span></span>  
 <span data-ttu-id="6c9d8-122">`true` Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="6c9d8-122">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c9d8-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c9d8-123">Remarks</span></span>  
 <span data-ttu-id="6c9d8-124">Pokud `StrongNameSignatureVerificationFromImage` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="6c9d8-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c9d8-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c9d8-125">Requirements</span></span>  
 <span data-ttu-id="6c9d8-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c9d8-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c9d8-127">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="6c9d8-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="6c9d8-128">**Knihovna:** Zahrnuté jako prostředek v mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6c9d8-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="6c9d8-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c9d8-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c9d8-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c9d8-130">See also</span></span>
- [<span data-ttu-id="6c9d8-131">StrongNameSignatureVerificationFromImage – metoda</span><span class="sxs-lookup"><span data-stu-id="6c9d8-131">StrongNameSignatureVerificationFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [<span data-ttu-id="6c9d8-132">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c9d8-132">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
