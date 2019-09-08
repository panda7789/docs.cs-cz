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
ms.openlocfilehash: aee9b986c1e26c1b2e34dac7151a00172451bbad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796549"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="383af-102">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="383af-102">IAssemblyName Interface</span></span>
<span data-ttu-id="383af-103">Poskytuje metody pro popis a práci s jedinečnou identitou sestavení.</span><span class="sxs-lookup"><span data-stu-id="383af-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="383af-104">Metody</span><span class="sxs-lookup"><span data-stu-id="383af-104">Methods</span></span>  
  
|<span data-ttu-id="383af-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="383af-105">Method</span></span>|<span data-ttu-id="383af-106">Popis</span><span class="sxs-lookup"><span data-stu-id="383af-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="383af-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="383af-107">Clone Method</span></span>](iassemblyname-clone-method.md)|<span data-ttu-id="383af-108">Vytvoří kopii tohoto `IAssemblyName` objektu bez podstruktury.</span><span class="sxs-lookup"><span data-stu-id="383af-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="383af-109">Finalize – metoda</span><span class="sxs-lookup"><span data-stu-id="383af-109">Finalize Method</span></span>](iassemblyname-finalize-method.md)|<span data-ttu-id="383af-110">Umožňuje tomuto `IAssemblyName` objektu uvolnit prostředky a provést jiné operace čištění před voláním jeho destruktoru.</span><span class="sxs-lookup"><span data-stu-id="383af-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="383af-111">GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="383af-111">GetDisplayName Method</span></span>](iassemblyname-getdisplayname-method.md)|<span data-ttu-id="383af-112">Získá popisný název sestavení, na které odkazuje tento `IAssemblyName` objekt.</span><span class="sxs-lookup"><span data-stu-id="383af-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="383af-113">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="383af-113">GetName Method</span></span>](iassemblyname-getname-method.md)|<span data-ttu-id="383af-114">Získá jednoduchý, nešifrovaný název sestavení, na který odkazuje tento `IAssemblyName` objekt.</span><span class="sxs-lookup"><span data-stu-id="383af-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="383af-115">GetProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="383af-115">GetProperty Method</span></span>](iassemblyname-getproperty-method.md)|<span data-ttu-id="383af-116">Získá ukazatel na vlastnost, na kterou odkazuje zadaný `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="383af-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="383af-117">GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="383af-117">GetVersion Method</span></span>](iassemblyname-getversion-method.md)|<span data-ttu-id="383af-118">Získá informace o verzi sestavení, na které odkazuje tento `IAssemblyName` objekt.</span><span class="sxs-lookup"><span data-stu-id="383af-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="383af-119">IsEqual – metoda</span><span class="sxs-lookup"><span data-stu-id="383af-119">IsEqual Method</span></span>](iassemblyname-isequal-method.md)|<span data-ttu-id="383af-120">Určuje `IAssemblyName`, zda je `IAssemblyName` zadaný objekt na základě zadaných příznaků porovnávání stejný.</span><span class="sxs-lookup"><span data-stu-id="383af-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="383af-121">SetProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="383af-121">SetProperty Method</span></span>](iassemblyname-setproperty-method.md)|<span data-ttu-id="383af-122">Nastaví hodnotu vlastnosti, na kterou odkazuje zadaný `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="383af-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="383af-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="383af-123">Requirements</span></span>  
 <span data-ttu-id="383af-124">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="383af-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="383af-125">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="383af-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="383af-126">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="383af-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="383af-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="383af-127">See also</span></span>

- [<span data-ttu-id="383af-128">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="383af-128">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="383af-129">IAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="383af-129">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
