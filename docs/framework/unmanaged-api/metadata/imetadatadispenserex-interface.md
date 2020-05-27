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
ms.openlocfilehash: 96f0c0c254ce255581ac2937c805096918ab29e8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008050"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="12e8b-102">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12e8b-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="12e8b-103">Rozšiřuje rozhraní [rozhraní IMetaDataDispenser](imetadatadispenser-interface.md) , aby poskytovala schopnost řídit způsob, jakým rozhraní API metadat pracují v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="12e8b-103">Extends the [IMetaDataDispenser Interface](imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="12e8b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="12e8b-104">Methods</span></span>  
  
|<span data-ttu-id="12e8b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="12e8b-105">Method</span></span>|<span data-ttu-id="12e8b-106">Description</span><span class="sxs-lookup"><span data-stu-id="12e8b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="12e8b-107">FindAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="12e8b-107">FindAssembly Method</span></span>](imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="12e8b-108">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="12e8b-108">This method is not implemented.</span></span> <span data-ttu-id="12e8b-109">Při volání Vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="12e8b-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="12e8b-110">FindAssemblyModule – metoda</span><span class="sxs-lookup"><span data-stu-id="12e8b-110">FindAssemblyModule Method</span></span>](imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="12e8b-111">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="12e8b-111">This method is not implemented.</span></span> <span data-ttu-id="12e8b-112">Při volání Vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="12e8b-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="12e8b-113">GetCORSystemDirectory – metoda</span><span class="sxs-lookup"><span data-stu-id="12e8b-113">GetCORSystemDirectory Method</span></span>](imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="12e8b-114">Načte adresář, který obsahuje aktuální modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="12e8b-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="12e8b-115">Tato metoda je podporována pouze pro použití vnitroprocesové ladicí program.</span><span class="sxs-lookup"><span data-stu-id="12e8b-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="12e8b-116">Pokud se volá z jiné součásti, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="12e8b-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="12e8b-117">GetOption – metoda</span><span class="sxs-lookup"><span data-stu-id="12e8b-117">GetOption Method</span></span>](imetadatadispenserex-getoption-method.md)|<span data-ttu-id="12e8b-118">Získá hodnotu zadané možnosti pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="12e8b-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="12e8b-119">Možnost určuje, jak jsou zpracovávány volání do aktuálního oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="12e8b-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="12e8b-120">OpenScopeOnITypeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="12e8b-120">OpenScopeOnITypeInfo Method</span></span>](imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="12e8b-121">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="12e8b-121">This method is not implemented.</span></span> <span data-ttu-id="12e8b-122">Při volání Vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="12e8b-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="12e8b-123">SetOption – metoda</span><span class="sxs-lookup"><span data-stu-id="12e8b-123">SetOption Method</span></span>](imetadatadispenserex-setoption-method.md)|<span data-ttu-id="12e8b-124">Nastaví zadanou možnost na danou hodnotu pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="12e8b-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="12e8b-125">Možnost určuje, jak jsou zpracovávány volání do aktuálního oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="12e8b-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="12e8b-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12e8b-126">Requirements</span></span>  
 <span data-ttu-id="12e8b-127">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12e8b-127">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12e8b-128">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="12e8b-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12e8b-129">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="12e8b-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="12e8b-130">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12e8b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e8b-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="12e8b-131">See also</span></span>

- [<span data-ttu-id="12e8b-132">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="12e8b-132">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="12e8b-133">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12e8b-133">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="12e8b-134">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12e8b-134">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="12e8b-135">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12e8b-135">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
