---
title: "StrongNameSignatureVerificationEx – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureVerificationEx
helpviewer_keywords: StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0aebb53c6718a6812cbe6a6888f389c7b1a52dda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="e1b2f-102">StrongNameSignatureVerificationEx – funkce</span><span class="sxs-lookup"><span data-stu-id="e1b2f-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="e1b2f-103">Získá hodnotu označující, zda manifest sestavení v zadaná cesta obsahuje podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="e1b2f-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="e1b2f-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="e1b2f-104">This function has been deprecated.</span></span> <span data-ttu-id="e1b2f-105">Použití [iclrstrongname::strongnamesignatureverificationex –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="e1b2f-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1b2f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1b2f-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1b2f-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1b2f-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="e1b2f-108">[v] Cesta k přenosné spustitelný soubor (.exe nebo .dll) souboru pro sestavení, které má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="e1b2f-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="e1b2f-109">[v] `true` provést ověření, i když je nezbytné pro přepsání nastavení registru; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="e1b2f-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="e1b2f-110">[out] `true` Pokud podpis silného názvu byl ověřený, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="e1b2f-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="e1b2f-111">`pfWasVerified`je také nastavena na `false` Pokud ověření bylo úspěšné z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="e1b2f-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1b2f-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e1b2f-112">Return Value</span></span>  
 <span data-ttu-id="e1b2f-113">`true`Pokud ověření byla úspěšná. v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="e1b2f-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1b2f-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1b2f-114">Remarks</span></span>  
 <span data-ttu-id="e1b2f-115">`StrongNameSignatureVerificationEx`poskytuje podobné funkce [strongnamesignatureverification –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="e1b2f-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="e1b2f-116">Ale druhý vstupní parametr a výstupní parametr pro `StrongNameSignatureVerificationEx` typu `BOOLEAN` místo `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="e1b2f-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1b2f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1b2f-117">Requirements</span></span>  
 <span data-ttu-id="e1b2f-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1b2f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1b2f-119">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e1b2f-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e1b2f-120">**Knihovna:** zahrnuty jako prostředek v mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e1b2f-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="e1b2f-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1b2f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1b2f-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1b2f-122">See Also</span></span>  
 [<span data-ttu-id="e1b2f-123">Strongnamesignatureverificationex – metoda</span><span class="sxs-lookup"><span data-stu-id="e1b2f-123">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="e1b2f-124">Strongnamesignatureverification – metoda</span><span class="sxs-lookup"><span data-stu-id="e1b2f-124">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="e1b2f-125">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1b2f-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
