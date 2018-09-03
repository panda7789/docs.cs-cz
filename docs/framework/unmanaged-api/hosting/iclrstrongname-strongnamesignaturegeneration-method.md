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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1571e43d6a89af453d6289ccb646c7222f0a5ad6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483107"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="f81f0-102">ICLRStrongName::StrongNameSignatureGeneration – metoda</span><span class="sxs-lookup"><span data-stu-id="f81f0-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="f81f0-103">Podpis silného názvu generuje pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="f81f0-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f81f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f81f0-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f81f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f81f0-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="f81f0-106">[in] Cesta k souboru, který obsahuje manifest sestavení, pro který se vygeneruje podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="f81f0-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="f81f0-107">[in] Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="f81f0-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="f81f0-108">Pokud `pbKeyBlob` má hodnotu null, `wszKeyContainer` musíte zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="f81f0-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="f81f0-109">V takovém případě uložený v kontejneru pár klíčů se používá k podepsání souboru.</span><span class="sxs-lookup"><span data-stu-id="f81f0-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="f81f0-110">Pokud `pbKeyBlob` nemá hodnotu null, pár klíčů se předpokládá, že mají být obsažena v klíče binární velkých objektů (BLOB).</span><span class="sxs-lookup"><span data-stu-id="f81f0-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="f81f0-111">Klíče musí být Rivest-Shamir-Adleman 1024 bitů (RSA) podpisových klíčů.</span><span class="sxs-lookup"><span data-stu-id="f81f0-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="f81f0-112">Jiné typy klíčů jsou v tuto chvíli nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="f81f0-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="f81f0-113">[in] Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="f81f0-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="f81f0-114">Tento pár je ve formátu vytvořené Win32 `CryptExportKey` funkce.</span><span class="sxs-lookup"><span data-stu-id="f81f0-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="f81f0-115">Pokud `pbKeyBlob` je null, použije kontejneru klíčů určeném parametrem `wszKeyContainer` se předpokládá, že obsahuje pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="f81f0-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="f81f0-116">[in] Velikost v bajtech, z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="f81f0-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="f81f0-117">[out] Ukazatel na umístění, do kterého modul common language runtime vrací podpis.</span><span class="sxs-lookup"><span data-stu-id="f81f0-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="f81f0-118">Pokud `ppbSignatureBlob` je null, podpis modul runtime ukládá do souboru určeného `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="f81f0-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="f81f0-119">Pokud `ppbSignatureBlob` je nenulová, modul common language runtime přiděluje místo ke signatura vrácení.</span><span class="sxs-lookup"><span data-stu-id="f81f0-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="f81f0-120">Volající musí pomocí bezplatné toto místo [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="f81f0-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="f81f0-121">[out] Velikost v bajtech, vrácený podpis.</span><span class="sxs-lookup"><span data-stu-id="f81f0-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f81f0-122">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f81f0-122">Return Value</span></span>  
 <span data-ttu-id="f81f0-123">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="f81f0-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f81f0-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f81f0-124">Remarks</span></span>  
 <span data-ttu-id="f81f0-125">Zadejte hodnotu null pro `wszFilePath` vypočítat velikost podpisu bez vytvoření podpisu.</span><span class="sxs-lookup"><span data-stu-id="f81f0-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="f81f0-126">Podpis může být buď přímo v souboru uložit nebo vrátit zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="f81f0-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f81f0-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f81f0-127">Requirements</span></span>  
 <span data-ttu-id="f81f0-128">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f81f0-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f81f0-129">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f81f0-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f81f0-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f81f0-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f81f0-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f81f0-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f81f0-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="f81f0-132">See Also</span></span>  
 [<span data-ttu-id="f81f0-133">StrongNameSignatureGenerationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="f81f0-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [<span data-ttu-id="f81f0-134">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f81f0-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
