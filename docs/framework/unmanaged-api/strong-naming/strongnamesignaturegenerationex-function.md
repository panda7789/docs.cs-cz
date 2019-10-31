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
ms.openlocfilehash: e8f63a6379af8f2b7b88c511840622d49d65d587
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141584"
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="52e10-102">StrongNameSignatureGenerationEx – funkce</span><span class="sxs-lookup"><span data-stu-id="52e10-102">StrongNameSignatureGenerationEx Function</span></span>
<span data-ttu-id="52e10-103">Vygeneruje podpis silného názvu pro zadané sestavení podle zadaných příznaků.</span><span class="sxs-lookup"><span data-stu-id="52e10-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="52e10-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="52e10-104">This function has been deprecated.</span></span> <span data-ttu-id="52e10-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameSignatureGenerationEx –](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="52e10-105">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52e10-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52e10-106">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="52e10-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="52e10-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="52e10-108">pro Cesta k souboru, který obsahuje manifest sestavení, pro který bude vytvořen podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="52e10-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="52e10-109">pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="52e10-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="52e10-110">Pokud má `pbKeyBlob` hodnotu null, musí `wszKeyContainer` zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="52e10-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="52e10-111">V tomto případě se k podepsání souboru používá pár klíčů uložený v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="52e10-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="52e10-112">Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.</span><span class="sxs-lookup"><span data-stu-id="52e10-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="52e10-113">pro Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="52e10-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="52e10-114">Tato dvojice je ve formátu vytvořeném funkcí Win32 `CryptExportKey`.</span><span class="sxs-lookup"><span data-stu-id="52e10-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="52e10-115">Je-li `pbKeyBlob` null, předpokládá se, že kontejner klíčů určený parametrem `wszKeyContainer` obsahuje dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="52e10-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="52e10-116">pro Velikost `pbKeyBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="52e10-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="52e10-117">mimo Ukazatel na umístění, do kterého modul common language runtime vrátí podpis.</span><span class="sxs-lookup"><span data-stu-id="52e10-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="52e10-118">Pokud je `ppbSignatureBlob` null, modul runtime uloží podpis do souboru určeného parametrem `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="52e10-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="52e10-119">Pokud `ppbSignatureBlob` není null, modul CLR (Common Language Runtime) přidělí místo, ve kterém se podpis vrátí.</span><span class="sxs-lookup"><span data-stu-id="52e10-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="52e10-120">Volající musí uvolnit toto místo pomocí funkce [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="52e10-120">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="52e10-121">mimo Velikost vráceného podpisu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="52e10-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="52e10-122">pro Jedna nebo více z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="52e10-122">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="52e10-123">`SN_SIGN_ALL_FILES` (0x00000001) – přepočítá všechny hodnoty hash pro propojené moduly.</span><span class="sxs-lookup"><span data-stu-id="52e10-123">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="52e10-124">`SN_TEST_SIGN` (0x00000002) – otestuje podpis sestavení.</span><span class="sxs-lookup"><span data-stu-id="52e10-124">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52e10-125">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="52e10-125">Return Value</span></span>  
 <span data-ttu-id="52e10-126">`true` po úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="52e10-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52e10-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52e10-127">Remarks</span></span>  
 <span data-ttu-id="52e10-128">Zadejte hodnotu null pro `wszFilePath` pro výpočet velikosti podpisu bez vytvoření podpisu.</span><span class="sxs-lookup"><span data-stu-id="52e10-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="52e10-129">Podpis může být buď uložen přímo v souboru, nebo vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="52e10-129">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="52e10-130">Pokud je zadána `SN_SIGN_ALL_FILES`, ale není k dispozici veřejný klíč (`pbKeyBlob` i `wszFilePath` mají hodnotu null), jsou přepočítány hodnoty hash pro propojené moduly, ale sestavení není znovu podepsáno.</span><span class="sxs-lookup"><span data-stu-id="52e10-130">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="52e10-131">Je-li zadán `SN_TEST_SIGN`, není záhlaví modulu CLR (Common Language Runtime) upraveno, aby označovalo, že sestavení je podepsáno silným názvem.</span><span class="sxs-lookup"><span data-stu-id="52e10-131">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="52e10-132">Pokud se funkce `StrongNameSignatureGenerationEx` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="52e10-132">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52e10-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52e10-133">Requirements</span></span>  
 <span data-ttu-id="52e10-134">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52e10-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52e10-135">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="52e10-135">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="52e10-136">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="52e10-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="52e10-137">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52e10-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e10-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52e10-138">See also</span></span>

- [<span data-ttu-id="52e10-139">StrongNameSignatureGenerationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="52e10-139">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="52e10-140">StrongNameSignatureGeneration – metoda</span><span class="sxs-lookup"><span data-stu-id="52e10-140">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="52e10-141">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52e10-141">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
