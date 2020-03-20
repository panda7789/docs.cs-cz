---
title: StrongNameGetPublicKeyEx – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: 93afe1afd9ea9637d039a8b4a4e81267d49c08b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176224"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="bd5a5-102">StrongNameGetPublicKeyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="bd5a5-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="bd5a5-103">Získá veřejný klíč z dvojice veřejného a soukromého klíče a určuje algoritmus hash a algoritmus podpisu.</span><span class="sxs-lookup"><span data-stu-id="bd5a5-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd5a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd5a5-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd5a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd5a5-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="bd5a5-106">[v] Název kontejneru klíčů, který obsahuje dvojici veřejného a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="bd5a5-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="bd5a5-107">Pokud `pbKeyBlob` je `szKeyContainer` null, musí zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="bd5a5-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="bd5a5-108">V tomto případě `StrongNameGetPublicKeyEx` metoda extrahuje veřejný klíč z dvojice klíčů uložené v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="bd5a5-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="bd5a5-109">Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů je obsažena v binárním velkém objektu klíče (BLOB).</span><span class="sxs-lookup"><span data-stu-id="bd5a5-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="bd5a5-110">Klíče musí být 1024bitové podpisové klíče Rivest-Shamir-Adleman (RSA).</span><span class="sxs-lookup"><span data-stu-id="bd5a5-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="bd5a5-111">V současné době nejsou podporovány žádné jiné typy klíčů.</span><span class="sxs-lookup"><span data-stu-id="bd5a5-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="bd5a5-112">[v] Ukazatel na dvojici veřejného a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="bd5a5-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="bd5a5-113">Tento pár je ve formátu vytvořeném `CryptExportKey` funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="bd5a5-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="bd5a5-114">Pokud `pbKeyBlob` je null, předpokládá `szKeyContainer` se, že kontejner klíčů určený podle je obsahující dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="bd5a5-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="bd5a5-115">[v] Velikost v bajtů `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="bd5a5-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="bd5a5-116">[out] Vrácený veřejný klíč BLOB.</span><span class="sxs-lookup"><span data-stu-id="bd5a5-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="bd5a5-117">Parametr `ppbPublicKeyBlob` je přidělen a běžný jazyk runtime a vrácena volajícímu.</span><span class="sxs-lookup"><span data-stu-id="bd5a5-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="bd5a5-118">Volající musí uvolnit paměť pomocí metody [ICLRStrongName::StrongNameFreeBuffer.](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)</span><span class="sxs-lookup"><span data-stu-id="bd5a5-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="bd5a5-119">[out] Velikost vráceného objektu BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="bd5a5-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="bd5a5-120">[v] Algoritmus hash sestavení.</span><span class="sxs-lookup"><span data-stu-id="bd5a5-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="bd5a5-121">Seznam přijatých hodnot naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="bd5a5-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="bd5a5-122">[v] Vyhrazeno pro budoucí použití; výchozí hodnota null.</span><span class="sxs-lookup"><span data-stu-id="bd5a5-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd5a5-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bd5a5-123">Return Value</span></span>  
 <span data-ttu-id="bd5a5-124">`S_OK`pokud byla metoda úspěšně dokončena; jinak hodnota HRESULT, která označuje selhání (viz [běžné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="bd5a5-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd5a5-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd5a5-125">Remarks</span></span>  
 <span data-ttu-id="bd5a5-126">Veřejný klíč je obsažen ve struktuře [PublicKeyBlob.](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)</span><span class="sxs-lookup"><span data-stu-id="bd5a5-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd5a5-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd5a5-127">Remarks</span></span>  
 <span data-ttu-id="bd5a5-128">V následující tabulce je uvedena sada `uHashAlgId` přijatých hodnot pro parametr.</span><span class="sxs-lookup"><span data-stu-id="bd5a5-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="bd5a5-129">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="bd5a5-129">Name</span></span>|<span data-ttu-id="bd5a5-130">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bd5a5-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="bd5a5-131">Žádný</span><span class="sxs-lookup"><span data-stu-id="bd5a5-131">None</span></span>|<span data-ttu-id="bd5a5-132">0</span><span class="sxs-lookup"><span data-stu-id="bd5a5-132">0</span></span>|  
|<span data-ttu-id="bd5a5-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="bd5a5-133">SHA-1</span></span>|<span data-ttu-id="bd5a5-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="bd5a5-134">0x8004</span></span>|  
|<span data-ttu-id="bd5a5-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="bd5a5-135">SHA-256</span></span>|<span data-ttu-id="bd5a5-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="bd5a5-136">0x800c</span></span>|  
|<span data-ttu-id="bd5a5-137">ŠA-384</span><span class="sxs-lookup"><span data-stu-id="bd5a5-137">SHA-384</span></span>|<span data-ttu-id="bd5a5-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="bd5a5-138">0x800d</span></span>|  
|<span data-ttu-id="bd5a5-139">ŠA-512</span><span class="sxs-lookup"><span data-stu-id="bd5a5-139">SHA-512</span></span>|<span data-ttu-id="bd5a5-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="bd5a5-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bd5a5-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd5a5-141">Requirements</span></span>  
 <span data-ttu-id="bd5a5-142">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd5a5-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd5a5-143">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="bd5a5-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bd5a5-144">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bd5a5-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd5a5-145">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd5a5-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd5a5-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd5a5-146">See also</span></span>

- [<span data-ttu-id="bd5a5-147">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="bd5a5-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="bd5a5-148">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="bd5a5-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="bd5a5-149">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd5a5-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="bd5a5-150">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="bd5a5-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
