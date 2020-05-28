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
ms.openlocfilehash: 50aebb09924b93a622e5b7d84e65e41ee91f6018
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006191"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="647a6-102">IMetaDataDispenserEx::FindAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="647a6-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="647a6-103">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="647a6-103">This method is not implemented.</span></span> <span data-ttu-id="647a6-104">Při volání Vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="647a6-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="647a6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="647a6-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="647a6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="647a6-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="647a6-107">pro Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="647a6-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="647a6-108">pro Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="647a6-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="647a6-109">pro Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="647a6-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="647a6-110">pro Sestavení, které má být nalezeno.</span><span class="sxs-lookup"><span data-stu-id="647a6-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="647a6-111">mimo Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="647a6-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="647a6-112">pro Velikost v bajtech `szName` .</span><span class="sxs-lookup"><span data-stu-id="647a6-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="647a6-113">mimo Počet skutečně vrácených znaků `szName` .</span><span class="sxs-lookup"><span data-stu-id="647a6-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="647a6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="647a6-114">Requirements</span></span>  
 <span data-ttu-id="647a6-115">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="647a6-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="647a6-116">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="647a6-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="647a6-117">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="647a6-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="647a6-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="647a6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="647a6-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="647a6-119">See also</span></span>

- [<span data-ttu-id="647a6-120">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="647a6-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="647a6-121">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="647a6-121">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
