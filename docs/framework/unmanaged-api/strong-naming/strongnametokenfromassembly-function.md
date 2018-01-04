---
title: "StrongNameTokenFromAssembly – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameTokenFromAssembly
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameTokenFromAssembly
helpviewer_keywords: StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 29414522eb2586b00ba3158d79155675cb468815
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="cbd25-102">StrongNameTokenFromAssembly – funkce</span><span class="sxs-lookup"><span data-stu-id="cbd25-102">StrongNameTokenFromAssembly Function</span></span>
<span data-ttu-id="cbd25-103">Vytvoří token silným názvem ze zadaného souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="cbd25-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="cbd25-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="cbd25-104">This function has been deprecated.</span></span> <span data-ttu-id="cbd25-105">Použití [iclrstrongname::strongnametokenfromassembly –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="cbd25-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbd25-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbd25-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cbd25-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="cbd25-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="cbd25-108">[v] Cesta k souboru přenosné spustitelný soubor (PE) pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="cbd25-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="cbd25-109">[out] Token vrácený silným názvem.</span><span class="sxs-lookup"><span data-stu-id="cbd25-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="cbd25-110">[out] Velikost v bajtech, silný název tokenu.</span><span class="sxs-lookup"><span data-stu-id="cbd25-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbd25-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cbd25-111">Return Value</span></span>  
 <span data-ttu-id="cbd25-112">`true`Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="cbd25-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbd25-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cbd25-113">Remarks</span></span>  
 <span data-ttu-id="cbd25-114">Zkrácený tvar veřejný klíč je token silným názvem.</span><span class="sxs-lookup"><span data-stu-id="cbd25-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="cbd25-115">Token je 64 bitů hodnotu hash, který je vytvořený z veřejný klíč používaný k podepisování sestavení.</span><span class="sxs-lookup"><span data-stu-id="cbd25-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="cbd25-116">Token je součástí silného názvu pro sestavení a můžete číst z metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="cbd25-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="cbd25-117">Po vytvoření tokenu by měly volat [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce k uvolnění přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="cbd25-117">After the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="cbd25-118">Pokud `StrongNameTokenFromAssembly` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="cbd25-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbd25-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cbd25-119">Requirements</span></span>  
 <span data-ttu-id="cbd25-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbd25-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbd25-121">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="cbd25-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cbd25-122">**Knihovna:** zahrnuty jako prostředek v mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="cbd25-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="cbd25-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbd25-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbd25-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="cbd25-124">See Also</span></span>  
 [<span data-ttu-id="cbd25-125">StrongNameTokenFromAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="cbd25-125">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [<span data-ttu-id="cbd25-126">StrongNameTokenFromAssemblyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="cbd25-126">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [<span data-ttu-id="cbd25-127">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cbd25-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
