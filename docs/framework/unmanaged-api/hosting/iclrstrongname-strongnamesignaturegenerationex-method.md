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
ms.openlocfilehash: c5d2539bc732cdc41c7514fd5d81c449ed8f17a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992885"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="af2a3-102">ICLRStrongName::StrongNameSignatureGenerationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="af2a3-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="af2a3-103">Podpis silného názvu generuje pro zadané sestavení podle zadané příznaky.</span><span class="sxs-lookup"><span data-stu-id="af2a3-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af2a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af2a3-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="af2a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af2a3-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="af2a3-106">[in] Cesta k souboru, který obsahuje manifest sestavení, pro který se vygeneruje podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="af2a3-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="af2a3-107">[in] Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="af2a3-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="af2a3-108">Pokud `pbKeyBlob` má hodnotu null, `wszKeyContainer` musíte zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="af2a3-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="af2a3-109">V takovém případě uložený v kontejneru pár klíčů se používá k podepsání souboru.</span><span class="sxs-lookup"><span data-stu-id="af2a3-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="af2a3-110">Pokud `pbKeyBlob` nemá hodnotu null, pár klíčů se předpokládá, že mají být obsažena v klíče binární velkých objektů (BLOB).</span><span class="sxs-lookup"><span data-stu-id="af2a3-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="af2a3-111">[in] Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="af2a3-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="af2a3-112">Tento pár je ve formátu vytvořené Win32 `CryptExportKey` funkce.</span><span class="sxs-lookup"><span data-stu-id="af2a3-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="af2a3-113">Pokud `pbKeyBlob` je null, použije kontejneru klíčů určeném parametrem `wszKeyContainer` se předpokládá, že obsahuje pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="af2a3-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="af2a3-114">[in] Velikost v bajtech, z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="af2a3-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="af2a3-115">[out] Ukazatel na umístění, do kterého modul common language runtime vrací podpis.</span><span class="sxs-lookup"><span data-stu-id="af2a3-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="af2a3-116">Pokud `ppbSignatureBlob` je null, podpis modul runtime ukládá do souboru určeného `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="af2a3-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="af2a3-117">Pokud `ppbSignatureBlob` je nenulová, modul common language runtime přiděluje místo ke signatura vrácení.</span><span class="sxs-lookup"><span data-stu-id="af2a3-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="af2a3-118">Volající musí uvolnit prostor pomocí [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="af2a3-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="af2a3-119">[out] Velikost v bajtech, vrácený podpis.</span><span class="sxs-lookup"><span data-stu-id="af2a3-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="af2a3-120">[in] Jeden nebo více z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="af2a3-120">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="af2a3-121">`SN_SIGN_ALL_FILES` (0x00000001) - přepočítá všechny hodnoty hash pro propojený moduly.</span><span class="sxs-lookup"><span data-stu-id="af2a3-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="af2a3-122">`SN_TEST_SIGN` (0x00000002) - podpis testovacího sestavení.</span><span class="sxs-lookup"><span data-stu-id="af2a3-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af2a3-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="af2a3-123">Return Value</span></span>  
 <span data-ttu-id="af2a3-124">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="af2a3-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af2a3-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af2a3-125">Remarks</span></span>  
 <span data-ttu-id="af2a3-126">Zadejte hodnotu null pro `wszFilePath` vypočítat velikost podpisu bez vytvoření podpisu.</span><span class="sxs-lookup"><span data-stu-id="af2a3-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="af2a3-127">Podpis může být buď uloženy přímo v souboru nebo vrátit zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="af2a3-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="af2a3-128">Pokud `SN_SIGN_ALL_FILES` je zadán, ale není součástí veřejného klíče (obojí `pbKeyBlob` a `wszFilePath` má hodnotu Null), jsou přepočítány hodnoty hash propojených modulů, ale není znovu podepsat sestavení.</span><span class="sxs-lookup"><span data-stu-id="af2a3-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="af2a3-129">Pokud `SN_TEST_SIGN` je zadat hlavičce modulu CLR se nezmění k označení, že je sestavení podepsáno pomocí silného názvu.</span><span class="sxs-lookup"><span data-stu-id="af2a3-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af2a3-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af2a3-130">Requirements</span></span>  
 <span data-ttu-id="af2a3-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af2a3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af2a3-132">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="af2a3-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="af2a3-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="af2a3-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af2a3-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af2a3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af2a3-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af2a3-135">See also</span></span>

- [<span data-ttu-id="af2a3-136">StrongNameSignatureGeneration – metoda</span><span class="sxs-lookup"><span data-stu-id="af2a3-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="af2a3-137">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af2a3-137">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
