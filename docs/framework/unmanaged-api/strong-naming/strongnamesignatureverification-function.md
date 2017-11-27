---
title: "StrongNameSignatureVerification – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureVerification
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureVerification
helpviewer_keywords: StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a2c04aba5b774b299e26be8dc532b894b6c6fad5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="a51c3-102">StrongNameSignatureVerification – funkce</span><span class="sxs-lookup"><span data-stu-id="a51c3-102">StrongNameSignatureVerification Function</span></span>
<span data-ttu-id="a51c3-103">Získá hodnotu označující, zda manifest sestavení v zadaná cesta obsahuje podpis silného názvu, který bude ověřen podle zadaného příznaky.</span><span class="sxs-lookup"><span data-stu-id="a51c3-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="a51c3-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="a51c3-104">This function has been deprecated.</span></span> <span data-ttu-id="a51c3-105">Použití [iclrstrongname::strongnamesignatureverification –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="a51c3-105">Use the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a51c3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a51c3-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a51c3-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a51c3-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="a51c3-108">[v] Cesta k přenosné spustitelný (.dll nebo .exe) soubor pro ověření sestavení.</span><span class="sxs-lookup"><span data-stu-id="a51c3-108">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="a51c3-109">[v] Příznaky chcete změnit chování ověření.</span><span class="sxs-lookup"><span data-stu-id="a51c3-109">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="a51c3-110">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="a51c3-110">The following values are supported:</span></span>  
  
-   <span data-ttu-id="a51c3-111">`SN_INFLAG_FORCE_VER`(0x00000001) - vynutí ověření i v případě, že je nutné přepsat nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="a51c3-111">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="a51c3-112">`SN_INFLAG_INSTALL`(0x00000002) - určuje, že to je prvním ověření manifestu.</span><span class="sxs-lookup"><span data-stu-id="a51c3-112">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
-   <span data-ttu-id="a51c3-113">`SN_INFLAG_ADMIN_ACCESS`(0x00000004). - Určuje, že mezipaměť povolí přístup pouze uživatelům, kteří mají oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="a51c3-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="a51c3-114">`SN_INFLAG_USER_ACCESS`(0x00000008) - určuje, že sestavení budou přístupné pouze pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="a51c3-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="a51c3-115">`SN_INFLAG_ALL_ACCESS`(0x00000010) - určuje, že mezipaměti bude poskytovat žádné záruky omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="a51c3-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="a51c3-116">`SN_INFLAG_RUNTIME`(0x80000000) - vyhrazená pro interní ladění.</span><span class="sxs-lookup"><span data-stu-id="a51c3-116">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="a51c3-117">[out] Příznaky udávající, zda se ověřit podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="a51c3-117">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="a51c3-118">Je podporován následující hodnotu:</span><span class="sxs-lookup"><span data-stu-id="a51c3-118">The following value is supported:</span></span>  
  
-   <span data-ttu-id="a51c3-119">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001) – Tato hodnota nastavena na `false` k určení, že ověření proběhlo úspěšně z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="a51c3-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a51c3-120">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a51c3-120">Return Value</span></span>  
 <span data-ttu-id="a51c3-121">`true`Pokud ověření byla úspěšná. v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="a51c3-121">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a51c3-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a51c3-122">Requirements</span></span>  
 <span data-ttu-id="a51c3-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a51c3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a51c3-124">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a51c3-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a51c3-125">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a51c3-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a51c3-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a51c3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a51c3-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="a51c3-127">See Also</span></span>  
 [<span data-ttu-id="a51c3-128">Strongnamesignatureverification – metoda</span><span class="sxs-lookup"><span data-stu-id="a51c3-128">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="a51c3-129">Strongnamesignatureverificationex – metoda</span><span class="sxs-lookup"><span data-stu-id="a51c3-129">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="a51c3-130">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a51c3-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
