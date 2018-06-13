---
title: Rozhraní hostování
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2bef9e1671b8487a6702cce71106c84a2984317
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436157"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="76f6c-102">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="76f6c-102">Hosting Interfaces</span></span>
<span data-ttu-id="76f6c-103">Tato část popisuje rozhraní, která nespravované hostitelů můžete integrovat common language runtime (CLR) do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="76f6c-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="76f6c-104">Hostování rozhraní .NET Framework verze 2.0 mají přednost před rozhraní .NET Framework verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="76f6c-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="76f6c-105">Existují významné rozdíly mezi dvěma sadami rozhraní.</span><span class="sxs-lookup"><span data-stu-id="76f6c-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="76f6c-106">Kombinování je může způsobit neočekávané chování a nedoporučuje se používat.</span><span class="sxs-lookup"><span data-stu-id="76f6c-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="76f6c-107">Verze rozhraní .NET Framework 3.0 a 3.5 použít hostování rozhraní .NET Framework verze 2.0 a Nezavádět funkcí hostování.</span><span class="sxs-lookup"><span data-stu-id="76f6c-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="76f6c-108">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Hostingu rozhraní mají přednost před rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="76f6c-108">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="76f6c-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="76f6c-109">In This Section</span></span>  
 [<span data-ttu-id="76f6c-110">Zastaralá rozhraní a třídy typu Coclass pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="76f6c-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="76f6c-111">Popisuje rozhraní hostování byla zavedená v rozhraní .NET Framework verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="76f6c-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="76f6c-112">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="76f6c-112">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="76f6c-113">Popisuje rozhraní hostování byla zavedená v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="76f6c-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="76f6c-114">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="76f6c-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="76f6c-115">Popisuje rozhraní hostování počínaje [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="76f6c-115">Describes the hosting interfaces introduced in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="76f6c-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="76f6c-116">Related Sections</span></span>  
 [<span data-ttu-id="76f6c-117">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="76f6c-117">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="76f6c-118">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="76f6c-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="76f6c-119">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="76f6c-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
  
 [<span data-ttu-id="76f6c-120">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="76f6c-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
  
 [<span data-ttu-id="76f6c-121">Hostování</span><span class="sxs-lookup"><span data-stu-id="76f6c-121">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
  
 [<span data-ttu-id="76f6c-122">Modulu runtime</span><span class="sxs-lookup"><span data-stu-id="76f6c-122">Runtime Hosts</span></span>](http://msdn.microsoft.com/library/99d9246a-b994-4fe5-985c-8588d1d59998)
