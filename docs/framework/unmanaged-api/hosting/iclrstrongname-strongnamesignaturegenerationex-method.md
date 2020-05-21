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
ms.openlocfilehash: 3529eceb179cc4b08d39f83d97d001a16e716918
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763056"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="abe07-102">ICLRStrongName::StrongNameSignatureGenerationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="abe07-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="abe07-103">Vygeneruje podpis silného názvu pro zadané sestavení podle zadaných příznaků.</span><span class="sxs-lookup"><span data-stu-id="abe07-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abe07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abe07-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="abe07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="abe07-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="abe07-106">pro Cesta k souboru, který obsahuje manifest sestavení, pro který bude vytvořen podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="abe07-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="abe07-107">pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="abe07-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="abe07-108">Pokud `pbKeyBlob` má hodnotu null, `wszKeyContainer` musí určovat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="abe07-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="abe07-109">V tomto případě se k podepsání souboru používá pár klíčů uložený v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="abe07-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="abe07-110">Pokud hodnota `pbKeyBlob` není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.</span><span class="sxs-lookup"><span data-stu-id="abe07-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="abe07-111">pro Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="abe07-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="abe07-112">Tato dvojice je ve formátu vytvořeném `CryptExportKey` funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="abe07-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="abe07-113">Pokud `pbKeyBlob` má hodnotu null, předpokládá se, že kontejner klíčů určený parametrem `wszKeyContainer` obsahuje dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="abe07-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="abe07-114">pro Velikost v bajtech `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="abe07-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="abe07-115">mimo Ukazatel na umístění, do kterého modul common language runtime vrátí podpis.</span><span class="sxs-lookup"><span data-stu-id="abe07-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="abe07-116">Pokud `ppbSignatureBlob` je null, modul runtime uloží podpis do souboru určeného parametrem `wszFilePath` .</span><span class="sxs-lookup"><span data-stu-id="abe07-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="abe07-117">Pokud hodnota `ppbSignatureBlob` není null, modul CLR (Common Language Runtime) přidělí místo, ve kterém se podpis vrátí.</span><span class="sxs-lookup"><span data-stu-id="abe07-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="abe07-118">Volající musí uvolnit toto místo pomocí metody [ICLRStrongName:: StrongNameFreeBuffer –](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="abe07-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="abe07-119">mimo Velikost vráceného podpisu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="abe07-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="abe07-120">pro Jedna nebo více z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="abe07-120">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="abe07-121">`SN_SIGN_ALL_FILES`(0x00000001) – přepočítá všechny hodnoty hash pro propojené moduly.</span><span class="sxs-lookup"><span data-stu-id="abe07-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="abe07-122">`SN_TEST_SIGN`(0x00000002) – otestuje podpis sestavení.</span><span class="sxs-lookup"><span data-stu-id="abe07-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abe07-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="abe07-123">Return Value</span></span>  
 <span data-ttu-id="abe07-124">`S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="abe07-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abe07-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="abe07-125">Remarks</span></span>  
 <span data-ttu-id="abe07-126">`wszFilePath`Chcete-li vypočítat velikost podpisu bez vytvoření podpisu, zadejte hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="abe07-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="abe07-127">Podpis může být buď uložen přímo v souboru, nebo vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="abe07-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="abe07-128">Pokud `SN_SIGN_ALL_FILES` je zadána, ale veřejný klíč není zahrnut ( `pbKeyBlob` a `wszFilePath` jsou null), jsou přepočítány hodnoty hash pro propojené moduly, ale sestavení není znovu podepsáno.</span><span class="sxs-lookup"><span data-stu-id="abe07-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="abe07-129">Pokud `SN_TEST_SIGN` je zadána, hlavička společného jazykového modulu runtime není upravena, aby označovala, že je sestavení podepsáno silným názvem.</span><span class="sxs-lookup"><span data-stu-id="abe07-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abe07-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="abe07-130">Requirements</span></span>  
 <span data-ttu-id="abe07-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abe07-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abe07-132">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="abe07-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="abe07-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="abe07-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abe07-134">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abe07-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe07-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="abe07-135">See also</span></span>

- [<span data-ttu-id="abe07-136">StrongNameSignatureGeneration – metoda</span><span class="sxs-lookup"><span data-stu-id="abe07-136">StrongNameSignatureGeneration Method</span></span>](iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="abe07-137">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="abe07-137">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
