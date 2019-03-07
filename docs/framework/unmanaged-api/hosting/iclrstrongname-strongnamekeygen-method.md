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
ms.openlocfilehash: 98a53f488467ed1c66543c9861f056bc9890f617
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478515"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="64a02-102">ICLRStrongName::StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="64a02-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="64a02-103">Vytvoří nový pár veřejného a privátního klíče pro použití silným názvem.</span><span class="sxs-lookup"><span data-stu-id="64a02-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64a02-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64a02-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64a02-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64a02-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="64a02-106">[in] Název požadovaný kontejner klíče.</span><span class="sxs-lookup"><span data-stu-id="64a02-106">[in] The requested key container name.</span></span> <span data-ttu-id="64a02-107">`wszKeyContainer` musí být neprázdný řetězec nebo hodnota null pro generování dočasný název.</span><span class="sxs-lookup"><span data-stu-id="64a02-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="64a02-108">[in] Hodnota, která určuje, zda má zůstat zkratku zaregistrovanou.</span><span class="sxs-lookup"><span data-stu-id="64a02-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="64a02-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="64a02-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="64a02-110">0x00000000 - nepoužívá, pokud `wszKeyContainer` má hodnotu null. k vygenerování názvu dočasného kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="64a02-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="64a02-111">0x00000001 (`SN_LEAVE_KEY`)-určuje, že klíč by měl být vlevo zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="64a02-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="64a02-112">[out] Vrácený pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="64a02-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="64a02-113">[out] Velikost v bajtech, z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="64a02-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64a02-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="64a02-114">Return Value</span></span>  
 <span data-ttu-id="64a02-115">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="64a02-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64a02-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64a02-116">Remarks</span></span>  
 <span data-ttu-id="64a02-117">[Iclrstrongname::strongnamekeygen –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) metoda vytvoří klíče 1 024 bitů.</span><span class="sxs-lookup"><span data-stu-id="64a02-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="64a02-118">Po načtení klíče, měli byste zavolat [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodu pro uvolnění přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="64a02-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64a02-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64a02-119">Requirements</span></span>  
 <span data-ttu-id="64a02-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64a02-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64a02-121">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="64a02-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="64a02-122">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="64a02-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64a02-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64a02-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64a02-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64a02-124">See also</span></span>
- [<span data-ttu-id="64a02-125">StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="64a02-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="64a02-126">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64a02-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
