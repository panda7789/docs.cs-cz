---
title: "StrongNameTokenFromPublicKey – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0cb649f43bfea2e11c986aa3fff5a702e2b58c25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="9bd42-102">StrongNameTokenFromPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="9bd42-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="9bd42-103">Získá token představující veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="9bd42-103">Gets a token representing a public key.</span></span> <span data-ttu-id="9bd42-104">Zkrácený tvar veřejný klíč je token silným názvem.</span><span class="sxs-lookup"><span data-stu-id="9bd42-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="9bd42-105">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="9bd42-105">This function has been deprecated.</span></span> <span data-ttu-id="9bd42-106">Použití [iclrstrongname::strongnametokenfrompublickey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="9bd42-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bd42-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bd42-107">Syntax</span></span>  
  
```  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bd42-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="9bd42-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="9bd42-109">[v] Struktura typu [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) obsahující veřejnou část páru klíčů sloužící ke generování podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="9bd42-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="9bd42-110">[v] Velikost v bajtech z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="9bd42-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="9bd42-111">[out] Silný název tokenu odpovídající klíč předaná `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="9bd42-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="9bd42-112">Modul common language runtime přidělí paměť k vrácení tokenu.</span><span class="sxs-lookup"><span data-stu-id="9bd42-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="9bd42-113">Volající musí uvolněte tuto paměť pomocí [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="9bd42-113">The caller must free this memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="9bd42-114">[out] Velikost v bajtech, vrácený silný název tokenu.</span><span class="sxs-lookup"><span data-stu-id="9bd42-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9bd42-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9bd42-115">Return Value</span></span>  
 <span data-ttu-id="9bd42-116">`true`Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="9bd42-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bd42-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9bd42-117">Remarks</span></span>  
 <span data-ttu-id="9bd42-118">Silný název tokenu je zkrácený tvar veřejný klíč používaný ušetřit místo na při ukládání informací o klíči v metadatech.</span><span class="sxs-lookup"><span data-stu-id="9bd42-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="9bd42-119">Konkrétně silným názvem tokeny se používají v odkazy na sestavení odkazovat na závislého sestavení.</span><span class="sxs-lookup"><span data-stu-id="9bd42-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="9bd42-120">Pokud `StrongNameTokenFromPublicKey` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="9bd42-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bd42-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9bd42-121">Requirements</span></span>  
 <span data-ttu-id="9bd42-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bd42-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bd42-123">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="9bd42-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9bd42-124">**Knihovna:** zahrnuty jako prostředek v mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9bd42-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="9bd42-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bd42-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd42-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="9bd42-126">See Also</span></span>  
 [<span data-ttu-id="9bd42-127">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="9bd42-127">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="9bd42-128">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="9bd42-128">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="9bd42-129">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="9bd42-129">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
