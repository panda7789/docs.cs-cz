---
title: StrongNameSignatureVerification – funkce
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de267042eab8d0f3d8dc2562c13bcdd068837220
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559469"
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="23a73-102">StrongNameSignatureVerification – funkce</span><span class="sxs-lookup"><span data-stu-id="23a73-102">StrongNameSignatureVerification Function</span></span>
<span data-ttu-id="23a73-103">Získá hodnotu označující, zda obsahuje manifest sestavení v zadané cestě podpis silného názvu, který je ověřen podle zadané příznaky.</span><span class="sxs-lookup"><span data-stu-id="23a73-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="23a73-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="23a73-104">This function has been deprecated.</span></span> <span data-ttu-id="23a73-105">Použití [iclrstrongname::strongnamesignatureverification –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="23a73-105">Use the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23a73-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23a73-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23a73-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="23a73-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="23a73-108">[in] Cesta k přenositelný spustitelný (.dll nebo .exe) soubor pro sestavení k ověření.</span><span class="sxs-lookup"><span data-stu-id="23a73-108">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="23a73-109">[in] Příznaky, které upravují chování ověřování.</span><span class="sxs-lookup"><span data-stu-id="23a73-109">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="23a73-110">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="23a73-110">The following values are supported:</span></span>  
  
-   <span data-ttu-id="23a73-111">`SN_INFLAG_FORCE_VER` (0x00000001) – vynutí ověření i v případě, že je potřeba přepsat nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="23a73-111">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="23a73-112">`SN_INFLAG_INSTALL` (0x00000002) - určuje, že to je poprvé, kdy je ověřený v manifestu.</span><span class="sxs-lookup"><span data-stu-id="23a73-112">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
-   <span data-ttu-id="23a73-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - určuje, že mezipaměť bude umožňovat přístup pouze uživatelům, kteří mají oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="23a73-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="23a73-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - určuje, zda sestavení přístupné pouze pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="23a73-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="23a73-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - určuje, že mezipaměť bude poskytovat žádné záruky omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="23a73-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="23a73-116">`SN_INFLAG_RUNTIME` (0x80000000) – vyhrazené pro interní ladění.</span><span class="sxs-lookup"><span data-stu-id="23a73-116">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="23a73-117">[out] Příznaky určující, zda se ověřit podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="23a73-117">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="23a73-118">Je podporován následující hodnotu:</span><span class="sxs-lookup"><span data-stu-id="23a73-118">The following value is supported:</span></span>  
  
-   <span data-ttu-id="23a73-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) – Tato hodnota nastavená na `false` k určení, že ověření proběhlo úspěšně z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="23a73-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23a73-120">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="23a73-120">Return Value</span></span>  
 <span data-ttu-id="23a73-121">`true` Pokud bude ověření úspěšné; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="23a73-121">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23a73-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="23a73-122">Requirements</span></span>  
 <span data-ttu-id="23a73-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23a73-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23a73-124">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="23a73-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="23a73-125">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="23a73-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="23a73-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23a73-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a73-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23a73-127">See also</span></span>
- [<span data-ttu-id="23a73-128">StrongNameSignatureVerification – metoda</span><span class="sxs-lookup"><span data-stu-id="23a73-128">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="23a73-129">StrongNameSignatureVerificationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="23a73-129">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="23a73-130">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="23a73-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
