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
ms.openlocfilehash: d7f481e5c61ec65d2e7414bd47227866f3435028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176900"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="15e74-102">StrongNameSignatureGeneration – funkce</span><span class="sxs-lookup"><span data-stu-id="15e74-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="15e74-103">Generuje podpis silného názvu pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="15e74-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="15e74-104">Tato funkce byla zastaralá.</span><span class="sxs-lookup"><span data-stu-id="15e74-104">This function has been deprecated.</span></span> <span data-ttu-id="15e74-105">Místo toho použijte metodu [ICLRStrongName::StrongNameSignatureGeneration.](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)</span><span class="sxs-lookup"><span data-stu-id="15e74-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15e74-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15e74-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="15e74-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="15e74-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="15e74-108">[v] Cesta k souboru, který obsahuje manifest sestavení, pro které bude generován podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="15e74-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="15e74-109">[v] Název kontejneru klíčů, který obsahuje dvojici veřejného a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="15e74-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="15e74-110">Pokud `pbKeyBlob` je `wszKeyContainer` null, musí zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="15e74-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="15e74-111">V tomto případě dvojice klíčů uložená v kontejneru se používá k podepsání souboru.</span><span class="sxs-lookup"><span data-stu-id="15e74-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="15e74-112">Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů je obsažena v binárním velkém objektu klíče (BLOB).</span><span class="sxs-lookup"><span data-stu-id="15e74-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="15e74-113">Klíče musí být 1024bitové podpisové klíče Rivest-Shamir-Adleman (RSA).</span><span class="sxs-lookup"><span data-stu-id="15e74-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="15e74-114">V současné době nejsou podporovány žádné jiné typy klíčů.</span><span class="sxs-lookup"><span data-stu-id="15e74-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="15e74-115">[v] Ukazatel na dvojici veřejného a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="15e74-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="15e74-116">Tento pár je ve formátu vytvořeném `CryptExportKey` funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="15e74-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="15e74-117">Pokud `pbKeyBlob` je null, předpokládá `wszKeyContainer` se, že kontejner klíčů určený podle je obsahující dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="15e74-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="15e74-118">[v] Velikost v bajtů `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="15e74-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="15e74-119">[out] Ukazatel na umístění, do kterého běžný jazyk runtime vrátí podpis.</span><span class="sxs-lookup"><span data-stu-id="15e74-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="15e74-120">Pokud `ppbSignatureBlob` je null, runtime ukládá podpis v `wszFilePath`souboru určeném .</span><span class="sxs-lookup"><span data-stu-id="15e74-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="15e74-121">Pokud `ppbSignatureBlob` není null, běžný jazyk common time přiděluje místo, ve kterém chcete vrátit podpis.</span><span class="sxs-lookup"><span data-stu-id="15e74-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="15e74-122">Volající musí uvolnit toto místo pomocí funkce [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)</span><span class="sxs-lookup"><span data-stu-id="15e74-122">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="15e74-123">[out] Velikost vráceného podpisu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="15e74-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15e74-124">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="15e74-124">Return Value</span></span>  
 <span data-ttu-id="15e74-125">`true`po úspěšném dokončení; v `false`opačném případě .</span><span class="sxs-lookup"><span data-stu-id="15e74-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15e74-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15e74-126">Remarks</span></span>  
 <span data-ttu-id="15e74-127">Zadejte `wszFilePath` hodnotu null pro výpočet velikosti podpisu bez vytvoření podpisu.</span><span class="sxs-lookup"><span data-stu-id="15e74-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="15e74-128">Podpis může být uložen buď přímo v souboru, nebo vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="15e74-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="15e74-129">Pokud `StrongNameSignatureGeneration` se funkce nedokončí úspěšně, zavolejte funkci [StrongNameErrorInfo,](strongnameerrorinfo-function.md) abyste načetli poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="15e74-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15e74-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15e74-130">Requirements</span></span>  
 <span data-ttu-id="15e74-131">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15e74-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15e74-132">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="15e74-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="15e74-133">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="15e74-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="15e74-134">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15e74-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15e74-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="15e74-135">See also</span></span>

- [<span data-ttu-id="15e74-136">StrongNameSignatureGeneration – metoda</span><span class="sxs-lookup"><span data-stu-id="15e74-136">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="15e74-137">StrongNameSignatureGenerationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="15e74-137">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="15e74-138">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15e74-138">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
