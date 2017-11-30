---
title: "ICLRStrongName::StrongNameTokenFromAssembly – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameTokenFromAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b236fe3b041277401c2983cf229981253c01328
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="08c6b-102">ICLRStrongName::StrongNameTokenFromAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="08c6b-102">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>
<span data-ttu-id="08c6b-103">Vytvoří token silným názvem ze zadaného souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="08c6b-103">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08c6b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08c6b-104">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08c6b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08c6b-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="08c6b-106">[v] Cesta k souboru přenosné spustitelný soubor (PE) pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="08c6b-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="08c6b-107">[out] Token vrácený silným názvem.</span><span class="sxs-lookup"><span data-stu-id="08c6b-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="08c6b-108">[out] Velikost v bajtech, silný název tokenu.</span><span class="sxs-lookup"><span data-stu-id="08c6b-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08c6b-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="08c6b-109">Return Value</span></span>  
 <span data-ttu-id="08c6b-110">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="08c6b-110">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08c6b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="08c6b-111">Remarks</span></span>  
 <span data-ttu-id="08c6b-112">Zkrácený tvar veřejný klíč je token silným názvem.</span><span class="sxs-lookup"><span data-stu-id="08c6b-112">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="08c6b-113">Token je 64 bitů hodnotu hash, který je vytvořený z veřejný klíč používaný k podepisování sestavení.</span><span class="sxs-lookup"><span data-stu-id="08c6b-113">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="08c6b-114">Token je součástí silného názvu pro sestavení a můžete číst z metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="08c6b-114">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="08c6b-115">Po vytvoření tokenu by měly volat [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodu pro uvolnění přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="08c6b-115">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08c6b-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08c6b-116">Requirements</span></span>  
 <span data-ttu-id="08c6b-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08c6b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08c6b-118">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="08c6b-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="08c6b-119">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="08c6b-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08c6b-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08c6b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c6b-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="08c6b-121">See Also</span></span>  
 [<span data-ttu-id="08c6b-122">Strongnametokenfromassemblyex – metoda</span><span class="sxs-lookup"><span data-stu-id="08c6b-122">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [<span data-ttu-id="08c6b-123">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="08c6b-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
