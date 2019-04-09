---
title: ICLRStrongName::StrongNameKeyGen – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abeb731ecd66e4412f904b085abcfc7b5b3a3c4b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169777"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="a5c9a-102">ICLRStrongName::StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="a5c9a-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="a5c9a-103">Vytvoří nový pár veřejného a privátního klíče pro použití silným názvem.</span><span class="sxs-lookup"><span data-stu-id="a5c9a-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5c9a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5c9a-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5c9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5c9a-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="a5c9a-106">[in] Název požadovaný kontejner klíče.</span><span class="sxs-lookup"><span data-stu-id="a5c9a-106">[in] The requested key container name.</span></span> `wszKeyContainer` <span data-ttu-id="a5c9a-107">musí být neprázdný řetězec nebo hodnota null pro generování dočasný název.</span><span class="sxs-lookup"><span data-stu-id="a5c9a-107">must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a5c9a-108">[in] Hodnota, která určuje, zda má zůstat zkratku zaregistrovanou.</span><span class="sxs-lookup"><span data-stu-id="a5c9a-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="a5c9a-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="a5c9a-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="a5c9a-110">0x00000000 - nepoužívá, pokud `wszKeyContainer` má hodnotu null. k vygenerování názvu dočasného kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="a5c9a-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="a5c9a-111">0x00000001 (`SN_LEAVE_KEY`)-určuje, že klíč by měl být vlevo zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="a5c9a-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="a5c9a-112">[out] Vrácený pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="a5c9a-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="a5c9a-113">[out] Velikost v bajtech, z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="a5c9a-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5c9a-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a5c9a-114">Return Value</span></span>  
 `S_OK` <span data-ttu-id="a5c9a-115">Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="a5c9a-115">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5c9a-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5c9a-116">Remarks</span></span>  
 <span data-ttu-id="a5c9a-117">[Iclrstrongname::strongnamekeygen –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) metoda vytvoří klíče 1 024 bitů.</span><span class="sxs-lookup"><span data-stu-id="a5c9a-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="a5c9a-118">Po načtení klíče, měli byste zavolat [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodu pro uvolnění přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="a5c9a-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5c9a-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5c9a-119">Requirements</span></span>  
 <span data-ttu-id="a5c9a-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5c9a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5c9a-121">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a5c9a-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a5c9a-122">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a5c9a-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="a5c9a-123">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a5c9a-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a5c9a-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5c9a-124">See also</span></span>

- [<span data-ttu-id="a5c9a-125">StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="a5c9a-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="a5c9a-126">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5c9a-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
