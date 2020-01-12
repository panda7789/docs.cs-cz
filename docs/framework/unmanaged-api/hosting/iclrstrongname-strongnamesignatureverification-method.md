---
title: ICLRStrongName::StrongNameSignatureVerification – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 6375fd8e4a314403267a4cdf2e8356677e9e7a06
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899486"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="fd293-102">ICLRStrongName::StrongNameSignatureVerification – metoda</span><span class="sxs-lookup"><span data-stu-id="fd293-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>
<span data-ttu-id="fd293-103">Získá hodnotu, která označuje, zda manifest sestavení v zadané cestě obsahuje podpis silného názvu, který je ověřen podle zadaných příznaků.</span><span class="sxs-lookup"><span data-stu-id="fd293-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd293-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd293-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd293-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd293-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="fd293-106">pro Cesta k přenositelnému spustitelnému souboru (. dll nebo. exe) pro sestavení, které se má ověřit</span><span class="sxs-lookup"><span data-stu-id="fd293-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="fd293-107">pro Příznaky pro změnu chování ověřování.</span><span class="sxs-lookup"><span data-stu-id="fd293-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="fd293-108">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="fd293-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="fd293-109">`SN_INFLAG_FORCE_VER` (0x00000001) – vynutí ověření i v případě, že je nutné přepsat nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="fd293-109">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="fd293-110">`SN_INFLAG_INSTALL` (0x00000002) – určuje, že se jedná o první ověření manifestu.</span><span class="sxs-lookup"><span data-stu-id="fd293-110">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="fd293-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) – určuje, že mezipaměť bude umožňovat přístup pouze uživatelům, kteří mají oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="fd293-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="fd293-112">`SN_INFLAG_USER_ACCESS` (0x00000008) – určuje, zda bude sestavení přístupné pouze pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="fd293-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="fd293-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) – určuje, že mezipaměť nebude poskytovat žádné záruky omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="fd293-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="fd293-114">`SN_INFLAG_RUNTIME` (0x80000000) – vyhrazeno pro interní ladění.</span><span class="sxs-lookup"><span data-stu-id="fd293-114">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="fd293-115">mimo Příznaky označující, zda byl ověřen podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="fd293-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="fd293-116">Je podporována následující hodnota:</span><span class="sxs-lookup"><span data-stu-id="fd293-116">The following value is supported:</span></span>  
  
- <span data-ttu-id="fd293-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) – Tato hodnota je nastavena na hodnotu `false` a určí, že ověření proběhlo úspěšně z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="fd293-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd293-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fd293-118">Return Value</span></span>  
 <span data-ttu-id="fd293-119">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="fd293-119">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd293-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fd293-120">Requirements</span></span>  
 <span data-ttu-id="fd293-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd293-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd293-122">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="fd293-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fd293-123">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fd293-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd293-124">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd293-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd293-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd293-125">See also</span></span>

- [<span data-ttu-id="fd293-126">StrongNameSignatureVerificationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="fd293-126">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="fd293-127">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd293-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
