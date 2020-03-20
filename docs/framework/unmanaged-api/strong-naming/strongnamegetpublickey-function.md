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
ms.openlocfilehash: fcdd4a3f07b4499fd2388b5d165c409da9150466
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176926"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="bca59-102">StrongNameGetPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="bca59-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="bca59-103">Získá veřejný klíč z dvojice soukromého a veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="bca59-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="bca59-104">Pár klíčů lze dodat buď jako název kontejneru klíčů v rámci zprostředkovatele kryptografických služeb (CSP) nebo jako nezpracovaná kolekce bajtů.</span><span class="sxs-lookup"><span data-stu-id="bca59-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="bca59-105">Tato funkce byla zastaralá.</span><span class="sxs-lookup"><span data-stu-id="bca59-105">This function has been deprecated.</span></span> <span data-ttu-id="bca59-106">Místo toho použijte metodu [ICLRStrongName::StrongNameGetPublicKey.](../hosting/iclrstrongname-strongnamegetpublickey-method.md)</span><span class="sxs-lookup"><span data-stu-id="bca59-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca59-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bca59-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bca59-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="bca59-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="bca59-109">[v] Název kontejneru klíčů, který obsahuje dvojici veřejného a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="bca59-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="bca59-110">Pokud `pbKeyBlob` je `szKeyContainer` null, musí zadat platný kontejner v rámci ověřovatce.</span><span class="sxs-lookup"><span data-stu-id="bca59-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="bca59-111">V tomto `StrongNameGetPublicKey` případě extrahuje veřejný klíč z dvojice klíčů uložené v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="bca59-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="bca59-112">Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů je obsažena v binárním velkém objektu klíče (BLOB).</span><span class="sxs-lookup"><span data-stu-id="bca59-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="bca59-113">Klíče musí být 1024bitové podpisové klíče Rivest-Shamir-Adleman (RSA).</span><span class="sxs-lookup"><span data-stu-id="bca59-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="bca59-114">V současné době nejsou podporovány žádné jiné typy klíčů.</span><span class="sxs-lookup"><span data-stu-id="bca59-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="bca59-115">[v] Ukazatel na dvojici veřejného a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="bca59-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="bca59-116">Tento pár je ve formátu vytvořeném `CryptExportKey` funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="bca59-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="bca59-117">Pokud `pbKeyBlob` je null, předpokládá `szKeyContainer` se, že kontejner klíčů určený podle je obsahující dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="bca59-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="bca59-118">[v] Velikost v bajtů `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="bca59-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="bca59-119">[out] Vrácený veřejný klíč BLOB.</span><span class="sxs-lookup"><span data-stu-id="bca59-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="bca59-120">Parametr `ppbPublicKeyBlob` je přidělen a běžný jazyk runtime a vrácena volajícímu.</span><span class="sxs-lookup"><span data-stu-id="bca59-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="bca59-121">Volající musí uvolnit paměť pomocí funkce [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)</span><span class="sxs-lookup"><span data-stu-id="bca59-121">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="bca59-122">[out] Velikost vráceného objektu BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="bca59-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bca59-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bca59-123">Return Value</span></span>  
 <span data-ttu-id="bca59-124">`true`po úspěšném dokončení; v `false`opačném případě .</span><span class="sxs-lookup"><span data-stu-id="bca59-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bca59-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bca59-125">Remarks</span></span>  
 <span data-ttu-id="bca59-126">Veřejný klíč je obsažen ve struktuře [PublicKeyBlob.](publickeyblob-structure.md)</span><span class="sxs-lookup"><span data-stu-id="bca59-126">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="bca59-127">Pokud `StrongNameGetPublicKey` se funkce nedokončí úspěšně, zavolejte funkci [StrongNameErrorInfo,](strongnameerrorinfo-function.md) abyste načetli poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="bca59-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bca59-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bca59-128">Requirements</span></span>  
 <span data-ttu-id="bca59-129">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bca59-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bca59-130">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="bca59-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="bca59-131">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bca59-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bca59-132">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bca59-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca59-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="bca59-133">See also</span></span>

- [<span data-ttu-id="bca59-134">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="bca59-134">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="bca59-135">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="bca59-135">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="bca59-136">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bca59-136">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="bca59-137">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="bca59-137">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
