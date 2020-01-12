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
ms.openlocfilehash: ced7540afe931fb91240c770d76d205400157a51
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901103"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="f5c56-102">ICLRStrongName::StrongNameSignatureGeneration – metoda</span><span class="sxs-lookup"><span data-stu-id="f5c56-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="f5c56-103">Vygeneruje podpis silného názvu pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="f5c56-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5c56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5c56-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5c56-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5c56-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="f5c56-106">pro Cesta k souboru, který obsahuje manifest sestavení, pro který bude vytvořen podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="f5c56-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="f5c56-107">pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="f5c56-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="f5c56-108">Pokud má `pbKeyBlob` hodnotu null, musí `wszKeyContainer` zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="f5c56-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="f5c56-109">V tomto případě se k podepsání souboru používá pár klíčů uložený v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="f5c56-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="f5c56-110">Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.</span><span class="sxs-lookup"><span data-stu-id="f5c56-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="f5c56-111">Klíče musí být 1024-bit Rivest-Shamir-Adleman (RSA) Signing Keys.</span><span class="sxs-lookup"><span data-stu-id="f5c56-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="f5c56-112">V tuto chvíli není podporovaný žádný jiný typ klíčů.</span><span class="sxs-lookup"><span data-stu-id="f5c56-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="f5c56-113">pro Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="f5c56-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="f5c56-114">Tato dvojice je ve formátu vytvořeném funkcí Win32 `CryptExportKey`.</span><span class="sxs-lookup"><span data-stu-id="f5c56-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="f5c56-115">Je-li `pbKeyBlob` null, předpokládá se, že kontejner klíčů určený parametrem `wszKeyContainer` obsahuje dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="f5c56-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="f5c56-116">pro Velikost `pbKeyBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="f5c56-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="f5c56-117">mimo Ukazatel na umístění, do kterého modul common language runtime vrátí podpis.</span><span class="sxs-lookup"><span data-stu-id="f5c56-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="f5c56-118">Pokud je `ppbSignatureBlob` null, modul runtime uloží podpis do souboru určeného parametrem `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="f5c56-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="f5c56-119">Pokud `ppbSignatureBlob` není null, modul CLR (Common Language Runtime) přidělí místo, ve kterém se podpis vrátí.</span><span class="sxs-lookup"><span data-stu-id="f5c56-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="f5c56-120">Volající musí uvolnit toto místo pomocí metody [ICLRStrongName:: StrongNameFreeBuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f5c56-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="f5c56-121">mimo Velikost vráceného podpisu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="f5c56-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5c56-122">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f5c56-122">Return Value</span></span>  
 <span data-ttu-id="f5c56-123">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="f5c56-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5c56-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5c56-124">Remarks</span></span>  
 <span data-ttu-id="f5c56-125">Zadejte hodnotu null pro `wszFilePath` pro výpočet velikosti podpisu bez vytvoření podpisu.</span><span class="sxs-lookup"><span data-stu-id="f5c56-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="f5c56-126">Podpis může být uložen buď přímo v souboru, nebo vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="f5c56-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5c56-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5c56-127">Requirements</span></span>  
 <span data-ttu-id="f5c56-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5c56-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5c56-129">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="f5c56-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f5c56-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f5c56-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5c56-131">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5c56-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c56-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5c56-132">See also</span></span>

- [<span data-ttu-id="f5c56-133">StrongNameSignatureGenerationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="f5c56-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="f5c56-134">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5c56-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
