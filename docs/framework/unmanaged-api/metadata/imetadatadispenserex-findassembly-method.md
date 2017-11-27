---
title: "IMetaDataDispenserEx::FindAssembly – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.FindAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7a70d1e2b3636a405fe28b84c2e76dd7264df4f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="30e24-102">IMetaDataDispenserEx::FindAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="30e24-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="30e24-103">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="30e24-103">This method is not implemented.</span></span> <span data-ttu-id="30e24-104">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="30e24-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30e24-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30e24-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="30e24-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="30e24-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="30e24-107">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="30e24-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="30e24-108">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="30e24-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="30e24-109">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="30e24-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="30e24-110">[v] Sestavení, která se má najít.</span><span class="sxs-lookup"><span data-stu-id="30e24-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="30e24-111">[out] Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="30e24-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="30e24-112">[v] Velikost v bajtech z `szName`.</span><span class="sxs-lookup"><span data-stu-id="30e24-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="30e24-113">[out] Počet znaků, které jsou ve skutečnosti, vrátí se v `szName`.</span><span class="sxs-lookup"><span data-stu-id="30e24-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30e24-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30e24-114">Requirements</span></span>  
 <span data-ttu-id="30e24-115">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30e24-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30e24-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="30e24-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="30e24-117">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="30e24-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30e24-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30e24-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30e24-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="30e24-119">See Also</span></span>  
 [<span data-ttu-id="30e24-120">Imetadatadispenserex – rozhraní</span><span class="sxs-lookup"><span data-stu-id="30e24-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="30e24-121">Imetadatadispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="30e24-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
