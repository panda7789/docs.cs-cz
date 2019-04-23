---
title: StrongNameSignatureVerificationEx – funkce
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 049b7b11473a05d74dc311ca6ee79947039b0dd1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112902"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="e035e-102">StrongNameSignatureVerificationEx – funkce</span><span class="sxs-lookup"><span data-stu-id="e035e-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="e035e-103">Získá hodnotu označující, zda obsahuje manifest sestavení v zadané cestě podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="e035e-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="e035e-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="e035e-104">This function has been deprecated.</span></span> <span data-ttu-id="e035e-105">Použití [iclrstrongname::strongnamesignatureverificationex –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="e035e-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e035e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e035e-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e035e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e035e-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="e035e-108">[in] Cesta k přenositelný spustitelný soubor (.exe nebo .dll) soubor pro sestavení, který se má ověřit.</span><span class="sxs-lookup"><span data-stu-id="e035e-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="e035e-109">[in] `true` provádět ověřování, i když je potřeba přepsat nastavení registru; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="e035e-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="e035e-110">[out] `true` Pokud byl podpis silného názvu ověřené; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="e035e-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="e035e-111">`pfWasVerified` je také nastavena na `false` Pokud bude ověření úspěšné z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="e035e-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e035e-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e035e-112">Return Value</span></span>  
 <span data-ttu-id="e035e-113">`true` Pokud bude ověření úspěšné; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="e035e-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e035e-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e035e-114">Remarks</span></span>  
 <span data-ttu-id="e035e-115">`StrongNameSignatureVerificationEx` poskytuje podobné funkci [strongnamesignatureverification –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="e035e-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="e035e-116">Ale druhé vstupní parametr a výstupní parametr pro `StrongNameSignatureVerificationEx` jsou typu `BOOLEAN` místo `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="e035e-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e035e-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e035e-117">Requirements</span></span>  
 <span data-ttu-id="e035e-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e035e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e035e-119">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e035e-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e035e-120">**Knihovna:** Zahrnuté jako prostředek v mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e035e-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="e035e-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e035e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e035e-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e035e-122">See also</span></span>

- [<span data-ttu-id="e035e-123">StrongNameSignatureVerificationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="e035e-123">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="e035e-124">StrongNameSignatureVerification – metoda</span><span class="sxs-lookup"><span data-stu-id="e035e-124">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="e035e-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e035e-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
