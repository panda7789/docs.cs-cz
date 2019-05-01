---
title: StrongNameSignatureGenerationEx – funkce
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGenerationEx
helpviewer_keywords:
- StrongNameSignatureGenerationEx function [.NET Framework strong naming]
ms.assetid: 9a75469e-aa49-4e32-ad48-3bafd5202f09
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5d60b9a9ae566b5bd686b27b2e09861a8414979
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000230"
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="37d3d-102">StrongNameSignatureGenerationEx – funkce</span><span class="sxs-lookup"><span data-stu-id="37d3d-102">StrongNameSignatureGenerationEx Function</span></span>
<span data-ttu-id="37d3d-103">Podpis silného názvu generuje pro zadané sestavení podle zadané příznaky.</span><span class="sxs-lookup"><span data-stu-id="37d3d-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="37d3d-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="37d3d-104">This function has been deprecated.</span></span> <span data-ttu-id="37d3d-105">Použití [iclrstrongname::strongnamesignaturegenerationex –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="37d3d-105">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37d3d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37d3d-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37d3d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="37d3d-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="37d3d-108">[in] Cesta k souboru, který obsahuje manifest sestavení, pro který se vygeneruje podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="37d3d-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="37d3d-109">[in] Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="37d3d-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="37d3d-110">Pokud `pbKeyBlob` má hodnotu null, `wszKeyContainer` musíte zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="37d3d-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="37d3d-111">V takovém případě uložený v kontejneru pár klíčů se používá k podepsání souboru.</span><span class="sxs-lookup"><span data-stu-id="37d3d-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="37d3d-112">Pokud `pbKeyBlob` nemá hodnotu null, pár klíčů se předpokládá, že mají být obsažena v klíče binární velkých objektů (BLOB).</span><span class="sxs-lookup"><span data-stu-id="37d3d-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="37d3d-113">[in] Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="37d3d-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="37d3d-114">Tento pár je ve formátu vytvořené Win32 `CryptExportKey` funkce.</span><span class="sxs-lookup"><span data-stu-id="37d3d-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="37d3d-115">Pokud `pbKeyBlob` je null, použije kontejneru klíčů určeném parametrem `wszKeyContainer` se předpokládá, že obsahuje pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="37d3d-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="37d3d-116">[in] Velikost v bajtech, z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="37d3d-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="37d3d-117">[out] Ukazatel na umístění, do kterého modul common language runtime vrací podpis.</span><span class="sxs-lookup"><span data-stu-id="37d3d-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="37d3d-118">Pokud `ppbSignatureBlob` je null, podpis modul runtime ukládá do souboru určeného `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="37d3d-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="37d3d-119">Pokud `ppbSignatureBlob` je nenulová, modul common language runtime přiděluje místo ke signatura vrácení.</span><span class="sxs-lookup"><span data-stu-id="37d3d-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="37d3d-120">Volající musí uvolnit prostor pomocí [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="37d3d-120">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="37d3d-121">[out] Velikost v bajtech, vrácený podpis.</span><span class="sxs-lookup"><span data-stu-id="37d3d-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="37d3d-122">[in] Jeden nebo více z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="37d3d-122">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="37d3d-123">`SN_SIGN_ALL_FILES` (0x00000001) - přepočítá všechny hodnoty hash pro propojený moduly.</span><span class="sxs-lookup"><span data-stu-id="37d3d-123">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="37d3d-124">`SN_TEST_SIGN` (0x00000002) - podpis testovacího sestavení.</span><span class="sxs-lookup"><span data-stu-id="37d3d-124">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37d3d-125">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="37d3d-125">Return Value</span></span>  
 <span data-ttu-id="37d3d-126">`true` Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="37d3d-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37d3d-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37d3d-127">Remarks</span></span>  
 <span data-ttu-id="37d3d-128">Zadejte hodnotu null pro `wszFilePath` vypočítat velikost podpisu bez vytvoření podpisu.</span><span class="sxs-lookup"><span data-stu-id="37d3d-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="37d3d-129">Podpis může být buď uloženy přímo v souboru nebo vrátit zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="37d3d-129">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="37d3d-130">Pokud `SN_SIGN_ALL_FILES` je zadán, ale není součástí veřejného klíče (obojí `pbKeyBlob` a `wszFilePath` má hodnotu Null), jsou přepočítány hodnoty hash propojených modulů, ale není znovu podepsat sestavení.</span><span class="sxs-lookup"><span data-stu-id="37d3d-130">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="37d3d-131">Pokud `SN_TEST_SIGN` je zadat hlavičce modulu CLR se nezmění k označení, že je sestavení podepsáno pomocí silného názvu.</span><span class="sxs-lookup"><span data-stu-id="37d3d-131">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="37d3d-132">Pokud `StrongNameSignatureGenerationEx` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="37d3d-132">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37d3d-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37d3d-133">Requirements</span></span>  
 <span data-ttu-id="37d3d-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37d3d-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37d3d-135">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="37d3d-135">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="37d3d-136">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="37d3d-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37d3d-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37d3d-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37d3d-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37d3d-138">See also</span></span>

- [<span data-ttu-id="37d3d-139">StrongNameSignatureGenerationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="37d3d-139">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="37d3d-140">StrongNameSignatureGeneration – metoda</span><span class="sxs-lookup"><span data-stu-id="37d3d-140">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="37d3d-141">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37d3d-141">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
