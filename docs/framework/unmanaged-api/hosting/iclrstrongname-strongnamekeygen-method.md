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
ms.openlocfilehash: e437ee2ab04d3b1126ec2911553e87586e74e54e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899619"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="a8237-102">ICLRStrongName::StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="a8237-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="a8237-103">Vytvoří nový pár veřejného a privátního klíče pro použití se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="a8237-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8237-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8237-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8237-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8237-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="a8237-106">pro Požadovaný název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="a8237-106">[in] The requested key container name.</span></span> <span data-ttu-id="a8237-107">aby bylo možné vytvořit dočasný název, `wszKeyContainer` musí být buď neprázdný řetězec, nebo hodnota null.</span><span class="sxs-lookup"><span data-stu-id="a8237-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a8237-108">pro Hodnota, která určuje, zda má být klíč ponechán zaregistrovaný.</span><span class="sxs-lookup"><span data-stu-id="a8237-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="a8237-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="a8237-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="a8237-110">0x00000000 – používá se, když `wszKeyContainer` má hodnotu null, aby vygenerovala dočasný název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="a8237-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="a8237-111">0x00000001 (`SN_LEAVE_KEY`) – určuje, že klíč by měl zůstat registrovaný.</span><span class="sxs-lookup"><span data-stu-id="a8237-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="a8237-112">mimo Vrácený pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="a8237-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="a8237-113">mimo Velikost `ppbKeyBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="a8237-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8237-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a8237-114">Return Value</span></span>  
 <span data-ttu-id="a8237-115">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="a8237-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8237-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8237-116">Remarks</span></span>  
 <span data-ttu-id="a8237-117">Metoda [ICLRStrongName:: StrongNameKeyGen –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) vytvoří 1024 bitový klíč.</span><span class="sxs-lookup"><span data-stu-id="a8237-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="a8237-118">Po načtení klíče byste měli zavolat metodu [ICLRStrongName:: StrongNameFreeBuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) pro uvolnění přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="a8237-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8237-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8237-119">Requirements</span></span>  
 <span data-ttu-id="a8237-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8237-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8237-121">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="a8237-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a8237-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a8237-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8237-123">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8237-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8237-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8237-124">See also</span></span>

- [<span data-ttu-id="a8237-125">StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="a8237-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="a8237-126">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8237-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
