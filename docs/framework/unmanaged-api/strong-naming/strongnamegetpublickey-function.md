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
ms.openlocfilehash: ae87ebd0b8225f14ca029fac80528d47f5a866cf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799056"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="406ca-102">StrongNameGetPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="406ca-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="406ca-103">Získá veřejný klíč z páru privátních a veřejných klíčů.</span><span class="sxs-lookup"><span data-stu-id="406ca-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="406ca-104">Pár klíčů je možné zadat buď jako název kontejneru klíčů v rámci zprostředkovatele kryptografických služeb (CSP), nebo jako nezpracovaných kolekcí bajtů.</span><span class="sxs-lookup"><span data-stu-id="406ca-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="406ca-105">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="406ca-105">This function has been deprecated.</span></span> <span data-ttu-id="406ca-106">Místo toho použijte metodu [ICLRStrongName:: StrongNameGetPublicKey –](../hosting/iclrstrongname-strongnamegetpublickey-method.md) .</span><span class="sxs-lookup"><span data-stu-id="406ca-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="406ca-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="406ca-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="406ca-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="406ca-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="406ca-109">pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="406ca-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="406ca-110">Pokud `pbKeyBlob` má hodnotu null `szKeyContainer` , musí v rámci CSP určovat platný kontejner.</span><span class="sxs-lookup"><span data-stu-id="406ca-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="406ca-111">V tomto případě `StrongNameGetPublicKey` extrahuje veřejný klíč z páru klíčů, který je uložený v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="406ca-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="406ca-112">Pokud `pbKeyBlob` hodnota není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.</span><span class="sxs-lookup"><span data-stu-id="406ca-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="406ca-113">Klíče musí být 1024-bit Rivest-Shamir-Adleman (RSA) Signing Keys.</span><span class="sxs-lookup"><span data-stu-id="406ca-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="406ca-114">V tuto chvíli není podporovaný žádný jiný typ klíčů.</span><span class="sxs-lookup"><span data-stu-id="406ca-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="406ca-115">pro Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="406ca-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="406ca-116">Tato dvojice je ve formátu vytvořeném funkcí Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="406ca-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="406ca-117">Pokud `pbKeyBlob` má hodnotu null, předpokládá se, že `szKeyContainer` kontejner klíčů určený parametrem obsahuje dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="406ca-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="406ca-118">pro Velikost v bajtech `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="406ca-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="406ca-119">mimo Vrácený objekt BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="406ca-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="406ca-120">`ppbPublicKeyBlob` Parametr je přidělen modulem CLR (Common Language Runtime) a vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="406ca-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="406ca-121">Volající musí uvolnit paměť pomocí funkce [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="406ca-121">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="406ca-122">mimo Velikost vráceného objektu BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="406ca-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="406ca-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="406ca-123">Return Value</span></span>  
 <span data-ttu-id="406ca-124">`true`Po úspěšném dokončení; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="406ca-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="406ca-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="406ca-125">Remarks</span></span>  
 <span data-ttu-id="406ca-126">Veřejný klíč je obsažen ve struktuře [PublicKeyBlob –](publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="406ca-126">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="406ca-127">Pokud se `StrongNameGetPublicKey` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="406ca-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="406ca-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="406ca-128">Requirements</span></span>  
 <span data-ttu-id="406ca-129">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="406ca-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="406ca-130">**Hlaviček** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="406ca-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="406ca-131">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="406ca-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="406ca-132">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="406ca-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="406ca-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="406ca-133">See also</span></span>

- [<span data-ttu-id="406ca-134">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="406ca-134">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="406ca-135">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="406ca-135">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="406ca-136">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="406ca-136">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="406ca-137">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="406ca-137">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
