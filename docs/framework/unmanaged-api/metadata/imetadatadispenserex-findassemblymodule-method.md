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
ms.openlocfilehash: 64f1e2a8f05616c7ca84bc130428629b1176e985
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006178"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="a205d-102">IMetaDataDispenserEx::FindAssemblyModule – metoda</span><span class="sxs-lookup"><span data-stu-id="a205d-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="a205d-103">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="a205d-103">This method is not implemented.</span></span> <span data-ttu-id="a205d-104">Při volání Vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="a205d-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a205d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a205d-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="a205d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a205d-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="a205d-107">pro Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="a205d-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="a205d-108">pro Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="a205d-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="a205d-109">pro Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="a205d-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="a205d-110">pro Název modulu.</span><span class="sxs-lookup"><span data-stu-id="a205d-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="a205d-111">pro Sestavení, které má být nalezeno.</span><span class="sxs-lookup"><span data-stu-id="a205d-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="a205d-112">mimo Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="a205d-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="a205d-113">pro Velikost v bajtech `szName` .</span><span class="sxs-lookup"><span data-stu-id="a205d-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="a205d-114">mimo Počet skutečně vrácených znaků `szName` .</span><span class="sxs-lookup"><span data-stu-id="a205d-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a205d-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a205d-115">Requirements</span></span>  
 <span data-ttu-id="a205d-116">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a205d-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a205d-117">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a205d-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a205d-118">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="a205d-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a205d-119">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a205d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a205d-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a205d-120">See also</span></span>

- [<span data-ttu-id="a205d-121">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a205d-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="a205d-122">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a205d-122">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
