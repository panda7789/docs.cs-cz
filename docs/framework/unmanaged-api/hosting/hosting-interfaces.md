---
title: "Rozhraní hostování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46208d6db716f7e1e7a443d958c059b22f74c46f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-interfaces"></a><span data-ttu-id="011a7-102">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="011a7-102">Hosting Interfaces</span></span>
<span data-ttu-id="011a7-103">Tato část popisuje rozhraní, která nespravované hostitelů můžete integrovat common language runtime (CLR) do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="011a7-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="011a7-104">Hostování rozhraní .NET Framework verze 2.0 mají přednost před rozhraní .NET Framework verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="011a7-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="011a7-105">Existují významné rozdíly mezi dvěma sadami rozhraní.</span><span class="sxs-lookup"><span data-stu-id="011a7-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="011a7-106">Kombinování je může způsobit neočekávané chování a nedoporučuje se používat.</span><span class="sxs-lookup"><span data-stu-id="011a7-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="011a7-107">Verze rozhraní .NET Framework 3.0 a 3.5 použít hostování rozhraní .NET Framework verze 2.0 a Nezavádět funkcí hostování.</span><span class="sxs-lookup"><span data-stu-id="011a7-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="011a7-108">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Hostingu rozhraní mají přednost před rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="011a7-108">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="011a7-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="011a7-109">In This Section</span></span>  
 [<span data-ttu-id="011a7-110">Zastaralá rozhraní a třídy typu Coclass pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="011a7-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="011a7-111">Popisuje rozhraní hostování byla zavedená v rozhraní .NET Framework verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="011a7-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="011a7-112">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="011a7-112">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="011a7-113">Popisuje rozhraní hostování byla zavedená v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="011a7-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="011a7-114">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="011a7-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="011a7-115">Popisuje rozhraní hostování počínaje [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="011a7-115">Describes the hosting interfaces introduced in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="011a7-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="011a7-116">Related Sections</span></span>  
 [<span data-ttu-id="011a7-117">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="011a7-117">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="011a7-118">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="011a7-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="011a7-119">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="011a7-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
  
 [<span data-ttu-id="011a7-120">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="011a7-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
  
 [<span data-ttu-id="011a7-121">Hostování</span><span class="sxs-lookup"><span data-stu-id="011a7-121">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
  
 [<span data-ttu-id="011a7-122">Modulu runtime</span><span class="sxs-lookup"><span data-stu-id="011a7-122">Runtime Hosts</span></span>](http://msdn.microsoft.com/en-us/99d9246a-b994-4fe5-985c-8588d1d59998)
