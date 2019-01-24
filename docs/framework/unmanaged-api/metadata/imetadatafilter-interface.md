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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e1975a5063217299ddbcdce6f625d5a1285d5b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642552"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="a36bb-102">IMetaDataFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a36bb-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="a36bb-103">Poskytuje metody pro označení a filtrování tokeny metadat předcházet opakování akce, které již byly provedeny.</span><span class="sxs-lookup"><span data-stu-id="a36bb-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a36bb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a36bb-104">Methods</span></span>  
  
|<span data-ttu-id="a36bb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a36bb-105">Method</span></span>|<span data-ttu-id="a36bb-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a36bb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a36bb-107">IsTokenMarked – metoda</span><span class="sxs-lookup"><span data-stu-id="a36bb-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="a36bb-108">Získá hodnotu označující, zda token Zadaná metadata byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="a36bb-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="a36bb-109">MarkToken – metoda</span><span class="sxs-lookup"><span data-stu-id="a36bb-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="a36bb-110">Nastaví hodnotu označující, že token Zadaná metadata byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="a36bb-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="a36bb-111">UnmarkAll – metoda</span><span class="sxs-lookup"><span data-stu-id="a36bb-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="a36bb-112">Odstraní značky zpracování ze všech tokenů v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="a36bb-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a36bb-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a36bb-113">Requirements</span></span>  
 <span data-ttu-id="a36bb-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a36bb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a36bb-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a36bb-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a36bb-116">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a36bb-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a36bb-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a36bb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a36bb-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a36bb-118">See also</span></span>
- [<span data-ttu-id="a36bb-119">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="a36bb-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
