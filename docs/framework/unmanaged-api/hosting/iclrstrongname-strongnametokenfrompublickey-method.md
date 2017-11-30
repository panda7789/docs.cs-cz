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
ms.openlocfilehash: 84f47fcef7c896b197de410234694c211d07c30b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="13a18-102">ICLRStrongName::StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="13a18-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="13a18-103">Získá token, který představuje veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="13a18-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="13a18-104">Zkrácený tvar veřejný klíč je token silným názvem.</span><span class="sxs-lookup"><span data-stu-id="13a18-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13a18-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13a18-105">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13a18-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="13a18-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="13a18-107">[v] Struktura typu [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) obsahující veřejnou část páru klíčů sloužící ke generování podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="13a18-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="13a18-108">[v] Velikost v bajtech z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="13a18-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="13a18-109">[out] Silný název tokenu odpovídající klíč předaná `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="13a18-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="13a18-110">Modul common language runtime přidělí paměť k vrácení tokenu.</span><span class="sxs-lookup"><span data-stu-id="13a18-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="13a18-111">Volající musí uvolněte tuto paměť pomocí [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="13a18-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="13a18-112">[out] Velikost v bajtech, vrácený silný název tokenu.</span><span class="sxs-lookup"><span data-stu-id="13a18-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13a18-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="13a18-113">Return Value</span></span>  
 <span data-ttu-id="13a18-114">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="13a18-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13a18-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13a18-115">Remarks</span></span>  
 <span data-ttu-id="13a18-116">Silný název tokenu je zkrácený tvar veřejný klíč, který se používá pro uložení místa při ukládání informací o klíči v metadatech.</span><span class="sxs-lookup"><span data-stu-id="13a18-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="13a18-117">Konkrétně silným názvem tokeny se používají v odkazy na sestavení odkazovat na závislého sestavení.</span><span class="sxs-lookup"><span data-stu-id="13a18-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13a18-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13a18-118">Requirements</span></span>  
 <span data-ttu-id="13a18-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13a18-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13a18-120">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="13a18-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="13a18-121">**Knihovna:** zahrnuty jako prostředek v mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="13a18-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="13a18-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13a18-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13a18-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="13a18-123">See Also</span></span>  
 [<span data-ttu-id="13a18-124">Strongnamegetpublickey – metoda</span><span class="sxs-lookup"><span data-stu-id="13a18-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="13a18-125">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="13a18-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="13a18-126">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13a18-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
