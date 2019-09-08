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
ms.openlocfilehash: 8943df861b1bff2b28c68d0233fc336d1b5d4579
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798945"
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="d191a-102">StrongNameSignatureVerification – funkce</span><span class="sxs-lookup"><span data-stu-id="d191a-102">StrongNameSignatureVerification Function</span></span>
<span data-ttu-id="d191a-103">Získá hodnotu, která označuje, zda manifest sestavení v zadané cestě obsahuje podpis silného názvu, který je ověřen podle zadaných příznaků.</span><span class="sxs-lookup"><span data-stu-id="d191a-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="d191a-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="d191a-104">This function has been deprecated.</span></span> <span data-ttu-id="d191a-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameSignatureVerification –](../hosting/iclrstrongname-strongnamesignatureverification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d191a-105">Use the [ICLRStrongName::StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d191a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d191a-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d191a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d191a-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d191a-108">pro Cesta k přenositelnému spustitelnému souboru (. dll nebo. exe) pro sestavení, které se má ověřit</span><span class="sxs-lookup"><span data-stu-id="d191a-108">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="d191a-109">pro Příznaky pro změnu chování ověřování.</span><span class="sxs-lookup"><span data-stu-id="d191a-109">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="d191a-110">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="d191a-110">The following values are supported:</span></span>  
  
- <span data-ttu-id="d191a-111">`SN_INFLAG_FORCE_VER`(0x00000001) – vynutí ověření i v případě, že je nutné přepsat nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="d191a-111">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="d191a-112">`SN_INFLAG_INSTALL`(0x00000002) – určuje, že se jedná o první ověření manifestu.</span><span class="sxs-lookup"><span data-stu-id="d191a-112">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="d191a-113">`SN_INFLAG_ADMIN_ACCESS`(0x00000004) – určuje, že mezipaměť povolí přístup pouze uživatelům, kteří mají oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="d191a-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="d191a-114">`SN_INFLAG_USER_ACCESS`(0x00000008) – určuje, zda bude sestavení přístupné pouze pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="d191a-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="d191a-115">`SN_INFLAG_ALL_ACCESS`(0x00000010) – určuje, že mezipaměť nebude poskytovat žádné záruky omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="d191a-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="d191a-116">`SN_INFLAG_RUNTIME`(0x80000000) – rezervované pro interní ladění.</span><span class="sxs-lookup"><span data-stu-id="d191a-116">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="d191a-117">mimo Příznaky označující, zda byl ověřen podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="d191a-117">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="d191a-118">Je podporována následující hodnota:</span><span class="sxs-lookup"><span data-stu-id="d191a-118">The following value is supported:</span></span>  
  
- <span data-ttu-id="d191a-119">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001) – Tato hodnota je nastavena `false` na hodnotu, chcete-li určit, že ověření proběhlo úspěšně z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="d191a-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d191a-120">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d191a-120">Return Value</span></span>  
 <span data-ttu-id="d191a-121">`true`Pokud bylo ověření úspěšné; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="d191a-121">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d191a-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d191a-122">Requirements</span></span>  
 <span data-ttu-id="d191a-123">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d191a-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d191a-124">**Hlaviček** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="d191a-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d191a-125">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d191a-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d191a-126">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d191a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d191a-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d191a-127">See also</span></span>

- [<span data-ttu-id="d191a-128">StrongNameSignatureVerification – metoda</span><span class="sxs-lookup"><span data-stu-id="d191a-128">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="d191a-129">StrongNameSignatureVerificationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="d191a-129">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="d191a-130">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d191a-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
