---
title: IMetaDataDispenserEx::FindAssembly – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d204ec29304fe0c4596950cd17c48d0c1d2ac616
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152617"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="9b848-102">IMetaDataDispenserEx::FindAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="9b848-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="9b848-103">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="9b848-103">This method is not implemented.</span></span> <span data-ttu-id="9b848-104">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="9b848-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b848-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b848-105">Syntax</span></span>  
  
```  
HRESULT FindAssembly(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b848-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b848-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="9b848-107">[in] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="9b848-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="9b848-108">[in] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="9b848-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="9b848-109">[in] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="9b848-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="9b848-110">[in] Sestavení, která se má najít.</span><span class="sxs-lookup"><span data-stu-id="9b848-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="9b848-111">[out] Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b848-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="9b848-112">[in] Velikost v bajtech, z `szName`.</span><span class="sxs-lookup"><span data-stu-id="9b848-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="9b848-113">[out] Počet znaků ve skutečnosti vrátí v `szName`.</span><span class="sxs-lookup"><span data-stu-id="9b848-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b848-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b848-114">Requirements</span></span>  
 <span data-ttu-id="9b848-115">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b848-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b848-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9b848-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b848-117">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9b848-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="9b848-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9b848-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9b848-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b848-119">See also</span></span>

- [<span data-ttu-id="9b848-120">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b848-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="9b848-121">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b848-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
