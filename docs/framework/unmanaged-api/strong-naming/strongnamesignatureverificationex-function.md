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
ms.openlocfilehash: 08247c1ec5b868055e4836b3c0fb520a536374e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798913"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="644e0-102">StrongNameSignatureVerificationEx – funkce</span><span class="sxs-lookup"><span data-stu-id="644e0-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="644e0-103">Načte hodnotu, která označuje, zda manifest sestavení v zadané cestě obsahuje podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="644e0-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="644e0-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="644e0-104">This function has been deprecated.</span></span> <span data-ttu-id="644e0-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameSignatureVerificationEx –](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="644e0-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="644e0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="644e0-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="644e0-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="644e0-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="644e0-108">pro Cesta k přenositelnému spustitelnému souboru (. exe nebo. dll) pro sestavení, které má být ověřeno.</span><span class="sxs-lookup"><span data-stu-id="644e0-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="644e0-109">pro provést ověření, i když je nutné přepsat nastavení registru, `false`jinak. `true`</span><span class="sxs-lookup"><span data-stu-id="644e0-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="644e0-110">mimo Pokud byl podpis silného názvu ověřen; `false`v opačném případě. `true`</span><span class="sxs-lookup"><span data-stu-id="644e0-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="644e0-111">`pfWasVerified`je také nastaveno na `false` , pokud bylo ověření úspěšné z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="644e0-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="644e0-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="644e0-112">Return Value</span></span>  
 <span data-ttu-id="644e0-113">`true`Pokud bylo ověření úspěšné; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="644e0-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="644e0-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="644e0-114">Remarks</span></span>  
 <span data-ttu-id="644e0-115">`StrongNameSignatureVerificationEx`poskytuje funkci podobnou funkci [StrongNameSignatureVerification –](strongnamesignatureverification-function.md) .</span><span class="sxs-lookup"><span data-stu-id="644e0-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="644e0-116">Druhý vstupní parametr a výstupní parametr pro `StrongNameSignatureVerificationEx` jsou však typu `BOOLEAN` místo `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="644e0-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="644e0-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="644e0-117">Requirements</span></span>  
 <span data-ttu-id="644e0-118">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="644e0-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="644e0-119">**Hlaviček** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="644e0-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="644e0-120">**Knihovna** Zahrnuto jako prostředek v knihovně Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="644e0-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="644e0-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="644e0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="644e0-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="644e0-122">See also</span></span>

- [<span data-ttu-id="644e0-123">StrongNameSignatureVerificationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="644e0-123">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="644e0-124">StrongNameSignatureVerification – metoda</span><span class="sxs-lookup"><span data-stu-id="644e0-124">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="644e0-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="644e0-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
