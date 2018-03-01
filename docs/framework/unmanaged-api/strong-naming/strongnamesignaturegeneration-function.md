---
title: "StrongNameSignatureGeneration – funkce"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c26e230f2bc0b115d898a34742fe3e637f934fd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="b110a-102">StrongNameSignatureGeneration – funkce</span><span class="sxs-lookup"><span data-stu-id="b110a-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="b110a-103">Podpis silného názvu generuje pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="b110a-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="b110a-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="b110a-104">This function has been deprecated.</span></span> <span data-ttu-id="b110a-105">Použití [iclrstrongname::strongnamesignaturegeneration –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="b110a-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b110a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b110a-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b110a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="b110a-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b110a-108">[v] Cesta k souboru, který obsahuje manifest sestavení, pro které se budou generovat podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="b110a-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="b110a-109">[v] Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="b110a-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="b110a-110">Pokud `pbKeyBlob` má hodnotu null, `wszKeyContainer` musíte zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="b110a-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="b110a-111">Pár klíčů, ukládat do kontejneru v takovém případě se používá k podepsání souboru.</span><span class="sxs-lookup"><span data-stu-id="b110a-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="b110a-112">Pokud `pbKeyBlob` nemá hodnotu null, dvojici klíčů se předpokládá, že mají být obsažena v klíče binární rozsáhlý objekt (binární rozsáhlý OBJEKT).</span><span class="sxs-lookup"><span data-stu-id="b110a-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="b110a-113">Klíče musí být Rivest-Shamir-Adleman 1024 bitů (RSA) podpisových klíčů.</span><span class="sxs-lookup"><span data-stu-id="b110a-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="b110a-114">Žádné jiné typy klíčů jsou podporovány v tuto chvíli.</span><span class="sxs-lookup"><span data-stu-id="b110a-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="b110a-115">[v] Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="b110a-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="b110a-116">Tato dvojice je ve formátu vytvořené Win32 `CryptExportKey` funkce.</span><span class="sxs-lookup"><span data-stu-id="b110a-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="b110a-117">Pokud `pbKeyBlob` je null, kontejner klíčů určeného `wszKeyContainer` se předpokládá, že obsahovat dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="b110a-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="b110a-118">[v] Velikost v bajtech z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="b110a-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="b110a-119">[out] Ukazatel na umístění, do které modul common language runtime vrátí podpis.</span><span class="sxs-lookup"><span data-stu-id="b110a-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="b110a-120">Pokud `ppbSignatureBlob` je null, podpis modulu runtime ukládá do souboru určeného `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="b110a-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="b110a-121">Pokud `ppbSignatureBlob` je hodnotou not null, modul common language runtime přiděluje místo k vrácení podpis.</span><span class="sxs-lookup"><span data-stu-id="b110a-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="b110a-122">Volající musí volné toto místo pomocí [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="b110a-122">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="b110a-123">[out] Velikost v bajtech vrácený podpis.</span><span class="sxs-lookup"><span data-stu-id="b110a-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b110a-124">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b110a-124">Return Value</span></span>  
 <span data-ttu-id="b110a-125">`true`Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="b110a-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b110a-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b110a-126">Remarks</span></span>  
 <span data-ttu-id="b110a-127">Zadejte hodnotu null pro `wszFilePath` vypočítat velikost podpisu bez vytvoření podpisu.</span><span class="sxs-lookup"><span data-stu-id="b110a-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="b110a-128">Podpis může být uložená buď přímo v souboru nebo vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="b110a-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="b110a-129">Pokud `StrongNameSignatureGeneration` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="b110a-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b110a-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b110a-130">Requirements</span></span>  
 <span data-ttu-id="b110a-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b110a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b110a-132">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="b110a-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b110a-133">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b110a-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b110a-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b110a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b110a-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="b110a-135">See Also</span></span>  
 [<span data-ttu-id="b110a-136">StrongNameSignatureGeneration – metoda</span><span class="sxs-lookup"><span data-stu-id="b110a-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [<span data-ttu-id="b110a-137">StrongNameSignatureGenerationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="b110a-137">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [<span data-ttu-id="b110a-138">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b110a-138">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
