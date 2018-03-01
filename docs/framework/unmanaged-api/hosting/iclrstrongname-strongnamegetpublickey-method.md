---
title: "ICLRStrongName::StrongNameGetPublicKey – metoda"
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
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9a639644405ce215a373dadf248e9a0e1a5558ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="5ed51-102">ICLRStrongName::StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="5ed51-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="5ed51-103">Získá veřejný klíč z pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="5ed51-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="5ed51-104">Pár klíčů můžete zadat jako název kontejneru klíčů v rámci zprostředkovatele kryptografických služeb (CSP) nebo jako soubor raw bajtů.</span><span class="sxs-lookup"><span data-stu-id="5ed51-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ed51-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ed51-105">Syntax</span></span>  
  
```  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ed51-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ed51-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="5ed51-107">[v] Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="5ed51-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="5ed51-108">Pokud `pbKeyBlob` má hodnotu null, `szKeyContainer` musíte zadat platný kontejner v rámci CSP.</span><span class="sxs-lookup"><span data-stu-id="5ed51-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="5ed51-109">V takovém případě [iclrstrongname::strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) metoda extrahuje veřejný klíč z tohoto páru klíčů ukládat do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5ed51-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="5ed51-110">Pokud `pbKeyBlob` nemá hodnotu null, dvojici klíčů se předpokládá, že mají být obsažena v klíče binární rozsáhlý objekt (binární rozsáhlý OBJEKT).</span><span class="sxs-lookup"><span data-stu-id="5ed51-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="5ed51-111">Klíče musí být Rivest-Shamir-Adleman 1024 bitů (RSA) podpisových klíčů.</span><span class="sxs-lookup"><span data-stu-id="5ed51-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="5ed51-112">Žádné jiné typy klíčů jsou podporovány v tuto chvíli.</span><span class="sxs-lookup"><span data-stu-id="5ed51-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="5ed51-113">[v] Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="5ed51-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="5ed51-114">Tato dvojice je ve formátu vytvořené Win32 `CryptExportKey` funkce.</span><span class="sxs-lookup"><span data-stu-id="5ed51-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="5ed51-115">Pokud `pbKeyBlob` je null, kontejner klíčů určeného `szKeyContainer` se předpokládá, že obsahovat dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="5ed51-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="5ed51-116">[v] Velikost v bajtech z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="5ed51-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="5ed51-117">[out] Vrácený veřejný klíč objektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="5ed51-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="5ed51-118">`ppbPublicKeyBlob` Parametr je přidělena modul common language runtime a vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="5ed51-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="5ed51-119">Volající musí uvolnění paměti pomocí [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="5ed51-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="5ed51-120">[out] Velikost veřejného klíče vráceného objektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="5ed51-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ed51-121">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5ed51-121">Return Value</span></span>  
 <span data-ttu-id="5ed51-122">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="5ed51-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ed51-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ed51-123">Remarks</span></span>  
 <span data-ttu-id="5ed51-124">Veřejný klíč je součástí [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="5ed51-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ed51-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5ed51-125">Requirements</span></span>  
 <span data-ttu-id="5ed51-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ed51-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ed51-127">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5ed51-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5ed51-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5ed51-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ed51-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ed51-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed51-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ed51-130">See Also</span></span>  
 [<span data-ttu-id="5ed51-131">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="5ed51-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="5ed51-132">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="5ed51-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="5ed51-133">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5ed51-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
