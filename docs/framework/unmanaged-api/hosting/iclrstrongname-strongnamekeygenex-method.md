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
ms.openlocfilehash: 93377f82992b8d7d55b21b53abfd7d7c2e9e620b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45658558"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="8323d-102">ICLRStrongName::StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="8323d-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="8323d-103">Generuje nový pár veřejného a privátního klíče se zadanou velikost klíče pro použití silným názvem.</span><span class="sxs-lookup"><span data-stu-id="8323d-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8323d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8323d-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8323d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8323d-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="8323d-106">[in] Název požadovaný kontejner klíče.</span><span class="sxs-lookup"><span data-stu-id="8323d-106">[in] The requested key container name.</span></span> <span data-ttu-id="8323d-107">`wszKeyContainer` musí být neprázdný řetězec nebo hodnota null pro generování dočasný název.</span><span class="sxs-lookup"><span data-stu-id="8323d-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8323d-108">[in] Hodnota, která určuje, zda má zůstat zkratku zaregistrovanou.</span><span class="sxs-lookup"><span data-stu-id="8323d-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="8323d-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="8323d-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="8323d-110">0x00000000 - nepoužívá, pokud `wszKeyContainer` má hodnotu null. k vygenerování názvu dočasného kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="8323d-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="8323d-111">0x00000001 (`SN_LEAVE_KEY`)-určuje, že klíč by měl být vlevo zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="8323d-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="8323d-112">[in] Požadovaná velikost klíče v bitech.</span><span class="sxs-lookup"><span data-stu-id="8323d-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="8323d-113">[out] Vrácený pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="8323d-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="8323d-114">[out] Velikost v bajtech, z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="8323d-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8323d-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8323d-115">Return Value</span></span>  
 <span data-ttu-id="8323d-116">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="8323d-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8323d-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8323d-117">Remarks</span></span>  
 <span data-ttu-id="8323d-118">Vyžadují rozhraní .NET Framework verze 1.0 a 1.1 `dwKeySize` z 1 024 bity k podepisování sestavení silným názvem; přidá verze 2.0 podporuje pro klíče 2048 bitů.</span><span class="sxs-lookup"><span data-stu-id="8323d-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="8323d-119">Po načtení klíče, měli byste zavolat [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodu pro uvolnění přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="8323d-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8323d-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8323d-120">Requirements</span></span>  
 <span data-ttu-id="8323d-121">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8323d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8323d-122">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8323d-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8323d-123">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8323d-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8323d-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8323d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8323d-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="8323d-125">See Also</span></span>  
 [<span data-ttu-id="8323d-126">StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="8323d-126">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="8323d-127">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8323d-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
