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
ms.openlocfilehash: adb3b4e33edafe6d25c8259e316a9b62e339f896
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092672"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="03085-102">ICLRStrongName::StrongNameSignatureVerificationFromImage – metoda</span><span class="sxs-lookup"><span data-stu-id="03085-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="03085-103">Ověřuje, že sestavení, které již bylo namapováno do paměti, je platné pro přidružený veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="03085-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03085-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03085-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03085-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03085-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="03085-106">pro Relativní virtuální adresa manifestu namapovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="03085-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="03085-107">pro Velikost mapované image v bajtech</span><span class="sxs-lookup"><span data-stu-id="03085-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="03085-108">pro Příznaky, které ovlivňují chování ověřování.</span><span class="sxs-lookup"><span data-stu-id="03085-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="03085-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="03085-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="03085-110">`SN_INFLAG_FORCE_VER` (0x00000001) – vynutí ověření i v případě, že je nutné přepsat nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="03085-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="03085-111">`SN_INFLAG_INSTALL` (0x00000002) – určuje, že se jedná o první ověření provedené na tomto obrázku.</span><span class="sxs-lookup"><span data-stu-id="03085-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="03085-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) – určuje, že mezipaměť bude umožňovat přístup pouze uživatelům, kteří mají oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="03085-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="03085-113">`SN_INFLAG_USER_ACCESS` (0x00000008) – určuje, zda bude sestavení přístupné pouze pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="03085-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="03085-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) – určuje, že mezipaměť nebude poskytovat žádné záruky omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="03085-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="03085-115">`SN_INFLAG_RUNTIME` (0x80000000) – vyhrazeno pro interní ladění.</span><span class="sxs-lookup"><span data-stu-id="03085-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="03085-116">mimo Příznak pro další informace o výstupu.</span><span class="sxs-lookup"><span data-stu-id="03085-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="03085-117">Je podporována následující hodnota:</span><span class="sxs-lookup"><span data-stu-id="03085-117">The following value is supported:</span></span>  
  
- <span data-ttu-id="03085-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) – Tato hodnota je nastavena na hodnotu `false` a určí, že ověření proběhlo úspěšně z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="03085-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03085-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="03085-119">Return Value</span></span>  
 <span data-ttu-id="03085-120">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="03085-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03085-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03085-121">Requirements</span></span>  
 <span data-ttu-id="03085-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03085-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03085-123">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="03085-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="03085-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="03085-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03085-125">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03085-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03085-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03085-126">See also</span></span>

- [<span data-ttu-id="03085-127">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03085-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
