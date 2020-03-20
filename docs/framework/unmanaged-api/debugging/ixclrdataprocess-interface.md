---
title: IXCLRDataProcess – rozhraní
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e7e53615e38d0ab76f9e7c0a753be3c13780057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178378"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="c7b1d-102">IXCLRDataProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7b1d-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="c7b1d-103">Poskytuje metody pro dotazování na informace o procesu.</span><span class="sxs-lookup"><span data-stu-id="c7b1d-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="c7b1d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c7b1d-104">Methods</span></span>

| <span data-ttu-id="c7b1d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c7b1d-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="c7b1d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c7b1d-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="c7b1d-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="c7b1d-107">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="c7b1d-108">Získá `AppDomain` v procesu jeho jedinečné id.</span><span class="sxs-lookup"><span data-stu-id="c7b1d-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="c7b1d-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="c7b1d-109">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="c7b1d-110">Poskytuje popisovač pro výčet modulů procesu.</span><span class="sxs-lookup"><span data-stu-id="c7b1d-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="c7b1d-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="c7b1d-111">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="c7b1d-112">Vyjmenovává moduly tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="c7b1d-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="c7b1d-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="c7b1d-113">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="c7b1d-114">Uvolní prostředky používané interními iterátory používanými při výčtu modulu.</span><span class="sxs-lookup"><span data-stu-id="c7b1d-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="c7b1d-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="c7b1d-115">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="c7b1d-116">Poskytuje popisovač pro výčet instance metody `AppDomain` počínaje danou adresou.</span><span class="sxs-lookup"><span data-stu-id="c7b1d-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="c7b1d-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="c7b1d-117">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="c7b1d-118">Vyjmenovává instance metody tohoto procesu počínaje posunem adresy.</span><span class="sxs-lookup"><span data-stu-id="c7b1d-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="c7b1d-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="c7b1d-119">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="c7b1d-120">Uvolní prostředky používané interními iterátory používanými při výčtu instancí.</span><span class="sxs-lookup"><span data-stu-id="c7b1d-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="c7b1d-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7b1d-121">Remarks</span></span>

<span data-ttu-id="c7b1d-122">Toto rozhraní žije uvnitř modulu runtime a není vystaveno prostřednictvím žádné hlavičky nebo soubory knihovny.</span><span class="sxs-lookup"><span data-stu-id="c7b1d-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="c7b1d-123">Je to však rozhraní COM, `IUnknown` které je `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` odvozeno z s identifikátorem GUID, které lze získat prostřednictvím obvyklých mechanismů COM.</span><span class="sxs-lookup"><span data-stu-id="c7b1d-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7b1d-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7b1d-124">Requirements</span></span>

<span data-ttu-id="c7b1d-125">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7b1d-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="c7b1d-126">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="c7b1d-126">**Header:** None</span></span>  
<span data-ttu-id="c7b1d-127">**Knihovna:** Žádný</span><span class="sxs-lookup"><span data-stu-id="c7b1d-127">**Library:** None</span></span>  
<span data-ttu-id="c7b1d-128">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c7b1d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c7b1d-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7b1d-129">See also</span></span>

- [<span data-ttu-id="c7b1d-130">ladění</span><span class="sxs-lookup"><span data-stu-id="c7b1d-130">Debugging</span></span>](index.md)
- [<span data-ttu-id="c7b1d-131">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7b1d-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
