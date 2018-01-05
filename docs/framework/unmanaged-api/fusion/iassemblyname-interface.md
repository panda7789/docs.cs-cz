---
title: "IAssemblyName – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName
helpviewer_keywords: IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 902ad9f67d06306e79666f0e10d85bdb9c65c377
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="5cdd5-102">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5cdd5-102">IAssemblyName Interface</span></span>
<span data-ttu-id="5cdd5-103">Poskytuje metody pro popisující a práci s jedinečnou identitu sestavení.</span><span class="sxs-lookup"><span data-stu-id="5cdd5-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5cdd5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5cdd5-104">Methods</span></span>  
  
|<span data-ttu-id="5cdd5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5cdd5-105">Method</span></span>|<span data-ttu-id="5cdd5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5cdd5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5cdd5-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="5cdd5-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|<span data-ttu-id="5cdd5-108">Vytvoří kopii bez podstruktury tohoto `IAssemblyName` objektu.</span><span class="sxs-lookup"><span data-stu-id="5cdd5-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="5cdd5-109">Finalize – metoda</span><span class="sxs-lookup"><span data-stu-id="5cdd5-109">Finalize Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|<span data-ttu-id="5cdd5-110">To umožňuje `IAssemblyName` objektu k uvolnění prostředků a provádění dalších operací čištění před jeho destruktoru.</span><span class="sxs-lookup"><span data-stu-id="5cdd5-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="5cdd5-111">GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="5cdd5-111">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|<span data-ttu-id="5cdd5-112">Získá popisný název sestavení odkazuje toto `IAssemblyName` objektu.</span><span class="sxs-lookup"><span data-stu-id="5cdd5-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="5cdd5-113">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="5cdd5-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|<span data-ttu-id="5cdd5-114">Získá název sestavení odkazuje toto jednoduché, nezašifrované `IAssemblyName` objektu.</span><span class="sxs-lookup"><span data-stu-id="5cdd5-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="5cdd5-115">GetProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="5cdd5-115">GetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|<span data-ttu-id="5cdd5-116">Získá ukazatel na vlastnost odkazuje zadaný `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="5cdd5-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="5cdd5-117">GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="5cdd5-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|<span data-ttu-id="5cdd5-118">Získá informace o verzi pro sestavení odkazuje toto `IAssemblyName` objektu.</span><span class="sxs-lookup"><span data-stu-id="5cdd5-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="5cdd5-119">IsEqual – metoda</span><span class="sxs-lookup"><span data-stu-id="5cdd5-119">IsEqual Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|<span data-ttu-id="5cdd5-120">Určuje, zda je zadané `IAssemblyName` objekt rovná to `IAssemblyName`, podle příznaky zadaný porovnání.</span><span class="sxs-lookup"><span data-stu-id="5cdd5-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="5cdd5-121">SetProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="5cdd5-121">SetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|<span data-ttu-id="5cdd5-122">Nastaví hodnotu vlastnosti odkazuje zadaný `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="5cdd5-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5cdd5-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5cdd5-123">Requirements</span></span>  
 <span data-ttu-id="5cdd5-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cdd5-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cdd5-125">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="5cdd5-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5cdd5-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cdd5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cdd5-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="5cdd5-127">See Also</span></span>  
 [<span data-ttu-id="5cdd5-128">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="5cdd5-128">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="5cdd5-129">IAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5cdd5-129">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
