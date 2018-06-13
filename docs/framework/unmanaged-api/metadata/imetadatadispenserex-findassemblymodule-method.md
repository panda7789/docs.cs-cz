---
title: IMetaDataDispenserEx::FindAssemblyModule – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssemblyModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 365bea0bdd32fa1b408ba0bfdf100cc443b5d419
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446222"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="d9a75-102">IMetaDataDispenserEx::FindAssemblyModule – metoda</span><span class="sxs-lookup"><span data-stu-id="d9a75-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="d9a75-103">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="d9a75-103">This method is not implemented.</span></span> <span data-ttu-id="d9a75-104">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="d9a75-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9a75-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9a75-105">Syntax</span></span>  
  
```  
HRESULT FindAssemblyModule(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [in]  LPCWSTR  szModuleName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9a75-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9a75-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="d9a75-107">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="d9a75-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="d9a75-108">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="d9a75-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="d9a75-109">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="d9a75-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="d9a75-110">[v] Název modulu.</span><span class="sxs-lookup"><span data-stu-id="d9a75-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="d9a75-111">[v] Sestavení, která se má najít.</span><span class="sxs-lookup"><span data-stu-id="d9a75-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="d9a75-112">[out] Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9a75-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d9a75-113">[v] Velikost v bajtech z `szName`.</span><span class="sxs-lookup"><span data-stu-id="d9a75-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="d9a75-114">[out] Počet znaků, které jsou ve skutečnosti, vrátí se v `szName`.</span><span class="sxs-lookup"><span data-stu-id="d9a75-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9a75-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9a75-115">Requirements</span></span>  
 <span data-ttu-id="d9a75-116">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9a75-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9a75-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d9a75-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9a75-118">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9a75-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d9a75-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9a75-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9a75-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9a75-120">See Also</span></span>  
 [<span data-ttu-id="d9a75-121">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9a75-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="d9a75-122">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9a75-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
