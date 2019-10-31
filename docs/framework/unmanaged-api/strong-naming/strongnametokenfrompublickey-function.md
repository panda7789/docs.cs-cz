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
ms.openlocfilehash: b95c96efeb666f25d04118aa8cb9b0da3a2e7924
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104166"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="ea195-102">StrongNameTokenFromPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="ea195-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="ea195-103">Získá token představující veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="ea195-103">Gets a token representing a public key.</span></span> <span data-ttu-id="ea195-104">Token silného názvu je zkrácenou formou veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="ea195-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="ea195-105">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="ea195-105">This function has been deprecated.</span></span> <span data-ttu-id="ea195-106">Místo toho použijte metodu [ICLRStrongName:: StrongNameTokenFromPublicKey –](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ea195-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea195-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea195-107">Syntax</span></span>  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea195-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea195-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="ea195-109">pro Struktura typu [PublicKeyBlob –](publickeyblob-structure.md) , která obsahuje veřejnou část páru klíčů sloužící k vygenerování podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="ea195-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="ea195-110">pro Velikost `pbPublicKeyBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="ea195-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="ea195-111">mimo Token silného názvu odpovídající klíči předanému `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ea195-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="ea195-112">Modul CLR (Common Language Runtime) přiděluje paměť, ve které má být token vrácen.</span><span class="sxs-lookup"><span data-stu-id="ea195-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="ea195-113">Volající musí uvolnit tuto paměť pomocí funkce [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="ea195-113">The caller must free this memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="ea195-114">mimo Velikost vráceného tokenu silného názvu (v bajtech)</span><span class="sxs-lookup"><span data-stu-id="ea195-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea195-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ea195-115">Return Value</span></span>  
 <span data-ttu-id="ea195-116">`true` po úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="ea195-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea195-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea195-117">Remarks</span></span>  
 <span data-ttu-id="ea195-118">Token silného názvu je zkrácený tvar veřejného klíče, který slouží k ukládání místa při ukládání klíčových informací v metadatech.</span><span class="sxs-lookup"><span data-stu-id="ea195-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="ea195-119">Konkrétně tokeny se silným názvem se používají v odkazech na sestavení pro odkazování na závislé sestavení.</span><span class="sxs-lookup"><span data-stu-id="ea195-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="ea195-120">Pokud se funkce `StrongNameTokenFromPublicKey` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="ea195-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea195-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea195-121">Requirements</span></span>  
 <span data-ttu-id="ea195-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea195-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea195-123">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="ea195-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ea195-124">**Knihovna:** Zahrnuto jako prostředek v knihovně Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ea195-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="ea195-125">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea195-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea195-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea195-126">See also</span></span>

- [<span data-ttu-id="ea195-127">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="ea195-127">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="ea195-128">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="ea195-128">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="ea195-129">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="ea195-129">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
