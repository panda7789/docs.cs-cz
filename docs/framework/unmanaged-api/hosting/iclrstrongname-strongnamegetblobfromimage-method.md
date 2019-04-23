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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fa83f55a03ebfff9ae88217b01c86272bf0de93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178968"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="50a94-102">ICLRStrongName::StrongNameGetBlobFromImage – metoda</span><span class="sxs-lookup"><span data-stu-id="50a94-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>
<span data-ttu-id="50a94-103">Získá binární vyjádření této bitové kopie sestavení na adrese zadaná paměťová.</span><span class="sxs-lookup"><span data-stu-id="50a94-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50a94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50a94-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50a94-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50a94-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="50a94-106">[in] Adresa paměti pro manifest sestavení pro mapovanou.</span><span class="sxs-lookup"><span data-stu-id="50a94-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="50a94-107">[in] Velikost v bajtech bitové kopie `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="50a94-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="50a94-108">[in] Vyrovnávací paměť obsahuje binární vyjádření této image.</span><span class="sxs-lookup"><span data-stu-id="50a94-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="50a94-109">[out v] Požadovanou maximální velikost v bajtech, `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="50a94-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="50a94-110">Po návratu, skutečná velikost v bajtech, z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="50a94-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50a94-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="50a94-111">Return Value</span></span>  
 <span data-ttu-id="50a94-112">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="50a94-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50a94-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50a94-113">Requirements</span></span>  
 <span data-ttu-id="50a94-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50a94-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50a94-115">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="50a94-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="50a94-116">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50a94-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50a94-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50a94-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50a94-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50a94-118">See also</span></span>

- [<span data-ttu-id="50a94-119">StrongNameGetBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="50a94-119">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="50a94-120">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50a94-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
