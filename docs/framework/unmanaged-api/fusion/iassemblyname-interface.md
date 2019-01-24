---
title: IAssemblyName – rozhraní
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22276e543e8eeb9c6cf9aeee7a9af92c503d3a7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549012"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="826a4-102">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="826a4-102">IAssemblyName Interface</span></span>
<span data-ttu-id="826a4-103">Poskytuje metody pro popisující a práci s jedinečnou identitu sestavení.</span><span class="sxs-lookup"><span data-stu-id="826a4-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="826a4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="826a4-104">Methods</span></span>  
  
|<span data-ttu-id="826a4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="826a4-105">Method</span></span>|<span data-ttu-id="826a4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="826a4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="826a4-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="826a4-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|<span data-ttu-id="826a4-108">Vytvoří Mělkou kopii to `IAssemblyName` objektu.</span><span class="sxs-lookup"><span data-stu-id="826a4-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="826a4-109">Finalize – metoda</span><span class="sxs-lookup"><span data-stu-id="826a4-109">Finalize Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|<span data-ttu-id="826a4-110">To umožňuje `IAssemblyName` objektu k uvolnění prostředků a provádět jiné operace čištění před jeho destruktoru je volána.</span><span class="sxs-lookup"><span data-stu-id="826a4-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="826a4-111">GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="826a4-111">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|<span data-ttu-id="826a4-112">Získá popisný název sestavení odkazuje situace `IAssemblyName` objektu.</span><span class="sxs-lookup"><span data-stu-id="826a4-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="826a4-113">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="826a4-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|<span data-ttu-id="826a4-114">Získá název jednoduchý a nešifrované sestavení odkazuje situace `IAssemblyName` objektu.</span><span class="sxs-lookup"><span data-stu-id="826a4-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="826a4-115">GetProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="826a4-115">GetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|<span data-ttu-id="826a4-116">Získá ukazatel na vlastnost odkazuje zadanou `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="826a4-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="826a4-117">GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="826a4-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|<span data-ttu-id="826a4-118">Získá informace o verzi pro sestavení odkazuje situace `IAssemblyName` objektu.</span><span class="sxs-lookup"><span data-stu-id="826a4-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="826a4-119">IsEqual – metoda</span><span class="sxs-lookup"><span data-stu-id="826a4-119">IsEqual Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|<span data-ttu-id="826a4-120">Určuje, zda zadané `IAssemblyName` objekt rovná tomuto `IAssemblyName`podle zadané porovnávací příznaky.</span><span class="sxs-lookup"><span data-stu-id="826a4-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="826a4-121">SetProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="826a4-121">SetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|<span data-ttu-id="826a4-122">Nastaví hodnotu vlastnosti odkazuje zadaný `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="826a4-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="826a4-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="826a4-123">Requirements</span></span>  
 <span data-ttu-id="826a4-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="826a4-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="826a4-125">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="826a4-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="826a4-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="826a4-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="826a4-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="826a4-127">See also</span></span>
- [<span data-ttu-id="826a4-128">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="826a4-128">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="826a4-129">IAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="826a4-129">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
