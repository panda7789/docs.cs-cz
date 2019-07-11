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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36ff06b4bbe916e7038840d9bf3cbc455f161b70
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768310"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="d3f66-102">StrongNameGetPublicKeyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="d3f66-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="d3f66-103">Získá veřejný klíč z dvojice veřejného/soukromého klíče a určuje algoritmus hash a algoritmus podpisu.</span><span class="sxs-lookup"><span data-stu-id="d3f66-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3f66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3f66-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d3f66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3f66-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="d3f66-106">[in] Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="d3f66-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="d3f66-107">Pokud `pbKeyBlob` má hodnotu null, `szKeyContainer` musíte zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="d3f66-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="d3f66-108">V takovém případě `StrongNameGetPublicKeyEx` metoda extrahuje veřejný klíč z páru klíčů ukládat do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="d3f66-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="d3f66-109">Pokud `pbKeyBlob` nemá hodnotu null, pár klíčů se předpokládá, že mají být obsažena v klíče binární velkých objektů (BLOB).</span><span class="sxs-lookup"><span data-stu-id="d3f66-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="d3f66-110">Klíče musí být Rivest-Shamir-Adleman 1024 bitů (RSA) podpisových klíčů.</span><span class="sxs-lookup"><span data-stu-id="d3f66-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="d3f66-111">Jiné typy klíčů jsou v tuto chvíli nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="d3f66-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="d3f66-112">[in] Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="d3f66-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="d3f66-113">Tento pár je ve formátu vytvořené Win32 `CryptExportKey` funkce.</span><span class="sxs-lookup"><span data-stu-id="d3f66-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="d3f66-114">Pokud `pbKeyBlob` je null, použije kontejneru klíčů určeném parametrem `szKeyContainer` se předpokládá, že obsahuje pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="d3f66-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="d3f66-115">[in] Velikost v bajtech, z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="d3f66-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="d3f66-116">[out] Vrácené veřejného klíče objektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="d3f66-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="d3f66-117">`ppbPublicKeyBlob` Parametr je přidělí modul common language runtime a vrátit zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="d3f66-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="d3f66-118">Volající musí uvolnit paměť pomocí [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d3f66-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="d3f66-119">[out] Velikost veřejného klíče vráceného objektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="d3f66-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="d3f66-120">[in] Algoritmus hash sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3f66-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="d3f66-121">V části poznámky pro seznam platných hodnot.</span><span class="sxs-lookup"><span data-stu-id="d3f66-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="d3f66-122">[in] Vyhrazeno pro budoucí použití; Výchozí hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="d3f66-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3f66-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d3f66-123">Return Value</span></span>  
 <span data-ttu-id="d3f66-124">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="d3f66-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3f66-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3f66-125">Remarks</span></span>  
 <span data-ttu-id="d3f66-126">Veřejný klíč je součástí [publickeyblob –](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="d3f66-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3f66-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3f66-127">Remarks</span></span>  
 <span data-ttu-id="d3f66-128">V následující tabulce jsou uvedeny sada platných hodnot pro `uHashAlgId` parametru.</span><span class="sxs-lookup"><span data-stu-id="d3f66-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="d3f66-129">Name</span><span class="sxs-lookup"><span data-stu-id="d3f66-129">Name</span></span>|<span data-ttu-id="d3f66-130">Value</span><span class="sxs-lookup"><span data-stu-id="d3f66-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="d3f66-131">Žádný</span><span class="sxs-lookup"><span data-stu-id="d3f66-131">None</span></span>|<span data-ttu-id="d3f66-132">0</span><span class="sxs-lookup"><span data-stu-id="d3f66-132">0</span></span>|  
|<span data-ttu-id="d3f66-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="d3f66-133">SHA-1</span></span>|<span data-ttu-id="d3f66-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="d3f66-134">0x8004</span></span>|  
|<span data-ttu-id="d3f66-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="d3f66-135">SHA-256</span></span>|<span data-ttu-id="d3f66-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="d3f66-136">0x800c</span></span>|  
|<span data-ttu-id="d3f66-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="d3f66-137">SHA-384</span></span>|<span data-ttu-id="d3f66-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="d3f66-138">0x800d</span></span>|  
|<span data-ttu-id="d3f66-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="d3f66-139">SHA-512</span></span>|<span data-ttu-id="d3f66-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="d3f66-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3f66-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3f66-141">Requirements</span></span>  
 <span data-ttu-id="d3f66-142">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3f66-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3f66-143">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d3f66-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d3f66-144">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3f66-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3f66-145">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3f66-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f66-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3f66-146">See also</span></span>

- [<span data-ttu-id="d3f66-147">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="d3f66-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="d3f66-148">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="d3f66-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="d3f66-149">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3f66-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="d3f66-150">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="d3f66-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
