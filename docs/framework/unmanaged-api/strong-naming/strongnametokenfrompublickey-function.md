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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b095d999f1e7e37c068c800e66f56c293422127
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490395"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="2d0c4-102">StrongNameTokenFromPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="2d0c4-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="2d0c4-103">Získá token představující veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="2d0c4-103">Gets a token representing a public key.</span></span> <span data-ttu-id="2d0c4-104">Zkráceným tvarem veřejný klíč je token silného názvu.</span><span class="sxs-lookup"><span data-stu-id="2d0c4-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="2d0c4-105">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="2d0c4-105">This function has been deprecated.</span></span> <span data-ttu-id="2d0c4-106">Použití [iclrstrongname::strongnametokenfrompublickey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="2d0c4-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d0c4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d0c4-107">Syntax</span></span>  
  
```  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d0c4-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d0c4-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="2d0c4-109">[in] Strukturu typu [publickeyblob –](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) obsahující veřejnou část páru klíčů podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="2d0c4-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="2d0c4-110">[in] Velikost v bajtech, z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="2d0c4-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="2d0c4-111">[out] Silný název tokenu odpovídající klíči předaný `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="2d0c4-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="2d0c4-112">Modul common language runtime přiděluje paměť ke vrácení tokenu.</span><span class="sxs-lookup"><span data-stu-id="2d0c4-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="2d0c4-113">Volající musí uvolnit tato paměť pomocí [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="2d0c4-113">The caller must free this memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="2d0c4-114">[out] Velikost v bajtech, token vrácený silného názvu.</span><span class="sxs-lookup"><span data-stu-id="2d0c4-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d0c4-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2d0c4-115">Return Value</span></span>  
 <span data-ttu-id="2d0c4-116">`true` Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="2d0c4-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d0c4-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d0c4-117">Remarks</span></span>  
 <span data-ttu-id="2d0c4-118">Token silného názvu je zkrácený tvar veřejný klíč používaný pro úsporu místa při ukládání informací o klíči v metadatech.</span><span class="sxs-lookup"><span data-stu-id="2d0c4-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="2d0c4-119">Konkrétně tokeny silným názvem se používají v odkazy na sestavení odkázat na závislého sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d0c4-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="2d0c4-120">Pokud `StrongNameTokenFromPublicKey` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="2d0c4-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d0c4-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d0c4-121">Requirements</span></span>  
 <span data-ttu-id="2d0c4-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d0c4-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d0c4-123">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="2d0c4-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2d0c4-124">**Knihovna:** Zahrnuté jako prostředek v mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2d0c4-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="2d0c4-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d0c4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d0c4-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d0c4-126">See also</span></span>
- [<span data-ttu-id="2d0c4-127">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="2d0c4-127">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="2d0c4-128">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="2d0c4-128">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="2d0c4-129">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="2d0c4-129">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
