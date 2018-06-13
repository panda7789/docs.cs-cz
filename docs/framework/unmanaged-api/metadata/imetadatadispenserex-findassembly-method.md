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
ms.openlocfilehash: 0b4caf27fe45ce0a85b7e1800827a1e5cd0893ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445235"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="8bfc6-102">IMetaDataDispenserEx::FindAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="8bfc6-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="8bfc6-103">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="8bfc6-103">This method is not implemented.</span></span> <span data-ttu-id="8bfc6-104">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="8bfc6-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bfc6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bfc6-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="8bfc6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bfc6-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="8bfc6-107">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="8bfc6-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="8bfc6-108">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="8bfc6-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="8bfc6-109">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="8bfc6-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="8bfc6-110">[v] Sestavení, která se má najít.</span><span class="sxs-lookup"><span data-stu-id="8bfc6-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="8bfc6-111">[out] Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="8bfc6-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8bfc6-112">[v] Velikost v bajtech z `szName`.</span><span class="sxs-lookup"><span data-stu-id="8bfc6-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="8bfc6-113">[out] Počet znaků, které jsou ve skutečnosti, vrátí se v `szName`.</span><span class="sxs-lookup"><span data-stu-id="8bfc6-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bfc6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8bfc6-114">Requirements</span></span>  
 <span data-ttu-id="8bfc6-115">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bfc6-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bfc6-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8bfc6-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8bfc6-117">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8bfc6-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8bfc6-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bfc6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bfc6-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bfc6-119">See Also</span></span>  
 [<span data-ttu-id="8bfc6-120">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bfc6-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="8bfc6-121">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bfc6-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
