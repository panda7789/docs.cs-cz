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
ms.openlocfilehash: 821936d20a421739e8eb3d5df228888df7f022e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503780"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="ffcb7-102">IMetaDataFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ffcb7-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="ffcb7-103">Poskytuje metody pro označování a filtrování tokenů metadat, aby nedocházelo k opakujícím se akcím, které již byly provedeny.</span><span class="sxs-lookup"><span data-stu-id="ffcb7-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ffcb7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ffcb7-104">Methods</span></span>  
  
|<span data-ttu-id="ffcb7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ffcb7-105">Method</span></span>|<span data-ttu-id="ffcb7-106">Description</span><span class="sxs-lookup"><span data-stu-id="ffcb7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ffcb7-107">IsTokenMarked – metoda</span><span class="sxs-lookup"><span data-stu-id="ffcb7-107">IsTokenMarked Method</span></span>](imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="ffcb7-108">Získá hodnotu, která označuje, zda byl zpracován zadaný token metadat.</span><span class="sxs-lookup"><span data-stu-id="ffcb7-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="ffcb7-109">MarkToken – metoda</span><span class="sxs-lookup"><span data-stu-id="ffcb7-109">MarkToken Method</span></span>](imetadatafilter-marktoken-method.md)|<span data-ttu-id="ffcb7-110">Nastaví hodnotu označující, že zadaný token metadat byl zpracován.</span><span class="sxs-lookup"><span data-stu-id="ffcb7-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="ffcb7-111">UnmarkAll – metoda</span><span class="sxs-lookup"><span data-stu-id="ffcb7-111">UnmarkAll Method</span></span>](imetadatafilter-unmarkall-method.md)|<span data-ttu-id="ffcb7-112">Odstraní značky zpracování ze všech tokenů v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="ffcb7-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ffcb7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ffcb7-113">Requirements</span></span>  
 <span data-ttu-id="ffcb7-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffcb7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffcb7-115">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ffcb7-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ffcb7-116">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="ffcb7-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ffcb7-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffcb7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffcb7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ffcb7-118">See also</span></span>

- [<span data-ttu-id="ffcb7-119">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="ffcb7-119">Metadata Interfaces</span></span>](metadata-interfaces.md)
