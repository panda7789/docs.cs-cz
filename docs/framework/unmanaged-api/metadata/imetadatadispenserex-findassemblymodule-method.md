---
title: "IMetaDataDispenserEx::FindAssemblyModule – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.FindAssemblyModule
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3911eeb5f6ff8122c71f0c1df973c4636ad8b665
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="004ae-102">IMetaDataDispenserEx::FindAssemblyModule – metoda</span><span class="sxs-lookup"><span data-stu-id="004ae-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="004ae-103">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="004ae-103">This method is not implemented.</span></span> <span data-ttu-id="004ae-104">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="004ae-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="004ae-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="004ae-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="004ae-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="004ae-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="004ae-107">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="004ae-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="004ae-108">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="004ae-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="004ae-109">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="004ae-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="004ae-110">[v] Název modulu.</span><span class="sxs-lookup"><span data-stu-id="004ae-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="004ae-111">[v] Sestavení, která se má najít.</span><span class="sxs-lookup"><span data-stu-id="004ae-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="004ae-112">[out] Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="004ae-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="004ae-113">[v] Velikost v bajtech z `szName`.</span><span class="sxs-lookup"><span data-stu-id="004ae-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="004ae-114">[out] Počet znaků, které jsou ve skutečnosti, vrátí se v `szName`.</span><span class="sxs-lookup"><span data-stu-id="004ae-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="004ae-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="004ae-115">Requirements</span></span>  
 <span data-ttu-id="004ae-116">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="004ae-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="004ae-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="004ae-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="004ae-118">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="004ae-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="004ae-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="004ae-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="004ae-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="004ae-120">See Also</span></span>  
 [<span data-ttu-id="004ae-121">Imetadatadispenserex – rozhraní</span><span class="sxs-lookup"><span data-stu-id="004ae-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="004ae-122">Imetadatadispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="004ae-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
