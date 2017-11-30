---
title: "ICLRStrongName::StrongNameKeyGen – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyGen
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 13eef3e4c0cf4aa8de55aa96335e570ef1985e9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="d23f5-102">ICLRStrongName::StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="d23f5-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="d23f5-103">Vytvoří nový pár veřejného a privátního klíče pro silné jméno použití.</span><span class="sxs-lookup"><span data-stu-id="d23f5-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d23f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d23f5-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d23f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d23f5-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="d23f5-106">[v] Název požadovaný kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="d23f5-106">[in] The requested key container name.</span></span> <span data-ttu-id="d23f5-107">`wszKeyContainer`musí být neprázdný řetězec nebo hodnota null pro generování dočasný název.</span><span class="sxs-lookup"><span data-stu-id="d23f5-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d23f5-108">[v] Hodnota, která určuje, zda chcete ponechat klíč zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="d23f5-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="d23f5-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="d23f5-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="d23f5-110">0x00000000 - použít, když `wszKeyContainer` má hodnotu null při generování názvu dočasné kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="d23f5-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="d23f5-111">0x00000001 (`SN_LEAVE_KEY`)-určuje, které by měl být klíč vlevo registrován.</span><span class="sxs-lookup"><span data-stu-id="d23f5-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="d23f5-112">[out] Vrácený veřejného a privátního klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="d23f5-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="d23f5-113">[out] Velikost v bajtech z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="d23f5-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d23f5-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d23f5-114">Return Value</span></span>  
 <span data-ttu-id="d23f5-115">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="d23f5-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d23f5-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d23f5-116">Remarks</span></span>  
 <span data-ttu-id="d23f5-117">[Iclrstrongname::strongnamekeygen –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) metoda vytvoří klíč 1024 bitů.</span><span class="sxs-lookup"><span data-stu-id="d23f5-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="d23f5-118">Po načtení klíč by měly volat [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodu pro uvolnění přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="d23f5-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d23f5-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d23f5-119">Requirements</span></span>  
 <span data-ttu-id="d23f5-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d23f5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d23f5-121">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d23f5-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d23f5-122">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d23f5-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d23f5-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d23f5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d23f5-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d23f5-124">See Also</span></span>  
 [<span data-ttu-id="d23f5-125">Strongnamekeygenex – metoda</span><span class="sxs-lookup"><span data-stu-id="d23f5-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [<span data-ttu-id="d23f5-126">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d23f5-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
