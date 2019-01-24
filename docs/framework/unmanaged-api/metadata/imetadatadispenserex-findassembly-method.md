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
ms.openlocfilehash: 5b35abe6a11b96a88bdd610a4018469bf747fe90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550705"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="73793-102">IMetaDataDispenserEx::FindAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="73793-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="73793-103">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="73793-103">This method is not implemented.</span></span> <span data-ttu-id="73793-104">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="73793-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73793-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73793-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="73793-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="73793-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="73793-107">[in] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="73793-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="73793-108">[in] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="73793-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="73793-109">[in] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="73793-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="73793-110">[in] Sestavení, která se má najít.</span><span class="sxs-lookup"><span data-stu-id="73793-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="73793-111">[out] Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="73793-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="73793-112">[in] Velikost v bajtech, z `szName`.</span><span class="sxs-lookup"><span data-stu-id="73793-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="73793-113">[out] Počet znaků ve skutečnosti vrátí v `szName`.</span><span class="sxs-lookup"><span data-stu-id="73793-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73793-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73793-114">Requirements</span></span>  
 <span data-ttu-id="73793-115">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73793-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73793-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="73793-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="73793-117">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="73793-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="73793-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73793-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73793-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73793-119">See also</span></span>
- [<span data-ttu-id="73793-120">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73793-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="73793-121">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73793-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
