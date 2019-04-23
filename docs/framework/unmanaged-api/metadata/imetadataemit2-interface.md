---
title: IMetaDataEmit2 – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87b5b60d75d5d28e100ec75192d0cacf51765927
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200191"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="90576-102">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90576-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="90576-103">Rozšiřuje [imetadataemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) rozhraní především k umožňují pracovat s obecných typů.</span><span class="sxs-lookup"><span data-stu-id="90576-103">Extends the [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="90576-104">Metody</span><span class="sxs-lookup"><span data-stu-id="90576-104">Methods</span></span>  
  
|<span data-ttu-id="90576-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="90576-105">Method</span></span>|<span data-ttu-id="90576-106">Popis</span><span class="sxs-lookup"><span data-stu-id="90576-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="90576-107">DefineGenericParam – metoda</span><span class="sxs-lookup"><span data-stu-id="90576-107">DefineGenericParam Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="90576-108">Vytvoří definici pro parametr obecného typu a získá token pro tento parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="90576-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="90576-109">DefineMethodSpec – metoda</span><span class="sxs-lookup"><span data-stu-id="90576-109">DefineMethodSpec Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="90576-110">Vytvoří instanci obecné metody a získá token pro definici.</span><span class="sxs-lookup"><span data-stu-id="90576-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="90576-111">GetDeltaSaveSize – metoda</span><span class="sxs-lookup"><span data-stu-id="90576-111">GetDeltaSaveSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="90576-112">Získá hodnotu, která rozdíl ve velikosti dat, který je potřeba express změny pro aktuální relaci edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="90576-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="90576-113">ResetENCLog – metoda</span><span class="sxs-lookup"><span data-stu-id="90576-113">ResetENCLog Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|<span data-ttu-id="90576-114">Obnoví protokolu edit-and-continue a spustí novou relaci.</span><span class="sxs-lookup"><span data-stu-id="90576-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="90576-115">SaveDelta – metoda</span><span class="sxs-lookup"><span data-stu-id="90576-115">SaveDelta Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|<span data-ttu-id="90576-116">Uloží změny z aktuální relace edit-and-continue do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="90576-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="90576-117">SaveDeltaToMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="90576-117">SaveDeltaToMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="90576-118">Uloží změny z aktuální relace edit-and-continue do paměti.</span><span class="sxs-lookup"><span data-stu-id="90576-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="90576-119">SaveDeltaToStream – metoda</span><span class="sxs-lookup"><span data-stu-id="90576-119">SaveDeltaToStream Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="90576-120">Uloží změny z aktuální relace edit-and-continue do zadaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="90576-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="90576-121">SetGenericParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="90576-121">SetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="90576-122">Nastavuje hodnoty vlastností pro obecný parametr definice odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="90576-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="90576-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90576-123">Requirements</span></span>  
 <span data-ttu-id="90576-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90576-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90576-125">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="90576-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90576-126">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90576-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="90576-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90576-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90576-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90576-128">See also</span></span>

- [<span data-ttu-id="90576-129">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="90576-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="90576-130">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90576-130">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
