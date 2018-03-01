---
title: "IMetaDataDispenserEx::FindAssembly – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f125008e4ae5b7f2abbe6d467b486b962700d42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="d96f7-102">IMetaDataDispenserEx::FindAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="d96f7-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="d96f7-103">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="d96f7-103">This method is not implemented.</span></span> <span data-ttu-id="d96f7-104">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="d96f7-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d96f7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d96f7-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="d96f7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d96f7-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="d96f7-107">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="d96f7-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="d96f7-108">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="d96f7-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="d96f7-109">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="d96f7-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="d96f7-110">[v] Sestavení, která se má najít.</span><span class="sxs-lookup"><span data-stu-id="d96f7-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="d96f7-111">[out] Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="d96f7-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d96f7-112">[v] Velikost v bajtech z `szName`.</span><span class="sxs-lookup"><span data-stu-id="d96f7-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="d96f7-113">[out] Počet znaků, které jsou ve skutečnosti, vrátí se v `szName`.</span><span class="sxs-lookup"><span data-stu-id="d96f7-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d96f7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d96f7-114">Requirements</span></span>  
 <span data-ttu-id="d96f7-115">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d96f7-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d96f7-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d96f7-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d96f7-117">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d96f7-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d96f7-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d96f7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d96f7-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="d96f7-119">See Also</span></span>  
 [<span data-ttu-id="d96f7-120">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d96f7-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="d96f7-121">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d96f7-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
