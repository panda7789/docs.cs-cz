---
title: "IMetaDataDispenserEx – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx
helpviewer_keywords: IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5ecb4e94c0deed3ed62b2d2eb8b0309ca092abf8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="b2809-102">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2809-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="b2809-103">Rozšiřuje [imetadatadispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) rozhraní poskytovat funkce řídit, jak pracovat metadat rozhraní API v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="b2809-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2809-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b2809-104">Methods</span></span>  
  
|<span data-ttu-id="b2809-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b2809-105">Method</span></span>|<span data-ttu-id="b2809-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b2809-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2809-107">Findassembly – metoda</span><span class="sxs-lookup"><span data-stu-id="b2809-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="b2809-108">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="b2809-108">This method is not implemented.</span></span> <span data-ttu-id="b2809-109">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="b2809-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="b2809-110">Findassemblymodule – metoda</span><span class="sxs-lookup"><span data-stu-id="b2809-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="b2809-111">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="b2809-111">This method is not implemented.</span></span> <span data-ttu-id="b2809-112">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="b2809-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="b2809-113">Getcorsystemdirectory – metoda</span><span class="sxs-lookup"><span data-stu-id="b2809-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="b2809-114">Získá adresář, který obsahuje modul aktuální CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="b2809-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="b2809-115">Tato metoda podporuje jenom pro použití ladicí programy mimo proces.</span><span class="sxs-lookup"><span data-stu-id="b2809-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="b2809-116">Pokud volání z jiné komponenty, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="b2809-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="b2809-117">Getoption – metoda</span><span class="sxs-lookup"><span data-stu-id="b2809-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="b2809-118">Získá hodnotu Zadaná možnost pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="b2809-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="b2809-119">Možnost určuje způsob zpracování volání do aktuálního oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="b2809-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="b2809-120">Openscopeonitypeinfo – metoda</span><span class="sxs-lookup"><span data-stu-id="b2809-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="b2809-121">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="b2809-121">This method is not implemented.</span></span> <span data-ttu-id="b2809-122">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="b2809-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="b2809-123">SetOption – metoda</span><span class="sxs-lookup"><span data-stu-id="b2809-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="b2809-124">Nastaví Zadaná možnost zadanou hodnotu pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="b2809-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="b2809-125">Možnost určuje způsob zpracování volání do aktuálního oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="b2809-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2809-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2809-126">Requirements</span></span>  
 <span data-ttu-id="b2809-127">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2809-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2809-128">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b2809-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2809-129">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2809-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2809-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2809-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2809-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2809-131">See Also</span></span>  
 [<span data-ttu-id="b2809-132">Rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="b2809-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="b2809-133">Imetadatadispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2809-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="b2809-134">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2809-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="b2809-135">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2809-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
