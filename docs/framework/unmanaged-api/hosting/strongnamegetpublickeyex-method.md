---
title: "StrongNameGetPublicKeyEx – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName2.StrongNameGetPublicKeyEx
api_location: mscoree.dll
api_type: COM
f1_keywords: StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f39c5c948d43fd0e9387c1cc0319a46d25ec86ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="ad124-102">StrongNameGetPublicKeyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="ad124-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="ad124-103">Získá veřejný klíč z páru veřejného a privátního klíče RSA a určuje algoritmus hash a algoritmus podpisu.</span><span class="sxs-lookup"><span data-stu-id="ad124-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad124-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad124-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad124-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad124-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="ad124-106">[v] Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="ad124-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="ad124-107">Pokud `pbKeyBlob` má hodnotu null, `szKeyContainer` musíte zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="ad124-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="ad124-108">V takovém případě `StrongNameGetPublicKeyEx` metoda extrahuje veřejný klíč z tohoto páru klíčů ukládat do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ad124-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="ad124-109">Pokud `pbKeyBlob` nemá hodnotu null, dvojici klíčů se předpokládá, že mají být obsažena v klíče binární rozsáhlý objekt (binární rozsáhlý OBJEKT).</span><span class="sxs-lookup"><span data-stu-id="ad124-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="ad124-110">Klíče musí být Rivest-Shamir-Adleman 1024 bitů (RSA) podpisových klíčů.</span><span class="sxs-lookup"><span data-stu-id="ad124-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="ad124-111">Žádné jiné typy klíčů jsou podporovány v tuto chvíli.</span><span class="sxs-lookup"><span data-stu-id="ad124-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ad124-112">[v] Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="ad124-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="ad124-113">Tato dvojice je ve formátu vytvořené Win32 `CryptExportKey` funkce.</span><span class="sxs-lookup"><span data-stu-id="ad124-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="ad124-114">Pokud `pbKeyBlob` je null, kontejner klíčů určeného `szKeyContainer` se předpokládá, že obsahovat dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="ad124-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ad124-115">[v] Velikost v bajtech z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ad124-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="ad124-116">[out] Vrácený veřejný klíč objektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="ad124-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="ad124-117">`ppbPublicKeyBlob` Parametr je přidělena modul common language runtime a vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="ad124-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="ad124-118">Volající musí uvolnění paměti pomocí [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="ad124-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="ad124-119">[out] Velikost veřejného klíče vráceného objektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="ad124-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="ad124-120">[v] Algoritmus hash sestavení.</span><span class="sxs-lookup"><span data-stu-id="ad124-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="ad124-121">Najdete v části poznámky seznam možné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ad124-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="ad124-122">[v] Vyhrazeno pro budoucí použití; Výchozí hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="ad124-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad124-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ad124-123">Return Value</span></span>  
 <span data-ttu-id="ad124-124">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="ad124-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad124-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad124-125">Remarks</span></span>  
 <span data-ttu-id="ad124-126">Veřejný klíč je součástí [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="ad124-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad124-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad124-127">Remarks</span></span>  
 <span data-ttu-id="ad124-128">V následující tabulce jsou uvedeny sadu přijaté hodnoty pro `uHashAlgId` parametr.</span><span class="sxs-lookup"><span data-stu-id="ad124-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="ad124-129">Název</span><span class="sxs-lookup"><span data-stu-id="ad124-129">Name</span></span>|<span data-ttu-id="ad124-130">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ad124-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="ad124-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="ad124-131">None</span></span>|<span data-ttu-id="ad124-132">0</span><span class="sxs-lookup"><span data-stu-id="ad124-132">0</span></span>|  
|<span data-ttu-id="ad124-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="ad124-133">SHA-1</span></span>|<span data-ttu-id="ad124-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="ad124-134">0x8004</span></span>|  
|<span data-ttu-id="ad124-135">ALGORITMUS SHA-256</span><span class="sxs-lookup"><span data-stu-id="ad124-135">SHA-256</span></span>|<span data-ttu-id="ad124-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="ad124-136">0x800c</span></span>|  
|<span data-ttu-id="ad124-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="ad124-137">SHA-384</span></span>|<span data-ttu-id="ad124-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="ad124-138">0x800d</span></span>|  
|<span data-ttu-id="ad124-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="ad124-139">SHA-512</span></span>|<span data-ttu-id="ad124-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="ad124-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ad124-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad124-141">Requirements</span></span>  
 <span data-ttu-id="ad124-142">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad124-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad124-143">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ad124-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ad124-144">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad124-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad124-145">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad124-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad124-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad124-146">See Also</span></span>  
 [<span data-ttu-id="ad124-147">Strongnametokenfrompublickey – metoda</span><span class="sxs-lookup"><span data-stu-id="ad124-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="ad124-148">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="ad124-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="ad124-149">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad124-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [<span data-ttu-id="ad124-150">Strongnamegetpublickey – metoda</span><span class="sxs-lookup"><span data-stu-id="ad124-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
