---
title: IXCLRDataProcess Interface
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
ms.openlocfilehash: 8c98dd42b4ac5593d96478c2286f49ad216a4bc1
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416092"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="ee367-102">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="ee367-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="ee367-103">Poskytuje metody pro dotazování na informace o procesu.</span><span class="sxs-lookup"><span data-stu-id="ee367-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="ee367-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ee367-104">Methods</span></span>

| <span data-ttu-id="ee367-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ee367-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="ee367-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ee367-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="ee367-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="ee367-107">GetAppDomainByUniqueId</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="ee367-108">Získá `AppDomain` v procesu podle jejího jedinečného ID.</span><span class="sxs-lookup"><span data-stu-id="ee367-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="ee367-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="ee367-109">StartEnumModules</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="ee367-110">Poskytuje popisovač na výčet modulů procesů.</span><span class="sxs-lookup"><span data-stu-id="ee367-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="ee367-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="ee367-111">EnumModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="ee367-112">Vytvoří výčet modulů tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="ee367-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="ee367-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="ee367-113">EndEnumModules</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="ee367-114">Uvolní prostředky využívané třídou interní iterátory využitých modulu výčtu.</span><span class="sxs-lookup"><span data-stu-id="ee367-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="ee367-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="ee367-115">StartEnumMethodInstancesByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="ee367-116">Poskytuje popisovač vytvořit výčet instancí metoda `AppDomain` spuštění na dané adrese.</span><span class="sxs-lookup"><span data-stu-id="ee367-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="ee367-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="ee367-117">EnumMethodInstanceByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="ee367-118">Vytvoří výčet metodu instance tohoto procesu začínající na posun adresy.</span><span class="sxs-lookup"><span data-stu-id="ee367-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="ee367-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="ee367-119">EndEnumMethodInstancesByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="ee367-120">Uvolní prostředky využívané třídou interní iterátory využitých instance výčtu.</span><span class="sxs-lookup"><span data-stu-id="ee367-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="ee367-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee367-121">Remarks</span></span>

<span data-ttu-id="ee367-122">Toto rozhraní se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="ee367-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="ee367-123">Je však rozhraní modelu COM, která je odvozena z `IUnknown` s identifikátorem GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` , který můžete získat prostřednictvím obvykle COM mechanismů.</span><span class="sxs-lookup"><span data-stu-id="ee367-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee367-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee367-124">Requirements</span></span>

<span data-ttu-id="ee367-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee367-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="ee367-126">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="ee367-126">**Header:** None</span></span>  
<span data-ttu-id="ee367-127">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="ee367-127">**Library:** None</span></span>  
<span data-ttu-id="ee367-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ee367-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ee367-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee367-129">See Also</span></span>

- [<span data-ttu-id="ee367-130">Ladění</span><span class="sxs-lookup"><span data-stu-id="ee367-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="ee367-131">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ee367-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
