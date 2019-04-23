---
title: IMetaDataDispenserEx – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96475086b1244ae75ed692dd10cb693af0be9af7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186950"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="fb539-102">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb539-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="fb539-103">Rozšiřuje [imetadatadispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) rozhraní poskytnout možnost řídit, jak použít metadat rozhraní API pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="fb539-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb539-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fb539-104">Methods</span></span>  
  
|<span data-ttu-id="fb539-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fb539-105">Method</span></span>|<span data-ttu-id="fb539-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fb539-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb539-107">FindAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="fb539-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="fb539-108">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="fb539-108">This method is not implemented.</span></span> <span data-ttu-id="fb539-109">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="fb539-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="fb539-110">FindAssemblyModule – metoda</span><span class="sxs-lookup"><span data-stu-id="fb539-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="fb539-111">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="fb539-111">This method is not implemented.</span></span> <span data-ttu-id="fb539-112">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="fb539-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="fb539-113">GetCORSystemDirectory – metoda</span><span class="sxs-lookup"><span data-stu-id="fb539-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="fb539-114">Získá adresář, který obsahuje aktuální modul (CLR).</span><span class="sxs-lookup"><span data-stu-id="fb539-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="fb539-115">Tato metoda je podporována pouze pro použití ladicími mimo proces.</span><span class="sxs-lookup"><span data-stu-id="fb539-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="fb539-116">Pokud je volána z jiné součásti, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="fb539-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="fb539-117">GetOption – metoda</span><span class="sxs-lookup"><span data-stu-id="fb539-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="fb539-118">Získá hodnotu zadané možnosti pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="fb539-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="fb539-119">Možnost řídí, jak se zpracovává volání na aktuální metadat.</span><span class="sxs-lookup"><span data-stu-id="fb539-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="fb539-120">OpenScopeOnITypeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="fb539-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="fb539-121">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="fb539-121">This method is not implemented.</span></span> <span data-ttu-id="fb539-122">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="fb539-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="fb539-123">SetOption – metoda</span><span class="sxs-lookup"><span data-stu-id="fb539-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="fb539-124">Nastaví zadanou možnost dané hodnotě pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="fb539-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="fb539-125">Možnost řídí, jak se zpracovává volání na aktuální metadat.</span><span class="sxs-lookup"><span data-stu-id="fb539-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fb539-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb539-126">Requirements</span></span>  
 <span data-ttu-id="fb539-127">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb539-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb539-128">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fb539-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fb539-129">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fb539-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fb539-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb539-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb539-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb539-131">See also</span></span>

- [<span data-ttu-id="fb539-132">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="fb539-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="fb539-133">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb539-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="fb539-134">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb539-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fb539-135">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb539-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
