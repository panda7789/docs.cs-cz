---
title: StrongNameTokenFromAssembly – funkce
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71058a1ff82335b2a341904805d06738e662c296
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798871"
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="52e1d-102">StrongNameTokenFromAssembly – funkce</span><span class="sxs-lookup"><span data-stu-id="52e1d-102">StrongNameTokenFromAssembly Function</span></span>
<span data-ttu-id="52e1d-103">Vytvoří ze zadaného souboru sestavení token se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="52e1d-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="52e1d-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="52e1d-104">This function has been deprecated.</span></span> <span data-ttu-id="52e1d-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameTokenFromAssembly –](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="52e1d-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52e1d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52e1d-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52e1d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="52e1d-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="52e1d-108">pro Cesta k přenosnému spustitelnému souboru (PE) pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="52e1d-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="52e1d-109">mimo Vrácený token silného názvu.</span><span class="sxs-lookup"><span data-stu-id="52e1d-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="52e1d-110">mimo Velikost tokenu silného názvu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="52e1d-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52e1d-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="52e1d-111">Return Value</span></span>  
 <span data-ttu-id="52e1d-112">`true`Po úspěšném dokončení; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="52e1d-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52e1d-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52e1d-113">Remarks</span></span>  
 <span data-ttu-id="52e1d-114">Token silného názvu je zkrácenou formou veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="52e1d-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="52e1d-115">Token je 64 hodnota hash, která je vytvořena z veřejného klíče použitého k podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="52e1d-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="52e1d-116">Token je součástí silného názvu sestavení a lze ho číst z metadat sestavení.</span><span class="sxs-lookup"><span data-stu-id="52e1d-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="52e1d-117">Po vytvoření tokenu byste měli zavolat funkci [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) a uvolnit tak přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="52e1d-117">After the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="52e1d-118">Pokud se `StrongNameTokenFromAssembly` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="52e1d-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52e1d-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52e1d-119">Requirements</span></span>  
 <span data-ttu-id="52e1d-120">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52e1d-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52e1d-121">**Hlaviček** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="52e1d-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="52e1d-122">**Knihovna** Zahrnuto jako prostředek v knihovně Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="52e1d-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="52e1d-123">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52e1d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e1d-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52e1d-124">See also</span></span>

- [<span data-ttu-id="52e1d-125">StrongNameTokenFromAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="52e1d-125">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="52e1d-126">StrongNameTokenFromAssemblyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="52e1d-126">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="52e1d-127">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52e1d-127">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
