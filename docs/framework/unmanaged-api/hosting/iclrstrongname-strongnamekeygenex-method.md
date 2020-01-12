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
ms.openlocfilehash: b09677a45c5d515aacb2cac709599140039a9dd8
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899559"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="21f53-102">ICLRStrongName::StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="21f53-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="21f53-103">Vygeneruje nový pár veřejného a privátního klíče se zadanou velikostí klíče pro použití silného názvu.</span><span class="sxs-lookup"><span data-stu-id="21f53-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21f53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21f53-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21f53-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21f53-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="21f53-106">pro Požadovaný název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="21f53-106">[in] The requested key container name.</span></span> <span data-ttu-id="21f53-107">aby bylo možné vytvořit dočasný název, `wszKeyContainer` musí být buď neprázdný řetězec, nebo hodnota null.</span><span class="sxs-lookup"><span data-stu-id="21f53-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="21f53-108">pro Hodnota, která určuje, zda má být klíč ponechán zaregistrovaný.</span><span class="sxs-lookup"><span data-stu-id="21f53-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="21f53-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="21f53-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="21f53-110">0x00000000 – používá se, když `wszKeyContainer` má hodnotu null, aby vygenerovala dočasný název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="21f53-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="21f53-111">0x00000001 (`SN_LEAVE_KEY`) – určuje, že klíč by měl zůstat registrovaný.</span><span class="sxs-lookup"><span data-stu-id="21f53-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="21f53-112">pro Požadovaná velikost klíče v bitech.</span><span class="sxs-lookup"><span data-stu-id="21f53-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="21f53-113">mimo Vrácený pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="21f53-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="21f53-114">mimo Velikost `ppbKeyBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="21f53-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21f53-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="21f53-115">Return Value</span></span>  
 <span data-ttu-id="21f53-116">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="21f53-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21f53-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21f53-117">Remarks</span></span>  
 <span data-ttu-id="21f53-118">.NET Framework verze 1,0 a 1,1 vyžadují `dwKeySize` 1024 bitů pro podepsání sestavení silným názvem; verze 2,0 přidává podporu pro 2048 bitové klávesy.</span><span class="sxs-lookup"><span data-stu-id="21f53-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="21f53-119">Po načtení klíče byste měli zavolat metodu [ICLRStrongName:: StrongNameFreeBuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) pro uvolnění přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="21f53-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21f53-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21f53-120">Requirements</span></span>  
 <span data-ttu-id="21f53-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21f53-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21f53-122">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="21f53-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="21f53-123">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="21f53-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21f53-124">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21f53-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f53-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21f53-125">See also</span></span>

- [<span data-ttu-id="21f53-126">StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="21f53-126">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="21f53-127">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21f53-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
