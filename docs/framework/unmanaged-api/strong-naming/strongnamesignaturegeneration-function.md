---
title: StrongNameSignatureGeneration – funkce
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1abb7efe0f30ff14d51f9486d6d5b04d2faa053
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773747"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="a9336-102">StrongNameSignatureGeneration – funkce</span><span class="sxs-lookup"><span data-stu-id="a9336-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="a9336-103">Podpis silného názvu generuje pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="a9336-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="a9336-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="a9336-104">This function has been deprecated.</span></span> <span data-ttu-id="a9336-105">Použití [iclrstrongname::strongnamesignaturegeneration –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="a9336-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9336-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9336-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9336-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9336-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="a9336-108">[in] Cesta k souboru, který obsahuje manifest sestavení, pro který se vygeneruje podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="a9336-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="a9336-109">[in] Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="a9336-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="a9336-110">Pokud `pbKeyBlob` má hodnotu null, `wszKeyContainer` musíte zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="a9336-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="a9336-111">V takovém případě uložený v kontejneru pár klíčů se používá k podepsání souboru.</span><span class="sxs-lookup"><span data-stu-id="a9336-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="a9336-112">Pokud `pbKeyBlob` nemá hodnotu null, pár klíčů se předpokládá, že mají být obsažena v klíče binární velkých objektů (BLOB).</span><span class="sxs-lookup"><span data-stu-id="a9336-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="a9336-113">Klíče musí být Rivest-Shamir-Adleman 1024 bitů (RSA) podpisových klíčů.</span><span class="sxs-lookup"><span data-stu-id="a9336-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="a9336-114">Jiné typy klíčů jsou v tuto chvíli nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="a9336-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="a9336-115">[in] Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="a9336-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="a9336-116">Tento pár je ve formátu vytvořené Win32 `CryptExportKey` funkce.</span><span class="sxs-lookup"><span data-stu-id="a9336-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="a9336-117">Pokud `pbKeyBlob` je null, použije kontejneru klíčů určeném parametrem `wszKeyContainer` se předpokládá, že obsahuje pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="a9336-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="a9336-118">[in] Velikost v bajtech, z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="a9336-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="a9336-119">[out] Ukazatel na umístění, do kterého modul common language runtime vrací podpis.</span><span class="sxs-lookup"><span data-stu-id="a9336-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="a9336-120">Pokud `ppbSignatureBlob` je null, podpis modul runtime ukládá do souboru určeného `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="a9336-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="a9336-121">Pokud `ppbSignatureBlob` je nenulová, modul common language runtime přiděluje místo ke signatura vrácení.</span><span class="sxs-lookup"><span data-stu-id="a9336-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="a9336-122">Volající musí uvolnit prostor pomocí [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="a9336-122">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="a9336-123">[out] Velikost v bajtech, vrácený podpis.</span><span class="sxs-lookup"><span data-stu-id="a9336-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9336-124">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a9336-124">Return Value</span></span>  
 <span data-ttu-id="a9336-125">`true` Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="a9336-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9336-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9336-126">Remarks</span></span>  
 <span data-ttu-id="a9336-127">Zadejte hodnotu null pro `wszFilePath` vypočítat velikost podpisu bez vytvoření podpisu.</span><span class="sxs-lookup"><span data-stu-id="a9336-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="a9336-128">Podpis může být buď přímo v souboru uložit nebo vrátit zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="a9336-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="a9336-129">Pokud `StrongNameSignatureGeneration` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="a9336-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9336-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9336-130">Requirements</span></span>  
 <span data-ttu-id="a9336-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9336-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9336-132">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a9336-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a9336-133">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9336-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9336-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9336-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9336-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9336-135">See also</span></span>

- [<span data-ttu-id="a9336-136">StrongNameSignatureGeneration – metoda</span><span class="sxs-lookup"><span data-stu-id="a9336-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="a9336-137">StrongNameSignatureGenerationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="a9336-137">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="a9336-138">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9336-138">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
