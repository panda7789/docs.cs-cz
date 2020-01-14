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
ms.openlocfilehash: 13c1c505d939c1048eebef3d1d6b2abe493d319e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937422"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="9b943-102">ICLRStrongName::StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="9b943-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="9b943-103">Získá token, který představuje veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="9b943-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="9b943-104">Token silného názvu je zkrácenou formou veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="9b943-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b943-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b943-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b943-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b943-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="9b943-107">pro Struktura typu [PublicKeyBlob –](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) , která obsahuje veřejnou část páru klíčů sloužící k vygenerování podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="9b943-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="9b943-108">pro Velikost `pbPublicKeyBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="9b943-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="9b943-109">mimo Token silného názvu odpovídající klíči předanému `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="9b943-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="9b943-110">Modul CLR (Common Language Runtime) přiděluje paměť, ve které má být token vrácen.</span><span class="sxs-lookup"><span data-stu-id="9b943-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="9b943-111">Volající musí uvolnit tuto paměť pomocí metody [ICLRStrongName:: StrongNameFreeBuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9b943-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="9b943-112">mimo Velikost vráceného tokenu silného názvu (v bajtech)</span><span class="sxs-lookup"><span data-stu-id="9b943-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b943-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9b943-113">Return Value</span></span>  
 <span data-ttu-id="9b943-114">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="9b943-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b943-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b943-115">Remarks</span></span>  
 <span data-ttu-id="9b943-116">Token silného názvu je zkráceným tvarem veřejného klíče, který se používá k ukládání místa při ukládání klíčových informací v metadatech.</span><span class="sxs-lookup"><span data-stu-id="9b943-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="9b943-117">Konkrétně tokeny se silným názvem se používají v odkazech na sestavení pro odkazování na závislé sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b943-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b943-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b943-118">Requirements</span></span>  
 <span data-ttu-id="9b943-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b943-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b943-120">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="9b943-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9b943-121">**Knihovna:** Zahrnuto jako prostředek v knihovně Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9b943-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="9b943-122">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b943-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b943-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b943-123">See also</span></span>

- [<span data-ttu-id="9b943-124">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="9b943-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="9b943-125">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="9b943-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="9b943-126">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b943-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
