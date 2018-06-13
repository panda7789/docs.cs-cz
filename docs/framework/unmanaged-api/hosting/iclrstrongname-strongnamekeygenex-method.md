---
title: ICLRStrongName::StrongNameKeyGenEx – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b213285b3c533488cfa48198951275925c0e37ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436183"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="99e82-102">ICLRStrongName::StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="99e82-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="99e82-103">Generuje nový pár veřejného a privátního klíče pomocí zadané velikost klíče pro použití silným názvem.</span><span class="sxs-lookup"><span data-stu-id="99e82-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99e82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99e82-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99e82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99e82-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="99e82-106">[v] Název požadovaný kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="99e82-106">[in] The requested key container name.</span></span> <span data-ttu-id="99e82-107">`wszKeyContainer` musí být neprázdný řetězec nebo hodnota null pro generování dočasný název.</span><span class="sxs-lookup"><span data-stu-id="99e82-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="99e82-108">[v] Hodnota, která určuje, zda chcete ponechat klíč zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="99e82-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="99e82-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="99e82-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="99e82-110">0x00000000 - použít, když `wszKeyContainer` má hodnotu null při generování názvu dočasné kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="99e82-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="99e82-111">0x00000001 (`SN_LEAVE_KEY`)-určuje, které by měl být klíč vlevo registrován.</span><span class="sxs-lookup"><span data-stu-id="99e82-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="99e82-112">[v] Požadovaná velikost klíče v bitech.</span><span class="sxs-lookup"><span data-stu-id="99e82-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="99e82-113">[out] Vrácený veřejného a privátního klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="99e82-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="99e82-114">[out] Velikost v bajtech z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="99e82-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99e82-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="99e82-115">Return Value</span></span>  
 <span data-ttu-id="99e82-116">`S_OK` Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="99e82-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99e82-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99e82-117">Remarks</span></span>  
 <span data-ttu-id="99e82-118">Vyžadují rozhraní .NET Framework verze 1.0 a 1.1 `dwKeySize` 1 024 bitů pro podepsání sestavení silným názvem; verze 2.0 přidá podporuje pro klíče 2048 bitů.</span><span class="sxs-lookup"><span data-stu-id="99e82-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="99e82-119">Po načtení klíč by měly volat [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodu pro uvolnění přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="99e82-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99e82-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99e82-120">Requirements</span></span>  
 <span data-ttu-id="99e82-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99e82-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99e82-122">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="99e82-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="99e82-123">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99e82-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99e82-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99e82-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99e82-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="99e82-125">See Also</span></span>  
 [<span data-ttu-id="99e82-126">StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="99e82-126">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="99e82-127">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99e82-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
