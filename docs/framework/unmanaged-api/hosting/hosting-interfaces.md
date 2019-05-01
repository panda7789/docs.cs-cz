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
ms.openlocfilehash: e330e0d06077d1eef63cf44f31bbcbf7c3431b59
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985540"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="8974a-102">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="8974a-102">Hosting Interfaces</span></span>
<span data-ttu-id="8974a-103">Tato část popisuje rozhraní, která nespravovaných hostitelů můžete použít k integraci common language runtime (CLR) do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="8974a-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="8974a-104">Rozhraní hostování rozhraní .NET Framework verze 2.0 mají přednost před rozhraní .NET Framework verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="8974a-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="8974a-105">Existují významné rozdíly mezi těmito dvěma sadami rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8974a-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="8974a-106">Kombinování je může způsobit neočekávané chování a nedoporučuje se používat.</span><span class="sxs-lookup"><span data-stu-id="8974a-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="8974a-107">Verze rozhraní .NET Framework 3.0 a 3.5 použít rozhraní hostování rozhraní .NET Framework verze 2.0 a ne provádět všechny funkce hostování.</span><span class="sxs-lookup"><span data-stu-id="8974a-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="8974a-108">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Nahrazují rozhraní hostování rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="8974a-108">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="8974a-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8974a-109">In This Section</span></span>  
 [<span data-ttu-id="8974a-110">Zastaralá rozhraní a třídy typu Coclass pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="8974a-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="8974a-111">Popisuje hostitelské rozhraní zavedené v rozhraní .NET Framework verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="8974a-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="8974a-112">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="8974a-112">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="8974a-113">Popisuje hostitelské rozhraní zavedené v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="8974a-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="8974a-114">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="8974a-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="8974a-115">Popisuje hostitelské rozhraní zavedený [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8974a-115">Describes the hosting interfaces introduced in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8974a-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="8974a-116">Related Sections</span></span>  
 [<span data-ttu-id="8974a-117">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="8974a-117">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="8974a-118">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="8974a-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="8974a-119">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="8974a-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
  
 [<span data-ttu-id="8974a-120">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="8974a-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
  
 [<span data-ttu-id="8974a-121">Hostování</span><span class="sxs-lookup"><span data-stu-id="8974a-121">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
  
 <span data-ttu-id="8974a-122">[Hostitelská prostředí modulu runtime](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8974a-122">[Runtime Hosts](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
