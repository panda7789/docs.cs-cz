---
title: "ICLRStrongName::StrongNameTokenFromAssemblyEx – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b8b3437d8c07cd57a4791995890cab1b06aafc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a><span data-ttu-id="849dc-102">ICLRStrongName::StrongNameTokenFromAssemblyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="849dc-102">ICLRStrongName::StrongNameTokenFromAssemblyEx Method</span></span>
<span data-ttu-id="849dc-103">Vytvoří token silným názvem ze zadaného souboru sestavení a vrátí veřejný klíč, který představuje daný token.</span><span class="sxs-lookup"><span data-stu-id="849dc-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="849dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="849dc-104">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="849dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="849dc-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="849dc-106">[v] Cesta k souboru přenosné spustitelný soubor (PE) pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="849dc-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="849dc-107">[out] Token vrácený silným názvem.</span><span class="sxs-lookup"><span data-stu-id="849dc-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="849dc-108">[out] Velikost v bajtech, silný název tokenu.</span><span class="sxs-lookup"><span data-stu-id="849dc-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="849dc-109">[out] Vrácený veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="849dc-109">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="849dc-110">[out] Velikost v bajtech, veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="849dc-110">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="849dc-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="849dc-111">Return Value</span></span>  
 <span data-ttu-id="849dc-112">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="849dc-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="849dc-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="849dc-113">Remarks</span></span>  
 <span data-ttu-id="849dc-114">Zkrácený tvar veřejný klíč je token silným názvem.</span><span class="sxs-lookup"><span data-stu-id="849dc-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="849dc-115">Token je 64 bitů hodnotu hash, který je vytvořený z veřejný klíč používaný k podepisování sestavení.</span><span class="sxs-lookup"><span data-stu-id="849dc-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="849dc-116">Token je součástí silného názvu pro sestavení a můžete číst z metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="849dc-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="849dc-117">Jakmile načítání klíče a token je vytvořen, by měly volat [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodu pro uvolnění přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="849dc-117">After the key is retrieved and the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="849dc-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="849dc-118">Requirements</span></span>  
 <span data-ttu-id="849dc-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="849dc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="849dc-120">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="849dc-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="849dc-121">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="849dc-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="849dc-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="849dc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="849dc-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="849dc-123">See Also</span></span>  
 [<span data-ttu-id="849dc-124">StrongNameTokenFromAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="849dc-124">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [<span data-ttu-id="849dc-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="849dc-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
