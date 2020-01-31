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
ms.openlocfilehash: 708c681a98113a406249a360c2fc81087e5b97f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790423"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="47166-102">IXCLRDataMethodDefinition – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47166-102">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="47166-103">Poskytuje metody pro dotazování na informace o definici metody.</span><span class="sxs-lookup"><span data-stu-id="47166-103">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="47166-104">Metody</span><span class="sxs-lookup"><span data-stu-id="47166-104">Methods</span></span>

<span data-ttu-id="47166-105">Následující metody jsou některé z metod, které jsou k dispozici v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="47166-105">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="47166-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="47166-106">Method</span></span>                                                                                                                          | <span data-ttu-id="47166-107">Popis</span><span class="sxs-lookup"><span data-stu-id="47166-107">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="47166-108">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="47166-108">StartEnumInstances</span></span>](ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="47166-109">Poskytuje popisovač pro výčet instancí metody pro daný `IXCLRDataAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="47166-109">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="47166-110">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="47166-110">EnumInstance</span></span>](ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="47166-111">Vytvoří výčet instancí této definice metody.</span><span class="sxs-lookup"><span data-stu-id="47166-111">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="47166-112">EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="47166-112">EndEnumInstances</span></span>](ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="47166-113">Uvolní prostředky používané interními iterátory použitými během výčtu instance.</span><span class="sxs-lookup"><span data-stu-id="47166-113">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="47166-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47166-114">Remarks</span></span>

<span data-ttu-id="47166-115">Toto rozhraní je v modulu runtime a není zveřejněné prostřednictvím hlaviček nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="47166-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="47166-116">Jedná se však o rozhraní modelu COM, které je odvozeno od `IUnknown` s identifikátorem GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97`, které lze získat prostřednictvím obvyklých mechanismů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="47166-116">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="47166-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47166-117">Requirements</span></span>

<span data-ttu-id="47166-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47166-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="47166-119">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="47166-119">**Header:** None</span></span>  
<span data-ttu-id="47166-120">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="47166-120">**Library:** None</span></span>  
<span data-ttu-id="47166-121">**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="47166-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="47166-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47166-122">See also</span></span>

- [<span data-ttu-id="47166-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="47166-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="47166-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="47166-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
