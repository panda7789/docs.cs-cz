---
title: Rozhraní hostování
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
ms.openlocfilehash: d1668f52ff305ec36fb520c7828c822537da0d02
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616096"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="bd06d-102">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="bd06d-102">Hosting Interfaces</span></span>
<span data-ttu-id="bd06d-103">Tato část popisuje rozhraní, která nespravované hostitele můžou použít k integraci modulu CLR (Common Language Runtime) do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="bd06d-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="bd06d-104">Rozhraní pro hostování .NET Framework verze 2,0 nahrazují rozhraní .NET Framework verze 1,0 a 1,1.</span><span class="sxs-lookup"><span data-stu-id="bd06d-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="bd06d-105">Existují významné rozdíly mezi dvěma sadami rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bd06d-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="bd06d-106">Jejich kombinování může způsobit neočekávané chování a nedoporučuje se.</span><span class="sxs-lookup"><span data-stu-id="bd06d-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="bd06d-107">.NET Framework verze 3,0 a 3,5 používají rozhraní .NET Framework verze 2,0 pro hostování rozhraní a nezavádí žádné funkce hostování.</span><span class="sxs-lookup"><span data-stu-id="bd06d-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="bd06d-108">Rozhraní pro hostování .NET Framework 4 nahrazují rozhraní .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="bd06d-108">The .NET Framework 4 hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="bd06d-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="bd06d-109">In This Section</span></span>  
 [<span data-ttu-id="bd06d-110">Zastaralá rozhraní a třídy typu Coclass pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="bd06d-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="bd06d-111">Popisuje rozhraní hostování zavedená v .NET Framework verzích 1,0 a 1,1.</span><span class="sxs-lookup"><span data-stu-id="bd06d-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="bd06d-112">Rozhraní hostování CLR</span><span class="sxs-lookup"><span data-stu-id="bd06d-112">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="bd06d-113">Popisuje rozhraní hostování zavedená ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="bd06d-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="bd06d-114">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="bd06d-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="bd06d-115">Popisuje rozhraní hostování zavedená v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="bd06d-115">Describes the hosting interfaces introduced in the .NET Framework 4.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bd06d-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="bd06d-116">Related Sections</span></span>  
 [<span data-ttu-id="bd06d-117">Třídy typu coclass hostování</span><span class="sxs-lookup"><span data-stu-id="bd06d-117">Hosting Coclasses</span></span>](hosting-coclasses.md)  
  
 [<span data-ttu-id="bd06d-118">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="bd06d-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="bd06d-119">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="bd06d-119">Hosting Enumerations</span></span>](hosting-enumerations.md)  
  
 [<span data-ttu-id="bd06d-120">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="bd06d-120">Hosting Structures</span></span>](hosting-structures.md)  
  
 [<span data-ttu-id="bd06d-121">Hostování</span><span class="sxs-lookup"><span data-stu-id="bd06d-121">Hosting</span></span>](index.md)  
  
 <span data-ttu-id="bd06d-122">[Hostitelé modulu runtime](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bd06d-122">[Runtime Hosts](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
