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
ms.openlocfilehash: ca428d680df1710d8e74441d9945d4c3545b0482
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121149"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="313c6-102">StrongNameSignatureVerificationEx – funkce</span><span class="sxs-lookup"><span data-stu-id="313c6-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="313c6-103">Načte hodnotu, která označuje, zda manifest sestavení v zadané cestě obsahuje podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="313c6-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="313c6-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="313c6-104">This function has been deprecated.</span></span> <span data-ttu-id="313c6-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameSignatureVerificationEx –](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="313c6-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="313c6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="313c6-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="313c6-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="313c6-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="313c6-108">pro Cesta k přenositelnému spustitelnému souboru (. exe nebo. dll) pro sestavení, které má být ověřeno.</span><span class="sxs-lookup"><span data-stu-id="313c6-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="313c6-109">[in] `true` provádět ověřování, i když je nutné přepsat nastavení registru. v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="313c6-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="313c6-110">[out] `true`, jestli se podpis silného názvu ověřil; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="313c6-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="313c6-111">`pfWasVerified` je také nastaveno na `false`, pokud bylo ověření úspěšné z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="313c6-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="313c6-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="313c6-112">Return Value</span></span>  
 <span data-ttu-id="313c6-113">`true`, zda bylo ověření úspěšné; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="313c6-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="313c6-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="313c6-114">Remarks</span></span>  
 <span data-ttu-id="313c6-115">`StrongNameSignatureVerificationEx` poskytuje možnost podobnou funkci [StrongNameSignatureVerification –](strongnamesignatureverification-function.md) .</span><span class="sxs-lookup"><span data-stu-id="313c6-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="313c6-116">Druhý vstupní parametr a výstupní parametr pro `StrongNameSignatureVerificationEx` jsou však typu `BOOLEAN` namísto `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="313c6-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="313c6-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="313c6-117">Requirements</span></span>  
 <span data-ttu-id="313c6-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="313c6-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="313c6-119">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="313c6-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="313c6-120">**Knihovna:** Zahrnuto jako prostředek v knihovně Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="313c6-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="313c6-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="313c6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="313c6-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="313c6-122">See also</span></span>

- [<span data-ttu-id="313c6-123">StrongNameSignatureVerificationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="313c6-123">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="313c6-124">StrongNameSignatureVerification – metoda</span><span class="sxs-lookup"><span data-stu-id="313c6-124">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="313c6-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="313c6-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
