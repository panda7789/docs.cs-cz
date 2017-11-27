---
title: "IMetaDataEmit2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2
helpviewer_keywords: IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 235134c66395f04a87ed4f3325f5cc4cd9fecfc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="d8ba8-102">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8ba8-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="d8ba8-103">Rozšiřuje [imetadataemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) rozhraní hlavně kvůli umožňují pracovat s obecné typy.</span><span class="sxs-lookup"><span data-stu-id="d8ba8-103">Extends the [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8ba8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d8ba8-104">Methods</span></span>  
  
|<span data-ttu-id="d8ba8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d8ba8-105">Method</span></span>|<span data-ttu-id="d8ba8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d8ba8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d8ba8-107">Definegenericparam – metoda</span><span class="sxs-lookup"><span data-stu-id="d8ba8-107">DefineGenericParam Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="d8ba8-108">Vytvoří definici pro parametr obecného typu a získá token pro tento parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d8ba8-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="d8ba8-109">Definemethodspec – metoda</span><span class="sxs-lookup"><span data-stu-id="d8ba8-109">DefineMethodSpec Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="d8ba8-110">Vytvoří instanci obecné metody a získá token k definici.</span><span class="sxs-lookup"><span data-stu-id="d8ba8-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="d8ba8-111">Getdeltasavesize – metoda</span><span class="sxs-lookup"><span data-stu-id="d8ba8-111">GetDeltaSaveSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="d8ba8-112">Získá hodnotu, která určuje rozdíl ve velikosti dat, který je potřeba express změny pro aktuální relaci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="d8ba8-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="d8ba8-113">Resetenclog – metoda</span><span class="sxs-lookup"><span data-stu-id="d8ba8-113">ResetENCLog Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|<span data-ttu-id="d8ba8-114">Obnoví protokol upravit a pokračovat a spustí novou relaci.</span><span class="sxs-lookup"><span data-stu-id="d8ba8-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="d8ba8-115">Savedelta – metoda</span><span class="sxs-lookup"><span data-stu-id="d8ba8-115">SaveDelta Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|<span data-ttu-id="d8ba8-116">Uloží změny z aktuální relace upravit a pokračovat do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="d8ba8-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="d8ba8-117">Savedeltatomemory – metoda</span><span class="sxs-lookup"><span data-stu-id="d8ba8-117">SaveDeltaToMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="d8ba8-118">Uloží změny do paměti z aktuální relace upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="d8ba8-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="d8ba8-119">Savedeltatostream – metoda</span><span class="sxs-lookup"><span data-stu-id="d8ba8-119">SaveDeltaToStream Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="d8ba8-120">Uloží změny do zadaného datového proudu z aktuální relace upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="d8ba8-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="d8ba8-121">Setgenericparamprops – metoda</span><span class="sxs-lookup"><span data-stu-id="d8ba8-121">SetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="d8ba8-122">Nastaví hodnoty vlastností pro definici obecný parametr odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="d8ba8-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8ba8-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8ba8-123">Requirements</span></span>  
 <span data-ttu-id="d8ba8-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ba8-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ba8-125">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d8ba8-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8ba8-126">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d8ba8-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d8ba8-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ba8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ba8-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8ba8-128">See Also</span></span>  
 [<span data-ttu-id="d8ba8-129">Rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="d8ba8-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="d8ba8-130">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8ba8-130">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
