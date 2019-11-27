---
title: IMetaDataDispenser – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser
helpviewer_keywords:
- IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type:
- apiref
ms.openlocfilehash: b7ce76c22e7188117bddd9e4f328e323f6742685
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436235"
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="e032e-102">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e032e-102">IMetaDataDispenser Interface</span></span>
<span data-ttu-id="e032e-103">Poskytuje metody pro vytvoření nového oboru metadat nebo otevření existujícího.</span><span class="sxs-lookup"><span data-stu-id="e032e-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e032e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e032e-104">Methods</span></span>  
  
|<span data-ttu-id="e032e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e032e-105">Method</span></span>|<span data-ttu-id="e032e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e032e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e032e-107">DefineScope – metoda</span><span class="sxs-lookup"><span data-stu-id="e032e-107">DefineScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-definescope-method.md)|<span data-ttu-id="e032e-108">Vytvoří novou oblast v paměti, kde můžete vytvořit nová metadata.</span><span class="sxs-lookup"><span data-stu-id="e032e-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="e032e-109">OpenScope – metoda</span><span class="sxs-lookup"><span data-stu-id="e032e-109">OpenScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)|<span data-ttu-id="e032e-110">Otevře existující soubor na disku a namapuje jeho metadata do paměti.</span><span class="sxs-lookup"><span data-stu-id="e032e-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="e032e-111">OpenScopeOnMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="e032e-111">OpenScopeOnMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="e032e-112">Otevře oblast paměti, která obsahuje existující metadata.</span><span class="sxs-lookup"><span data-stu-id="e032e-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="e032e-113">To znamená, že tato metoda otevře zadanou oblast paměti, ve které jsou stávající data považována za metadata.</span><span class="sxs-lookup"><span data-stu-id="e032e-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e032e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e032e-114">Requirements</span></span>  
 <span data-ttu-id="e032e-115">**Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e032e-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e032e-116">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e032e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e032e-117">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="e032e-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e032e-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e032e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e032e-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e032e-119">See also</span></span>

- [<span data-ttu-id="e032e-120">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e032e-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="e032e-121">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="e032e-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
