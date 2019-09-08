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
ms.openlocfilehash: 48cdd550e5d8c7c75a603d74456e99a066d5c599
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798977"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="9c3fc-102">StrongNameSignatureGeneration – funkce</span><span class="sxs-lookup"><span data-stu-id="9c3fc-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="9c3fc-103">Vygeneruje podpis silného názvu pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="9c3fc-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-104">This function has been deprecated.</span></span> <span data-ttu-id="9c3fc-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameSignatureGeneration –](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9c3fc-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c3fc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c3fc-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9c3fc-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c3fc-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="9c3fc-108">pro Cesta k souboru, který obsahuje manifest sestavení, pro který bude vytvořen podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="9c3fc-109">pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="9c3fc-110">Pokud `pbKeyBlob` má hodnotu null `wszKeyContainer` , musí určovat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="9c3fc-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="9c3fc-111">V tomto případě se k podepsání souboru používá pár klíčů uložený v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="9c3fc-112">Pokud `pbKeyBlob` hodnota není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="9c3fc-113">Klíče musí být 1024-bit Rivest-Shamir-Adleman (RSA) Signing Keys.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="9c3fc-114">V tuto chvíli není podporovaný žádný jiný typ klíčů.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="9c3fc-115">pro Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="9c3fc-116">Tato dvojice je ve formátu vytvořeném funkcí Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="9c3fc-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="9c3fc-117">Pokud `pbKeyBlob` má hodnotu null, předpokládá se, že `wszKeyContainer` kontejner klíčů určený parametrem obsahuje dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="9c3fc-118">pro Velikost v bajtech `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="9c3fc-119">mimo Ukazatel na umístění, do kterého modul common language runtime vrátí podpis.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="9c3fc-120">Pokud `ppbSignatureBlob` je null, modul runtime uloží podpis do souboru určeného parametrem `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="9c3fc-121">Pokud `ppbSignatureBlob` hodnota není null, modul CLR (Common Language Runtime) přidělí místo, ve kterém se podpis vrátí.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="9c3fc-122">Volající musí uvolnit toto místo pomocí funkce [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="9c3fc-122">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="9c3fc-123">mimo Velikost vráceného podpisu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c3fc-124">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9c3fc-124">Return Value</span></span>  
 <span data-ttu-id="9c3fc-125">`true`Po úspěšném dokončení; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="9c3fc-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c3fc-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9c3fc-126">Remarks</span></span>  
 <span data-ttu-id="9c3fc-127">`wszFilePath` Chcete-li vypočítat velikost podpisu bez vytvoření podpisu, zadejte hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="9c3fc-128">Podpis může být uložen buď přímo v souboru, nebo vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="9c3fc-129">Pokud se `StrongNameSignatureGeneration` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="9c3fc-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c3fc-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c3fc-130">Requirements</span></span>  
 <span data-ttu-id="9c3fc-131">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c3fc-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c3fc-132">**Hlaviček** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="9c3fc-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9c3fc-133">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9c3fc-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c3fc-134">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c3fc-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c3fc-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c3fc-135">See also</span></span>

- [<span data-ttu-id="9c3fc-136">StrongNameSignatureGeneration – metoda</span><span class="sxs-lookup"><span data-stu-id="9c3fc-136">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="9c3fc-137">StrongNameSignatureGenerationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="9c3fc-137">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="9c3fc-138">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c3fc-138">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
