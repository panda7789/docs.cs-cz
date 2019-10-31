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
ms.openlocfilehash: 4f3574e282d24fa11ffa2f85463f682c42098ae7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135043"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="e35cc-102">ICLRStrongName::StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="e35cc-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="e35cc-103">Vytvoří nový pár veřejného a privátního klíče pro použití se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="e35cc-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e35cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e35cc-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e35cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e35cc-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="e35cc-106">pro Požadovaný název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="e35cc-106">[in] The requested key container name.</span></span> <span data-ttu-id="e35cc-107">aby bylo možné vytvořit dočasný název, `wszKeyContainer` musí být buď neprázdný řetězec, nebo hodnota null.</span><span class="sxs-lookup"><span data-stu-id="e35cc-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e35cc-108">pro Hodnota, která určuje, zda má být klíč ponechán zaregistrovaný.</span><span class="sxs-lookup"><span data-stu-id="e35cc-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="e35cc-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="e35cc-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="e35cc-110">0x00000000 – používá se, když `wszKeyContainer` má hodnotu null, aby vygenerovala dočasný název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="e35cc-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="e35cc-111">0x00000001 (`SN_LEAVE_KEY`) – určuje, že klíč by měl zůstat registrovaný.</span><span class="sxs-lookup"><span data-stu-id="e35cc-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="e35cc-112">mimo Vrácený pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="e35cc-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="e35cc-113">mimo Velikost `ppbKeyBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="e35cc-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e35cc-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e35cc-114">Return Value</span></span>  
 <span data-ttu-id="e35cc-115">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="e35cc-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e35cc-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e35cc-116">Remarks</span></span>  
 <span data-ttu-id="e35cc-117">Metoda [ICLRStrongName:: StrongNameKeyGen –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) vytvoří 1024 bitový klíč.</span><span class="sxs-lookup"><span data-stu-id="e35cc-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="e35cc-118">Po načtení klíče byste měli zavolat metodu [ICLRStrongName:: StrongNameFreeBuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) pro uvolnění přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="e35cc-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e35cc-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e35cc-119">Requirements</span></span>  
 <span data-ttu-id="e35cc-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e35cc-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e35cc-121">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="e35cc-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e35cc-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e35cc-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e35cc-123">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e35cc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e35cc-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e35cc-124">See also</span></span>

- [<span data-ttu-id="e35cc-125">StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="e35cc-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="e35cc-126">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e35cc-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
