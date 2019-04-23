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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dda284fc86f0a82472c59d6bab08fd4a87364723
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225973"
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="62526-102">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62526-102">IMetaDataDispenser Interface</span></span>
<span data-ttu-id="62526-103">Poskytuje metody pro vytvoření nového oboru metadat, nebo otevřete existující.</span><span class="sxs-lookup"><span data-stu-id="62526-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="62526-104">Metody</span><span class="sxs-lookup"><span data-stu-id="62526-104">Methods</span></span>  
  
|<span data-ttu-id="62526-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="62526-105">Method</span></span>|<span data-ttu-id="62526-106">Popis</span><span class="sxs-lookup"><span data-stu-id="62526-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="62526-107">DefineScope – metoda</span><span class="sxs-lookup"><span data-stu-id="62526-107">DefineScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-definescope-method.md)|<span data-ttu-id="62526-108">Vytvoří nové oblasti v paměti, kde můžete vytvořit nová metadata.</span><span class="sxs-lookup"><span data-stu-id="62526-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="62526-109">OpenScope – metoda</span><span class="sxs-lookup"><span data-stu-id="62526-109">OpenScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)|<span data-ttu-id="62526-110">Otevření existujícího souboru na disku a mapuje jeho metadata do paměti.</span><span class="sxs-lookup"><span data-stu-id="62526-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="62526-111">OpenScopeOnMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="62526-111">OpenScopeOnMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="62526-112">Otevře se oblast paměti, která obsahuje existující metadata.</span><span class="sxs-lookup"><span data-stu-id="62526-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="62526-113">To znamená, že tato metoda otevře oblastí paměti, ve kterém existujících dat je považován za metadat.</span><span class="sxs-lookup"><span data-stu-id="62526-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62526-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62526-114">Requirements</span></span>  
 <span data-ttu-id="62526-115">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62526-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62526-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="62526-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="62526-117">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="62526-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="62526-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62526-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62526-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62526-119">See also</span></span>

- [<span data-ttu-id="62526-120">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62526-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="62526-121">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="62526-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
