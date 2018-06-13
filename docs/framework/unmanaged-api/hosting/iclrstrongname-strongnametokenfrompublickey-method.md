---
title: ICLRStrongName::StrongNameTokenFromPublicKey – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 587e2086a03e9c9ba57ae3b68de841f12543404e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435605"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="5301c-102">ICLRStrongName::StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="5301c-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="5301c-103">Získá token, který představuje veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="5301c-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="5301c-104">Zkrácený tvar veřejný klíč je token silným názvem.</span><span class="sxs-lookup"><span data-stu-id="5301c-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5301c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5301c-105">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5301c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5301c-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="5301c-107">[v] Struktura typu [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) obsahující veřejnou část páru klíčů sloužící ke generování podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="5301c-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="5301c-108">[v] Velikost v bajtech z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="5301c-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="5301c-109">[out] Silný název tokenu odpovídající klíč předaná `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="5301c-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="5301c-110">Modul common language runtime přidělí paměť k vrácení tokenu.</span><span class="sxs-lookup"><span data-stu-id="5301c-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="5301c-111">Volající musí uvolněte tuto paměť pomocí [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="5301c-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="5301c-112">[out] Velikost v bajtech, vrácený silný název tokenu.</span><span class="sxs-lookup"><span data-stu-id="5301c-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5301c-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5301c-113">Return Value</span></span>  
 <span data-ttu-id="5301c-114">`S_OK` Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="5301c-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5301c-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5301c-115">Remarks</span></span>  
 <span data-ttu-id="5301c-116">Silný název tokenu je zkrácený tvar veřejný klíč, který se používá pro uložení místa při ukládání informací o klíči v metadatech.</span><span class="sxs-lookup"><span data-stu-id="5301c-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="5301c-117">Konkrétně silným názvem tokeny se používají v odkazy na sestavení odkazovat na závislého sestavení.</span><span class="sxs-lookup"><span data-stu-id="5301c-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5301c-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5301c-118">Requirements</span></span>  
 <span data-ttu-id="5301c-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5301c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5301c-120">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5301c-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5301c-121">**Knihovna:** zahrnuty jako prostředek v mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5301c-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="5301c-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5301c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5301c-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="5301c-123">See Also</span></span>  
 [<span data-ttu-id="5301c-124">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="5301c-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="5301c-125">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="5301c-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="5301c-126">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5301c-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
