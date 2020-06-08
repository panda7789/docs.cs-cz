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
ms.openlocfilehash: 5a232f30da8812c6f3bd94647d74151312a8593b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493033"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="c8087-102">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8087-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="c8087-103">Rozšiřuje rozhraní [IMetaDataEmit](imetadataemit-interface.md) primárně tak, aby poskytovala schopnost pracovat s obecnými typy.</span><span class="sxs-lookup"><span data-stu-id="c8087-103">Extends the [IMetaDataEmit](imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c8087-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c8087-104">Methods</span></span>  
  
|<span data-ttu-id="c8087-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c8087-105">Method</span></span>|<span data-ttu-id="c8087-106">Description</span><span class="sxs-lookup"><span data-stu-id="c8087-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c8087-107">DefineGenericParam – metoda</span><span class="sxs-lookup"><span data-stu-id="c8087-107">DefineGenericParam Method</span></span>](imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="c8087-108">Vytvoří definici pro parametr obecného typu a získá token k tomuto parametru obecného typu.</span><span class="sxs-lookup"><span data-stu-id="c8087-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="c8087-109">DefineMethodSpec – metoda</span><span class="sxs-lookup"><span data-stu-id="c8087-109">DefineMethodSpec Method</span></span>](imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="c8087-110">Vytvoří obecnou instanci metody a získá do definice token.</span><span class="sxs-lookup"><span data-stu-id="c8087-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="c8087-111">GetDeltaSaveSize – metoda</span><span class="sxs-lookup"><span data-stu-id="c8087-111">GetDeltaSaveSize Method</span></span>](imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="c8087-112">Získá hodnotu označující rozdíl velikosti dat, který je potřeba k vyjádření změn pro aktuální relaci úprav a pokračování.</span><span class="sxs-lookup"><span data-stu-id="c8087-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="c8087-113">ResetENCLog – metoda</span><span class="sxs-lookup"><span data-stu-id="c8087-113">ResetENCLog Method</span></span>](imetadataemit2-resetenclog-method.md)|<span data-ttu-id="c8087-114">Obnoví protokol Edit-and-Continue a spustí novou relaci.</span><span class="sxs-lookup"><span data-stu-id="c8087-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="c8087-115">SaveDelta – metoda</span><span class="sxs-lookup"><span data-stu-id="c8087-115">SaveDelta Method</span></span>](imetadataemit2-savedelta-method.md)|<span data-ttu-id="c8087-116">Uloží změny z aktuální relace úprav a pokračování do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="c8087-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="c8087-117">SaveDeltaToMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="c8087-117">SaveDeltaToMemory Method</span></span>](imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="c8087-118">Uloží změny z aktuální relace úprav a pokračování do paměti.</span><span class="sxs-lookup"><span data-stu-id="c8087-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="c8087-119">SaveDeltaToStream – metoda</span><span class="sxs-lookup"><span data-stu-id="c8087-119">SaveDeltaToStream Method</span></span>](imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="c8087-120">Uloží změny z aktuální relace úprav a pokračování do zadaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="c8087-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="c8087-121">SetGenericParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="c8087-121">SetGenericParamProps Method</span></span>](imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="c8087-122">Nastaví hodnoty vlastností pro definici obecného parametru, na kterou odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="c8087-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c8087-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8087-123">Requirements</span></span>  
 <span data-ttu-id="c8087-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8087-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8087-125">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c8087-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c8087-126">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="c8087-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c8087-127">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8087-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8087-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8087-128">See also</span></span>

- [<span data-ttu-id="c8087-129">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="c8087-129">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="c8087-130">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8087-130">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
