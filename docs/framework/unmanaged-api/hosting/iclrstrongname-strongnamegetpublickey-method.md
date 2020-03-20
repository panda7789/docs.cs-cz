---
title: ICLRStrongName::StrongNameGetPublicKey – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: cb96c7e17627205db0573e56fc8c2a29e7717434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181940"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="619cb-102">ICLRStrongName::StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="619cb-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="619cb-103">Získá veřejný klíč z dvojice veřejného a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="619cb-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="619cb-104">Pár klíčů lze dodat buď jako název kontejneru klíčů v rámci zprostředkovatele kryptografických služeb (CSP) nebo jako nezpracovaná kolekce bajtů.</span><span class="sxs-lookup"><span data-stu-id="619cb-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="619cb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="619cb-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="619cb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="619cb-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="619cb-107">[v] Název kontejneru klíčů, který obsahuje dvojici veřejného a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="619cb-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="619cb-108">Pokud `pbKeyBlob` je `szKeyContainer` null, musí zadat platný kontejner v rámci ověřovatce.</span><span class="sxs-lookup"><span data-stu-id="619cb-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="619cb-109">V tomto případě [metoda ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) extrahuje veřejný klíč z dvojice klíčů uložených v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="619cb-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="619cb-110">Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů je obsažena v binárním velkém objektu klíče (BLOB).</span><span class="sxs-lookup"><span data-stu-id="619cb-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="619cb-111">Klíče musí být 1024bitové podpisové klíče Rivest-Shamir-Adleman (RSA).</span><span class="sxs-lookup"><span data-stu-id="619cb-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="619cb-112">V současné době nejsou podporovány žádné jiné typy klíčů.</span><span class="sxs-lookup"><span data-stu-id="619cb-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="619cb-113">[v] Ukazatel na dvojici veřejného a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="619cb-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="619cb-114">Tento pár je ve formátu vytvořeném `CryptExportKey` funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="619cb-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="619cb-115">Pokud `pbKeyBlob` je null, předpokládá `szKeyContainer` se, že kontejner klíčů určený podle je obsahující dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="619cb-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="619cb-116">[v] Velikost v bajtů `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="619cb-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="619cb-117">[out] Vrácený veřejný klíč BLOB.</span><span class="sxs-lookup"><span data-stu-id="619cb-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="619cb-118">Parametr `ppbPublicKeyBlob` je přidělen a běžný jazyk runtime a vrácena volajícímu.</span><span class="sxs-lookup"><span data-stu-id="619cb-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="619cb-119">Volající musí uvolnit paměť pomocí metody [ICLRStrongName::StrongNameFreeBuffer.](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)</span><span class="sxs-lookup"><span data-stu-id="619cb-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="619cb-120">[out] Velikost vráceného objektu BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="619cb-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="619cb-121">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="619cb-121">Return Value</span></span>  
 <span data-ttu-id="619cb-122">`S_OK`pokud byla metoda úspěšně dokončena; jinak hodnota HRESULT, která označuje selhání (viz [běžné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="619cb-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="619cb-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="619cb-123">Remarks</span></span>  
 <span data-ttu-id="619cb-124">Veřejný klíč je obsažen ve struktuře [PublicKeyBlob.](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)</span><span class="sxs-lookup"><span data-stu-id="619cb-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="619cb-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="619cb-125">Requirements</span></span>  
 <span data-ttu-id="619cb-126">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="619cb-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="619cb-127">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="619cb-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="619cb-128">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="619cb-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="619cb-129">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="619cb-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="619cb-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="619cb-130">See also</span></span>

- [<span data-ttu-id="619cb-131">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="619cb-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="619cb-132">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="619cb-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="619cb-133">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="619cb-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
