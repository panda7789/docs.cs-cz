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
ms.openlocfilehash: 966a2a628f30f1999688da7b6ba435c1d6cb830c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094668"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="c3f3a-102">StrongNameGetPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="c3f3a-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="c3f3a-103">Získá veřejný klíč z páru privátních a veřejných klíčů.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="c3f3a-104">Pár klíčů je možné zadat buď jako název kontejneru klíčů v rámci zprostředkovatele kryptografických služeb (CSP), nebo jako nezpracovaných kolekcí bajtů.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="c3f3a-105">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-105">This function has been deprecated.</span></span> <span data-ttu-id="c3f3a-106">Místo toho použijte metodu [ICLRStrongName:: StrongNameGetPublicKey –](../hosting/iclrstrongname-strongnamegetpublickey-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c3f3a-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3f3a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3f3a-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3f3a-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3f3a-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="c3f3a-109">pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="c3f3a-110">Pokud je `pbKeyBlob` null, musí `szKeyContainer` v rámci CSP určovat platný kontejner.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="c3f3a-111">V tomto případě `StrongNameGetPublicKey` extrahuje veřejný klíč z páru klíčů, který je uložený v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="c3f3a-112">Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="c3f3a-113">Klíče musí být 1024-bit Rivest-Shamir-Adleman (RSA) Signing Keys.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="c3f3a-114">V tuto chvíli není podporovaný žádný jiný typ klíčů.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="c3f3a-115">pro Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="c3f3a-116">Tato dvojice je ve formátu vytvořeném funkcí Win32 `CryptExportKey`.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="c3f3a-117">Je-li `pbKeyBlob` null, předpokládá se, že kontejner klíčů určený parametrem `szKeyContainer` obsahuje dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="c3f3a-118">pro Velikost `pbKeyBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="c3f3a-119">mimo Vrácený objekt BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="c3f3a-120">Parametr `ppbPublicKeyBlob` je přidělen modulem CLR (Common Language Runtime) a vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="c3f3a-121">Volající musí uvolnit paměť pomocí funkce [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="c3f3a-121">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="c3f3a-122">mimo Velikost vráceného objektu BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3f3a-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c3f3a-123">Return Value</span></span>  
 <span data-ttu-id="c3f3a-124">`true` po úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3f3a-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3f3a-125">Remarks</span></span>  
 <span data-ttu-id="c3f3a-126">Veřejný klíč je obsažen ve struktuře [PublicKeyBlob –](publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="c3f3a-126">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="c3f3a-127">Pokud se funkce `StrongNameGetPublicKey` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="c3f3a-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3f3a-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3f3a-128">Requirements</span></span>  
 <span data-ttu-id="c3f3a-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3f3a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3f3a-130">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="c3f3a-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c3f3a-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c3f3a-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c3f3a-132">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3f3a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3f3a-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3f3a-133">See also</span></span>

- [<span data-ttu-id="c3f3a-134">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="c3f3a-134">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="c3f3a-135">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="c3f3a-135">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="c3f3a-136">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3f3a-136">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="c3f3a-137">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="c3f3a-137">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
