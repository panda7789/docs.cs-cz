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
ms.openlocfilehash: 985cdea670714394119fb846e9e55a01713559a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431142"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="ee424-102">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee424-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="ee424-103">Rozšiřuje rozhraní [rozhraní IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) , aby poskytovala schopnost řídit způsob, jakým rozhraní API metadat pracují v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="ee424-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee424-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ee424-104">Methods</span></span>  
  
|<span data-ttu-id="ee424-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ee424-105">Method</span></span>|<span data-ttu-id="ee424-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ee424-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee424-107">FindAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="ee424-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="ee424-108">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="ee424-108">This method is not implemented.</span></span> <span data-ttu-id="ee424-109">Při volání Vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="ee424-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="ee424-110">FindAssemblyModule – metoda</span><span class="sxs-lookup"><span data-stu-id="ee424-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="ee424-111">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="ee424-111">This method is not implemented.</span></span> <span data-ttu-id="ee424-112">Při volání Vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="ee424-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="ee424-113">GetCORSystemDirectory – metoda</span><span class="sxs-lookup"><span data-stu-id="ee424-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="ee424-114">Načte adresář, který obsahuje aktuální modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="ee424-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="ee424-115">Tato metoda je podporována pouze pro použití vnitroprocesové ladicí program.</span><span class="sxs-lookup"><span data-stu-id="ee424-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="ee424-116">Pokud se volá z jiné součásti, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="ee424-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="ee424-117">GetOption – metoda</span><span class="sxs-lookup"><span data-stu-id="ee424-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="ee424-118">Získá hodnotu zadané možnosti pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="ee424-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="ee424-119">Možnost určuje, jak jsou zpracovávány volání do aktuálního oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="ee424-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="ee424-120">OpenScopeOnITypeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="ee424-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="ee424-121">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="ee424-121">This method is not implemented.</span></span> <span data-ttu-id="ee424-122">Při volání Vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="ee424-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="ee424-123">SetOption – metoda</span><span class="sxs-lookup"><span data-stu-id="ee424-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="ee424-124">Nastaví zadanou možnost na danou hodnotu pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="ee424-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="ee424-125">Možnost určuje, jak jsou zpracovávány volání do aktuálního oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="ee424-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ee424-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee424-126">Requirements</span></span>  
 <span data-ttu-id="ee424-127">**Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee424-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee424-128">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ee424-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ee424-129">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="ee424-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ee424-130">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee424-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee424-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee424-131">See also</span></span>

- [<span data-ttu-id="ee424-132">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="ee424-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="ee424-133">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee424-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="ee424-134">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee424-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ee424-135">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee424-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
