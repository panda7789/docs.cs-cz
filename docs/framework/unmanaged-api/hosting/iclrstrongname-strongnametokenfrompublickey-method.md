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
ms.openlocfilehash: 2e595904eacebdd42467fc4e0550db77578c075c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169725"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="eac67-102">ICLRStrongName::StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="eac67-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="eac67-103">Získá token, který představuje veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="eac67-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="eac67-104">Zkráceným tvarem veřejný klíč je token silného názvu.</span><span class="sxs-lookup"><span data-stu-id="eac67-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eac67-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eac67-105">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eac67-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="eac67-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="eac67-107">[in] Strukturu typu [publickeyblob –](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) obsahující veřejnou část páru klíčů podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="eac67-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="eac67-108">[in] Velikost v bajtech, z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="eac67-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="eac67-109">[out] Silný název tokenu odpovídající klíči předaný `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="eac67-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="eac67-110">Modul common language runtime přiděluje paměť ke vrácení tokenu.</span><span class="sxs-lookup"><span data-stu-id="eac67-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="eac67-111">Volající musí uvolnit tato paměť pomocí [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="eac67-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="eac67-112">[out] Velikost v bajtech, token vrácený silného názvu.</span><span class="sxs-lookup"><span data-stu-id="eac67-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eac67-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eac67-113">Return Value</span></span>  
 `S_OK` <span data-ttu-id="eac67-114">Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="eac67-114">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eac67-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eac67-115">Remarks</span></span>  
 <span data-ttu-id="eac67-116">Token silného názvu je zkrácený tvar veřejný klíč, který se používá pro úsporu místa při ukládání informací o klíči v metadatech.</span><span class="sxs-lookup"><span data-stu-id="eac67-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="eac67-117">Konkrétně tokeny silným názvem se používají v odkazy na sestavení odkázat na závislého sestavení.</span><span class="sxs-lookup"><span data-stu-id="eac67-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eac67-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eac67-118">Requirements</span></span>  
 <span data-ttu-id="eac67-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eac67-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eac67-120">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="eac67-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="eac67-121">**Knihovna:** Zahrnuté jako prostředek v mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="eac67-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 **<span data-ttu-id="eac67-122">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="eac67-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eac67-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eac67-123">See also</span></span>

- [<span data-ttu-id="eac67-124">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="eac67-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="eac67-125">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="eac67-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="eac67-126">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eac67-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
