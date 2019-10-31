---
title: ICLRStrongName::StrongNameCompareAssemblies – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
ms.openlocfilehash: fdca03b781e07b709cbc54e673dbaa2a1130fbe3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135151"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="e0532-102">ICLRStrongName::StrongNameCompareAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="e0532-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="e0532-103">Určuje, zda se dvě sestavení liší pouze signaturami silného názvu.</span><span class="sxs-lookup"><span data-stu-id="e0532-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0532-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0532-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0532-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0532-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="e0532-106">pro Cesta k prvnímu sestavení</span><span class="sxs-lookup"><span data-stu-id="e0532-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="e0532-107">pro Cesta k druhému sestavení</span><span class="sxs-lookup"><span data-stu-id="e0532-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="e0532-108">mimo Jedna z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="e0532-108">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="e0532-109">`SN_CMP_DIFFERENT` (0) – určuje, že sestavení obsahují odlišná data.</span><span class="sxs-lookup"><span data-stu-id="e0532-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="e0532-110">`SN_CMP_IDENTICAL` (1) – určuje, že sestavení jsou přesně stejná, včetně jejich podpisů a kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="e0532-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="e0532-111">`SN_CMP_SIGONLY` (2) – určuje, že se sestavení liší pouze pomocí signatury a kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="e0532-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0532-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e0532-112">Return Value</span></span>  
 <span data-ttu-id="e0532-113">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="e0532-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0532-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0532-114">Requirements</span></span>  
 <span data-ttu-id="e0532-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0532-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0532-116">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="e0532-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e0532-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e0532-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0532-118">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0532-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0532-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0532-119">Remarks</span></span>  
 <span data-ttu-id="e0532-120">Podpis silného názvu sestavení se skládá z textového názvu sestavení, verze, jazykové verze a tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="e0532-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0532-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0532-121">See also</span></span>

- [<span data-ttu-id="e0532-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0532-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
