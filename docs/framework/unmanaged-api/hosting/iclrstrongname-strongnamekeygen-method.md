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
ms.openlocfilehash: db5c0dbe57607c7a3bf8b97cee734415aa934336
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763082"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="0d46e-102">ICLRStrongName::StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="0d46e-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="0d46e-103">Vytvoří nový pár veřejného a privátního klíče pro použití se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="0d46e-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d46e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d46e-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d46e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d46e-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="0d46e-106">pro Požadovaný název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="0d46e-106">[in] The requested key container name.</span></span> <span data-ttu-id="0d46e-107">`wszKeyContainer`aby bylo možné vygenerovat dočasný název, musí být buď neprázdný řetězec, nebo hodnota null.</span><span class="sxs-lookup"><span data-stu-id="0d46e-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="0d46e-108">pro Hodnota, která určuje, zda má být klíč ponechán zaregistrovaný.</span><span class="sxs-lookup"><span data-stu-id="0d46e-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="0d46e-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="0d46e-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="0d46e-110">0x00000000 – používá se `wszKeyContainer` , pokud je null k vygenerování dočasného názvu kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="0d46e-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="0d46e-111">0x00000001 ( `SN_LEAVE_KEY` ) – určuje, že klíč by měl zůstat registrovaný.</span><span class="sxs-lookup"><span data-stu-id="0d46e-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="0d46e-112">mimo Vrácený pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="0d46e-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="0d46e-113">mimo Velikost v bajtech `ppbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="0d46e-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d46e-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0d46e-114">Return Value</span></span>  
 <span data-ttu-id="0d46e-115">`S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="0d46e-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d46e-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d46e-116">Remarks</span></span>  
 <span data-ttu-id="0d46e-117">Metoda [ICLRStrongName:: StrongNameKeyGen –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) vytvoří 1024 bitový klíč.</span><span class="sxs-lookup"><span data-stu-id="0d46e-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="0d46e-118">Po načtení klíče byste měli zavolat metodu [ICLRStrongName:: StrongNameFreeBuffer –](iclrstrongname-strongnamefreebuffer-method.md) pro uvolnění přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="0d46e-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d46e-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d46e-119">Requirements</span></span>  
 <span data-ttu-id="0d46e-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d46e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d46e-121">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="0d46e-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0d46e-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0d46e-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d46e-123">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d46e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d46e-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d46e-124">See also</span></span>

- [<span data-ttu-id="0d46e-125">StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="0d46e-125">StrongNameKeyGenEx Method</span></span>](iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="0d46e-126">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d46e-126">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
