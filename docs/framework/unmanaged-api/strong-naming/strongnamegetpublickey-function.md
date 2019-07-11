---
title: StrongNameGetPublicKey – funkce
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6e9e5c199ad437290d7bf19d65b5f29a0abed5e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780113"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="5a95c-102">StrongNameGetPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="5a95c-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="5a95c-103">Získá veřejný klíč z páru klíčů privátní nebo veřejné.</span><span class="sxs-lookup"><span data-stu-id="5a95c-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="5a95c-104">Pár klíčů může být zadán buď jako název kontejneru klíčů ve zprostředkovateli kryptografických služeb (CSP), nebo jako nezpracovaný kolekce bajtů.</span><span class="sxs-lookup"><span data-stu-id="5a95c-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="5a95c-105">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="5a95c-105">This function has been deprecated.</span></span> <span data-ttu-id="5a95c-106">Použití [iclrstrongname::strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="5a95c-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a95c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a95c-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a95c-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a95c-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="5a95c-109">[in] Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="5a95c-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="5a95c-110">Pokud `pbKeyBlob` má hodnotu null, `szKeyContainer` musíte zadat platný kontejner ve zprostředkovateli CSP.</span><span class="sxs-lookup"><span data-stu-id="5a95c-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="5a95c-111">V takovém případě `StrongNameGetPublicKey` extrahuje veřejný klíč z páru klíčů ukládat do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5a95c-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="5a95c-112">Pokud `pbKeyBlob` nemá hodnotu null, pár klíčů se předpokládá, že mají být obsažena v klíče binární velkých objektů (BLOB).</span><span class="sxs-lookup"><span data-stu-id="5a95c-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="5a95c-113">Klíče musí být Rivest-Shamir-Adleman 1024 bitů (RSA) podpisových klíčů.</span><span class="sxs-lookup"><span data-stu-id="5a95c-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="5a95c-114">Jiné typy klíčů jsou v tuto chvíli nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="5a95c-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="5a95c-115">[in] Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="5a95c-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="5a95c-116">Tento pár je ve formátu vytvořené Win32 `CryptExportKey` funkce.</span><span class="sxs-lookup"><span data-stu-id="5a95c-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="5a95c-117">Pokud `pbKeyBlob` je null, použije kontejneru klíčů určeném parametrem `szKeyContainer` se předpokládá, že obsahuje pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="5a95c-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="5a95c-118">[in] Velikost v bajtech, z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="5a95c-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="5a95c-119">[out] Vrácené veřejného klíče objektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="5a95c-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="5a95c-120">`ppbPublicKeyBlob` Parametr je přidělí modul common language runtime a vrátit zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="5a95c-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="5a95c-121">Volající musí uvolnit paměť pomocí [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="5a95c-121">The caller must free the memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="5a95c-122">[out] Velikost veřejného klíče vráceného objektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="5a95c-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a95c-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5a95c-123">Return Value</span></span>  
 <span data-ttu-id="5a95c-124">`true` Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="5a95c-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a95c-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a95c-125">Remarks</span></span>  
 <span data-ttu-id="5a95c-126">Veřejný klíč je součástí [publickeyblob –](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="5a95c-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="5a95c-127">Pokud `StrongNameGetPublicKey` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="5a95c-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a95c-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a95c-128">Requirements</span></span>  
 <span data-ttu-id="5a95c-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a95c-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a95c-130">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="5a95c-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="5a95c-131">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5a95c-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5a95c-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a95c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a95c-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a95c-133">See also</span></span>

- [<span data-ttu-id="5a95c-134">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="5a95c-134">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="5a95c-135">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="5a95c-135">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="5a95c-136">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a95c-136">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="5a95c-137">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="5a95c-137">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
