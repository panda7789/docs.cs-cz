---
title: ICLRStrongName::StrongNameSignatureGeneration – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
ms.openlocfilehash: e58ac181c4e472c469076b880ff71e0c6afa30fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178043"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="7147c-102">ICLRStrongName::StrongNameSignatureGeneration – metoda</span><span class="sxs-lookup"><span data-stu-id="7147c-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="7147c-103">Generuje podpis silného názvu pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="7147c-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7147c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7147c-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7147c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7147c-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="7147c-106">[v] Cesta k souboru, který obsahuje manifest sestavení, pro které bude generován podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="7147c-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="7147c-107">[v] Název kontejneru klíčů, který obsahuje dvojici veřejného a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="7147c-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="7147c-108">Pokud `pbKeyBlob` je `wszKeyContainer` null, musí zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="7147c-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="7147c-109">V tomto případě dvojice klíčů uložená v kontejneru se používá k podepsání souboru.</span><span class="sxs-lookup"><span data-stu-id="7147c-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="7147c-110">Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů je obsažena v binárním velkém objektu klíče (BLOB).</span><span class="sxs-lookup"><span data-stu-id="7147c-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="7147c-111">Klíče musí být 1024bitové podpisové klíče Rivest-Shamir-Adleman (RSA).</span><span class="sxs-lookup"><span data-stu-id="7147c-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="7147c-112">V současné době nejsou podporovány žádné jiné typy klíčů.</span><span class="sxs-lookup"><span data-stu-id="7147c-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="7147c-113">[v] Ukazatel na dvojici veřejného a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="7147c-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="7147c-114">Tento pár je ve formátu vytvořeném `CryptExportKey` funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="7147c-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="7147c-115">Pokud `pbKeyBlob` je null, předpokládá `wszKeyContainer` se, že kontejner klíčů určený podle je obsahující dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="7147c-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="7147c-116">[v] Velikost v bajtů `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="7147c-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="7147c-117">[out] Ukazatel na umístění, do kterého běžný jazyk runtime vrátí podpis.</span><span class="sxs-lookup"><span data-stu-id="7147c-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="7147c-118">Pokud `ppbSignatureBlob` je null, runtime ukládá podpis v `wszFilePath`souboru určeném .</span><span class="sxs-lookup"><span data-stu-id="7147c-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="7147c-119">Pokud `ppbSignatureBlob` není null, běžný jazyk common time přiděluje místo, ve kterém chcete vrátit podpis.</span><span class="sxs-lookup"><span data-stu-id="7147c-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="7147c-120">Volající musí uvolnit toto místo pomocí [metody ICLRStrongName::StrongNameFreeBuffer.](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)</span><span class="sxs-lookup"><span data-stu-id="7147c-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="7147c-121">[out] Velikost vráceného podpisu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="7147c-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7147c-122">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7147c-122">Return Value</span></span>  
 <span data-ttu-id="7147c-123">`S_OK`pokud byla metoda úspěšně dokončena; jinak hodnota HRESULT, která označuje selhání (viz [běžné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="7147c-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7147c-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7147c-124">Remarks</span></span>  
 <span data-ttu-id="7147c-125">Zadejte `wszFilePath` hodnotu null pro výpočet velikosti podpisu bez vytvoření podpisu.</span><span class="sxs-lookup"><span data-stu-id="7147c-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="7147c-126">Podpis může být uložen buď přímo v souboru, nebo vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="7147c-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7147c-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7147c-127">Requirements</span></span>  
 <span data-ttu-id="7147c-128">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7147c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7147c-129">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7147c-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7147c-130">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7147c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7147c-131">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7147c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7147c-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="7147c-132">See also</span></span>

- [<span data-ttu-id="7147c-133">StrongNameSignatureGenerationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="7147c-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="7147c-134">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7147c-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
