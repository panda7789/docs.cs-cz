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
ms.openlocfilehash: 6a6def8fc10f04b89aa8d8c735025b01f9b6ddfb
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420757"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="e496c-102">IXCLRDataProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e496c-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="e496c-103">Poskytuje metody pro dotazování na informace o procesu.</span><span class="sxs-lookup"><span data-stu-id="e496c-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="e496c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e496c-104">Methods</span></span>

| <span data-ttu-id="e496c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e496c-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="e496c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e496c-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="e496c-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="e496c-107">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="e496c-108">Načte `AppDomain` v procesu jeho jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="e496c-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="e496c-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="e496c-109">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="e496c-110">Poskytuje popisovač pro zobrazení výčtu modulů procesu.</span><span class="sxs-lookup"><span data-stu-id="e496c-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="e496c-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="e496c-111">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="e496c-112">Vytvoří výčet modulů tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="e496c-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="e496c-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="e496c-113">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="e496c-114">Uvolňuje prostředky používané vnitřními iterátory použitými při výčtu modulů.</span><span class="sxs-lookup"><span data-stu-id="e496c-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="e496c-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="e496c-115">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="e496c-116">Poskytuje popisovač pro zobrazení výčtu instancí metod, které `AppDomain` začínají na dané adrese.</span><span class="sxs-lookup"><span data-stu-id="e496c-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="e496c-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="e496c-117">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="e496c-118">Vytvoří výčet instancí metody tohoto procesu počínaje posunem adresy.</span><span class="sxs-lookup"><span data-stu-id="e496c-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="e496c-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="e496c-119">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="e496c-120">Uvolní prostředky používané interními iterátory použitými během výčtu instance.</span><span class="sxs-lookup"><span data-stu-id="e496c-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="e496c-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e496c-121">Remarks</span></span>

<span data-ttu-id="e496c-122">Toto rozhraní je v modulu runtime a není zveřejněné prostřednictvím hlaviček nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="e496c-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="e496c-123">Jedná se však o rozhraní modelu COM, které je odvozeno z `IUnknown` identifikátoru GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` , který lze získat prostřednictvím obvyklých mechanismů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e496c-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="e496c-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e496c-124">Requirements</span></span>

<span data-ttu-id="e496c-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e496c-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="e496c-126">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="e496c-126">**Header:** None</span></span>  
<span data-ttu-id="e496c-127">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="e496c-127">**Library:** None</span></span>  
<span data-ttu-id="e496c-128">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e496c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e496c-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="e496c-129">See also</span></span>

- [<span data-ttu-id="e496c-130">Ladění</span><span class="sxs-lookup"><span data-stu-id="e496c-130">Debugging</span></span>](index.md)
- [<span data-ttu-id="e496c-131">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e496c-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
