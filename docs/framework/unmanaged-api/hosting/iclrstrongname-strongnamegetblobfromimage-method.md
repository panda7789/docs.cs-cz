---
title: ICLRStrongName::StrongNameGetBlobFromImage – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetBlobFromImage method [.NET Framework hosting]
ms.assetid: 0f5a2ec8-e776-4fd8-bda6-937b6834575a
topic_type:
- apiref
ms.openlocfilehash: a0bcc62a1715fb455f0affee64a351cabe0ba3f6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901125"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="69666-102">ICLRStrongName::StrongNameGetBlobFromImage – metoda</span><span class="sxs-lookup"><span data-stu-id="69666-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>
<span data-ttu-id="69666-103">Načte binární reprezentaci image sestavení v zadané adrese paměti.</span><span class="sxs-lookup"><span data-stu-id="69666-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69666-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69666-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69666-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69666-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="69666-106">pro Adresa paměti namapovaného manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="69666-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="69666-107">pro Velikost bitové kopie v bajtech v `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="69666-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="69666-108">pro Vyrovnávací paměť obsahující binární reprezentaci obrázku.</span><span class="sxs-lookup"><span data-stu-id="69666-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="69666-109">[in, out] Požadovaná maximální velikost v bajtech `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="69666-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="69666-110">Po návratu se skutečná velikost `pbBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="69666-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69666-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="69666-111">Return Value</span></span>  
 <span data-ttu-id="69666-112">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="69666-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69666-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69666-113">Requirements</span></span>  
 <span data-ttu-id="69666-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69666-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69666-115">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="69666-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="69666-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="69666-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69666-117">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69666-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69666-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69666-118">See also</span></span>

- [<span data-ttu-id="69666-119">StrongNameGetBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="69666-119">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="69666-120">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69666-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
