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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cdc59228ff9913be808d3909ca3fe9e38a7c72f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584307"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="a5b59-102">ICLRStrongName::StrongNameCompareAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="a5b59-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="a5b59-103">Určuje, zda se dvě sestavení liší pouze v jejich podpisy se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="a5b59-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5b59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5b59-104">Syntax</span></span>  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5b59-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5b59-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="a5b59-106">[in] Cesta k sestavení první.</span><span class="sxs-lookup"><span data-stu-id="a5b59-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="a5b59-107">[in] Cesta k druhé sestavení.</span><span class="sxs-lookup"><span data-stu-id="a5b59-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="a5b59-108">[out] Jeden z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="a5b59-108">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="a5b59-109">`SN_CMP_DIFFERENT` (0) – určuje, zda sestavení obsahovat různé datové.</span><span class="sxs-lookup"><span data-stu-id="a5b59-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="a5b59-110">`SN_CMP_IDENTICAL` (1) – určuje, že sestavení jsou stejné, včetně jejich podpisy a kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="a5b59-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="a5b59-111">`SN_CMP_SIGONLY` (2) – určuje, že sestavení liší pouze v podpisu a kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="a5b59-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5b59-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a5b59-112">Return Value</span></span>  
 <span data-ttu-id="a5b59-113">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="a5b59-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5b59-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5b59-114">Requirements</span></span>  
 <span data-ttu-id="a5b59-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5b59-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5b59-116">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a5b59-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a5b59-117">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a5b59-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5b59-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5b59-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5b59-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5b59-119">Remarks</span></span>  
 <span data-ttu-id="a5b59-120">Podpis silného názvu sestavení se skládá z textový název sestavení, verzi, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="a5b59-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b59-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5b59-121">See also</span></span>

- [<span data-ttu-id="a5b59-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5b59-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
