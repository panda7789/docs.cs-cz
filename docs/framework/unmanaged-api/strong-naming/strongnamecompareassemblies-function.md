---
title: "StrongNameCompareAssemblies – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameCompareAssemblies
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameCompareAssemblies
helpviewer_keywords: StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ed98b1713427a71c73c30ddd64188f61d51045c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="39e9c-102">StrongNameCompareAssemblies – funkce</span><span class="sxs-lookup"><span data-stu-id="39e9c-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="39e9c-103">Určuje, zda dva sestavení liší pouze jejich podpisy silným názvem.</span><span class="sxs-lookup"><span data-stu-id="39e9c-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="39e9c-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="39e9c-104">This function has been deprecated.</span></span> <span data-ttu-id="39e9c-105">Použití [iclrstrongname::strongnamecompareassemblies –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="39e9c-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39e9c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39e9c-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39e9c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="39e9c-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="39e9c-108">[v] Cesta k první sestavení.</span><span class="sxs-lookup"><span data-stu-id="39e9c-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="39e9c-109">[v] Cesta k sestavení druhý.</span><span class="sxs-lookup"><span data-stu-id="39e9c-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="39e9c-110">[out] Jedna z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="39e9c-110">[out] One of the following values:</span></span>  
  
-   <span data-ttu-id="39e9c-111">`SN_CMP_DIFFERENT`(0) - určuje, že sestavení obsahovat různé data.</span><span class="sxs-lookup"><span data-stu-id="39e9c-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
-   <span data-ttu-id="39e9c-112">`SN_CMP_IDENTICAL`(1) - určuje, že sestavení jsou stejné, včetně jejich podpisy a kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="39e9c-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   <span data-ttu-id="39e9c-113">`SN_CMP_SIGONLY`(2) - určuje, že sestavení liší pouze podpisu a kontrolních součtů.</span><span class="sxs-lookup"><span data-stu-id="39e9c-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39e9c-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="39e9c-114">Return Value</span></span>  
 <span data-ttu-id="39e9c-115">`true`Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="39e9c-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39e9c-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="39e9c-116">Requirements</span></span>  
 <span data-ttu-id="39e9c-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39e9c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39e9c-118">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="39e9c-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="39e9c-119">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="39e9c-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="39e9c-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39e9c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39e9c-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39e9c-121">Remarks</span></span>  
 <span data-ttu-id="39e9c-122">Podpis silného názvu sestavení se skládá z textu název sestavení, verzi, jazykovou verzi a tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="39e9c-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="39e9c-123">Pokud `StrongNameCompareAssemblies` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="39e9c-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39e9c-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="39e9c-124">See Also</span></span>  
 [<span data-ttu-id="39e9c-125">StrongNameCompareAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="39e9c-125">StrongNameCompareAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)  
 [<span data-ttu-id="39e9c-126">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="39e9c-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
