---
title: "ICLRStrongName::StrongNameSignatureGenerationEx – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 247bcfa3c9f7a02dea331ff14948a00812fb06e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="81939-102">ICLRStrongName::StrongNameSignatureGenerationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="81939-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="81939-103">Generuje pro zadané sestavení, podle zadaného příznaky podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="81939-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81939-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81939-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81939-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81939-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="81939-106">[v] Cesta k souboru, který obsahuje manifest sestavení, pro které se budou generovat podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="81939-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="81939-107">[v] Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="81939-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="81939-108">Pokud `pbKeyBlob` má hodnotu null, `wszKeyContainer` musíte zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="81939-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="81939-109">Pár klíčů, ukládat do kontejneru v takovém případě se používá k podepsání souboru.</span><span class="sxs-lookup"><span data-stu-id="81939-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="81939-110">Pokud `pbKeyBlob` nemá hodnotu null, dvojici klíčů se předpokládá, že mají být obsažena v klíče binární rozsáhlý objekt (binární rozsáhlý OBJEKT).</span><span class="sxs-lookup"><span data-stu-id="81939-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="81939-111">[v] Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="81939-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="81939-112">Tato dvojice je ve formátu vytvořené Win32 `CryptExportKey` funkce.</span><span class="sxs-lookup"><span data-stu-id="81939-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="81939-113">Pokud `pbKeyBlob` je null, kontejner klíčů určeného `wszKeyContainer` se předpokládá, že obsahovat dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="81939-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="81939-114">[v] Velikost v bajtech z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="81939-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="81939-115">[out] Ukazatel na umístění, do které modul common language runtime vrátí podpis.</span><span class="sxs-lookup"><span data-stu-id="81939-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="81939-116">Pokud `ppbSignatureBlob` je null, podpis modulu runtime ukládá do souboru určeného `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="81939-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="81939-117">Pokud `ppbSignatureBlob` je hodnotou not null, modul common language runtime přiděluje místo k vrácení podpis.</span><span class="sxs-lookup"><span data-stu-id="81939-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="81939-118">Volající musí volné toto místo pomocí [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="81939-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="81939-119">[out] Velikost v bajtech vrácený podpis.</span><span class="sxs-lookup"><span data-stu-id="81939-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="81939-120">[v] Jeden nebo více z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="81939-120">[in] One or more of the following values:</span></span>  
  
-   <span data-ttu-id="81939-121">`SN_SIGN_ALL_FILES`(0x00000001) - přepočítala všechny hodnoty hash pro propojené moduly.</span><span class="sxs-lookup"><span data-stu-id="81939-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
-   <span data-ttu-id="81939-122">`SN_TEST_SIGN`(0x00000002) - test podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="81939-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81939-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="81939-123">Return Value</span></span>  
 <span data-ttu-id="81939-124">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="81939-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81939-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81939-125">Remarks</span></span>  
 <span data-ttu-id="81939-126">Zadejte hodnotu null pro `wszFilePath` vypočítat velikost podpisu bez vytvoření podpisu.</span><span class="sxs-lookup"><span data-stu-id="81939-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="81939-127">Podpis může být buď uložené přímo v souboru nebo vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="81939-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="81939-128">Pokud `SN_SIGN_ALL_FILES` je zadán, ale není zahrnutý veřejný klíč (obě `pbKeyBlob` a `wszFilePath` mají hodnotu null), hodnoty hash pro propojené moduly jsou přepočítávány, ale není znovu podepisovat sestavení.</span><span class="sxs-lookup"><span data-stu-id="81939-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="81939-129">Pokud `SN_TEST_SIGN` není zadaný, společné hlavičky runtime jazyka není upravit tak, aby znamenat, že je podepsaná sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="81939-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81939-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81939-130">Requirements</span></span>  
 <span data-ttu-id="81939-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81939-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81939-132">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="81939-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="81939-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="81939-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81939-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81939-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81939-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="81939-135">See Also</span></span>  
 [<span data-ttu-id="81939-136">StrongNameSignatureGeneration – metoda</span><span class="sxs-lookup"><span data-stu-id="81939-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [<span data-ttu-id="81939-137">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81939-137">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
