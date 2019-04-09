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
ms.openlocfilehash: 2d1d97e443be884f45187a2811ddfce106249515
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183128"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="8d16d-102">IMetaDataDispenserEx::FindAssemblyModule – metoda</span><span class="sxs-lookup"><span data-stu-id="8d16d-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="8d16d-103">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="8d16d-103">This method is not implemented.</span></span> <span data-ttu-id="8d16d-104">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="8d16d-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d16d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d16d-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8d16d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d16d-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="8d16d-107">[in] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="8d16d-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="8d16d-108">[in] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="8d16d-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="8d16d-109">[in] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="8d16d-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="8d16d-110">[in] Název modulu.</span><span class="sxs-lookup"><span data-stu-id="8d16d-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="8d16d-111">[in] Sestavení, která se má najít.</span><span class="sxs-lookup"><span data-stu-id="8d16d-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="8d16d-112">[out] Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="8d16d-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8d16d-113">[in] Velikost v bajtech, z `szName`.</span><span class="sxs-lookup"><span data-stu-id="8d16d-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="8d16d-114">[out] Počet znaků ve skutečnosti vrátí v `szName`.</span><span class="sxs-lookup"><span data-stu-id="8d16d-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d16d-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d16d-115">Requirements</span></span>  
 <span data-ttu-id="8d16d-116">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d16d-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d16d-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8d16d-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d16d-118">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d16d-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="8d16d-119">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8d16d-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8d16d-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d16d-120">See also</span></span>

- [<span data-ttu-id="8d16d-121">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d16d-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="8d16d-122">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d16d-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
