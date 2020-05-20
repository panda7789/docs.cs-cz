---
title: IXCLRDataMethodDefinition – rozhraní
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition Interface
helpviewer.keywords:
- IXCLRDataMethodDefinition Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ebb689eee4a89a70e81d8f9d958e7826c3b3421b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420952"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="42b1d-102">IXCLRDataMethodDefinition – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42b1d-102">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="42b1d-103">Poskytuje metody pro dotazování na informace o definici metody.</span><span class="sxs-lookup"><span data-stu-id="42b1d-103">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="42b1d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="42b1d-104">Methods</span></span>

<span data-ttu-id="42b1d-105">Následující metody jsou některé z metod, které jsou k dispozici v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="42b1d-105">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="42b1d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="42b1d-106">Method</span></span>                                                                                                                          | <span data-ttu-id="42b1d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="42b1d-107">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="42b1d-108">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="42b1d-108">StartEnumInstances</span></span>](ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="42b1d-109">Poskytuje popisovač pro výčet instancí metody pro daný objekt `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="42b1d-109">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="42b1d-110">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="42b1d-110">EnumInstance</span></span>](ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="42b1d-111">Vytvoří výčet instancí této definice metody.</span><span class="sxs-lookup"><span data-stu-id="42b1d-111">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="42b1d-112">EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="42b1d-112">EndEnumInstances</span></span>](ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="42b1d-113">Uvolní prostředky používané interními iterátory použitými během výčtu instance.</span><span class="sxs-lookup"><span data-stu-id="42b1d-113">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="42b1d-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42b1d-114">Remarks</span></span>

<span data-ttu-id="42b1d-115">Toto rozhraní je v modulu runtime a není zveřejněné prostřednictvím hlaviček nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="42b1d-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="42b1d-116">Jedná se však o rozhraní modelu COM, které je odvozeno z `IUnknown` identifikátoru GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` , který lze získat prostřednictvím obvyklých mechanismů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="42b1d-116">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="42b1d-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42b1d-117">Requirements</span></span>

<span data-ttu-id="42b1d-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42b1d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="42b1d-119">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="42b1d-119">**Header:** None</span></span>  
<span data-ttu-id="42b1d-120">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="42b1d-120">**Library:** None</span></span>  
<span data-ttu-id="42b1d-121">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="42b1d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="42b1d-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="42b1d-122">See also</span></span>

- [<span data-ttu-id="42b1d-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="42b1d-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="42b1d-124">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42b1d-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
