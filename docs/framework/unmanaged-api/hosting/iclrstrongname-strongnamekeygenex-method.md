---
title: "ICLRStrongName::StrongNameKeyGenEx – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyGenEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 581f486a2def90f44c0fb3f1bcf9d3bbcc1fc317
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="cfaef-102">ICLRStrongName::StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="cfaef-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="cfaef-103">Generuje nový pár veřejného a privátního klíče pomocí zadané velikost klíče pro použití silným názvem.</span><span class="sxs-lookup"><span data-stu-id="cfaef-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfaef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfaef-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfaef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cfaef-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="cfaef-106">[v] Název požadovaný kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="cfaef-106">[in] The requested key container name.</span></span> <span data-ttu-id="cfaef-107">`wszKeyContainer`musí být neprázdný řetězec nebo hodnota null pro generování dočasný název.</span><span class="sxs-lookup"><span data-stu-id="cfaef-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="cfaef-108">[v] Hodnota, která určuje, zda chcete ponechat klíč zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="cfaef-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="cfaef-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="cfaef-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="cfaef-110">0x00000000 - použít, když `wszKeyContainer` má hodnotu null při generování názvu dočasné kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="cfaef-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="cfaef-111">0x00000001 (`SN_LEAVE_KEY`)-určuje, které by měl být klíč vlevo registrován.</span><span class="sxs-lookup"><span data-stu-id="cfaef-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="cfaef-112">[v] Požadovaná velikost klíče v bitech.</span><span class="sxs-lookup"><span data-stu-id="cfaef-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="cfaef-113">[out] Vrácený veřejného a privátního klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="cfaef-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="cfaef-114">[out] Velikost v bajtech z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="cfaef-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfaef-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cfaef-115">Return Value</span></span>  
 <span data-ttu-id="cfaef-116">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="cfaef-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfaef-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cfaef-117">Remarks</span></span>  
 <span data-ttu-id="cfaef-118">Vyžadují rozhraní .NET Framework verze 1.0 a 1.1 `dwKeySize` 1 024 bitů pro podepsání sestavení silným názvem; verze 2.0 přidá podporuje pro klíče 2048 bitů.</span><span class="sxs-lookup"><span data-stu-id="cfaef-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="cfaef-119">Po načtení klíč by měly volat [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodu pro uvolnění přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="cfaef-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfaef-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cfaef-120">Requirements</span></span>  
 <span data-ttu-id="cfaef-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfaef-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfaef-122">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="cfaef-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cfaef-123">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cfaef-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cfaef-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfaef-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfaef-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="cfaef-125">See Also</span></span>  
 [<span data-ttu-id="cfaef-126">StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="cfaef-126">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="cfaef-127">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfaef-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
