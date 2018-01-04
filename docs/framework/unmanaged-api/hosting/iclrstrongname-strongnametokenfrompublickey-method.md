---
title: "ICLRStrongName::StrongNameTokenFromPublicKey – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameTokenFromPublicKey
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5ee9153cec51f279e08b0ac0838456645cd7ada
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="af31e-102">ICLRStrongName::StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="af31e-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="af31e-103">Získá token, který představuje veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="af31e-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="af31e-104">Zkrácený tvar veřejný klíč je token silným názvem.</span><span class="sxs-lookup"><span data-stu-id="af31e-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af31e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af31e-105">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af31e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="af31e-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="af31e-107">[v] Struktura typu [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) obsahující veřejnou část páru klíčů sloužící ke generování podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="af31e-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="af31e-108">[v] Velikost v bajtech z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="af31e-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="af31e-109">[out] Silný název tokenu odpovídající klíč předaná `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="af31e-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="af31e-110">Modul common language runtime přidělí paměť k vrácení tokenu.</span><span class="sxs-lookup"><span data-stu-id="af31e-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="af31e-111">Volající musí uvolněte tuto paměť pomocí [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="af31e-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="af31e-112">[out] Velikost v bajtech, vrácený silný název tokenu.</span><span class="sxs-lookup"><span data-stu-id="af31e-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af31e-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="af31e-113">Return Value</span></span>  
 <span data-ttu-id="af31e-114">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="af31e-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af31e-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af31e-115">Remarks</span></span>  
 <span data-ttu-id="af31e-116">Silný název tokenu je zkrácený tvar veřejný klíč, který se používá pro uložení místa při ukládání informací o klíči v metadatech.</span><span class="sxs-lookup"><span data-stu-id="af31e-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="af31e-117">Konkrétně silným názvem tokeny se používají v odkazy na sestavení odkazovat na závislého sestavení.</span><span class="sxs-lookup"><span data-stu-id="af31e-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af31e-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af31e-118">Requirements</span></span>  
 <span data-ttu-id="af31e-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af31e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af31e-120">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="af31e-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="af31e-121">**Knihovna:** zahrnuty jako prostředek v mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="af31e-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="af31e-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af31e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af31e-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="af31e-123">See Also</span></span>  
 [<span data-ttu-id="af31e-124">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="af31e-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="af31e-125">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="af31e-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="af31e-126">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af31e-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
