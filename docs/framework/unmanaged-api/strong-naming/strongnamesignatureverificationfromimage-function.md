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
ms.openlocfilehash: c22339b7d48e89f99d1500cfdda53f00f1234b80
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799078"
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="94539-102">StrongNameSignatureVerificationFromImage – funkce</span><span class="sxs-lookup"><span data-stu-id="94539-102">StrongNameSignatureVerificationFromImage Function</span></span>
<span data-ttu-id="94539-103">Ověřuje, že sestavení, které již bylo namapováno do paměti, je platné pro přidružený veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="94539-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="94539-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="94539-104">This function has been deprecated.</span></span> <span data-ttu-id="94539-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) .</span><span class="sxs-lookup"><span data-stu-id="94539-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94539-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94539-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94539-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="94539-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="94539-108">pro Relativní virtuální adresa manifestu namapovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="94539-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="94539-109">pro Velikost mapované image v bajtech</span><span class="sxs-lookup"><span data-stu-id="94539-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="94539-110">pro Příznaky, které ovlivňují chování ověřování.</span><span class="sxs-lookup"><span data-stu-id="94539-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="94539-111">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="94539-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="94539-112">`SN_INFLAG_FORCE_VER`(0x00000001) – vynutí ověření i v případě, že je nutné přepsat nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="94539-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="94539-113">`SN_INFLAG_INSTALL`(0x00000002) – určuje, že se jedná o první ověření provedené na tomto obrázku.</span><span class="sxs-lookup"><span data-stu-id="94539-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="94539-114">`SN_INFLAG_ADMIN_ACCESS`(0x00000004) – určuje, že mezipaměť povolí přístup pouze uživatelům, kteří mají oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="94539-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="94539-115">`SN_INFLAG_USER_ACCESS`(0x00000008) – určuje, zda bude sestavení přístupné pouze pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="94539-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="94539-116">`SN_INFLAG_ALL_ACCESS`(0x00000010) – určuje, že mezipaměť nebude poskytovat žádné záruky omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="94539-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="94539-117">`SN_INFLAG_RUNTIME`(0x80000000) – rezervované pro interní ladění.</span><span class="sxs-lookup"><span data-stu-id="94539-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="94539-118">mimo Příznak pro další informace o výstupu.</span><span class="sxs-lookup"><span data-stu-id="94539-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="94539-119">Je podporována následující hodnota:</span><span class="sxs-lookup"><span data-stu-id="94539-119">The following value is supported:</span></span>  
  
- <span data-ttu-id="94539-120">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001) – Tato hodnota je nastavena `false` na hodnotu, chcete-li určit, že ověření proběhlo úspěšně z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="94539-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94539-121">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="94539-121">Return Value</span></span>  
 <span data-ttu-id="94539-122">`true`Po úspěšném dokončení; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="94539-122">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94539-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94539-123">Remarks</span></span>  
 <span data-ttu-id="94539-124">Pokud se `StrongNameSignatureVerificationFromImage` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="94539-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94539-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94539-125">Requirements</span></span>  
 <span data-ttu-id="94539-126">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94539-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94539-127">**Hlaviček** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="94539-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="94539-128">**Knihovna** Zahrnuto jako prostředek v knihovně Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="94539-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="94539-129">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94539-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94539-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94539-130">See also</span></span>

- [<span data-ttu-id="94539-131">StrongNameSignatureVerificationFromImage – metoda</span><span class="sxs-lookup"><span data-stu-id="94539-131">StrongNameSignatureVerificationFromImage Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [<span data-ttu-id="94539-132">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="94539-132">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
