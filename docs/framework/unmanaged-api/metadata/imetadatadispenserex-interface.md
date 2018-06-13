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
ms.openlocfilehash: 7d930088d6e621885d14fc4bdab2475aa27594e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448697"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="2d21f-102">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d21f-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="2d21f-103">Rozšiřuje [imetadatadispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) rozhraní poskytovat funkce řídit, jak pracovat metadat rozhraní API v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="2d21f-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d21f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2d21f-104">Methods</span></span>  
  
|<span data-ttu-id="2d21f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2d21f-105">Method</span></span>|<span data-ttu-id="2d21f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2d21f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2d21f-107">FindAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="2d21f-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="2d21f-108">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="2d21f-108">This method is not implemented.</span></span> <span data-ttu-id="2d21f-109">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="2d21f-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="2d21f-110">FindAssemblyModule – metoda</span><span class="sxs-lookup"><span data-stu-id="2d21f-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="2d21f-111">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="2d21f-111">This method is not implemented.</span></span> <span data-ttu-id="2d21f-112">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="2d21f-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="2d21f-113">GetCORSystemDirectory – metoda</span><span class="sxs-lookup"><span data-stu-id="2d21f-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="2d21f-114">Získá adresář, který obsahuje modul aktuální CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="2d21f-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="2d21f-115">Tato metoda podporuje jenom pro použití ladicí programy mimo proces.</span><span class="sxs-lookup"><span data-stu-id="2d21f-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="2d21f-116">Pokud volání z jiné komponenty, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="2d21f-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="2d21f-117">GetOption – metoda</span><span class="sxs-lookup"><span data-stu-id="2d21f-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="2d21f-118">Získá hodnotu Zadaná možnost pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="2d21f-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="2d21f-119">Možnost určuje způsob zpracování volání do aktuálního oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="2d21f-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="2d21f-120">OpenScopeOnITypeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="2d21f-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="2d21f-121">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="2d21f-121">This method is not implemented.</span></span> <span data-ttu-id="2d21f-122">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="2d21f-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="2d21f-123">SetOption – metoda</span><span class="sxs-lookup"><span data-stu-id="2d21f-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="2d21f-124">Nastaví Zadaná možnost zadanou hodnotu pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="2d21f-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="2d21f-125">Možnost určuje způsob zpracování volání do aktuálního oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="2d21f-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2d21f-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d21f-126">Requirements</span></span>  
 <span data-ttu-id="2d21f-127">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d21f-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d21f-128">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2d21f-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d21f-129">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2d21f-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2d21f-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d21f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d21f-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d21f-131">See Also</span></span>  
 [<span data-ttu-id="2d21f-132">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="2d21f-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="2d21f-133">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d21f-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="2d21f-134">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d21f-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="2d21f-135">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d21f-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
