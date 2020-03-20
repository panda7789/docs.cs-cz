---
title: StrongNameTokenFromPublicKey – funkce
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
ms.openlocfilehash: 20be3114908ef78966eead05ae8ba6333a491404
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175054"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="36b4e-102">StrongNameTokenFromPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="36b4e-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="36b4e-103">Získá token představující veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="36b4e-103">Gets a token representing a public key.</span></span> <span data-ttu-id="36b4e-104">Token silného názvu je zkrácená forma veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="36b4e-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="36b4e-105">Tato funkce byla zastaralá.</span><span class="sxs-lookup"><span data-stu-id="36b4e-105">This function has been deprecated.</span></span> <span data-ttu-id="36b4e-106">Místo toho použijte metodu [ICLRStrongName::StrongNameTokenFromPublicKey.](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)</span><span class="sxs-lookup"><span data-stu-id="36b4e-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36b4e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36b4e-107">Syntax</span></span>  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36b4e-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="36b4e-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="36b4e-109">[v] Struktura typu [PublicKeyBlob,](publickeyblob-structure.md) který obsahuje veřejnou část dvojice klíčů slouží ke generování podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="36b4e-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="36b4e-110">[v] Velikost v bajtů `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="36b4e-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="36b4e-111">[out] Token silného názvu odpovídající klíči předaný v `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="36b4e-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="36b4e-112">Běžný jazyk runtime přiděluje paměť, ve kterém chcete vrátit token.</span><span class="sxs-lookup"><span data-stu-id="36b4e-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="36b4e-113">Volající musí uvolnit tuto paměť pomocí funkce [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)</span><span class="sxs-lookup"><span data-stu-id="36b4e-113">The caller must free this memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="36b4e-114">[out] Velikost tokenu vráceného silného názvu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="36b4e-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36b4e-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="36b4e-115">Return Value</span></span>  
 <span data-ttu-id="36b4e-116">`true`po úspěšném dokončení; v `false`opačném případě .</span><span class="sxs-lookup"><span data-stu-id="36b4e-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36b4e-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36b4e-117">Remarks</span></span>  
 <span data-ttu-id="36b4e-118">Token silného názvu je zkrácená forma veřejného klíče, který slouží k úspoře místa při ukládání informací o klíči v metadatech.</span><span class="sxs-lookup"><span data-stu-id="36b4e-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="36b4e-119">Konkrétně tokeny silného názvu se používají v odkazech na sestavení odkazovat na závislé sestavení.</span><span class="sxs-lookup"><span data-stu-id="36b4e-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="36b4e-120">Pokud `StrongNameTokenFromPublicKey` se funkce nedokončí úspěšně, zavolejte funkci [StrongNameErrorInfo,](strongnameerrorinfo-function.md) abyste načetli poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="36b4e-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36b4e-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36b4e-121">Requirements</span></span>  
 <span data-ttu-id="36b4e-122">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36b4e-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36b4e-123">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="36b4e-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="36b4e-124">**Knihovna:** Zahrnuto jako zdroj v souboru mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="36b4e-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="36b4e-125">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36b4e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36b4e-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="36b4e-126">See also</span></span>

- [<span data-ttu-id="36b4e-127">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="36b4e-127">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="36b4e-128">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="36b4e-128">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="36b4e-129">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="36b4e-129">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
