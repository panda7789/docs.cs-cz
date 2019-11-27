---
title: IMetaDataFilter – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
ms.openlocfilehash: e8b15f478eb3b94b7cdcab3b69d54e7cc99be13b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440162"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="89f02-102">IMetaDataFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89f02-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="89f02-103">Poskytuje metody pro označování a filtrování tokenů metadat, aby nedocházelo k opakujícím se akcím, které již byly provedeny.</span><span class="sxs-lookup"><span data-stu-id="89f02-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="89f02-104">Metody</span><span class="sxs-lookup"><span data-stu-id="89f02-104">Methods</span></span>  
  
|<span data-ttu-id="89f02-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="89f02-105">Method</span></span>|<span data-ttu-id="89f02-106">Popis</span><span class="sxs-lookup"><span data-stu-id="89f02-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="89f02-107">IsTokenMarked – metoda</span><span class="sxs-lookup"><span data-stu-id="89f02-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="89f02-108">Získá hodnotu, která označuje, zda byl zpracován zadaný token metadat.</span><span class="sxs-lookup"><span data-stu-id="89f02-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="89f02-109">MarkToken – metoda</span><span class="sxs-lookup"><span data-stu-id="89f02-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="89f02-110">Nastaví hodnotu označující, že zadaný token metadat byl zpracován.</span><span class="sxs-lookup"><span data-stu-id="89f02-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="89f02-111">UnmarkAll – metoda</span><span class="sxs-lookup"><span data-stu-id="89f02-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="89f02-112">Odstraní značky zpracování ze všech tokenů v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="89f02-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89f02-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89f02-113">Requirements</span></span>  
 <span data-ttu-id="89f02-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89f02-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89f02-115">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="89f02-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89f02-116">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="89f02-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89f02-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89f02-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f02-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89f02-118">See also</span></span>

- [<span data-ttu-id="89f02-119">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="89f02-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
