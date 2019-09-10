---
title: ICLRStrongName::StrongNameSignatureGenerationEx – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b411a51a5640a924d3eeae5d52102a842966d3fa
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855507"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="dd88c-102">ICLRStrongName::StrongNameSignatureGenerationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="dd88c-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="dd88c-103">Vygeneruje podpis silného názvu pro zadané sestavení podle zadaných příznaků.</span><span class="sxs-lookup"><span data-stu-id="dd88c-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd88c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd88c-104">Syntax</span></span>  
  
```cpp
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
  
## <a name="parameters"></a><span data-ttu-id="dd88c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd88c-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="dd88c-106">pro Cesta k souboru, který obsahuje manifest sestavení, pro který bude vytvořen podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="dd88c-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="dd88c-107">pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="dd88c-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="dd88c-108">Pokud `pbKeyBlob` má hodnotu null `wszKeyContainer` , musí určovat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="dd88c-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="dd88c-109">V tomto případě se k podepsání souboru používá pár klíčů uložený v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="dd88c-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="dd88c-110">Pokud `pbKeyBlob` hodnota není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.</span><span class="sxs-lookup"><span data-stu-id="dd88c-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="dd88c-111">pro Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="dd88c-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="dd88c-112">Tato dvojice je ve formátu vytvořeném funkcí Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="dd88c-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="dd88c-113">Pokud `pbKeyBlob` má hodnotu null, předpokládá se, že `wszKeyContainer` kontejner klíčů určený parametrem obsahuje dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="dd88c-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="dd88c-114">pro Velikost v bajtech `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="dd88c-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="dd88c-115">mimo Ukazatel na umístění, do kterého modul common language runtime vrátí podpis.</span><span class="sxs-lookup"><span data-stu-id="dd88c-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="dd88c-116">Pokud `ppbSignatureBlob` je null, modul runtime uloží podpis do souboru určeného parametrem `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="dd88c-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="dd88c-117">Pokud `ppbSignatureBlob` hodnota není null, modul CLR (Common Language Runtime) přidělí místo, ve kterém se podpis vrátí.</span><span class="sxs-lookup"><span data-stu-id="dd88c-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="dd88c-118">Volající musí uvolnit toto místo pomocí metody [ICLRStrongName:: StrongNameFreeBuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dd88c-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="dd88c-119">mimo Velikost vráceného podpisu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="dd88c-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="dd88c-120">pro Jedna nebo více z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="dd88c-120">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="dd88c-121">`SN_SIGN_ALL_FILES`(0x00000001) – přepočítá všechny hodnoty hash pro propojené moduly.</span><span class="sxs-lookup"><span data-stu-id="dd88c-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="dd88c-122">`SN_TEST_SIGN`(0x00000002) – otestuje podpis sestavení.</span><span class="sxs-lookup"><span data-stu-id="dd88c-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd88c-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dd88c-123">Return Value</span></span>  
 <span data-ttu-id="dd88c-124">`S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="dd88c-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd88c-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd88c-125">Remarks</span></span>  
 <span data-ttu-id="dd88c-126">`wszFilePath` Chcete-li vypočítat velikost podpisu bez vytvoření podpisu, zadejte hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="dd88c-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="dd88c-127">Podpis může být buď uložen přímo v souboru, nebo vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="dd88c-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="dd88c-128">Pokud `SN_SIGN_ALL_FILES` je zadána, ale veřejný klíč není zahrnut `pbKeyBlob` (a `wszFilePath` jsou null), jsou přepočítány hodnoty hash pro propojené moduly, ale sestavení není znovu podepsáno.</span><span class="sxs-lookup"><span data-stu-id="dd88c-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="dd88c-129">Pokud `SN_TEST_SIGN` je zadána, hlavička společného jazykového modulu runtime není upravena, aby označovala, že je sestavení podepsáno silným názvem.</span><span class="sxs-lookup"><span data-stu-id="dd88c-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd88c-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd88c-130">Requirements</span></span>  
 <span data-ttu-id="dd88c-131">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd88c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd88c-132">**Hlaviček** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="dd88c-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="dd88c-133">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dd88c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd88c-134">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd88c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd88c-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd88c-135">See also</span></span>

- [<span data-ttu-id="dd88c-136">StrongNameSignatureGeneration – metoda</span><span class="sxs-lookup"><span data-stu-id="dd88c-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="dd88c-137">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd88c-137">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
